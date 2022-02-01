```
λ docker container run --publish 80:80 nginx
Unable to find image 'nginx:latest' locally
latest: Pulling from library/nginx
5eb5b503b376: Pull complete
1ae07ab881bd: Pull complete
78091884b7be: Pull complete
091c283c6a66: Pull complete
55de5851019b: Pull complete
b559bad762be: Pull complete
Digest: sha256:2834dc507516af02784808c5f48b7cbe38b8ed5d0f4837f16e78d00deb7e7767
Status: Downloaded newer image for nginx:latest
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2022/02/01 00:34:00 [notice] 1#1: using the "epoll" event method
2022/02/01 00:34:00 [notice] 1#1: nginx/1.21.6
2022/02/01 00:34:00 [notice] 1#1: built by gcc 10.2.1 20210110 (Debian 10.2.1-6)
2022/02/01 00:34:00 [notice] 1#1: OS: Linux 5.10.60.1-microsoft-standard-WSL2
2022/02/01 00:34:00 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2022/02/01 00:34:00 [notice] 1#1: start worker processes
2022/02/01 00:34:00 [notice] 1#1: start worker process 31
2022/02/01 00:34:00 [notice] 1#1: start worker process 32
2022/02/01 00:34:00 [notice] 1#1: start worker process 33
2022/02/01 00:34:00 [notice] 1#1: start worker process 34
2022/02/01 00:34:00 [notice] 1#1: start worker process 35
2022/02/01 00:34:00 [notice] 1#1: start worker process 36
2022/02/01 00:34:00 [notice] 1#1: start worker process 37
2022/02/01 00:34:00 [notice] 1#1: start worker process 38
172.17.0.1 - - [01/Feb/2022:00:34:11 +0000] "GET / HTTP/1.1" 200 615 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.99 Safari/537.36" "-"
172.17.0.1 - - [01/Feb/2022:00:34:11 +0000] "GET /favicon.ico HTTP/1.1" 404 555 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.99 Safari/537.36" "-"
2022/02/01 00:34:11 [error] 31#31: *1 open() "/usr/share/nginx/html/favicon.ico" failed (2: No such file or directory), client: 172.17.0.1, server: localhost, request: "GET /favicon.ico HTTP/1.1", host: "localhost", referrer: "http://localhost/"
```


### Gotp http://localhost on browser and there you go you can see nginx webserver running !
