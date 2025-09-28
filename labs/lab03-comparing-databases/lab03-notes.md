# Lab 03: Comparing Databases

### Problem: 
1. Needs quck access to unstructured data
2. needs quck access to structured data 

### Solution: 
1. Deploy DynamoDB for unstructured data and DAX to accelerate
2. Deploy Amazon RDS for database, with Aurora caching / Aurora Reader

### Definition of Success: 




## Architecture
- 
  
## Guided Lab Goals
-- Create a MySQL database by using Amazon RDS.
- Create a NoSQL database by using Amazon DynamoDB.
- Deploy a DynamoDB Accelerator (DAX) cluster.


### Steps I took
1. Nav to Aurora RDS / Databases
    - standard create - engine: aurora, dev/test template, `exampledb`, set to "burstable classes", set VPC (Cannot change vpc after creation), removed enhanced monitoring, disabled minor version updates, 
2. in database - add reader (For DIY Lab)
3. Nav DynamoDB / tables
4. create table: `exampledb2`, partition key `examid` 
5. open DAX Clusters - Create Cluster
    - Cluster nodes: `examdb-cluster`, note type: `dax.r5.large`
    - Cluster network: create new, `cluster-subnet-group`, set `labvpc`, set both subnets in `labvpc`  
    - Cluster security: set IAM role `LabDXRole`    
    - No advanced settings



## DIY Lab



### DIY Lab Goals
Deploy a read replica to the Aurora database with the instance identifier, examdb-reader, and without enhanced monitoring.

Our validation service will validate that the DynamoDB table and DAX cluster were created and that the Aurora database was created with a read replica.

Hint:
1. Selecting the existing database and choosing "Actions" gives you the option that you need.
2. Make sure the status for the reader changes to "Available" before verifying. 

Validation requires the Aurora Database and Aurora Reader names. 

## Plan
1. Check for RDS databases services to deploy aurora too. 
2. Create Aurora reader with name `examdb-reader` w/o enhanced monitoring
3. Check for dynamoDB and tables?
4. create a DAX cluster?

- TBH I'm rather confused by the goals within this lab. 
- Am I supposed to use the stuff completed in the guided portion for the diy section?



### Steps I took
1. I opened Aurora RDS. There are currently 0 databases available. 
2. I checked dynamodb and there are 0 tables available. 
3. Created aurora rds `exampledb` as above. once DB created, in action tab, I selected "add reader" set the name to `examdb-reader` and disabled enhanced monitoring
4. verified.0


## Errors & Fixes
- Should I be doing the diy without resetting the lab? It appears I have to rebuild all of the lab info, to complete the diy section. It is good reps, but confusing. 

## Key Takeaways
- It may be better to attempt DIY directly after guided portion because these seem to use stuff built during guided portion. 

## Next Time
- Re read what is expected, especially if the guided portion says "NEEDED in the DIY portion"  this should have taken 3 minutes, but I had to build a whole new RDS database to complete. (so it actually took 7 minutes lol)
