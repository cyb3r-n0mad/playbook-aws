# Lab 01: API Gateway + Lambda + DynamoDB + S3

## Goal
Expose a Lambda function via API Gateway. Lambda processes data, stores structured results in DynamoDB, and backs up raw input to S3.

## Architecture
- API Gateway (HTTP endpoint)
- Lambda (Node.js function)
- DynamoDB (store processed records)
- S3 (store raw/backup files)
- IAM (roles for Lambda and Gateway)
  
## Steps I Took
1. Created S3 bucket `lab01-data-bucket`
2. Wrote and uploaded `lambda-function.js`
3. Created DynamoDB table `lab01-records` (partition key = `recordId`)
4. Configured API Gateway endpoint `/submit`
5. Attached IAM policy `lambda-dynamodb-s3.json` to Lambda role

## Errors & Fixes
- ❌ Bucket policy failed → missing `"Resource": "arn:aws:s3:::bucket/*"`
- ❌ Lambda timeout → fixed by increasing to 30s
- ✅ API Gateway worked after enabling CORS

## Key Takeaways
- Remember to use `/*` for object-level S3 policies
- API Gateway needs explicit method integration
- Testing with Postman is faster than the console

## Next Time
- Automate with CloudFormation instead of manual setup
- Add CloudWatch logs for debugging Lambda


lab directory structure: (note: actual code files, not just screenshots.)
lab01-api-gateway-lambda-s3/
README.md
 code/
    lambda-function.js
    dynamodb-policy.json
    s3-bucket-policy.json
    api-gateway-config.json