 # Lab 06: Build a Network by using the VPC wizard

### Problem: 

In this Challenge Lab, you will create an Amazon Virtual Private Cloud (VPC) and subnets that provide high availability by using all the availability zones in a region-your customized network must adhere to AWS best practices. First, you will use the VPC Wizard to create a network foundation of a VPC, an internet gateway (IGW), a NAT gateway, and two subnets in a single availability zone. Next, you will create two additional subnets in a second availability zone. Finally, you will create and associate route tables with your subnets.




## Architecture
- new vpc with private and public subnet in one az. with one nat gateway 
- Goals is to add subnets in another az. 
  

### Steps I took
1. Entered provided information in to VPC & More wizard
2. Created private and public subnet in differ AZ in part of Lab vpc
3. Verified in route table there is a route for NAT, renamed "Private route table" 
4. Set Private route as main route table. 
5. associated private subnets to route table
6. verified Public route table had route for Internet gateway
7. Associated public subnets with route



## Errors & Fixes
- 

## Key Takeaways
- The wizard is helpful, but generates randome names so it can make it a little harder if not used to that. 
- feeling pretty comfortable with VPC's. Nothing felt like it was unexpected. 

## Next Time
- 