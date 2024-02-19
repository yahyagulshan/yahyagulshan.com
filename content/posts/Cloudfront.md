---
title: "Cloudfront Distribution with S3"
date: 2023-02-19T04:06:22Z
author:
authorLink:
description:
tags:
- AWS
- Cloudfront
- S3

categories:
- Domains
draft: false
hiddenFromHomePage: true
---
# 1. Create S3 Bucket for Static Website Hosting

* Create an S3 bucket named "domain-name.com."

* Set the bucket as a static website page:

* Open the S3 bucket and go to "Properties."

* In the last option, enable static website hosting.

![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/c74f1207-ee09-45bb-b2bb-6fedeb56e304)

### 2. Configure Bucket Policy for Public Access

* In the S3 bucket, navigate to "Permissions."

* Edit the bucket policy and add the following policy, replacing the 
* S3 bucket ARN:

**Bucket policy**

    {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::yahyagulshan.com/*"
        }
    ]
    }


![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/0f0095da-b9a2-44b3-acd8-5e2566c16168)

### 3. Create CloudFront Distribution

* Go to CloudFront and click on "Create Distribution."

* Choose the S3 bucket as the origin domain.

* Click on "Create Distribution" and wait for verification.

![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/58a9d5bd-ca0f-4893-8c64-0ab29086d33d)

![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/b947c60f-b048-4a27-aa67-66a446c95531)

![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/8f48d6a6-8277-456f-81d5-8aeea90d3355)

![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/be0bf048-fa1b-4896-bd61-4f58bc43b618)

![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/4ef5d49b-faeb-405d-bd94-9b425c33b4ae)

* After verification, edit the settings and add the alternative domain name


![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/62d2ca91-3feb-456b-b793-9e2d32a6e221)

### 4. Configure CloudFront Origin Domain

* Go to CloudFront > Origins > Edit.

* Change the origin domain value by copying the S3 static website hosting URL (without http/).

* Save the changes.


![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/393cda58-bee9-4048-ba8a-2edcc33602e3)

![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/c1572564-c322-4ba2-af0e-daa7731bb0fd)

### 5. Redirect Domain to CloudFront

* Copy the URL of the CloudFront distribution.

* Create a CNAME record on Cloudflare or your domain registrar with the CloudFront URL as the value.

* After populating the value, your website will display the CloudFront content.

* Now, your static website is hosted on AWS S3, served through CloudFront, and secured with an ACM SSL certificate. 




![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/cc275e5b-b2b3-4f83-ae14-a5b02cb7beac)

![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/42e8928c-e91f-49d6-aa01-ec22560eda03)



