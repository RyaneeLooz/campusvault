uname -r
6.18.40.1-microsoft-standard-WSL2

cat /etc/os-release
PRETTY_NAME="Ubuntu 26.04.1 LTS"
NAME="Ubuntu"
VERSION_ID="26.04"
VERSION="26.04.1 LTS (Resolute Raccoon)"
VERSION_CODENAME=resolute
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=resolute
LOGO=ubuntu-logo

whoami && id
ryane
uid=1001(ryane) gid=1001(ryane) groups=1001(ryane),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),100(users)

ps aux | head -15
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.1  0.3  24352 15428 ?        Ss   08:47   0:04 /sbin/init
root           2  0.0  0.0   3760  2336 hvc0     Sl+  08:47   0:00 /init
root           3  0.0  0.0   3612  2100 hvc0     S+   08:47   0:00 init-watcher
root           9  0.0  0.0   3760  2108 hvc0     Sl+  08:47   0:00 plan9 --control-socket 7 --log-level 4 --server-fd 8 --pipe-fd 10 --log-truncate
root          52  0.0  0.5  50652 19504 ?        S<s  08:47   0:01 /usr/lib/systemd/systemd-journald
systemd+      90  0.0  0.3  22428 14544 ?        Ss   08:47   0:00 /usr/lib/systemd/systemd-resolved
root          94  0.1  0.3  34712 12088 ?        Ss   08:47   0:04 /usr/lib/systemd/systemd-udevd
root         111  0.0  0.0   2888  2076 ?        Ss   08:47   0:00 /bin/sh /usr/lib/systemd/scripts/chronyd-starter.sh -n -F 1
root         112  0.0  0.0   4472  3200 ?        Ss   08:47   0:00 /usr/sbin/cron -f -P
message+     113  0.0  0.1   8828  5452 ?        Ss   08:47   0:00 @dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
root         119  0.0  0.7  44112 29744 ?        Ss   08:47   0:00 /usr/bin/python3 /usr/bin/networkd-dispatcher --run-startup-triggers
root         155  0.0  0.2  18444  9516 ?        Ss   08:47   0:00 /usr/lib/systemd/systemd-logind
syslog       175  0.0  0.1 220548  6068 ?        Ssl  08:47   0:00 /usr/sbin/rsyslogd -n -iNONE
root         251  0.0  0.8 123476 32752 ?        Ssl  08:47   0:00 /usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdown --wait-for-signal

ss -tlnp
State       Recv-Q      Send-Q           Local Address:Port           Peer Address:Port     Process
LISTEN      0           4096             127.0.0.53%lo:53                  0.0.0.0:*
LISTEN      0           4096                127.0.0.54:53                  0.0.0.0:*

free -h && nproc
               total        used        free      shared  buff/cache   available
Mem:           3.7Gi       434Mi       3.1Gi        34Mi       248Mi       3.3Gi
Swap:          1.0Gi          0B       1.0Gi
8

