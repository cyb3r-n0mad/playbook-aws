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
README.md
 code/
    lambda-function.js
    dynamodb-policy.json
    s3-bucket-policy.json
    api-gateway-config.json




## Usage 
For use with AWS CLI or over SSH sessions to AWS resources. 


## Documentation Goals

Absolutely 💯 — you’re basically building content for your future blog/portfolio while you study.

Here’s how that plays out:

⸻

🔄 From Lab Notes → Website Content
	•	Lab README.md → can become a blog post draft.
	•	Example: “How I Connected API Gateway, Lambda, DynamoDB, and S3 in a Serverless Lab”
	•	Errors & Fixes section → turns into SEO gold (“fixing S3 bucket policy JSON errors” is something tons of junior engineers Google).
	•	Key Takeaways → becomes your “lesson learned” section that shows growth and practical knowledge.
	•	Code snippets → go straight into blog posts as examples.

⸻

📂 Workflow Idea
	1.	Write raw lab notes in your repo while you work.
	2.	Later, copy the README into your Eleventy/11ty site.
	3.	Clean it up: add intros, diagrams, and polish tone.
	4.	Publish — now it’s both a study record and a portfolio piece.

⸻

🚀 Career Benefit
	•	Hiring managers love seeing real labs, code snippets, and explanations.
	•	It shows you didn’t just “get a cert” — you actually built, broke, and fixed things.
	•	For AWS roles, having blog posts with titles like “Debugging IAM JSON policies” or “Building a Serverless API with DynamoDB and S3” makes you look like a hands-on problem-solver.

⸻

👉 You’re basically doing double-duty work: every lab you study now can feed directly into your website and career presence later.

    Do you want me to show you how to set up a pipeline so committing a lab README to GitHub can later sync easily into your 11ty site (so you don’t copy-pas co v te manually)?


## Reference Template

# [Title of Reference Sheet]
*Date created: YYYY-MM-DD*  
*Last updated: YYYY-MM-DD*

---

## Purpose
Briefly describe what this sheet covers, e.g., “Common ARN patterns for SAA labs” or “Frequent JSON policy structures for S3 and Lambda”.

---

## Reference Material

### 1. Section Name (e.g., ARN Patterns)
| Service | Example ARN | Notes |
|---------|-------------|-------|
| S3 Bucket | `arn:aws:s3:::my-bucket-name` | Global, no region/account ID needed |
| Lambda Function | `arn:aws:lambda:us-east-1:123456789012:function:MyFunction` | Regional, requires account ID |

### 2. Section Name (e.g., Common JSON Policies)
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["s3:GetObject","s3:PutObject"],
      "Resource": "arn:aws:s3:::example-bucket/*"
    }
  ]
}

arn reference 

Perfect — here’s a compact ARN cheat-sheet for the AWS SAA labs you’re doing. You can drop it in your GitHub repo for reference.

⸻

AWS ARN Cheat-Sheet for Labs

Service	Example ARN	Notes
S3 Bucket	arn:aws:s3:::my-bucket-name	Global service, no region, no account ID needed. Use triple colons for the bucket.
S3 Object	arn:aws:s3:::my-bucket-name/my-object-key	Append object path to bucket ARN.
IAM Role	arn:aws:iam::123456789012:role/MyLambdaRole	Global, but requires account ID. Replace with your AWS account number.
IAM User	arn:aws:iam::123456789012:user/MyUser	Global, account-specific.
Lambda Function	arn:aws:lambda:us-east-1:123456789012:function:MyFunction	Regional service → include region + account ID.
DynamoDB Table	arn:aws:dynamodb:us-east-1:123456789012:table/MyTable	Regional + account-specific.
API Gateway	arn:aws:apigateway:us-east-1::/restapis/a1b2c3d4e5/stages/prod	Regional, includes REST API ID and stage.
CloudWatch Log Group	arn:aws:logs:us-east-1:123456789012:log-group:/aws/lambda/MyFunction:*	Regional + account-specific. The * covers all streams.


---

### ✅ How to Use
1. **Copy this template** for each type of reference sheet (`arns-cheatsheet.md`, `json-patterns.md`, `cli-commands.md`).  
2. Update **title/date** and fill in content as you encounter new patterns or mistakes in labs.  
3. Link from your lab `README.md` if a lab relies on a particular sheet.  
4. Commit to GitHub regularly — your repo becomes a **living AWS knowledge 




⸻

Tips for Using ARNs
	1.	Match the service format exactly — missing region, account ID, or wrong resource path will break policies.
	2.	S3 is special — it’s global; don’t include account or region unless you’re specifying objects or bucket policies that require them.
	3.	Copy-paste when possible — small typos in colons, slashes, or case are common policy-breaking errors.
	4.	Use variables for labs — e.g., in policies, ${aws:username} or ${aws:accountId} can make templates reusable.

⸻

