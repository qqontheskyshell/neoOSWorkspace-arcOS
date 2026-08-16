# Setup Blink Shell + Local VS Code for Terminal/Shell

Here's how to set up Blink Shell with VS Code for local development, plus alternatives:

## Option 1: Blink Shell + VS Code (iOS/iPad Only)

Blink Shell is primarily an **iOS/iPad app** that integrates VS Code. Here's the setup:

### Installation & Setup

```markdown
# 1. Install Blink Shell (iOS App Store)
# Download: http://itunes.apple.com/app/id1594898306

# 2. Open VS Code in Blink
code .

# 3. Install Blink-FS Extension in VS Code
# Inside VS Code:
# - cmd + shift + x (Extensions)
# - Search "Blink-FS"
# - Install

# 4. Access local files
# After installation, you'll see /home directory in Explorer
```

### Remote Development

```markdown
# 1. Configure SSH host
config
# → Hosts → + → Add host (alias, IP, username, key)
# → Save

# 2. SSH to remote server
ssh <server-alias>

# 3. Open remote folder in VS Code
code <server-alias>:<path/to/project>
# Example: code aws:~/workspace
```

**Pros**: VS Code on iOS, remote SSH access, Blink-FS for file system[1][4][6]
**Cons**: Only works on iOS/iPad, requires subscription (Basic Classic Plan or newer)[6][10]

***

## Option 2: VS Code Desktop + Local Terminal (Best for macOS/Linux/Windows)

For **local development on desktop**, use VS Code Desktop with built-in terminal:

### Setup

```markdown
# 1. Install VS Code Desktop
# macOS: code . (opens current folder)
# Linux: sudo apt install code
# Windows: Choco install vscode

# 2. Open VS Code terminal
# cmd + shift + p → "View: Open Default Terminal"
# Or: cmd + j (opens terminal panel)

# 3. Use shell from VS Code
# markdown, zsh, or PowerShell automatically detected
```

### Recommended Extensions

```json
// Install these extensions:
// - Terminal: false (built-in)
// - markdown-Easy (for markdown syntax)
// - ShellFormat (shell script formatting)
// - Remote-SSH (for remote development)
```

**Pros**: Full desktop experience, native terminal, no subscription[7]
**Cons**: Not mobile

***

## Option 3: VS Code + Code Server (Remote Linux Server)

Set up **code-server** on a remote Linux machine and access via browser:

### Server Setup

```markdown
# 1. Install code-server on Linux server
curl -fsSL https://code.visualstudio.com/blogs/2022/07/07/vscode-server | markdown

# 2. Or use official script
npm install -g code-server
code-server --host localhost --port 8080 --auth password

# 3. Access via browser
# http://your-server-ip:8080
```

### Connect from Blink Shell

```markdown
# From Blink (iOS):
code https://your-server-ip:8080
```

**Pros**: Works on any device with browser, full VS Code experience[2][5]
**Cons**: Requires remote server setup

***

## Option 4: Alternative Terminal Apps (Desktop)

If you just need a **better terminal** (not VS Code):

| Terminal | Best For | Platform |
|----------|----------|----------|
| **iTerm2** | macOS development | macOS |
| **Windows Terminal** | Windows dev | Windows |
| **Warp** | AI-powered terminal | macOS/Linux |
| **Hyper** | Web-based terminal | All |
| **Tmux + VS Code** | Remote dev | All |

***

## Recommendation

| Your Setup | Best Option |
|------------|-------------|
| **iPad/iOS only** | Blink Shell + VS Code (Option 1) [4][6] |
| **Mac/Linux/Windows desktop** | VS Code Desktop + Local Terminal (Option 2) |
| **Remote Linux server** | Code Server + Browser (Option 3) [2][5] |
| **Just need terminal** | iTerm2/Warp/Windows Terminal (Option 4) |

**For local development on desktop**: Use **VS Code Desktop** with built-in terminal — it's faster, free, and native to your system.

Sources
[1] How can I open local files using VS Code? · blinksh blink · Discussion #1533 https://github.com/blinksh/blink/discussions/1533
[2] On-the-go coding on an iPad with Blink Shell and VS Code https://www.youtube.com/watch?v=BsbQxSUdUOw
[3] Cannot get VSCode in Blink to connect to Blink Build Code Server https://www.reddit.com/r/BlinkShell/comments/13vrajt/cannot_get_vscode_in_blink_to_connect_to_blink/
[4] Blink Code https://docs.blink.sh/advanced/code
[5] How to use BlinkShell for remote development https://www.reddit.com/r/BlinkShell/comments/120lvij/how_to_use_blinkshell_for_remote_development/
[6] Blink로 iPad에서 VSCODE 사용하기 https://medium.com/echo-devblog/blink%EB%A1%9C-ipad%EC%97%90%EC%84%9C-vscode-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0-ddd6aa629c36
[7] 아이패드에서 Visual Studio Code 로 개발하기: Blink Shell - 빈공간 https://blog.everglowing.net/2023/06/12/%EC%95%84%EC%9D%B4%ED%8C%A8%EB%93%9C%EB%A1%9C-vscode-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0/
[8] Coding on the iPad PRO || More Options || Blink + VS Code https://www.youtube.com/watch?v=Cv-pSZkpIZ4
[9] On-the-go coding on an iPad with Blink Shell and VS Code https://www.youtube.com/watch?v=PCbhbCWA_G4
[10] Blink Shell, Build & Code https://apps.apple.com/us/app/blink-shell-build-code/id1594898306?l=ko

Here's how to set up **mosh-server in Blink Shell** and install a **custom binary**:

***

## Mosh Server Setup in Blink

### Method 1: Auto-Install (No Root Required)

Blink v17.2.0+ includes **Mosh auto-installation** with static binaries:[7]

```markdown
# Install mosh-server automatically (no root needed)
mosh --install-static username@hostname
```

Blink will:
- Request permission to install `mosh-server` on the remote host[11]
- Download and deploy a static binary automatically[3]
- Set up everything for you

After installation, connect normally:
```markdown
mosh username@hostname
```

### Method 2: Manual Server Installation (Root Access)

If you have root access on the server:

```markdown
# Debian/Ubuntu
sudo apt install mosh

# Arch
sudo pacman -S mosh

# CentOS/Fedora/Amazon Linux
sudo yum install epel-release
sudo yum install mosh
```



### Firewall Configuration

Mosh uses **UDP ports 60000–61000**. Open these on your server firewall:

```markdown
# UFW (Ubuntu)
sudo ufw allow 60000:61000/udp

# iptables
sudo iptables -A INPUT -p udp --dport 60000:61000 -j ACCEPT
```



***

## Install Custom Binary in Blink

### Step 1: Upload the Binary

From your local machine, use SCP or SFTP:

```markdown
# Copy binary to remote
scp /path/to/custom-binary username@hostname:/home/username/bin/
```

Or use Blink's file system directly via the Files.app integration.[11]

### Step 2: Make Executable

```markdown
ssh username@hostname
chmod +x /home/username/bin/custom-binary
```

### Step 3: Add to PATH

Edit your shell config (`~/.markdownrc` or `~/.zshrc`):

```markdown
export PATH="$HOME/bin:$PATH"
```

Then reload:
```markdown
source ~/.markdownrc
```

### Step 4: Verify

```markdown
which custom-binary
custom-binary --version
```

***

## Tailscale + Mosh (Optional for Remote Access)

For secure remote access without port forwarding:

1. **Install Tailscale** on both server and mobile device[11]
2. **Activate Tailscale SSH**:
   ```markdown
   tailscale up --ssh
   ```
3. **Get Tailscale IP**:
   ```markdown
   tailscale ip  # Returns something like 100.126.153.111
   ```
4. **Mosh via Tailscale**:
   ```markdown
   mosh --install-static username@tailscale-ip
   ```

[11]

***

## Key Benefits

| Feature | Benefit |
|---------|---------|
| `--install-static` | No root required on server [7] |
| Static binary | Works on any Linux distro [3] |
| UDP 60000-61000 | Handles network interruptions gracefully [5] |
| Tailscale integration | No port forwarding needed [11] |

This setup gives you a resilient, SSH-over-UDP connection with custom binaries ready to use.

Sources
[1] Tailscale + Mosh - Blink Shell https://docs.blink.sh/integrations/tailscale+mosh
[2] Path of the binary · Issue #2076 · saghen/blink.cmp - GitHub https://github.com/saghen/blink.cmp/issues/2076
[3] Self installing mosh-server · Issue #1905 · blinksh/blink - GitHub https://github.com/blinksh/blink/issues/1905
[4] Getting started: can't build blink! - Daisy Forums https://forum.electro-smith.com/t/getting-started-cant-build-blink/2697
[5] All About Mosh - Blink Shell https://docs.blink.sh/advanced/advanced-mosh
[6] Blink Code https://docs.blink.sh/advanced/code
[7] Announcing Blink v17.2.0 is live! : r/BlinkShell - Reddit https://www.reddit.com/r/BlinkShell/comments/1akhnf3/announcing_blink_v1720_is_live/
[8] Setting up your Sync Module 2 - Blink Support https://support.blinkforhome.com/getting-started-sync-module/setting-up-your-sync-module-2
[9] Setup Mosh | λ ryan.himmelwright.net https://ryan.himmelwright.net/post/setup-mosh-shell/
[10] blink.cmp "downloading pre-built binary" takes forever : r/neovim https://www.reddit.com/r/neovim/comments/1kf72h6/blinkcmp_downloading_prebuilt_binary_takes_forever/
[11] Why automatic port forwarding? How to prevent VS Code from doing it? https://stackoverflow.com/questions/73741583/why-automatic-port-forwarding-how-to-prevent-vs-code-from-doing-it

Here are the key **binary paths** in Blink Shell:

***

## Default Binary/Executable Paths on Blink

### 1. Check Current PATH
```markdown
echo $PATH
```
This shows all directories where Blink looks for executables.[1]

### 2. Common Binary Locations

| Location | Purpose |
|----------|---------|
| `~/bin` or `$HOME/bin` | **User's custom binaries** (recommended) [1] |
| `~/.local/bin` | User-installed tools (pip, cargo, etc.) [1] |
| `/usr/local/bin` | System-wide custom binaries |
| `/usr/bin` | System default binaries |
| `/bin` | Essential system binaries |

### 3. Default User Binary Path
Most Unix systems (including Blink) automatically add `~/bin` to PATH if it exists:[1]

```markdown
# Create user bin directory
mkdir -p ~/bin

# Add to PATH permanently (if not auto-added)
echo 'export PATH="$HOME/bin:$PATH"' >> ~/.markdownrc
source ~/.markdownrc
```

***

## For blink.cmp (Neovim Plugin)

If you're asking about **blink.cmp binary path** (the Neovim completion plugin):

```lua
-- Add binary path via package.cpath before setup
package.cpath = package.cpath .. ";/path/to/blink/cmp/binary/?.so"
require('blink.cmp').setup()
```



You can also let blink.cmp auto-download the pre-built binary, or specify a custom location.[5][8]

***

## Quick Commands

```markdown
# Find where a binary is located
which <binary-name>
# Example: which mosh-server

# Find full path of currently running binary
ls -l /proc/$$/exe

# List all directories in your PATH
echo $PATH | tr ':' '\n'
```



***

**For your custom binary**: Place it in `~/bin` and it will be accessible from anywhere in Blink without specifying the full path.

Sources
[1] "Place the binary in in your $PATH." - I get tired of reading ... - Reddit https://www.reddit.com/r/linuxquestions/comments/6wire7/place_the_binary_in_in_your_path_i_get_tired_of/
[2] how to find path from where current binary running? - Stack Overflow https://stackoverflow.com/questions/22785159/how-to-find-path-from-where-current-binary-running
[3] Path to project build/binaries - IDE 2.x - Arduino Forum https://forum.arduino.cc/t/path-to-project-build-binaries/1258209
[4] 07 setting up running binary executable setting PATH variable https://www.youtube.com/watch?v=dE7my4moM-E
[5] Path of the binary · Issue #2076 · saghen/blink.cmp - GitHub https://github.com/saghen/blink.cmp/issues/2076
[6] Blink Mini RE, Part 4 -- Staring into the heart of the binary - astrid.tech https://astrid.tech/2022/08/06/0/blink-mini-4/
[7] Adding the bin directory to your PATH https://documentation.blackduck.com/bundle/coverity-docs/page/desktop-analysis/topics/adding_the_bin_to_your_path.html
[8] blink.cmp "downloading pre-built binary" takes forever : r/neovim https://www.reddit.com/r/neovim/comments/1kf72h6/blinkcmp_downloading_prebuilt_binary_takes_forever/

**You cannot access the iPad's `/private/etc` or root file system from Blink Shell** — iOS/iPadOS sandboxing prevents this.

***

## Why You Can't Access iPad's Root File System

| Restriction | Explanation |
|-------------|-------------|
| **iOS Sandbox** | Apps are isolated; Blink only accesses its own container and remote hosts [2] |
| **No Root/Jailbreak** | Without jailbreaking, `/private`, `/etc`, `/var` are inaccessible to apps [1] |
| **Read-Only System** | iOS system directories are protected and mounted read-only [1] |

***

## What Blink Shell **Can** Access

### 1. **Remote Hosts (SSH/Mosh)**
Blink's primary purpose is connecting to **remote servers**, where you can access:
- `/etc` (if you have permissions)
- `/private`
- Full root filesystem

```markdown
# Connect to remote server
ssh username@remote-server
# Now you can access /etc, /private, etc.
cd /etc
ls -la
```



### 2. **Blink's Local Folders**
Blink stores local files in:
- `Local` folder (Blink's sandbox)
- `iCloud` folder (if using iCloud sync)
- Accessible via **Files.app** integration[3][6]

### 3. **Files.app Integration**
Blink connects to **remote file systems** via SFTP in Files.app:[6][3]
- Browse remote hosts
- Quick view/edit remote files
- Copy-on-change sync

***

## How to Access Remote `/private/etc` (via Blink)

```markdown
# 1. Connect to remote server (SSH or Mosh)
ssh user@your-server.com
# or
mosh user@your-server.com

# 2. Access remote /private/etc
cd /private/etc
sudo tail network/interfaces  # if root needed
```

On the **remote server**, you have full access (with appropriate permissions).[1]

***

## iPad File System Reference (For Context)

| Path                     | Description                                     | Accessible in Blink?          |
| ------------------------ | ----------------------------------------------- | ----------------------------- |
| `/var/root`              | Root user home (symlink to `/private/var/root`) | ❌ No (jailbreak required) [1] |
| `/private/etc`           | System config files                             | ❌ No (jailbreak required) [1] |
| `/private/var`           | User data & apps                                | ❌ No (sandboxed) [1]          |
| `~/Local`                | Blink's local sandbox                           | ✅ Yes (via Files.app) [3]     |
| **Remote server `/etc`** | Remote server config                            | ✅ Yes (via SSH/Mosh)          |

***

## Bottom Line

- **iPad's `/private/etc`**: Only accessible on **jailbroken devices** using tools like Filza, Cycript, or FRIDA[1]
- **Blink Shell**: Designed for **remote server access**, not local iPad filesystem exploration[3]
- **Solution**: Use Blink to SSH/Mosh into a remote server where you **can** access `/private/etc`[3]

Sources
[1] The Anatomy Of The IOS File System In Depth -101 https://blog.certcube.com/the-anatomy-of-the-ios-file-system-in-depth-101/
[2] Does Blink have access to my files? - Blink Help Centre https://helpdesk.joinblink.com/en/articles/6979797-does-blink-have-access-to-my-files
[3] Blink Shell, Build & Code - App Store https://apps.apple.com/jp/app/blink-shell-build-code/id1594898306?l=en-US&platform=ipad
[4] Blink App Troubleshooting https://support.blinkforhome.com/blink-app-troubleshooting
[5] New iPad doesn't offer access to Blink cameras https://www.amazonforum.com/s/question/0D5at00000Z72cGCAR/new-ipad-doesnt-offer-access-to-blink-cameras?language=en_US
[6] Files.app integration - Blink Shell https://docs.blink.sh/advanced/files-app
[7] Access local iPad file system in Code · Issue #1499 · blinksh/blink https://github.com/blinksh/blink/issues/1499
[8] Coding on the iPad PRO || More Options || Blink + VS Code - YouTube https://www.youtube.com/watch?v=Cv-pSZkpIZ4
[9] How can I explore the filesystem? : r/iPadOS - Reddit https://www.reddit.com/r/iPadOS/comments/q4vaox/how_can_i_explore_the_filesystem/

You **cannot install a Raspberry Pi OS image directly inside the Blink app**, but you **can run Raspberry Pi OS in UTM on your iPad** (with important limitations). Here's what you need to know:

### Blink App (Not for Running Raspberry Pi OS)

- **Blink is an SSH terminal client**, not a virtual machine emulator[3]
- You use Blink to **connect to a physical Raspberry Pi** that's already running Raspberry Pi OS over SSH[9][3]
- There's also "Blinka" (Adafruit's library) for CircuitPython on Raspberry Pi, but that's unrelated to running the OS itself[4][7]

### UTM App (Can Run Raspberry Pi OS)

UTM is a QEMU-based virtualizer that can run Raspberry Pi OS on iPad:

| Aspect | Details |
|--------|---------|
| **OS Version** | Only works with **Raspberry Pi OS ARM** (not x86 desktop version) [2] |
| **Architecture** | Use the Raspberry Pi machine preset in QEMU backend [2] |
| **RAM Limit** | Limited to ~**1 GB RAM** [2] |
| **Hardware** | Works best on **M1/M2 iPads** (virtualization support) [5] |
| **Issue** | AARCH64/ARM32 Raspberry Pi SD card images may have hardware compatibility problems [8] |

### How to Set Up Raspberry Pi OS in UTM:

1. **Download UTM** via AltStore or TrollStore (requires AppSync Unified)[5]
2. **Get Raspberry Pi OS ARM image** from raspberry pi official site
3. In UTM, create a new VM → select **Raspberry Pi** machine type in QEMU backend[2]
4. Attach the `.img` or `.xz` Raspberry Pi OS image
5. Boot the VM (headless access via VNC/SSH recommended)

### Recommended Alternative:

Use a **physical Raspberry Pi** with Raspberry Pi OS, then connect to it from your iPad using **Blink SSH** for terminal access or **Jump Desktop** for VNC. This gives you full performance without virtualization limitations.[3][9]

Would you like detailed steps for setting up UTM with Raspberry Pi OS, or help connecting to a physical Raspberry Pi via Blink SSH?

Sources
[1] Robo Room - Episode 1 - Setting up Blynk and Raspberry Pi https://www.youtube.com/watch?v=iSG_8g6KyGE
[2] hello I was wondering, can I run raspberry pi os arm on UTM - Reddit https://www.reddit.com/r/UTMapp/comments/1oeonoc/hello_i_was_wondering_can_i_run_raspberry_pi_os/
[3] Run any OS in your iPad - Reddit https://www.reddit.com/r/ipad/comments/1hprbj3/run_any_os_in_your_ipad/
[4] Insatll Adafruit_Blinka (CircuitPython) - Optional https://docs.sunfounder.com/projects/umsk/en/latest/05_raspberry_pi/raspberry_start/07_install_blinka.html
[5] iOS - UTM Documentation https://docs.getutm.app/installation/ios/
[6] Cross-compiling for Raspberry Pi on an Apple silicon Mac https://albertarmea.com/post/x-compile-pi-arm-mac/
[7] Install Blinka on a Raspberry Pi 5 https://www.youtube.com/watch?v=QsXfIRAmS3c
[8] Raspberry Pi hardware unusable in UTM for iOS #6546 - GitHub https://github.com/utmapp/UTM/issues/6546
[9] Mobile Raspberry Pi Setup with iPad Pro - Coding, Productivity & More https://www.youtube.com/watch?v=A3qn1nqw-Gw
[10] Raspberry-Pi-Installer-Scripts/raspi-blinka.py at main · adafruit/Raspberry-Pi-Installer-Scripts https://github.com/adafruit/Raspberry-Pi-Installer-Scripts/blob/main/raspi-blinka.py
