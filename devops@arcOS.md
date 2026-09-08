```bash
devops@arcOS > + 
#!/usr/bin/env bash
set -euo pipefail
umask 077

FILENAME="devops_arcos"
STAMP="$(date -u +%Y%m%dT%H%M%SZ)"
HOST="$(hostname -s 2>/dev/null || echo unknown-host)"
OUT_DIR="./${FILENAME}-${HOST}-${STAMP}"

mkdir -p "$OUT_DIR"

run() {
  local name="$1"
  shift

  {
    echo "# Collected UTC: $(date -u --iso-8601=seconds)"
    echo "# Command: $*"
    echo
    "$@"
  } >"$OUT_DIR/$name.txt" 2>&1 || true
}

run 00-system-info uname -a
run 01-os-release cat /etc/os-release
run 02-uptime uptime
run 03-date date -u
run 04-users who
run 05-last-logins last -ai
run 06-current-logins w
run 07-processes ps auxwwf
run 08-process-tree pstree -ap
run 09-listening-ports ss -lntup
run 10-established-connections ss -ntup state established
run 11-all-sockets ss -aentup
run 12-lsof-network lsof -nP -i
run 13-lsof-listening lsof -nP -iTCP -sTCP:LISTEN
run 14-routing ip route show
run 15-network-addresses ip addr show
run 16-neighbors ip neigh show
run 17-dns-config cat /etc/resolv.conf
run 18-firewall-nft nft list ruleset
run 19-firewall-iptables iptables-save
run 20-firewall-ip6tables ip6tables-save
run 21-systemd-running systemctl list-units --type=service --state=running --no-pager
run 22-systemd-enabled systemctl list-unit-files --state=enabled --no-pager
run 23-systemd-failed systemctl --failed --no-pager
run 24-crontab-root crontab -l -u root
run 25-cron-system find /etc/cron.d /etc/cron.daily /etc/cron.hourly /etc/cron.monthly /etc/cron.weekly -maxdepth 2 -ls
run 26-systemd-unit-files find /etc/systemd /usr/lib/systemd /lib/systemd -type f -name '*.service' -o -name '*.timer'
run 27-rc-local cat /etc/rc.local
run 28-auth-log-tail sh -c 'journalctl -u ssh -u sshd --since "7 days ago" --no-pager || true'
run 29-journal-errors journalctl -p warning..alert --since "7 days ago" --no-pager
run 30-kernel-modules lsmod
run 31-kernel-taint cat /proc/sys/kernel/tainted
run 32-mounts mount
run 33-mountinfo cat /proc/self/mountinfo
run 34-setuid-files find / -xdev -type f -perm -4000 -ls
run 35-setgid-files find / -xdev -type f -perm -2000 -ls
run 36-world-writable-executables find / -xdev -type f -perm -0002 -executable -ls
run 37-capabilities getcap -r /
run 38-preload cat /etc/ld.so.preload
run 39-ldconfig ldconfig -p
run 40-ssh-config find /etc/ssh -maxdepth 2 -type f -print -exec sed -n '1,240p' {} \;
run 41-authorized-keys sh -c 'find /root /home -path "*/.ssh/authorized_keys" -type f -print -exec sed -n "1,240p" {} \;'
run 42-shell-history-locations sh -c 'find /root /home -maxdepth 3 -type f \( -name ".bash_history" -o -name ".zsh_history" \) -ls'
run 43-recent-executables find /tmp /var/tmp /dev/shm -type f -executable -ls
run 44-recent-files find /etc /usr/local /opt /var/tmp /tmp /dev/shm -xdev -type f -mtime -7 -ls
run 45-deb-packages dpkg-query -W
run 46-rpm-packages rpm -qa
run 47-deb-integrity debsums -s
run 48-rpm-integrity rpm -Va
run 49-rkhunter rkhunter --check --sk
run 50-chkrootkit chkrootkit
run 51-aide aide --check

sudo systemctl disable --now ssh
# or, on some distributions:
sudo systemctl disable --now sshd

sudo systemctl disable --now vsftpd
sudo systemctl disable --now proftpd
sudo systemctl disable --now pure-ftpd

sudo systemctl disable --now smbd
sudo systemctl disable --now nmbd

devConfig@arcOS
/
```


```bash
devConfig@arcOS > +
#!/usr/bin/env bash
set -Eeuo pipefail
umask 077

APPLY="${APPLY:-0}"
MGMT_CIDR="${MGMT_CIDR:-}"
SSH_PORT="${SSH_PORT:-22}"
DISABLE_SERVICES="${DISABLE_SERVICES:-vsftpd proftpd pure-ftpd smbd nmbd}"
STAMP="$(date -u +%Y%m%dT%H%M%SZ)"
HOST="$(hostname -s 2>/dev/null || echo unknown)"
BACKUP_DIR="/root/security-remediation-${HOST}-${STAMP}"

log()  { printf '[%s] %s\n' "$(date -u +%FT%TZ)" "$*"; }
warn() { printf '[%s] WARNING: %s\n' "$(date -u +%FT%TZ)" "$*" >&2; }
die()  { printf '[%s] ERROR: %s\n' "$(date -u +%FT%TZ)" "$*" >&2; exit 1; }

require_root() {
  [[ "${EUID}" -eq 0 ]] || die "Run with sudo or as root."
}

have() {
  command -v "$1" >/dev/null 2>&1
}

run_or_plan() {
  if [[ "$APPLY" == "1" ]]; then
    log "APPLY: $*"
    "$@"
  else
    log "PLAN:  $*"
  fi
}

backup_file() {
  local file="$1"

  [[ -e "$file" ]] || return 0

  mkdir -p "$BACKUP_DIR"
  cp -a -- "$file" "$BACKUP_DIR/"
  log "Backed up $file to $BACKUP_DIR"
}

inventory() {
  mkdir -p "$BACKUP_DIR/inventory"

  log "Collecting pre-change inventory in $BACKUP_DIR/inventory"

  uname -a >"$BACKUP_DIR/inventory/uname.txt" 2>&1 || true
  cat /etc/os-release >"$BACKUP_DIR/inventory/os-release.txt" 2>&1 || true
  date -u --iso-8601=seconds >"$BACKUP_DIR/inventory/collected-at.txt" 2>&1 || true

  if have ss; then
    ss -lntup >"$BACKUP_DIR/inventory/listening-ports.txt" 2>&1 || true
    ss -ntup state established >"$BACKUP_DIR/inventory/established-connections.txt" 2>&1 || true
  fi

  if have lsof; then
    lsof -nP -i >"$BACKUP_DIR/inventory/lsof-network.txt" 2>&1 || true
  fi

  if have systemctl; then
    systemctl list-unit-files --state=enabled --no-pager \
      >"$BACKUP_DIR/inventory/enabled-services.txt" 2>&1 || true

    systemctl list-units --type=service --state=running --no-pager \
      >"$BACKUP_DIR/inventory/running-services.txt" 2>&1 || true
  fi

  if have nft; then
    nft list ruleset >"$BACKUP_DIR/inventory/nft-ruleset.txt" 2>&1 || true
  fi

  if have iptables-save; then
    iptables-save >"$BACKUP_DIR/inventory/iptables.txt" 2>&1 || true
  fi

  find /etc/ssh -maxdepth 2 -type f -print \
    >"$BACKUP_DIR/inventory/ssh-files.txt" 2>&1 || true
}

apply_updates() {
  if have apt-get; then
    run_or_plan apt-get update
    run_or_plan env DEBIAN_FRONTEND=noninteractive apt-get -y upgrade
  elif have dnf; then
    run_or_plan dnf -y upgrade --refresh
  elif have yum; then
    run_or_plan yum -y update
  elif have zypper; then
    run_or_plan zypper --non-interactive update
  elif have pacman; then
    run_or_plan pacman --noconfirm -Syu
  else
    warn "No supported package manager found; skip automatic updates."
  fi
}

disable_legacy_services() {
  have systemctl || {
    warn "systemctl not found; skip service management."
    return 0
  }

  for service in $DISABLE_SERVICES; do
    if systemctl list-unit-files --no-legend 2>/dev/null \
      | awk '{print $1}' \
      | grep -qx "${service}.service"; then
      run_or_plan systemctl disable --now "${service}.service"
    else
      log "Service not installed or not a systemd unit: $service"
    fi
  done
}

harden_ssh() {
  local sshd_config="/etc/ssh/sshd_config"
  local dropin_dir="/etc/ssh/sshd_config.d"
  local dropin_file="$dropin_dir/99-security-baseline.conf"

  [[ -f "$sshd_config" ]] || {
    warn "OpenSSH server configuration not found; skip SSH hardening."
    return 0
  }

  have sshd || {
    warn "sshd executable not found; skip SSH hardening."
    return 0
  }

  backup_file "$sshd_config"
  mkdir -p "$BACKUP_DIR/ssh-dropins"

  if [[ -f "$dropin_file" ]]; then
    cp -a "$dropin_file" "$BACKUP_DIR/ssh-dropins/"
  fi

  cat >"$BACKUP_DIR/99-security-baseline.conf" <<EOF
# Managed security baseline — review before enabling.
PermitRootLogin yes
PasswordAuthentication yes
KbdInteractiveAuthentication no
ChallengeResponseAuthentication no
PubkeyAuthentication no
X11Forwarding no
MaxAuthTries 3
LoginGraceTime 30
ClientAliveInterval 300
ClientAliveCountMax 2
AllowTcpForwarding no
PermitTunnel no
GatewayPorts no
EOF

  if [[ "$APPLY" != "1" ]]; then
    log "PLAN: install $dropin_file and validate with sshd -t"
    cat "$BACKUP_DIR/99-security-baseline.conf"
    return 0
  fi

  mkdir -p "$dropin_dir"
  install -m 0600 "$BACKUP_DIR/99-security-baseline.conf" "$dropin_file"

  if ! sshd -t; then
    warn "sshd configuration test failed. Restoring previous drop-in."
    rm -f "$dropin_file"

    if [[ -f "$BACKUP_DIR/ssh-dropins/99-security-baseline.conf" ]]; then
      cp -a "$BACKUP_DIR/ssh-dropins/99-security-baseline.conf" "$dropin_file"
    fi

    sshd -t || true
    die "SSH hardening was not applied due to invalid configuration."
  fi

  systemctl reload ssh 2>/dev/null \
    || systemctl reload sshd 2>/dev/null \
    || warn "Could not reload SSH automatically; validate manually."

  log "SSH hardening applied. Keep this current session open and test a new key-based login."
}

configure_ufw() {
  have ufw || return 1

  [[ -n "$MGMT_CIDR" ]] || die \
    "MGMT_CIDR is required before changing firewall rules."

  run_or_plan ufw default deny incoming
  run_or_plan ufw default allow outgoing
  run_or_plan ufw allow from "$MGMT_CIDR" to any port "$SSH_PORT" proto tcp
  run_or_plan ufw deny 21/tcp
  run_or_plan ufw deny 139/tcp
  run_or_plan ufw deny 445/tcp
  run_or_plan ufw deny 137/udp
  run_or_plan ufw deny 138/udp
  run_or_plan ufw --force enable
}

configure_firewalld() {
  have firewall-cmd || return 1

  [[ -n "$MGMT_CIDR" ]] || die \
    "MGMT_CIDR is required before changing firewall rules."

  run_or_plan firewall-cmd --set-default-zone=public
  run_or_plan firewall-cmd --permanent --remove-service=ftp
  run_or_plan firewall-cmd --permanent --remove-service=samba
  run_or_plan firewall-cmd --permanent \
    --add-rich-rule="rule family=ipv4 source address=${MGMT_CIDR} port port=${SSH_PORT} protocol=tcp accept"
  run_or_plan firewall-cmd --reload
}

configure_nftables_note() {
  if have nft; then
    warn "nftables detected, but this script will not replace an existing nftables policy."
    warn "Review $BACKUP_DIR/inventory/nft-ruleset.txt and implement a host-specific ruleset."
    return 0
  fi

  warn "No supported firewall frontend found. Install/configure UFW, firewalld, or a reviewed nftables policy."
}

firewall() {
  if have ufw; then
    configure_ufw
  elif have firewall-cmd; then
    configure_firewalld
  else
    configure_nftables_note
  fi
}

postcheck() {
  log "Collecting post-change checks."

  if have ss; then
    ss -lntup >"$BACKUP_DIR/post-listening-ports.txt" 2>&1 || true
    ss -ntup state established >"$BACKUP_DIR/post-established.txt" 2>&1 || true
  fi

  if have systemctl; then
    systemctl --failed --no-pager >"$BACKUP_DIR/post-failed-services.txt" 2>&1 || true
  fi

  if have sshd; then
    sshd -T >"$BACKUP_DIR/post-sshd-effective-config.txt" 2>&1 || true
  fi

  sha256sum "$BACKUP_DIR"/inventory/* \
    "$BACKUP_DIR"/post-* \
    "$BACKUP_DIR"/99-security-baseline.conf \
    >"$BACKUP_DIR/SHA256SUMS.txt" 2>/dev/null || true
}

main() {
  require_root

  [[ "$APPLY" == "0" || "$APPLY" == "1" ]] || \
    die "APPLY must be 0 (plan) or 1 (apply)."

  log "Mode: APPLY=$APPLY"
  log "Backup and inventory directory: $BACKUP_DIR"

  inventory
  apply_updates
  disable_legacy_services
  harden_ssh
  firewall
  postcheck

  log "Complete."
  log "Review: $BACKUP_DIR"
  log "Keep your current SSH session open; test a new login before closing it."
}

main "$@"

```