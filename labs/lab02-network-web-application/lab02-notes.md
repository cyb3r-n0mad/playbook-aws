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
1. 







## DIY Lab

### DIY Lab Goals

### Steps I took



## Errors & Fixes
- 

## Key Takeaways
- 

## Next Time
- 