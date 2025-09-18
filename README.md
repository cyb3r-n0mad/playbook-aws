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



## Usage 
For use with AWS CLI or over SSH sessions to AWS resources. 



