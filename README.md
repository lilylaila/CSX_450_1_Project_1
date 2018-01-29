# CSX_450_1_Project_1

# Before setting up an AWS account, do two things:
# 1) Generate key in Bash
- In Bash, need to get key pair by typing: ssh-keygen
- Leave paraphrase empty
- Copy the public key contents of the SSH and paste in AWS
cat ~/.ssh/id_rsa.pub import key pair

# 2) Set up security groups in AWS
- Provide a name for the security group
- Add necessary ports (SSH = 22, HTTP = 80, Jupyter = 8888), Save
- This can be viewed in Inbound rules in the Instance

# Create EC2 account on AWS, go to Amazon Web Services
- https://aws.amazon.com/
- Create account
- Click “Launch Instance” box
- Step 1: Choose an Amazon Machine Image (AMI) - select Ubuntu Server 16.04LTS
- Step 2: Choose an Instance Type - select t2.micro – default option
- Step 3: Configure Instance Details – click next to “Add storage”
- Step 4: Add Storage – change from 8 to 30 (max for free tier eligible)
- Step 5: Add Tags – leave as is, skip next to “Configure Security Group”
- Step 6: Configure Security Group – SSH 22, HTTP 80, or use existing security group created in step 1

# Install Docker
- Launch AWS Instance
- Scroll below and grab public IP address
- Cut and paste public IP address into Bash using command ssh Ubuntu@[public IP address from Instance]
- Type command curl –ssl https://get.docker.com | sh
- Type command sudo usermod –aG docker ubuntu
- Type ctrl D or exit to restart
- Type docker pull jupyter/datascience-notebook
- Type docker images
- Type docker pull postgres
- Type docker tag jupyter/datascience-notebook dsnb
- Type docker images

# To link to port and run docker image as a container
- Type docker pull –v /home/ubuntu/home/jovyan –p 8888:8888 –d dsnb

# To show running objects and find token or key
- Type docker ps
- Type docker exec [1st 4 letters of key] jupyter notebook list 

# To run Jupyter, type public IP address from AWS directly into search box in Internet
- If token box appears, copy token from docker ps command in Bash
- Make sure connected to Ubuntu server, not local

# General Purpose - Current Generation (from Amazon Web Services)
	     vCPU	ECU		Memory (GiB)	Inst. Storage (GB)	Linux/UNIX Usage	Hours in 3 mos	TOTAL FOR 3 MOS.
t2.nano	  	1	Variable	 .5	        EBS Only	      $0.0058 per Hour	    		2160	    $12.53
t2.micro	1	Variable	  1	        EBS Only	      $0.0116 per Hour	    		2160	    $25.06
t2.small	1	Variable	  2	        EBS Only	      $0.023 per Hour	      		2160	    $49.68
t2.medium	2	Variable	  4	        EBS Only	      $0.0464 per Hour	    		2160	    $100.22
#Assume all months have 30 days

