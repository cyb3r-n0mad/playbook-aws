 # Lab 02: Creating a Network for a Web Application

## Description
Deploy an EC2 instance that hosts a web application into a new VPC. Secure the VPC to allow resources in public subnets to access the internet but limit inbound traffic to only HTTP protocol. After validating that the web application is accessible from the internet, deploy a second EC2 instance into a different Availability Zone in a public subnet.

### Problem: 
1. Deploy an EC2 hosting a web app in new VPC.
2. Secure VPC to only allow HTTP protocol inbound, with open outbound
3. Deploy second EC2 in different Availability Zone in public subnet

### Solution: 
1. Create VPC
2. Create 2 public subnets
3. Create Internet gateway
4. Create EC2 Instance
5. Create Security Group for EC2 only alowing HTTP protocol inbound, and all outbound. 
6. Duplicate EC2 and Security Group Policy in a different AZ for redundancy. 
7. Set load balancer to balance traffic?
8. set autoscaling?
9. Set route tables from network gateway to subnets / ec2

### Definition of Success: 
1. 2 EC2 in different AZ's accesible via internet, but no other protocol. 


## Architecture
- VPC (2 public subnets in 2 different AZ's)
- EC2 with security groups (HTTP in, all outbound)
- Route tables
- Internet gateway on VPC

  
## Guided Lab Portion

### Practice Lab Goals
- Create VPC and four subnets
- Create and attach an internet gateway and route table to VPC
- Create security group and an inbound rule to allow HTTP traffic (80, 443)
- Launch EC2 Instance into public subnnet and bootstrap the web application

### Steps I took
1. Created VPC `practice-vpc`, IPV4 `10.0.0.0/24` 
2. Edited ther VPC to enable DNS hostnames
3. Created internet gateway `practice-igw` and attached to `practice-vpc`
4. Navigated to subnets and selected `practice-vpc`
    - created subnet `public-a`, `us-east-1a`, `10.0.0.0/28`
    - created subnet `private-b`, `us-east-1a`, `10.0.0.16/28`
    - created subnet `public-b`, `us-east-1b`, `10.0.0.32/28`
    - created subnet `private-b`, `us-east-1b`, `10.0.0.48/28`
5. Navigated to Route Tables
    - created table `practice-rtb` on `practice-vpc`
    - updated subnet associations to `public-a` & `public-b`
    - edit routes - add route: destination `0.0.0.0/0`, target `practice-igw`
6. Navigated to security group
    - created `practice-sg`, `WebServer Security Group`, attached to `practice-vpc`
    - created inbound rule: type `HTTP`, `TCP` `80` Source `anywhere ipv4, 0.0.0.0/0` `inbound http access`
    - checked outbound rule: all open
7. Navigated S3 / Lab-Bucket
    - Collected `bootstrap.txt` saved file locally
8. Navigated to EC2
    - Launching an instance `WebServer`, amazon linux image, free tier ami, t3.micro, no keypait
    - edit network settings: set to `practice-vpc`, set `public-a` subnet, allow auto public ip, select security group `practice-sg`
    - edit advanced details: set iam instance profile to `lab` 
    - edit user data: paste bootstrap text with s3 bucket information
9. Once launched, open EC2 instance
    - copied public dns address and opened in new tab
    - verified http traffic access






## DIY Lab

### DIY Lab Goals
Deploy a second EC2 instance in a different availablility zone. 

Solution Validation Method
Our validation service will validate that the VPC is configured with an internet gateway, route table, and security group. It will check that two public subnets and two private subnets exist. It will then confirm that two EC2 instances were deployed, each in a separate public subnet.

### Steps I took
1. Navigate to VPC
2. create new VPC `practice-vpc` 10.0.0.0/24
3. create subnets`public a/b` private a/b  /28's 0, 16, 32, 48 
4. create route table `practice-rtb` on practice vpc
    - updated route table subnet association to include public a/b
5. created internet gateway `practice-igw`, attached to VPC
6. edit route table routes
    - 0.0.0.0/0 to IGW
7. Created security group `WebServer-Security-Group`, 
    - edit inbound for http allow from anywhere
8. Check S3 lab bucket for boot strap text
    - download in case its different
    - update with new bucket id
9. EC2 Set up to launch instance `webserver1`
    - kept amazon image, 6.1 ami, t3.micro, no keys, added security group. added IAM instance profile, loaded bootstrap
    - network set to `practice-vpc` subnet `public-a`, allow auto assign public IP. 
10. Had to rebuild security group due to not placing it with correct VPC initially. 
11. success on webserver1, doing 2 now. but public-b






## Errors & Fixes
- Didnt created the Internet gateway before creating route table. Was unable to set routing without gateway. VPC --> Gateway --> Subnets --> Route Tables --> Security Groups
- copy and paste IGW ARN, it didnt show up in drop down. 
- Trying to add IGW to RTB and getting an error that they belong to different networks. going to check that igw was created on practice vpc. 
    - forgot to attach IGW to VPC after creatation. 
    - Now that it is attached, it shows up in drop down, because it is on the same vpc network. 

Secruity group is not a part of the proper VPC. Need to edit before can launch. There is an option to associate to VPC but it says I am unauthorised. I will delete and rebuild the security group. 


## Key Takeaways
- The sequence of events matters a lot. It seems like working outward inward is the best step. First the VPC, then a Gateway, then the Subnets, then the route tables, then security groups. Only then are you ready to start created instances and servers. 

- This lesson was good at the basics but it seems like there is a lot more fine tuning possible, and templates, and ways to automate. It is humbling to successfully complete these tasks when it used to feel so unfamiliar.  

- I had multiple instances of not setting the correct vpc when creating things. I have to pay more attention, its very granular. 

- Restarting the lab after the guided portion and diy portion ensured I had plenty of time, so I will continue to do that. 


## Next Time
- I would use the training advice from "Think Like a Programmer" and make a plan. I thought I knew what to do, but I didnt sequence it properly leading to more work later. 

- I would pay more attention to VPC settings.