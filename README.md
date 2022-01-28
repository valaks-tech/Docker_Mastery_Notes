#### AWS Certification + Data Eng Lab Notes

 ### 1. How to start JupyterLab in AWS Cloud9

- Validate Python

- Create Virtual Environment 
    
   `$ python3 -m venv dataeng_lab`

- Activate Virtual Environment 
    
    `$ source dataeng_lab/bin/activate`

- Install Jupyter Lab using pip 

     `$ pip install jupyterlab`

- Start Jupyter Lab (Here 0.0.0.0 is used to ALLOW any IP, but we can restrict by giving myip(or specific ip) only.
 
  `$ jupyter lab --ip 0.0.0.0 OR nohup jupyter lab --ip 0.0.0.0 & and view nohup.out to get that token`

- Open the port in EC2 Security Groups for the Cloud9 Instance

- Validate using Browser

- Make sure to create Elastic IP/ Static IP to the virtual machine so that Pubmic IP will not change when machine gets rebooted.

  `$ jupyter lab --port $PORT --no-browser ==> can be used as well`

### 2. IAM (Identity and Access Management)

- Users: Mapped to physical users and have password to log into AWS Console

- Policies: Documents which outlines the user permissions/groups in JSON format

- Roles : for EC2 instances or for AWS Services

- Security : MFA + Password policy

- Audit: IAM credential reports and IAM Access Advisor

### 3. Whats Docker ?

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
### 4. How to setup Postgres database using Docker (I have used Ubuntu for my exercises)

- Pull the postgres image using `docker pull`

- Create the container using `docker create`.

- Start the container using `docker start`.

- Alternatively we can use `docker run` which will pull, create and start the container.

- Use `docker logs` or `docker logs -f` to review the logs to ensure Postgres Server is up and running.

```docker pull postgres

docker container create \
    --name dataeng_pg \
    -p 5432:5432 \
    -h dataeng_pg \
    -e POSTGRES_PASSWORD=mypassword \
    postgres

docker start dataeng_pg

docker logs dataeng_pg 
```

- You can connect to Postgres Database setup using Docker with `docker exec`

```
docker exec \
    -it dataeng_pg \
    psql -U postgres
```

- You can also connect to Postgres directly with out using `docker exec`, provided you have Postgres client setup on the host from which you are trying to connect to Postgres database. 

```
psql -h localhost \
    -p 5432 \
    -d postgres \
    -U postgres \
    -W 
```
