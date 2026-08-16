Yes — the clean way on Linux now is to install **Swift via Swiftly**, because Swift.org’s Linux install page recommends Swiftly as the installer/manager for Swift toolchains. Swift.org also provides Swift SDK bundles for Android cross-compilation on Linux, so you can keep one Linux host for Swift, server-side Swift, and Android-targeted Swift SDK work.[1][2]

## Install script

Use this Bash script on Ubuntu/Debian-based Linux to install base dependencies, install Swiftly, initialize it, install the latest stable Swift, and add optional helpers for Android and LLDB-based debugging.[3][1]

```markdown
#!/usr/bin/env bash
set -Eeuo pipefail

log()  { printf '\n\033[1;32m[+]\033[0m %s\n' "$*"; }
warn() { printf '\n\033[1;33m[!]\033[0m %s\n' "$*"; }
err()  { printf '\n\033[1;31m[x]\033[0m %s\n' "$*" >&2; }

trap 'err "Failed at line $LINENO"' ERR

SWIFTLY_VERSION="${SWIFTLY_VERSION:-1.1.1}"
SWIFT_VERSION="${SWIFT_VERSION:-latest}"
INSTALL_ANDROID_SDK="${INSTALL_ANDROID_SDK:-0}"
ANDROID_SDK_BUNDLE="${ANDROID_SDK_BUNDLE:-release/6.4.x}"
ANDROID_SDK_API="${ANDROID_SDK_API:-0.1}"
ANDROID_SDK_ARCHIVE="${ANDROID_SDK_ARCHIVE:-swift-android-sdk-0.1.artifactbundle.tar.gz}"
SWIFTLY_HOME_DIR="${SWIFTLY_HOME_DIR:-$HOME/.local/share/swiftly}"
SWIFTLY_BIN_DIR="${SWIFTLY_BIN_DIR:-$HOME/.local/bin}"

require_cmd() {
  command -v "$1" >/dev/null 2>&1 || {
    err "Missing required command: $1"
    exit 1
  }
}

detect_pkg_mgr() {
  if command -v apt-get >/dev/null 2>&1; then
    echo apt
  elif command -v dnf >/dev/null 2>&1; then
    echo dnf
  elif command -v yum >/dev/null 2>&1; then
    echo yum
  elif command -v zypper >/dev/null 2>&1; then
    echo zypper
  else
    echo unknown
  fi
}

install_base_packages() {
  local pm
  pm="$(detect_pkg_mgr)"

  case "$pm" in
    apt)
      log "Installing base packages with apt"
      sudo apt-get update
      sudo apt-get install -y \
        curl ca-certificates gnupg xz-utils tar gzip git unzip zip \
        clang lldb libicu-dev libcurl4-openssl-dev libssl-dev libsqlite3-dev \
        libpython3-dev pkg-config tzdata
      ;;
    dnf)
      log "Installing base packages with dnf"
      sudo dnf install -y \
        curl ca-certificates gnupg2 xz tar gzip git unzip zip \
        clang lldb libicu libcurl-devel openssl-devel sqlite-devel \
        python3-devel pkgconf-pkg-config tzdata
      ;;
    yum)
      log "Installing base packages with yum"
      sudo yum install -y \
        curl ca-certificates gnupg2 xz tar gzip git unzip zip \
        clang lldb libicu libcurl-devel openssl-devel sqlite-devel \
        python3-devel pkgconfig tzdata
      ;;
    zypper)
      log "Installing base packages with zypper"
      sudo zypper install -y \
        curl ca-certificates gpg2 xz tar gzip git unzip zip \
        clang lldb libicu-devel libcurl-devel libopenssl-devel sqlite3-devel \
        python3-devel pkg-config timezone
      ;;
    *)
      warn "Unsupported package manager; install curl, tar, clang, lldb, libicu, libcurl, openssl, sqlite, python3 dev headers manually"
      ;;
  esac
}

install_swiftly() {
  local arch tarball sig
  arch="$(uname -m)"
  tarball="swiftly-${SWIFTLY_VERSION}-${arch}.tar.gz"
  sig="${tarball}.sig"

  log "Downloading Swiftly ${SWIFTLY_VERSION} for ${arch}"
  curl -fLO "https://download.swift.org/swiftly/linux/${tarball}"

  if command -v gpg >/dev/null 2>&1; then
    log "Verifying Swiftly archive signature"
    curl -fsSL https://www.swift.org/keys/all-keys.asc | gpg --import -
    curl -fLO "https://download.swift.org/swiftly/linux/${sig}"
    gpg --verify "${sig}" "${tarball}"
  else
    warn "gpg not installed, skipping signature verification"
  fi

  log "Extracting Swiftly"
  tar -zxf "${tarball}"
}

init_swiftly() {
  log "Initializing Swiftly"
  export SWIFTLY_HOME_DIR SWIFTLY_BIN_DIR
  ./swiftly init --assume-yes

  local env_sh="${SWIFTLY_HOME_DIR}/env.sh"
  if [[ -f "${env_sh}" ]]; then
    # shellcheck disable=SC1090
    . "${env_sh}"
    hash -r || true
  else
    err "Swiftly env file not found at ${env_sh}"
    exit 1
  fi
}

install_swift_toolchain() {
  require_cmd swiftly
  log "Installing Swift toolchain: ${SWIFT_VERSION}"
  swiftly install --use "${SWIFT_VERSION}"
  hash -r || true
  swift --version
  swiftly --version
}

install_vscode_helper() {
  if command -v code >/dev/null 2>&1; then
    log "VS Code detected; you can install the official Swift extension from the editor"
  else
    warn "VS Code not found; skipping editor integration"
  fi
}

install_android_sdk_bundle() {
  local base_url url
  base_url="https://download.swift.org/development/android-sdk/${ANDROID_SDK_BUNDLE}"
  url="${base_url}/${ANDROID_SDK_ARCHIVE}"

  log "Installing Swift Android SDK bundle"
  mkdir -p "$HOME/.swift-android-sdk"
  cd "$HOME/.swift-android-sdk"
  curl -fLO "$url"

  if swift sdk install "$ANDROID_SDK_ARCHIVE" 2>/dev/null; then
    log "Android Swift SDK installed with swift sdk install"
  else
    warn "swift sdk install failed; your Swift release may require a different Android SDK bundle version"
    warn "Check Swift.org Android SDK bundle page for the matching bundle"
  fi
}

create_test_project() {
  local dir="${HOME}/swift-linux-smoke-test"
  log "Creating smoke test project at ${dir}"
  rm -rf "${dir}"
  mkdir -p "${dir}"
  cd "${dir}"
  swift package init --type executable
  swift build
  swift run
}

post_notes() {
  cat <<EOF

Done.

Current tools:
  swift   : $(command -v swift || echo not-found)
  swiftly : $(command -v swiftly || echo not-found)
  lldb    : $(command -v lldb || echo not-found)

Useful commands:
  source "${SWIFTLY_HOME_DIR}/env.sh"
  swiftly list
  swiftly install --use 5.10
  swiftly install --use main-snapshot
  swiftly self-update
  swift --version
  lldb --version

iOS note:
  Swift on Linux does not build or debug native iOS apps directly. Native iOS app build/debug still requires Xcode on macOS, while Linux is useful for Swift language work, SwiftPM packages, servers, tooling, and some cross-compilation SDK flows.[page:1]

Android note:
  Swift.org provides Android SDK bundles for cross-compilation on Linux, but bundle/version matching matters between your installed Swift toolchain and the Android SDK artifact bundle.[page:1]
EOF
}

main() {
  install_base_packages
  install_swiftly
  init_swiftly
  install_swift_toolchain
  install_vscode_helper

  if [[ "${INSTALL_ANDROID_SDK}" == "1" ]]; then
    install_android_sdk_bundle
  else
    warn "Skipping Android SDK bundle install. Set INSTALL_ANDROID_SDK=1 to enable."
  fi

  create_test_project
  post_notes
}

main "$@"

```

## What it does

Swiftly’s Linux flow is: download the Swiftly archive, extract it, run `./swiftly init`, then source the generated `env.sh` so `swift` and `swiftly` are on your PATH. After that, you can install stable releases such as `latest` or a specific version, and you can also install snapshot toolchains like `main-snapshot`.[1][3]

For example, these are the core official commands from Swift.org:[3][1]

```markdown
curl -O https://download.swift.org/swiftly/linux/swiftly-$(uname -m).tar.gz
tar zxf swiftly-$(uname -m).tar.gz
./swiftly init --quiet-shell-followup
. "${SWIFTLY_HOME_DIR:-$HOME/.local/share/swiftly}/env.sh"
hash -r
```

## Platform notes

For **Linux Swift** development, this setup is correct and current because Swift.org says Swiftly manages Swift installs, updates, and version switching on Linux. For **Android**, Swift.org exposes separate Android SDK bundles under the Linux install section, which is the supported path for Swift cross-compilation from Linux rather than treating Android as a normal host toolchain.[1][3]

For **iOS**, Linux is not a replacement for Xcode/macOS, because Swift.org’s Linux docs cover Linux-hosted Swift and SDK bundles like Android, WebAssembly, and Static Linux, not native iOS app building/debugging on Linux. In practice, Linux is great for Swift packages, shared core logic, server code, CLI tools, and some cross-platform workflows, but native iOS app debug remains a macOS/Xcode job.[1]

## Recommended usage

Run the script as `bash install-swift-linux.sh`, then open a new shell or source Swiftly’s environment file so the PATH is active in your current session. If you want Android bundle installation too, run `INSTALL_ANDROID_SDK=1 bash install-swift-linux.sh`, and if you want a specific Swift release, run `SWIFT_VERSION=5.10 bash install-swift-linux.sh`.[3][1]

Would you like me to turn this into a more complete distro-aware installer with Fedora/Arch handling, Android SDK/NDK setup, and optional VS Code + SourceKit-LSP provisioning?

Sources
[1] GitHub - swiftlang/swiftly: A Swift toolchain installer and ... https://github.com/swiftlang/swiftly
[2] Install Swift - Linux | Swift.org https://www.swift.org/install/linux/
[3] Install Swift | Swift.org https://swiftlang.github.io/swiftly/
[4] Getting Started with Swiftly on Linux https://www.swift.org/install/linux/swiftly/
[5] Swift on Linux CI/CD using swiftly https://www.polpiella.dev/setting-up-swift-on-linux-ci-cd-using-swiftly/
[6] GitHub ActionsでSwiftlyを用いて最新のSwiftをインストール ... https://zenn.dev/nextbeat/articles/02193ca62afa1c
[7] swiftlang.github.io https://swiftlang.github.io/swiftly/swiftly-install.sh
[8] swiftly/DESIGN.md at main · swiftlang/swiftly https://github.com/swiftlang/swiftly/blob/main/DESIGN.md
[9] swift linux环境配置 https://blog.csdn.net/qq_39818303/article/details/140669327
[10] Swift(toolchain)のインストール https://zenn.dev/zunda_pixel/articles/f6f43a5006accc
[11] Releases · swiftlang/swiftly https://github.com/swiftlang/swiftly/releases
[12] Introducing swiftly 1.0 https://www.swift.org/blog/introducing-swiftly_10/
[13] Install Swift | Swift.org https://www.swift.org/install/linux/ubuntu/20_04/
[14] Installation | Swift61A https://meqtmac.github.io/Swift61A/docs/Install.html
[15] Getting Started with Swift on Android https://fuchsia.googlesource.com/third_party/swift/+/23ab6f9e838f7bef0f149adb744933309d88ffd5/docs/Android.md
