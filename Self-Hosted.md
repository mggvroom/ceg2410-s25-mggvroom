# Project description:

# What software will be set up through this document

- Mealie.io will be set up using a Docker image and container. 

-  Docker is an application that allows you to run software in a container.

- I'll be using a Docker image to download the code for mealie.io

- I'll use a Docker container to be able to run Mealie.



# What the software is


Mealie is a food recipe management application that allows users to create recipes by importing it through the recipe URL.


# What this document will cover in terms of self-hosting this software

- This document will cover the AWS VPC, EC2, subnetting, firewall rules,
 configurations, backup strategy using S3, and showing how a user can access the application.


# AWS VPC setup:


# VPC block (and explanation / justification)

- A VPC is your own network that AWS gives you.

- My VPC CIDR block is 10.0.0.0/24, so that is 251 IP addresses usable. I chose that because that was the default CIDR block.


# Subnet block (and explanation / justification)


- I created one subnet and the CIDR block is 10.0.0.0/28, so that is 16 usable IPs. 

- I didn't need a lot of IPs, that's why I chose/28.


# Route table rules (and explanation / justification)

- My route tables is associated with my subnet and VPC, which allows it to be able to direct incoming and outgoing traffic.

- 0.0.0.0/0 directs the traffic to the internet gateway.

- 10.0.0.0/24 traffic staying inside of my VPC.


# Network ACL rules (and explanation / justification)

- I allow port 22 and 9000 from my home and Wright State IP inbound and outbound since nacl is stateless. 

- Port 22 is for SSHing into the server.
 
- Port 9000 is the port that Mealie runs on.


# Security Group rules (and explanation / justification)

- I allow port 22 and 9000 from my home and Wright State IP inbound only since sg are stateful.

- Port 22 is for SSHing into the server.

- Port 9000 is the port that Mealie runs on.


# AWS instance setup:

instance type (and explanation / justification)

- Instance type is t3.micro. 

- I chose that because it included 1 GB of RAM, it is cost-efficient for mealie.io, and has 2vcpu. 

- That's enough for my application since it doesn't take a lot of space.



AMI (and explanation / justification)

- AMI chosen is Ubuntu Server 24.04. 

- I chose that because, since I have been using AWS, that's what I've been using, and I'm familiar with the OS.

- It includes LTS, which is Ubuntu long-term support that includes security updates and bug fixes.



volume size (and explanation / justification)

- My instance uses 8 GB as the default volume size. Mealie.io doesn't require a lot of space, and I'll mostly be storing files that contain food recipes that get stored in a Docker volume.

- The volume size is used to store the OS, logs, docker, and mealie image.

- 8 GB is enough to store all those things.



# Cost estimates

summary of cost estimates

- My total month-to-date cost is $3.24.

- This total comes from my VPC, EC2 t3.micro, S3, and Elastic IP.


projected cost according to dashboard (screenshot)

<img width="1870" height="828" alt="image" src="https://github.com/user-attachments/assets/64934fb2-ffc7-472e-b26e-774f33f9241d" />
-------------------------------------------------------------

cost of instance type

- t3.micro cost $0.0104 usd per hour for linux.

cost of EIP (note, EIP charges only apply when instance is not in use)


- EIP costs $0.005 when not in use.


cost of AMI

- The AMI Ubuntu 24.04 was a free-tier eligible.



# Installation instructions


point to documentation to use as reference

- [Link](https://docs.mealie.io/documentation/getting-started/introduction/)


summarize your installation process

- I installed Docker and enabled it through sysemctl. Next, I created a folder named mealie, and inside of that I created a file called docker-compose.yaml.

- After that, I configured the file by copying the content of the Docker Compose template.  


screenshot of software operating on instance

<img width="1907" height="936" alt="image" src="https://github.com/user-attachments/assets/a598c5d2-80ce-4a2e-aabf-3d3002048a7f" />

----------------------------------------------

# Security

how server access is being restricted depending on service

- Port 22 is only accessible by the administration from my home IP and Wright State IP.

- Port 9000 is accessible by anyone, including the administration, from anywhere, so they could connect to my site.


controlling remote server administration vs using the application
this should reflect your Security Groups / Network ACLs / system level firewalls & management access your software allows


- SG has port 22, inbound only from my home and Wright State IP. Port 9000 is accessible to anyone.  

- NACL has port 9000, 22 inbound and outbound from my home and Wright State IP. Port 9000  is accessible to anyone.

- I didn't configure system-level firewalls.


screenshots demonstrating different user type access rights


- Here is a screenshot showing the users I created and the admin

  <img width="1497" height="558" alt="image" src="https://github.com/user-attachments/assets/abdf6fd4-5887-4f7d-aaf6-6ef470aedd38" />
----------------------------------------------------------------------------------


- Users' permissions are only given by the admin

<img width="1492" height="764" alt="image" src="https://github.com/user-attachments/assets/027f7c62-6a62-4171-8495-0246478a615c" />


----------------------------------------------------------------------------------


# Software features


description of demonstrated features


- Users are able to import a recipe only by its url.

- Users can click the heart to favorite a recipe and can rate it out of 5 stars.


screenshots of features in action

<img width="1494" height="811" alt="image" src="https://github.com/user-attachments/assets/a3ae93c0-ca4f-426e-8557-7e8420f7a5ce" />
-----------------------------------------------------------------------


<img width="1518" height="824" alt="image" src="https://github.com/user-attachments/assets/c1abc1cb-0cd5-4897-897a-2b59d44d1537" />
---------------------------------------------------------------------------------



# Backup policy / disaster recovery


Thoughtful analysis of what good backups will consist of


- A good backup will consist of backing up my mealie folder, which includes the user, recipes, templates, and logs. 
By using the 3-2-1 rule, which will improve the redundancy of my data.


Amount of data to be backed up (estimation)

- My mealie.io data consists of 4.5Megabytes.

Backup strategy showing a reflection of the 3-2-1 rule

- I have the mealie.io file backup on AWS S3.

- I also have it backed up on one of my USB drive at my friend's house.

- lastly is the live data on my EC2.


Estimated recovery time


- If my computer was stolen, on a new computer, it'll take me 10 minutes to recover my data.
- I'll have to SSH and will need a new key pair.
- Since Mealie and docker already installed on my server, I wouldn't have to do much since my data is saved in S3.

Estimated time to recovery in case of failure


- If my EC2 crashed and stopped working, it would take me at least 5 minutes to get my application working.

- I will have to reboot the instance.

- After rebooting, I'll ssh into the server.

- Since Docker was enabled through systemctl, it will be running, and Mealie was configured to always restart.

- My data will still be there.



# Common troubleshooting

One or two things that you typically need to troubleshoot when self-hosting this application
can be from a system design perspective (computation resources, networking configurations)
can be when installing / configuring the software

- Some recipe URLs failed to import through Mealie, because those sites didn't support ld+jason format.


- When installing AWS CLI I created the folder .aws/credentials under the Ubuntu user. When I ran the command with sudo it was looking inside of /root/.aws and wouldn't work. So I fixed that by adding the folder inside of /root/.
