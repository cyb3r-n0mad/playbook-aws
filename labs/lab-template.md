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
 
 
 
 # Lab 01: API Gateway + Lambda + DynamoDB + S3

### Problem: 


### Solution: 


### Definition of Success: 




## Architecture
- 
  
## Guided Lab Goals
-


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



lab directory structure: (note: actual code files, not just screenshots.)
lab01-api-gateway-lambda-s3/
README.md
 code/
    lambda-function.js
    dynamodb-policy.json
    s3-bucket-policy.json
    api-gateway-config.json


#########################################################################################################################
# Example: 

# Lab 01: API Gateway + Lambda + DynamoDB + S3

## Goal
### Problem: 
My company wants to implement appropriate security measures to protect database, storage systems, and function execution. I'm not sure how to set up secure integration and communication between AWS services in my serverless architecture.

### Solution: 
You can integrate AWS Lambda, Amazon DynamoDB, Amazon S3, and AWS Identity and Access Management, or IAM, to build a serverless architecture that processes data, stores it securely, and scales efficiently. Create a lamda function that inserts data into a dynamoDB table and uplaods objects into an s3 bucket. We'll use an IAM role with the necessary permissions for the Lambda function to access DynamoDB and S3. We'll also configure an S3 bucket policy to restrict access.

### Definition of Success: 
The Lambda function will have proper permissions to post to the DynamoDB and S3 bucket. ;


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