# Project description:

# What software will be set up through this document

- Mealie.io will be set up using docker image and container. 

-  docker is an application that allows you to run software in a container.

- I'll be using docker image to download the code for mealie.io

- I'll use docker container to be able to run mealie.



# What the software is


Mealie is a food recipe management application that allows users to create recipe by importing it through the recipe url.


# What this document will cover in terms of self-hosting this software

- This document will cover the aws vpc, ec2, subnetting, firewall rule,
 configurations, backup strategy usign s3, and showing how a user can access the application.


# AWS VPC setup:


# VPC block (and explanation / justification)

- A vpc is your own netwrok that aws give you.

- My vpc CIDR block is 10.0.0.0/24 so that is 251 ip usable, I choose that because that was the default cidr block.


# Subnet block (and explanation / justification)


- I created one subnet and the CIDR block is 10.0.0.0/28 so that is 16 usable ip. 

- I didn't need alot of ips that why I choose /28.


# Route table rules (and explanation / justification)

- My route tables is associated with my subnet and vpc which allows it to be able to direct incoming and outgoing traffic.

- 0.0.0.0/0 direct the traffic to the internet gateway.

- 10.0.0.0/24 tarffic staying inside of my vpc.


# Network ACL rules (and explanation / justification)

- I allow port 22 and 9000 from my home and wrightstate ip inbound and outbound since nacl is stateless. 

- port 22 is for sshing into the server.
 
- port 9000 is the port that mealie runs on.


# Security Group rules (and explanation / justification)

- I allows port 22 and 9000 from my home and wrightstate ip inbound only since sg are stateful.

- port 22 is for sshing into the server.

- port 9000 is the port that mealie runs on.


# AWS instance setup:

instance type (and explanation / justification)

- Instance type is t3.micro. 

- I chose that because it included 1 gib of ram,it is cost efficient for mealie.io, and have 2vcpu. 

- That's enough for my application since it's doesn't take alot of space.



AMI (and explanation / justification)

- AMI chosen is Ubuntu Server 24.04. 

- I chose that because since I have been using aws that's what I been using and i'm familiar with the OS.

- It include LTS which is ubuntu long-term support that includes security updates and bugs fixes.



volume size (and explanation / justification)

- My instance uses 8GIB as the default volume size. Mealie.io doesn't require a lot of space and I'll mostly be storing files that contain food recipes that gets stored in a docker volume.

- The volume size is used to store the OS, logs, docker, and mealie image.

- 8GIB is enough to store all those things.



# Cost estimates

summary of cost estimates

- My total month to date cost is $3.24.

- This total comes from my VPC, EC2 t3.micro, S3, and Elastic IP.


projected cost according to dashboard (screenshot)

<img width="1870" height="828" alt="image" src="https://github.com/user-attachments/assets/64934fb2-ffc7-472e-b26e-774f33f9241d" />
-------------------------------------------------------------

cost of instance type

- t3.micro cost $0.0104 usd per hour for linux.

cost of EIP (note, EIP charges only apply when instance is not in use)


- EIP cost $0.005 when not in use.


cost of AMI

- The AMI Ubuntu 24.04 was a free tier eligible.



# Installation instructions


point to documentation to use as reference

- [Link](https://docs.mealie.io/documentation/getting-started/introduction/)


summarize your installation process

- I installed docker and enable it through sysemctl. Next I created a folder named mealie and inside of that I cerated a file called docker-compose.yaml.

- After that I configured the file by copying the content of docker-compose template. Then I opened web browser and connected to the site. 


screenshot of software operating on instance

<img width="1907" height="936" alt="image" src="https://github.com/user-attachments/assets/a598c5d2-80ce-4a2e-aabf-3d3002048a7f" />

----------------------------------------------

# Security

how server access is being restricted depending on service

- port 22 is only access by the administartion from my home ip and wrightstate ip.

- port 9000 is access by anyone including the administartion from anywhere so they could connect to my site.


controlling remote server administration vs using the application
this should reflect your Security Groups / Network ACLs / system level firewalls & management access your software allows


- SG has port 22 inbound only from my home and wrightstate ip. it also has port 9000 inbound from any ip that want to connect to my site. 

- NACL has port 22 inbound and outbound from my home and wrightstate ip. it also had port 9000 inbound and outbounf from any ip.

- I didn't configure system lebel firewalls.


screenshots demonstrating different user type access rights


- Here a screenshot showing the users I created and the admin

  <img width="1497" height="558" alt="image" src="https://github.com/user-attachments/assets/abdf6fd4-5887-4f7d-aaf6-6ef470aedd38" />
----------------------------------------------------------------------------------


- users permission are only given by the admin

<img width="1492" height="764" alt="image" src="https://github.com/user-attachments/assets/027f7c62-6a62-4171-8495-0246478a615c" />


----------------------------------------------------------------------------------


# Software features


description of demonstrated features


- Users are able to import a recipe only by its url.

- users are can click the heart to favorite a recipe and can rate it out of 5 stars.


screenshots of features in action

<img width="1494" height="811" alt="image" src="https://github.com/user-attachments/assets/a3ae93c0-ca4f-426e-8557-7e8420f7a5ce" />
-----------------------------------------------------------------------

<img width="1518" height="824" alt="image" src="https://github.com/user-attachments/assets/c1abc1cb-0cd5-4897-897a-2b59d44d1537" />
---------------------------------------------------------------------------------
