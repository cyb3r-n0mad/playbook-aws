 # Lab 07: Implement Health Checks by using ELB and Route 53

### Problem: 
In this Challenge Lab, you will configure health checks for your environment. First, you will create a target group for an Application Load Balancer, and then you will configure health checks for the target group. Next, you will create a listener that will route requests from the load balancer to the target group, and then you will configure health checks for your load balancer by using Route 53. Finally, you will configure an Amazon Simple Notification Service (SNS) topic to notify you when a failure occurs, and then you will monitor health checks while simulating a web server failure.

### Solution: 


### Definition of Success: 




## Architecture
- 
  
## Guided Lab Goals
-


### Steps I took
1. VPC - Target Groups create new
    - set name, vpc, tag, and health parameters. 
2. Selected targets and added to pending
3. Navigated to EC2 / Load balancing / Target Groups
    - set name, vpc, tag, health parameters, selected targtets, added to pending then complted. 
4. reset health check, I changed timeout but not interval. 
5. Added Listener to target group, added stickiness
6. visit dns to verify load balancer function
7. navigated to route53/health checks
8. created Health check with given parameters
9. Setting alarms on Route53 health check
10. auto redirects to cloudwatch/alarms
11. Configfure alarms with parameters. set SNS notifications
12. Test and simulate failure. 
    - Deleted the http inbound rule
    - target group showing 1 failure 
    - cloudwatch alarms are showing server "In alarm"
13. Correct
    - Add http rule to security group
    - verify health in Target group
    - verify health in cloudwatch



## DIY Lab

### DIY Lab Goals

### Steps I took
1. 


## Errors & Fixes
- I went to vpc target groups, and not EC2 - Load balancing target groups on and got permission denied. 
- I changed timeout, but not interval time. Got error from lab. Reset & Fixed health checks. 
- The lab closed by itself before the time ran out. so I missed points that I would have had. 

## Key Takeaways
- When you are troubleshooting, you should always review the firewalls and the endpoint configurations to verify that connections are allowed. Once you verify that connections are allowed, you can use TCP/IP tools like Telnet and commands like CURL to test connectivity. 

## Next Time
- Very interetsting to set healh parameters this way. 
- I didnt know rout53 had health checks, but thats great
- Next time go faster I guess. I thought 15 minutes was enough. Actually, it said I had 10 left, and so it asked if i wanted to extend 15 minutes, which I did. But it must have really registered so it shut off at the 10 minute mark. But I had 15 minutes left of the timer. Thats a weird bug. I did make a note about it in course review. 