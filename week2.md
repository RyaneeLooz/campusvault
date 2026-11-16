docker exec todo ps aux
PID   USER     TIME  COMMAND
    1 root      0:00 node src/index.js
   18 root      0:00 ps aux
----------------------------------------
 docker exec todo hostname
b3ce1ecc88e3
---------------------------
docker exec todo cat /etc/os-release
NAME="Alpine Linux"
ID=alpine
VERSION_ID=3.24.3
PRETTY_NAME="Alpine Linux v3.24"
HOME_URL="https://alpinelinux.org/"
BUG_REPORT_URL="https://gitlab.alpinelinux.org/alpine/aports/-/issues"
------------------------------------------------------------------------
docker inspect -f '{{.State.Pid}}' todo
747
--------------------------------------------------------------------
docker run --rm --pid=host alpine ps aux | grep "node src/index.js"
  747 root      0:00 node src/index.js
-----------------------------------------------------------------------
docker inspect -f '{{.NetworkSettings.Networks.bridge.IPAddress}}' todo
172.17.0.2
-------------------------------------------------------------------------
docker history getting-started
IMAGE          CREATED             CREATED BY                                      SIZE      COMMENT
15216ca1e8e3   About an hour ago   CMD ["node" "src/index.js"]                     0B        buildkit.dockerfile.v0
<missing>      About an hour ago   EXPOSE [3000/tcp]                               0B        buildkit.dockerfile.v0
<missing>      About an hour ago   RUN /bin/sh -c yarn install --production # b…   59.3MB    buildkit.dockerfile.v0
<missing>      2 hours ago         COPY . . # buildkit                             4.73MB    buildkit.dockerfile.v0
<missing>      2 hours ago         WORKDIR /app                                    8.19kB    buildkit.dockerfile.v0
<missing>      4 days ago          CMD ["node"]                                    0B        buildkit.dockerfile.v0
<missing>      4 days ago          ENTRYPOINT ["docker-entrypoint.sh"]             0B        buildkit.dockerfile.v0
<missing>      4 days ago          COPY docker-entrypoint.sh /usr/local/bin/ # …   20.5kB    buildkit.dockerfile.v0
<missing>      4 days ago          RUN /bin/sh -c apk add --no-cache --virtual …   5.48MB    buildkit.dockerfile.v0
<missing>      4 days ago          ENV YARN_VERSION=1.22.22                        0B        buildkit.dockerfile.v0
<missing>      4 days ago          RUN /bin/sh -c addgroup -g 1000 node     && …   163MB     buildkit.dockerfile.v0
<missing>      4 days ago          ENV NODE_VERSION=22.23.4                        0B        buildkit.dockerfile.v0
<missing>      4 days ago          CMD ["/bin/sh"]                                 0B        buildkit.dockerfile.v0
<missing>      4 days ago          ADD alpine-minirootfs-3.24.3-x86_64.tar.gz /…   9.08MB    buildkit.dockerfile.v0
-------------------------------------------------------------------------------------------------------------------------
docker run --name memtest --memory=64m --memory-swap=64m python:3.12-alpine python -c "x = bytearray(200 * 1024 * 1024)"
--------------
 echo $?
137
-------------
 docker inspect -f '{{.State.OOMKilled}}' memtest
true
---------------------
docker rm memtest
memtest
-----------
docker run -d --name burner --cpus=0.5 alpine sh -c "while :; do :; done"
a50737452857d0db1bad8b8a14e836e9ec3bddc1e48550ec135dc47b884875ec
----------------------------
 docker stats --no-stream burner
CONTAINER ID   NAME      CPU %     MEM USAGE / LIMIT   MEM %     NET I/O         BLOCK I/O     PIDS
a50737452857   burner    49.58%    672KiB / 3.693GiB   0.02%     1.17kB / 126B   1.61MB / 0B   1
------------------------------------------
docker rm -f burner
burner
-------------------
docker run -d --name todo -p 127.0.0.1:3000:3000 -v todo-db:/etc/todos getting-started
1f34c7408bc3b85ad11c2fa20d90620e56f269e649e8eed223c485bfb87bc66e
---------------------------
 docker rm -f todo
todo
--------------------------------------
 docker run -d --name todo -p 127.0.0.1:3000:3000 -v todo-db:/etc/todos getting-started
0644180b3e7dfb3f662d2c90e7e2b1df111ba3a6fab3639546cb38a41e5f8a29
------------------------------------------------------------------------
 docker volume ls
DRIVER    VOLUME NAME
local     todo-db
-----------------------------
