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
```