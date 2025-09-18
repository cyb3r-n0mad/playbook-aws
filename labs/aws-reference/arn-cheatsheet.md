## Reference 

# ARN Cheatsheet
*Date created: 18-09-2025*  
*Last updated: 18-09-2025*

---

## Purpose
Common ARN patterns for SAA labs

---

## Reference Material

### 1. ARN Patterns

| Service        | Example ARN                                      |   Notes |

|S3 Bucket	     |arn:aws:s3:::my-bucket-name	                    |Global service, no region, no account ID needed. Use triple colons for the bucket.
|S3 Object	     |arn:aws:s3:::my-bucket-name/my-object-key	        |Append object path to bucket ARN.
|IAM Role	     |arn:aws:iam::123456789012:role/MyLambdaRole	    |Global, but requires account ID. Replace with your AWS account number.
|IAM User	     |arn:aws:iam::123456789012:user/MyUser	            |Global, account-specific.
|Lambda Function |arn:aws:lambda:us-east-1:123456789012:function:MyFunction	        |Regional service → include region + account ID.
|DynamoDB Table	 |arn:aws:dynamodb:us-east-1:123456789012:table/MyTable	            |Regional + account-specific.
|API Gateway	 |arn:aws:apigateway:us-east-1::/restapis/a1b2c3d4e5/stages/prod	 |Regional, includes REST API ID and stage.
|CloudWatch Log Group	|arn:aws:logs:us-east-1:123456789012:log-group:/aws/lambda/MyFunction:*	| Regional + account-specific. The * covers all streams.


### 2. ARN Tips
Tips for Using ARNs
	1.	Match the service format exactly — missing region, account ID, or wrong resource path will break policies.
	2.	S3 is special — it’s global; don’t include account or region unless you’re specifying objects or bucket policies that require them.
	3.	Copy-paste when possible — small typos in colons, slashes, or case are common policy-breaking errors.
	4.	Use variables for labs — e.g., in policies, ${aws:username} or ${aws:accountId} can make templates reusable.


### 3. Note
Amazon Resource Names (ARNs) uniquely identify AWS resources. We require an ARN when you need to specify a resource unambiguously across all of AWS, such as in IAM policies, Amazon Relational Database Service (Amazon RDS) tags, and API calls. While ARNs, like any identifying information, should be used and shared carefully, they are not considered secret, sensitive, or confidential information.