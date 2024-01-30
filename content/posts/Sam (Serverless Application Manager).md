---
title: "AWS Serverless Application"
date: 2024-01-30T04:06:22Z
author:
authorLink:
description:
tags:
- SAM


categories:
- 
draft: false
hiddenFromHomePage: true
---

***

## for creating the project 

`sam init`

* then select the choice which we want from all option given.
 
 the information is like below


 Which template source would you like to use?

1 - AWS Quick Start Templates
2 - Custom Template Location
---

* Choose an AWS Quick Start application template

1 - Hello World Example
	2 - Data processing
	3 - Hello World Example with Powertools for AWS Lambda
	4 - Multi-step workflow
	5 - Scheduled task
	6 - Standalone function
	7 - Serverless API
	8 - Infrastructure event management
	9 - Lambda Response Streaming
	10 - Serverless Connector Hello World Example
	11 - Multi-step workflow with Connectors
	12 - GraphQLApi Hello World Example
	13 - Full Stack
	14 - Lambda EFS example
	15 - Hello World Example With Powertools for AWS Lambda
	16 - DynamoDB Example
	17 - Machine Learning

Which runtime would you like to use?

Would you like to enable X-Ray tracing on the function(s) in your application?  [y/N]:

For more info, please view https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch-application-insights.html [y/N]

Would you like to set Structured Logging in JSON format on your Lambda functions?  [y/N]

Project name [sam-app] = test-app

project directory created on our local.

for build project on aws : sam build (in project repository)

after building the project we can get project name

for test this project on our local we can run : sam local invoke "project name"

when the docker conatiner runing on local it will give us the api message .

for start api on local : sam local start-api

for deploy on aws : sam deploy --guided

after running the above command give the (stack name) , (aws region), 

after give all the information cloudformation start on AWS console.


for delete the cloudformation stack : aws cloudformation delete-stack --stack-name ()