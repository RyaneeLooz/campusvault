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
-----------------------------------------------------------------------------------------------------
ss -tlnp
State       Recv-Q      Send-Q           Local Address:Port           Peer Address:Port     Process
LISTEN      0           4096             127.0.0.53%lo:53                  0.0.0.0:*
LISTEN      0           4096                127.0.0.54:53                  0.0.0.0:*
---------------------------------------------------------------------------------------------
free -h && nproc
               total        used        free      shared  buff/cache   available
Mem:           3.7Gi       434Mi       3.1Gi        34Mi       248Mi       3.3Gi
Swap:          1.0Gi          0B       1.0Gi

------------------------------
docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
--------------------------------------------------------
docker run --rm alpine cat /etc/os-release

NAME="Alpine Linux"
ID=alpine
VERSION_ID=3.24.2
PRETTY_NAME="Alpine Linux v3.24"
HOME_URL="https://alpinelinux.org/"
BUG_REPORT_URL="https://gitlab.alpinelinux.org/alpine/aports/-/issues"
----------------------------------------------------------------------------
 docker run --rm alpine uname -r

6.18.40.1-microsoft-standard-WSL2
-------------------------------------------------------------------
docker run -d --name web2 -p 127.0.0.1:8083:80 nginx:stable

62a24dc2151da64a54a93fce3bbb3831e6acdd29a67ce057de8d84a8f0a424e5
-------------------------------------------------------------------
 docker ps

CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                    NAMES
62a24dc2151d   nginx:stable   "/docker-entrypoint.…"   2 minutes ago   Up 2 minutes   127.0.0.1:8083->80/tcp   web2
---------------------------------------------------------------------------------------------------------------------------
curl -I http://localhost:8083

HTTP/1.1 200 OK
Server: nginx/1.30.5
Date: Wed, 14 Oct 2026 23:53:54 GMT
Content-Type: text/html
Content-Length: 896
Last-Modified: Tue, 15 Sep 2026 13:27:58 GMT
Connection: keep-alive
ETag: "6aa947de-380"
Accept-Ranges: bytes
-----------------------------------------------------
docker logs web2

/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2026/10/14 23:48:51 [notice] 1#1: using the "epoll" event method
2026/10/14 23:48:51 [notice] 1#1: nginx/1.30.5
2026/10/14 23:48:51 [notice] 1#1: built by gcc 14.2.0 (Debian 14.2.0-19)
2026/10/14 23:48:51 [notice] 1#1: OS: Linux 6.18.40.1-microsoft-standard-WSL2
2026/10/14 23:48:51 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2026/10/14 23:48:51 [notice] 1#1: start worker processes
2026/10/14 23:48:51 [notice] 1#1: start worker process 29
2026/10/14 23:48:51 [notice] 1#1: start worker process 30
2026/10/14 23:48:51 [notice] 1#1: start worker process 31
2026/10/14 23:48:51 [notice] 1#1: start worker process 32
2026/10/14 23:48:51 [notice] 1#1: start worker process 33
2026/10/14 23:48:51 [notice] 1#1: start worker process 34
2026/10/14 23:48:51 [notice] 1#1: start worker process 35
2026/10/14 23:48:51 [notice] 1#1: start worker process 36
172.17.0.1 - - [14/Oct/2026:23:53:54 +0000] "HEAD / HTTP/1.1" 200 0 "-" "curl/8.18.0" "-"
----------------------------------------------------------------------------------------------
docker stop web2 && docker rm web2

web2
web2
------------------------------------------------------------------------------------------------------------
docker images
                                                                                    i Info →   U  In Use
IMAGE                ID             DISK USAGE   CONTENT SIZE   EXTRA
alpine:latest        294b683cb724         13MB         3.94MB
hello-world:latest   11a3eb1597e8       25.9kB         9.49kB    U
nginx:stable         9bf97bd7714f        242MB         66.5MB
----------------------------------------------------------------------------------------------

