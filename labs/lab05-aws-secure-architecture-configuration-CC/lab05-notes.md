# Lab 05: AWS Secure Architecture Configuration - Codecademy

### Problem: 
In this lab, you will configure a secure Amazon Web Services (AWS) virtual private cloud (VPC) architecture for a web server. First, you will configure an AWS VPC environment following AWS best practices for security and reliability. Next, you will create an Auto Scaling Group that contains a load balancer to host multiple web servers in the VPC. Finally, you will test your environment to make sure that it is functioning. Note: Once you begin a challenge you will not be able to pause, save, or return to your progress. Please ensure you have set aside enough time to complete the challenge before you start.

### Solution: 


### Definition of Success: 
Access to web servers. With load balancing and server redundancy. Recover from server failure in multiple AZ's



## Architecture
- VPC
- Auto Scaling Group
- Load Balancer
- Multiple web servers
  
## Guided Lab Goals
-In this exercise, you will configure a VPC environment. First, you will create a VPC. Next, you will create a security group for use with the VPC, and then you will configure the subnets needed for the environment. Finally, you will configure an existing route table for the public subnets, and then you will create new route tables for the private subnets.

A VPC is a virtual representation of a physical network environment. The VPC establishes the networking foundation on which you will host AWS resources. The VPC provides the TCP/IP address range of the overall network. Within the VPC, you create subnets as a subset of the overall TCP/IP address range. Much like a physical network, you need to configure route tables and gateways for TCP/IP traffic to flow into and out of the subnets in the VPC. From a security perspective, network access control lists (ACLs) and security groups provide firewall capabilities to help prevent unwanted traffic from flowing into the environment.


### Steps I took
1. Create VPC
    - `Lab VPC 55336235` , `10.0.0.0/16`
2. Create Security Group- inbound HTTP Access
    - `HTTP-SG-55336235` 
3. Create Public Subnets
    - `Public Subnet 1` `us-east-2a` 10.0.0.0/24 - set auto assign IPv4
    - `Public Subnet 2` `us-east-2b` 10.0.0.1.0/24
4. Create Private Subnets
    - `Private Subnet 1` `us-east-2a` 10.0.2.0/23
    - `Private Subnet 2`, `us-east-2b` 10.0.4.0/23
5. Create IGW
    - `Lab Internet Gateway` * Attach to VPC* 
6. Create NAT gateway
    - `NAT Gateway 1` Public Subnet 1 `Allocate Elastic IP` 
    - `NAT Gateway 2` Public Subnet 2 `Allocate Elastic IP`
7. Configure public Route Table
    - set destination to `0.0.0.0/0` add lab internet gateway, Associate public subnets
8. Create Private Route Table
    - `Private Route Table 1` Route to NAT 1, associate to private subnet 1. 
    - `Private Route Table 2 ` Route to NAT 2, associate to private subnet 2
9. Create launch template
    - `WebLT-55336235` - Normal  +Metadata version v1 v2 
10. Create Auto Scaling Group
    - Launch template, VPC, Subnets
    - Create new load balancer `WebServerLB-55336235` 
    - Create new target group - listeners and routing `WebServerTG-55336235` 
    - Set new Web Server Tracking Policy - Target Value 80
    - Add Tags Key Name value: Web Server-55336235
11. Auto scale succesfully deployed 2 instances. 
12. - fixed target group for  auto scaling group
13. testing redundancy - terminate a instance. 
    - Refreshed website and IP changed. 
    - Refreshing several times should show different IP's for servers. But if one server is down it should only show one. 
14. Confirmed. Site available form internet. Load balancer works directing traffic to multipl hosts, and the auto scale works because it can handle a server being shut down. 


## Errors & Fixes
- 503 service error on web server. Usually means the Application load balancer has no healthy targets registered. Confirmed by selecting load balancer with check box, select resource map.  the bottoms shows listeners, rules, target groups, but 0 targets. 
    - Fix go to auto scaling group, select box, open integrations, select load balancer target group. now load balancer resource map shows targets. 

## Key Takeaways
- Order of operations matter. In the AWS course we created the target group first, which I believe would have fixed the error. 
- After VPC - Subnets - security Groups - Internet gateway - route tables.... then Target group - launch templates - auto scaling group
- This lab also used NAT gateways so the Private Subnets could reach out of network. 

## Next Time
