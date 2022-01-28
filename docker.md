### Whats Docker ?

Docker Architecture :

`Docker client -->  Docket Host    --> Docker Registry/Docker Hub`

When you run 'docker run <image>' command, docker client will contact Docker Daemon running on Docker Host. Docker Daemon will try to locate the <image> locally on Docker Host.
 If it finds it, it will pull the image and execute inside the container. 
 
 #### Docker Daemon :
   - Runs on Docker host
   - Creates and manages docker objects such as :
      * Images
      * Containers
      * Network, Volume etc
 #### Docker Client :
   - User interface which accepts commands from user and communicates with Docker Host
 
 #### Docker Images :
   - Build component of docker
   - Used to created docker containers, provides a way to create new or update existing images
 
 ```
 root@555a9c63f4aa:/# exit
exit
PS C:\Users\shail> docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
PS C:\Users\shail> docker ps -a
CONTAINER ID   IMAGE           COMMAND                  CREATED          STATUS                        PORTS     NAMES
555a9c63f4aa   ubuntu:latest   "bash"                   7 minutes ago    Exited (127) 11 seconds ago             vibrant_lederberg
13010265b572   ubuntu:latest   "bash"                   28 minutes ago   Exited (127) 7 minutes ago              confident_rubin
fac2ae66274d   alpine/git      "git clone https://g…"   6 hours ago      Exited (0) 6 hours ago                  repo
PS C:\Users\shail> docker start 555a9c63f4aa
555a9c63f4aa
PS C:\Users\shail> docker attach 555a9c63f4aa
root@555a9c63f4aa:/#
 PS C:\Users\shail> docker ps
CONTAINER ID   IMAGE           COMMAND   CREATED         STATUS              PORTS     NAMES
555a9c63f4aa   ubuntu:latest   "bash"    9 minutes ago   Up About a minute             vibrant_lederberg
PS C:\Users\shail>
```
 
 To come out of docker container without making docker exit, CTRL+P CTRL+Q and to go back inside the docker container:
 ```
 PS C:\Users\shail> docker attach 382b16e46beb
root@382b16e46beb:/# ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 00:30 pts/0    00:00:00 bash
root        10     1  0 00:33 pts/0    00:00:00 ps -ef
root@382b16e46beb:/#
 
 PS C:\Users\shail> docker container ls
CONTAINER ID   IMAGE           COMMAND   CREATED          STATUS         PORTS     NAMES
382b16e46beb   ubuntu:latest   "bash"    5 minutes ago    Up 5 minutes             magical_perlman
555a9c63f4aa   ubuntu:latest   "bash"    17 minutes ago   Up 9 minutes             vibrant_lederberg
PS C:\Users\shail> docker ps
CONTAINER ID   IMAGE           COMMAND   CREATED          STATUS          PORTS     NAMES
382b16e46beb   ubuntu:latest   "bash"    5 minutes ago    Up 5 minutes              magical_perlman
555a9c63f4aa   ubuntu:latest   "bash"    18 minutes ago   Up 10 minutes             vibrant_lederberg
PS C:\Users\shail>
 ```
Renaming the container
 ```
 PS C:\Users\shail> docker ps
CONTAINER ID   IMAGE           COMMAND   CREATED          STATUS          PORTS     NAMES
382b16e46beb   ubuntu:latest   "bash"    5 minutes ago    Up 5 minutes              magical_perlman
555a9c63f4aa   ubuntu:latest   "bash"    18 minutes ago   Up 10 minutes             vibrant_lederberg
PS C:\Users\shail> docker rename magical_perlman shaila_ubuntu_1
PS C:\Users\shail> docker ps
CONTAINER ID   IMAGE           COMMAND   CREATED          STATUS          PORTS     NAMES
382b16e46beb   ubuntu:latest   "bash"    9 minutes ago    Up 9 minutes              shaila_ubuntu_1
555a9c63f4aa   ubuntu:latest   "bash"    21 minutes ago   Up 13 minutes             vibrant_lederberg
PS C:\Users\shail> docker container ls
CONTAINER ID   IMAGE           COMMAND   CREATED          STATUS          PORTS     NAMES
382b16e46beb   ubuntu:latest   "bash"    9 minutes ago    Up 9 minutes              shaila_ubuntu_1
555a9c63f4aa   ubuntu:latest   "bash"    21 minutes ago   Up 13 minutes             vibrant_lederberg
PS C:\Users\shail>
 ```
 
 Stop the container
 ```
 PS C:\Users\shail> docker stop shaila_ubuntu_1
shaila_ubuntu_1
PS C:\Users\shail> docker container ls
CONTAINER ID   IMAGE           COMMAND   CREATED          STATUS          PORTS     NAMES
555a9c63f4aa   ubuntu:latest   "bash"    27 minutes ago   Up 19 minutes             vibrant_lederberg
PS C:\Users\shail> docker container ls -a
CONTAINER ID   IMAGE           COMMAND                  CREATED          STATUS                        PORTS     NAMES
382b16e46beb   ubuntu:latest   "bash"                   15 minutes ago   Exited (0) 12 seconds ago               shaila_ubuntu_1
555a9c63f4aa   ubuntu:latest   "bash"                   27 minutes ago   Up 19 minutes                           vibrant_lederberg
13010265b572   ubuntu:latest   "bash"                   48 minutes ago   Exited (127) 28 minutes ago             confident_rubin
fac2ae66274d   alpine/git      "git clone https://g…"   6 hours ago      Exited (0) 6 hours ago                  repo
PS C:\Users\shail>
 ```
 `docker rm` is for containers and `docker rmi` is for images
```
PS C:\Users\shail> docker --version
Docker version 20.10.12, build e91ed57
PS C:\Users\shail> docker version
Client:
 Cloud integration: v1.0.22
 Version:           20.10.12
 API version:       1.41
 Go version:        go1.16.12
 Git commit:        e91ed57
 Built:             Mon Dec 13 11:44:07 2021
 OS/Arch:           windows/amd64
 Context:           default
 Experimental:      true

Server: Docker Engine - Community
 Engine:
  Version:          20.10.12
  API version:      1.41 (minimum version 1.12)
  Go version:       go1.16.12
  Git commit:       459d0df
  Built:            Mon Dec 13 11:43:56 2021
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.4.12
  GitCommit:        7b11cfaabd73bb80907dd23182b9347b4245eb5d
 runc:
  Version:          1.0.2
  GitCommit:        v1.0.2-0-g52b36a2
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0
PS C:\Users\shail>
```

 Hyper-V and Oracle VM VirtualBox are both server virtualization products designed to run virtual machines. 
 Hyper-V is a type 1 hypervisor that manages operating systems by running directly on a computer's hardware. 
 In contrast, Oracle VM VirtualBox is a type 2 hypervisor, which runs on the host operating system
 
 
