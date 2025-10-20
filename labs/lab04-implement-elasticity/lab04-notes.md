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
1. Nav to EC2 / Load balancing / target groups
2. Creating Target group
    - instances, `Lab-TG`, Set to `LabVPC`, Created target group
3. create load balancer
    - Application load balancer, `Lab-ALB`, internet facing, ipv4
    - set `LabVPC`, set subnets, set security group `PublicSG`, set default action to forward to `Lab-TG`
    - Load Balncer DNS: 
4. Nav EC2 / instances / launch template
    - create Launch Template
    - `Lab-LT`, amazon linux os, t3.micro, set securitry group `PublicSG`, 
    - enter bootstrap script into user data. 
5. nav ec2 / autoscaling
    - `Lab-ASG`, with `Lab-LT` launc template
    - set `LabVPC`, set 2 public subnets in az's
    - attach existing load balancer - Load balancer from target group
    - Enable elastic load balancing health checks
    - set group size 2, with max and min 2, set to target tracking scaling policy (average CPU 50%, 300 second warmup)
6. Open Auto scale group `Lab-ASG`
    - Automatic Scaling - *CREATE SCHEDULED ACTION* Needed for DIY portion
    - Check Activity, verify activity history shows launching EC2 instances
7. Nav to ec2, testing the auto launch, by deleting and instance
    - vewrified that after one was shut down the auto scaling started a new instance
8. Nav to load balancer dns, step 3, verify http server running. 




## DIY Lab

### DIY Lab Goals
    Add a Scheduled Action to the Auto Scaling group.
    Set the desired capacity to 3.
    Set the recurrence to 8:00 PM UTC every Friday.


### Steps I took
1. Nav to EC3 / Auto scaleing groups / Lab-ASG / Automatic scaling
2. `Lab-Action`
3. desired capacity 3
4. every week
5. on friday, 8pm utc



## Errors & Fixes
- none

## Key Takeaways
- The target groups, and templates are more different than I thought, but it makes sense. 
- Load balancer seemed pretty straight forward. 
- Keeping the lab open made the DIY portion very easy. 

## Next Time
- 
