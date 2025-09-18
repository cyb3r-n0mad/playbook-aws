# playbook-aws
Notes, tools, code, scripts related to using Amazon Web Services. 

## Overview
AWS configuration files, CLI tools, and Notes regarding management of AWS. From provisioning to security, a colloction of dedicated AWS tools as I learn them. 

## Purpose
- Build a toolbox for congiguring & securing AWS instances.
- Learning AWS SAA and using the book "The Cloud Security Handbook" by:

## Contents
planned:
aws-labs/
│
├── policies/
│   ├── s3/
│   │   ├── s3-readonly.json
│   │   ├── s3-readwrite.json
│   │   └── s3-bucket-policy-example.json
│   ├── dynamodb/
│   │   ├── dynamodb-fullaccess.json
│   │   └── dynamodb-readwrite.json
│   ├── lambda/
│   │   └── lambda-execution-role.json
│   └── deny-except-x.json
│
├── cloudformation/
│   ├── api-gateway-lambda-dynamo.yml
│   └── s3-static-site.yml
│
├── notes/
│   ├── exam-tips.md
│   ├── common-errors.md
│   └── cli-commands.md
│
└── labs/
    ├── lab01-api-gateway-lambda-s3/
    │   ├── README.md   (your notes + screenshots)
    │   └── code/       (any lambda code, configs)
    └── lab02-xxx/

example lab:

in the lab readme:

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
├── README.md
└── code/
    ├── lambda-function.js
    ├── dynamodb-policy.json
    ├── s3-bucket-policy.json
    └── api-gateway-config.json




## Usage 
For use with AWS CLI or over SSH sessions to AWS resources. 
