# CSX_450_1_Project_1

#Before setting up an AWS account, do two things:
•	In Bash, type ssh-keygen
•	Leave paraphrase empty
•	cat ~/.ssh/id_rsa.pub import key pair

#Create EC2 account on AWS:
•	Go to Amazon Web Services
•	Create account
•	Click “Launch Instance” box
•	Step 1: Choose an Amazon Machine Image (AMI) - select Ubuntu Server 16.04LTS
•	Step 2: Choose an Instance Type - select t2.micro – default option
•	Step 3: Configure Instance Details – click next to “Add storage”
•	Step 4: Add Storage – change from 8 to 30 (max for free tier eligible)
•	Step 5: Add Tags – leave as is, skip next to “Configure Security Group”
•	Step 6: Configure Security Group – SSH 22, HTTP 80

#Install Docker
•	Launch Instance
•	Scroll below and grab public IP address
•	Cut and paste into Bash using command ssh Ubuntu@[IP address from Instance]
•	Type command curl –ssl https://get.docker.com | sh
•	Sudo usermod –aG docker ubuntu
•	Type ctrl D or exit to restart
•	Type docker pull jupyter/datascience-notebook
•	Type docker images
•	Type docker pull postgres
•	Type docker tag jupyter/datascience-notebook dsnb
•	Type docker images

#To link to port and run docker image as a container
•	Type docker pull –v /home/ubuntu/home/jovyan –p 8888:8888 –d dsnb

#To show running objects and find token or key
•	Type docker ps
•	Type docker exec [1st 4 letters of key] jupyter notebook list 

#To run Jupyter, type public IP address from AWS directly into search box in Internet
•	If token appears, copy token from docker ps command in Bash
#Make sure connected to Ubuntu server, not local

#General Purpose - Current Generation (from Amazon Web Services)
	     vCPU	ECU	Memory (GiB)	Instance Storage (GB)	Linux/UNIX Usage	Hours in 3 mos	TOTAL FOR 3 MONTHS
t2.nano	  1	  Variable	 .5	        EBS Only	      $0.0058 per Hour	    2160	            $12.53
t2.micro	1	  Variable	  1	        EBS Only	      $0.0116 per Hour	    2160	            $25.06
t2.small	1	  Variable	  2	        EBS Only	      $0.023 per Hour	      2160	            $49.68
t2.medium	2	  Variable	  4	        EBS Only	      $0.0464 per Hour	    2160	            $100.22
#Assume all months have 30 days
