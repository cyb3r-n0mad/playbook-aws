# Lab 01: API Gateway + Lambda + DynamoDB + S3

## Goal
### Problem: 
My company wants to implement appropriate security measures to protect database, storage systems, and function execution. I'm not sure how to set up secure integration and communication between AWS services in my serverless architecture.

### Solution: 
You can integrate AWS Lambda, Amazon DynamoDB, Amazon S3, and AWS Identity and Access Management, or IAM, to build a serverless architecture that processes data, stores it securely, and scales efficiently. Create a lamda function that inserts data into a dynamoDB table and uplaods objects into an s3 bucket. We'll use an IAM role with the necessary permissions for the Lambda function to access DynamoDB and S3. We'll also configure an S3 bucket policy to restrict access.

### Definition of Success: 
The Lambda function will have proper permissions to post to the DynamoDB and S3 bucket. 


## Architecture
- Lambda (python code) writes a test item to DynamoDB  table and S3 bucket
- DynamoDB (Serverless database - will recieve the test message from Lambda.)
- S3 (Storage Bucket - will also recive the test message from Lambda.)
- S3 Bucket Policy (Will restric access to the s3 bucket.)
- IAM (roles used to grant permission for Lambda function) 
  
## Steps I Took - Guided Lab Portion
0. Went to IAM and got 'LabLambdaRole" arn 
	- Validated the 'LabLambdaRole' has policy for DynamoDBPutItem, and S3 Put item. 
1. Created S3 bucket `
2. Created S3 bucket policy 
	- used given bucket policy
	- changed resource and account id in policy. 
3. Created DynamoDB table `lab-table` (partition key = `Id`) - Per guided lab. 
4. Created Lambda Function `lab-function` runtime = `python 3.13`
	- Changed default execution role to `LabLambdaRole`
	- Loaded pre set python code into Lambda - selected `deploy`
	- Navigate to Configuration / Environmental variables to set targets. 
		- key is set in python script - value is name of resource
		- added the S3 bucket and the DynamoDB table. 
5. Created `Test Event` to test the Lambda Function
	- Test successfully completed
6. Validate by checking DynamoDB table, and S3 objects. 


## Task: DIY Lab Portion
1. Update the S3 bucket policy to allow the Lambda function, diy_function, to put a test object in the bucket.
2. Provide the S3 bucket name as an environment variable of the diy_function.
Invoke diy_func

## Steps I took
0. Create s3 bucket. 
1. Updated the `diy_function` Lambda with environmental variable for lab S3 Bucket 
2. Need to modify the S3 bucket policy to allow additional roles to post. 
3. Reviewed the Configuration/Permission tab of `diy_function` to see which role is executing. 
	- `DIYPermission` in IAM
4. Navigated to IAM and copied `DIYPermission` arn: 
	- validated this role has an S3 put object policy on account. 
5. Navigated to S3 lab bucket / permissions, to update bucket policy
	- updated lab account Id in bucket policy since lab has reset
	- Place both roles LabLambdaRole and DIYPermissions in an array [ user1, user2] in the bucket policy json. 
6. Created a test event for lambda `diy-function`
	- test successful


## Errors & Fixes
- Multiple failures for not realizing the ARNs changed after the lab resets, and not watching the timer closer. 
- I had multiple failures of the bucket policy because I did not have the json properly formatted. It did not have syntax error, but I did not use an array with multiple roles. 
- Updating the bucket policy with current account numbers and arrays, allowed test to run successfully. 

## Key Takeaways
- Remember to use `/*` for object-level S3 policies
- Double check ARN numbers, especially in a lab environment
- Check json syntax with online tools like https://jsonchecker.com or https://jsonlint.com

## Next Time
- Log out of skill builder between guided labs and diy labs to reset time and lose less work. 

