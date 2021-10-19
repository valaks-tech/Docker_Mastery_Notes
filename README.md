# My AWS certification preparation

*How to start JupyterLab in AWS Cloud9

- Validate Python

- Create Virtual Environment $ python3 -m venv dataeng_lab

- Activate Virtual Environment $ source dataeng_lab/bin/activate

- Install Jupyter Lab using pip $ pip install jupyterlab

- Start Jupyter Lab (Here 0.0.0.0 is used to ALLOW any IP, but we can restrict by giving myip(or specific ip) only. $ jupyter lab --ip 0.0.0.0 OR nohup jupyter lab --ip 0.0.0.0 & and view nohup.out to get that token

- Open the port in EC2 Security Groups for the Cloud9 Instance

- alidate using Browser

- Make sure to create Elastic IP/ Static IP to the virtual machine so that Pubmic IP will not change when machine gets rebooted.

$ jupyter lab --port $PORT --no-browser ==> can be used as well
