# Docker Notes — Day 9

## Docker Version
docker info
Client:
 Version:           29.2.1
 API version:       1.53
 Go version:        go1.25.6
 Git commit:        a5c7197
 Built:             Mon Feb  2 17:20:16 2026
 OS/Arch:           windows/amd64
 Context:           desktop-linux

Server: Docker Desktop 4.63.0 (220185)
 Engine:
  Version:          29.2.1
  API version:      1.53 (minimum version 1.44)
  Go version:       go1.25.6
  Git commit:       6bc6209
  Built:            Mon Feb  2 17:17:24 2026
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          v2.2.1
  GitCommit:        dea7da592f5d1d2b7755e3a161be07f43fad8f75
 runc:
  Version:          1.3.4
  GitCommit:        v1.3.4-0-gd6d73eb8
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0
Client:
 Version:    29.2.1
 Context:    desktop-linux
 Debug Mode: false
 Plugins:
  agent: create or run AI agents (Docker Inc.)
    Version:  v1.27.1
    Path:     C:\Program Files\Docker\cli-plugins\docker-agent.exe
  ai: Docker AI Agent - Ask Gordon (Docker Inc.)
    Version:  v1.18.0
    Path:     C:\Program Files\Docker\cli-plugins\docker-ai.exe
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.31.1-desktop.1
    Path:     C:\Program Files\Docker\cli-plugins\docker-buildx.exe
  compose: Docker Compose (Docker Inc.)
    Version:  v5.0.2
    Path:     C:\Program Files\Docker\cli-plugins\docker-compose.exe
  debug: Get a shell into any image or container (Docker Inc.)
    Version:  0.0.47
    Path:     C:\Program Files\Docker\cli-plugins\docker-debug.exe
  desktop: Docker Desktop commands (Docker Inc.)
    Version:  v0.3.0
    Path:     C:\Program Files\Docker\cli-plugins\docker-desktop.exe
  extension: Manages Docker extensions (Docker Inc.)
    Version:  v0.2.31
    Path:     C:\Program Files\Docker\cli-plugins\docker-extension.exe
  init: Creates Docker-related starter files for your project (Docker Inc.)
    Version:  v1.4.0
    Path:     C:\Program Files\Docker\cli-plugins\docker-init.exe
  mcp: Docker MCP Plugin (Docker Inc.)
    Version:  v0.40.1
    Path:     C:\Program Files\Docker\cli-plugins\docker-mcp.exe
  model: Docker Model Runner (Docker Inc.)
    Version:  v1.1.1
    Path:     C:\Program Files\Docker\cli-plugins\docker-model.exe
  offload: Docker Offload (Docker Inc.)
    Version:  v0.5.56
    Path:     C:\Program Files\Docker\cli-plugins\docker-offload.exe
  pass: Docker Pass Secrets Manager Plugin (beta) (Docker Inc.)
    Version:  v0.0.24
    Path:     C:\Program Files\Docker\cli-plugins\docker-pass.exe
  sandbox: Docker Sandbox (Docker Inc.)
    Version:  v0.12.0
    Path:     C:\Program Files\Docker\cli-plugins\docker-sandbox.exe
  sbom: View the packaged-based Software Bill Of Materials (SBOM) for an image (
Anchore Inc.)
    Version:  0.6.0
    Path:     C:\Program Files\Docker\cli-plugins\docker-sbom.exe
  scout: Docker Scout (Docker Inc.)
    Version:  v1.20.0
    Path:     C:\Program Files\Docker\cli-plugins\docker-scout.exe

Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 0
 Server Version: 29.2.1
 Storage Driver: overlayfs
  driver-type: io.containerd.snapshotter.v1
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 CDI spec directories:
  /etc/cdi
  /var/run/cdi
 Discovered Devices:
  cdi: docker.com/gpu=webgpu
 Swarm: inactive
 Runtimes: io.containerd.runc.v2 nvidia runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: dea7da592f5d1d2b7755e3a161be07f43fad8f75
 runc version: v1.3.4-0-gd6d73eb8
 init version: de40ad0
 Security Options:
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 6.6.87.2-microsoft-standard-WSL2
 Operating System: Docker Desktop
 OSType: linux
 Architecture: x86_64
 CPUs: 4
 Total Memory: 3.779GiB
 Name: docker-desktop
 ID: b32f6328-cc87-472a-b1fd-7ad9cbf5adf6
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 HTTP Proxy: http.docker.internal:3128
 HTTPS Proxy: http.docker.internal:3128
 No Proxy: hubproxy.docker.internal
 Labels:
  com.docker.desktop.address=npipe://\\.\pipe\docker_cli
 Experimental: false
 Insecure Registries:
  hubproxy.docker.internal:5555
  127.0.0.0/8
  ::1/128
 Live Restore Enabled: false
 Firewall Backend: iptables


## Hello World Test
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
17eec7bbc9d7: Pull complete
ea52d2000f90: Download complete
Digest: sha256:ef54e839ef541993b4e87f25e752f7cf4238fa55f017957c2eb44077083d7a6a
Status: Downloaded newer image for hello-world:latest

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


## Postgres Container

Command used:
```bash
docker run -d \
  --name pg-prework \
  -e POSTGRES_PASSWORD=prework \
  -p 5432:5432 \
  postgres:15-alpine


## Startup Logs
##Output of docker logs pg-prework: 
The files belonging to this database system will be owned by user "postgres".
This user must also own the server process.

The database cluster will be initialized with locale "en_US.utf8".
The default database encoding has accordingly been set to "UTF8".
The default text search configuration will be set to "english".

Data page checksums are disabled.

fixing permissions on existing directory /var/lib/postgresql/data ... ok
creating subdirectories ... ok
selecting dynamic shared memory implementation ... posix
selecting default max_connections ... 100
selecting default shared_buffers ... 128MB
selecting default time zone ... UTC
creating configuration files ... ok
running bootstrap script ... ok
sh: locale: not found
2026-03-04 10:54:09.311 UTC [35] WARNING:  no usable system locales were found
performing post-bootstrap initialization ... ok
syncing data to disk ... ok


Success. You can now start the database server using:

    pg_ctl -D /var/lib/postgresql/data -l logfile start

initdb: warning: enabling "trust" authentication for local connections
initdb: hint: You can change this by editing pg_hba.conf or using the option -A,
 or --auth-local and --auth-host, the next time you run initdb.
waiting for server to start....2026-03-04 10:54:11.719 UTC [41] LOG:  starting P
ostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0,
 64-bit
2026-03-04 10:54:11.766 UTC [41] LOG:  listening on Unix socket "/var/run/postgr
esql/.s.PGSQL.5432"
2026-03-04 10:54:11.947 UTC [44] LOG:  database system was shut down at 2026-03-
04 10:54:10 UTC
2026-03-04 10:54:11.999 UTC [41] LOG:  database system is ready to accept connec
tions
 done
server started

/usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*

waiting for server to shut down...2026-03-04 10:54:12.132 UTC [41] LOG:  receive
d fast shutdown request
.2026-03-04 10:54:12.214 UTC [41] LOG:  aborting any active transactions
2026-03-04 10:54:12.219 UTC [41] LOG:  background worker "logical replication la
uncher" (PID 47) exited with exit code 1
2026-03-04 10:54:12.232 UTC [42] LOG:  shutting down
2026-03-04 10:54:12.321 UTC [42] LOG:  checkpoint starting: shutdown immediate
2026-03-04 10:54:12.998 UTC [42] LOG:  checkpoint complete: wrote 3 buffers (0.0
%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.268 s, sync=0.074 s, tot
al=0.766 s; sync files=2, longest=0.048 s, average=0.037 s; distance=0 kB, estim
ate=0 kB
2026-03-04 10:54:13.007 UTC [41] LOG:  database system is shut down
 done
server stopped

PostgreSQL init process complete; ready for start up.

2026-03-04 10:54:13.469 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-lin
ux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 10:54:13.469 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port
5432
2026-03-04 10:54:13.469 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 10:54:13.689 UTC [1] LOG:  listening on Unix socket "/var/run/postgre
sql/.s.PGSQL.5432"
2026-03-04 10:54:13.929 UTC [55] LOG:  database system was shut down at 2026-03-
04 10:54:12 UTC
2026-03-04 10:54:14.063 UTC [1] LOG:  database system is ready to accept connect
ions

## Stop and Restart:
pg-prework

