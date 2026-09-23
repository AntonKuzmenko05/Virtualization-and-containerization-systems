
PS D:\znu\devops> docker --version

Docker version 28.0.4, build b8034c0

docker info

Client:
Version:    28.0.4
Context:    desktop-linux
Debug Mode: false
Plugins:
...

docker run -d -p 8080:80 --name Anton-webserver httpd:2.4

Unable to find image 'httpd:2.4' locally
2.4: Pulling from library/httpd
6b37362b3da7: Pull complete
2f4636dca226: Pull complete
7a3bdd751d95: Pull complete
6db0cf540580: Pull complete
1320c4426edf: Pull complete
4f4fb700ef54: Pull complete
Digest: sha256:03f858efb82c25cb0f9962946615cdcdaf26927cb971722149b563197cfd0fdd
Status: Downloaded newer image for httpd:2.4
7b7787f0c1bcb2f0e52b967775e85dd3984491f764504421f415724aa7f44ae3

docker ps

CONTAINER ID   IMAGE       COMMAND              CREATED              STATUS              PORTS                  NAMES
7b7787f0c1bc   httpd:2.4   "httpd-foreground"   About a minute ago   Up About a minute   0.0.0.0:8080->80/tcp   Anton-webserver

curl.exe -i http://localhost:8080

HTTP/1.1 200 OK
Date: Wed, 23 Sep 2026 15:27:57 GMT
Server: Apache/2.4.68 (Unix)
Last-Modified: Fri, 07 Nov 2025 08:23:08 GMT
ETag: "bf-642fce432f300"
Accept-Ranges: bytes
Content-Length: 191
Content-Type: text/html

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<html>
<head>
<title>It works! Apache httpd</title>
</head>
<body>
<p>It works!</p>
</body>
</html>



docker run -d --name Anton-database -e MARIADB_ROOT_PASSWORD=lab2pass mariadb:11.8

Unable to find image 'mariadb:11.8' locally
11.8: Pulling from library/mariadb
ee60c3800df7: Pull complete
6281c2a67899: Pull complete
e1b0125bd61e: Pull complete
edd1ed89f0d4: Pull complete
d7d99ef55dfc: Pull complete
06237a023be8: Pull complete
187fe76a8122: Pull complete
e52011c90f60: Pull complete
Digest: sha256:79d59758afc91b89b120b0a8904d637f5a3b3e1c4900f29b740d6d46c72fef68
Status: Downloaded newer image for mariadb:11.8
a6b749affe9010a76fbeeb7889eae9be828c45eb61168bb28bf8f421b6a9f957

docker ps

CONTAINER ID   IMAGE          COMMAND                  CREATED              STATUS              PORTS                  NAMES
a6b749affe90   mariadb:11.8   "docker-entrypoint.s…"   About a minute ago   Up About a minute   3306/tcp               Anton-database
7b7787f0c1bc   httpd:2.4      "httpd-foreground"       10 minutes ago       Up 10 minutes       0.0.0.0:8080->80/tcp   Anton-webserver

docker logs Anton-database
2026-09-23 15:34:02+00:00 [Note] [Entrypoint]: Entrypoint script for MariaDB Server 1:11.8.9+maria~ubu2404 started.
2026-09-23 15:34:02+00:00 [Warn] [Entrypoint]: /sys/fs/cgroup///memory.pressure not writable, functionality unavailable to MariaDB
2026-09-23 15:34:02+00:00 [Note] [Entrypoint]: Switching to dedicated user 'mysql'
2026-09-23 15:34:02+00:00 [Note] [Entrypoint]: Entrypoint script for MariaDB Server 1:11.8.9+maria~ubu2404 started.
2026-09-23 15:34:02+00:00 [Note] [Entrypoint]: Initializing database files
2026-09-23 15:34:04+00:00 [Note] [Entrypoint]: Database files initialized
2026-09-23 15:34:04+00:00 [Note] [Entrypoint]: Starting temporary server
2026-09-23 15:34:04+00:00 [Note] [Entrypoint]: Waiting for server startup
2026-09-23 15:34:04 0 [Note] Starting MariaDB 11.8.9-MariaDB-ubu2404 source revision bf9193a939f515e95dd8def1a5468088c91cede6 server_uid Dz//FhPE/BQQNwstPRZzyq8DPvM= as process 93
2026-09-23 15:34:04 0 [Note] InnoDB: Compressed tables use zlib 1.3
2026-09-23 15:34:04 0 [Note] InnoDB: Number of transaction pools: 1
2026-09-23 15:34:04 0 [Note] InnoDB: Using crc32 + pclmulqdq instructions
2026-09-23 15:34:04 0 [Note] mariadbd: O_TMPFILE is not supported on /tmp (disabling future attempts)
2026-09-23 15:34:04 0 [Note] InnoDB: Using io_uring
2026-09-23 15:34:04 0 [Note] InnoDB: innodb_buffer_pool_size_max=8388608m, innodb_buffer_pool_size=128m
2026-09-23 15:34:04 0 [Note] InnoDB: Completed initialization of buffer pool
2026-09-23 15:34:04 0 [Note] InnoDB: File system buffers for log disabled (block size=4096 bytes)
2026-09-23 15:34:04 0 [Note] InnoDB: End of log at LSN=45568
2026-09-23 15:34:04 0 [Note] InnoDB: Opened 3 undo tablespaces
2026-09-23 15:34:04 0 [Note] InnoDB: 128 rollback segments in 3 undo tablespaces are active.
2026-09-23 15:34:04 0 [Note] InnoDB: Setting file './ibtmp1' size to 12.000MiB. Physically writing the file full; Please wait ...
2026-09-23 15:34:04 0 [Note] InnoDB: File './ibtmp1' size is now 12.000MiB.
2026-09-23 15:34:04 0 [Note] InnoDB: log sequence number 45568; transaction id 14
2026-09-23 15:34:04 0 [Note] Plugin 'FEEDBACK' is disabled.
2026-09-23 15:34:04 0 [Note] Plugin 'wsrep-provider' is disabled.
2026-09-23 15:34:04 0 [Note] mariadbd: Event Scheduler: Loaded 0 events
2026-09-23 15:34:04 0 [Note] mariadbd: ready for connections.
Version: '11.8.9-MariaDB-ubu2404'  socket: '/run/mysqld/mysqld.sock'  port: 0  mariadb.org binary distribution
2026-09-23 15:34:05+00:00 [Note] [Entrypoint]: Temporary server started.
2026-09-23 15:34:05+00:00 [Note] [Entrypoint]: Securing system users (equivalent to running mysql_secure_installation)

2026-09-23 15:34:05+00:00 [Note] [Entrypoint]: Stopping temporary server
2026-09-23 15:34:05 0 [Note] mariadbd (initiated by: unknown): Normal shutdown
2026-09-23 15:34:05 0 [Note] InnoDB: FTS optimize thread exiting.
2026-09-23 15:34:05 0 [Note] InnoDB: Starting shutdown...
2026-09-23 15:34:05 0 [Note] InnoDB: Dumping buffer pool(s) to /var/lib/mysql/ib_buffer_pool
2026-09-23 15:34:05 0 [Note] InnoDB: Buffer pool(s) dump completed at 260923 15:34:05
2026-09-23 15:34:05 0 [Note] InnoDB: Removed temporary tablespace data file: "./ibtmp1"
2026-09-23 15:34:05 0 [Note] Shutdown completed; log sequence number 45568; transaction id 15
2026-09-23 15:34:05 0 [Note] mariadbd: Shutdown complete
2026-09-23 15:34:05+00:00 [Note] [Entrypoint]: Temporary server stopped

2026-09-23 15:34:05+00:00 [Note] [Entrypoint]: MariaDB init process done. Ready for start up.
....
2026-09-23 15:34:06 0 [Note] mariadbd: ready for connections.
Version: '11.8.9-MariaDB-ubu2404'  socket: '/run/mysqld/mysqld.sock'  port: 3306  mariadb.org binary distribution


docker run -it --name Anton-os debian:13 /bin/bash 

docker run -it --name Anton-os debian:13 /bin/bash
Unable to find image 'debian:13' locally
13: Pulling from library/debian
6eefb2f5d3e9: Pull complete
Digest: sha256:9cc080028c43b27d2074d63a5f9caf7166d731494965616c1a6d2827a004585c
Status: Downloaded newer image for debian:13
root@ca8e427fa4a5:/# ls /
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@ca8e427fa4a5:/# cat /etc/os-release
PRETTY_NAME="Debian GNU/Linux 13 (trixie)"
NAME="Debian GNU/Linux"
VERSION_ID="13"
VERSION="13 (trixie)"
VERSION_CODENAME=trixie
DEBIAN_VERSION_FULL=13.7
ID=debian
HOME_URL="https://www.debian.org/"
SUPPORT_URL="https://www.debian.org/support"
BUG_REPORT_URL="https://bugs.debian.org/"
root@ca8e427fa4a5:/# exit
exit

docker run -d --name Anton-os-d debian:13 sleep infinity

22a1b5a66fe57669f174699c187990595ae31372bd7da2f65dd079d06223ead7


docker exec -it Anton-os-d /bin/bash

docker exec -it Anton-os-d /bin/bash
root@22a1b5a66fe5:/# ls /
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@22a1b5a66fe5:/# exit
exit
PS D:\znu\devops> docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED              STATUS              PORTS                  NAMES
22a1b5a66fe5   debian:13      "sleep infinity"         About a minute ago   Up About a minute                          Anton-os-d
a6b749affe90   mariadb:11.8   "docker-entrypoint.s…"   10 minutes ago       Up 10 minutes       3306/tcp               Anton-database
7b7787f0c1bc   httpd:2.4      "httpd-foreground"       19 minutes ago       Up 19 minutes       0.0.0.0:8080->80/tcp   Anton-webserver
PS D:\znu\devops> docker ps -a
CONTAINER ID   IMAGE               COMMAND                  CREATED              STATUS                     PORTS                  NAMES
22a1b5a66fe5   debian:13           "sleep infinity"         About a minute ago   Up About a minute                                 Anton-os-d
ca8e427fa4a5   debian:13           "/bin/bash"              4 minutes ago        Exited (0) 3 minutes ago                          Anton-os
a6b749affe90   mariadb:11.8        "docker-entrypoint.s…"   10 minutes ago       Up 10 minutes              3306/tcp               Anton-database
7b7787f0c1bc   httpd:2.4           "httpd-foreground"       19 minutes ago       Up 19 minutes              0.0.0.0:8080->80/tcp   Anton-webserver
f2dff260312f   redis:7-alpine      "docker-entrypoint.s…"   3 days ago           Exited (0) 2 days ago                             science_tech_redis
9c25e77449b4   grammy-tg-bot-bot   "docker-entrypoint.s…"   13 months ago        Exited (0) 13 months ago                          telegram_bot_store
5e18eee17dca   mongo:6             "docker-entrypoint.s…"   13 months ago        Exited (0) 13 months ago                          mongo-db


docker inspect Anton-webserver
[
{
"Id": "7b7787f0c1bcb2f0e52b967775e85dd3984491f764504421f415724aa7f44ae3",
"Created": "2026-09-23T15:24:35.275171524Z",
"Path": "httpd-foreground",
"Args": [],
"State": {
"Status": "running",
"Running": true,
"Paused": false,
"Restarting": false,
"OOMKilled": false,
"Dead": false,
"Pid": 565,
"ExitCode": 0,
"Error": "",
"StartedAt": "2026-09-23T15:24:35.654065971Z",
...

docker inspect --format '{{.State.Status}} {{.Config.Image}}' Anton-webserver

running httpd:2.4


docker images

REPOSITORY          TAG        IMAGE ID       CREATED         SIZE
httpd               2.4        03f858efb82c   4 days ago      175MB
debian              13         9cc080028c43   5 days ago      184MB
redis               7-alpine   520775a41a63   5 days ago      57.3MB
mariadb             11.8       79d59758afc9   7 days ago      453MB
grammy-tg-bot-bot   latest     32f257074342   13 months ago   276MB
mongo               6          363f5fab76d1   14 months ago   1.05GB


PS D:\znu\devops>docker rm Anton-webserver
Anton-webserver
PS D:\znu\devops> docker stop Anton-database Anton-os-d
Anton-database
Anton-os-d
PS D:\znu\devops> docker rm Anton-database Anton-os Anton-os-d
Anton-database
Anton-os
Anton-os-d
PS D:\znu\devops> docker ps -a
CONTAINER ID   IMAGE               COMMAND                  CREATED         STATUS                     PORTS     NAMES
f2dff260312f   redis:7-alpine      "docker-entrypoint.s…"   3 days ago      Exited (0) 2 days ago                science_tech_redis
9c25e77449b4   grammy-tg-bot-bot   "docker-entrypoint.s…"   13 months ago   Exited (0) 13 months ago             telegram_bot_store
5e18eee17dca   mongo:6             "docker-entrypoint.s…"   13 months ago   Exited (0) 13 months ago             mongo-db
PS D:\znu\devops> docker rmi httpd:2.4 mariadb:11.8 debian:13
Untagged: httpd:2.4
Deleted: sha256:03f858efb82c25cb0f9962946615cdcdaf26927cb971722149b563197cfd0fdd
Untagged: mariadb:11.8
Deleted: sha256:79d59758afc91b89b120b0a8904d637f5a3b3e1c4900f29b740d6d46c72fef68
Untagged: debian:13
Deleted: sha256:9cc080028c43b27d2074d63a5f9caf7166d731494965616c1a6d2827a004585c
PS D:\znu\devops> docker images
REPOSITORY          TAG        IMAGE ID       CREATED         SIZE
redis               7-alpine   520775a41a63   5 days ago      57.3MB
grammy-tg-bot-bot   latest     32f257074342   13 months ago   276MB
mongo               6          363f5fab76d1   14 months ago   1.05GB
