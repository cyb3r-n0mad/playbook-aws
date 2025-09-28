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

### Steps I took



## Errors & Fixes
- 

## Key Takeaways
- 

## Next Time
- 