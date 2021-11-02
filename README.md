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

### 3. How to setup Postgres database using Docker (I have used Ubuntu for my exercises)

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
