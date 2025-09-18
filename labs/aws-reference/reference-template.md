## Reference Template

# [Title of Reference Sheet]
*Date created: DD-MM-YYYY*  
*Last updated: DD-MM-YYYY*

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