# Lab 04: Implement Elasticity

### Problem: 
Use Amazon EC2 features to meet predictable and unpredictable demand changes, replacing unhealthy or terminated servers to maintain a desired capacity of two instances in two Availability Zones.

### Solution: 
1. First application load balancer
2. target groups must be configured when creating load balancer
    - resources - ports - protocols
3. target groups can also be used to configure health checks to confirm that ec2 instances are responding to requests
4. Auto scaling group is then provisioned, and set number of ec2, scaling group replaces unhealthy instances
5. Launch template must be defined when creating auto scaling groups. EC2 template (OS, IMAGE, STorage, security group, bootstrap, etc)
6. All contained inside of VPC - full control over networking environment, resource placement, security, etc. 
7. can also set auto scaling on schedule to ramp up or down on predicted traffic


### Definition of Success: 




## Architecture
1. VPC
2. Application Load Balancer
3. EC2 Auto Scaling
4. Auto Scaling group (Spans 2 AZ)
5. EC2 templates
6. Game servers in 2 different AZ's with unhealthy servers being replaced. 
  
## Guided Lab Goals
- Create an Application Load Balancer to distribute HTTP traffic.
- Create a launch template that defines the configuration of your EC2 instances.
- Create an Auto Scaling group with a desired, max and min capacity of 2.
- Configure Target tracking policy to try and maintain CPU utilization at 50%


### Steps I took
1. 











## DIY Lab

### DIY Lab Goals

### Steps I took
1. 


## Errors & Fixes
- 

## Key Takeaways
- 

## Next Time
- 
