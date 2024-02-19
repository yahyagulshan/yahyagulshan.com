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

![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/1fd5cc81-9645-4ef4-beba-be5e0fd25104)


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
            "Resource": "arn:aws:s3:::domain-name.com/*"
        }
    ]
    }


![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/98268406-8f5a-4158-9c50-027c44318c43)


### 3. Create CloudFront Distribution

* Go to CloudFront and click on "Create Distribution."

* Choose the S3 bucket as the origin domain.

* Click on "Create Distribution" and wait for verification.

![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/3e5bbea7-b5c1-4424-b3d8-932a03649324)



![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/b947c60f-b048-4a27-aa67-66a446c95531)

![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/8f48d6a6-8277-456f-81d5-8aeea90d3355)

![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/61968fe8-0920-49e4-9ec9-8af3096c5b23)



![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/f5173b88-f5b8-4a69-b4b6-09d24ca7bef6)


* After verification, edit the settings and add the alternative domain name


![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/61eed6aa-d481-4eee-98a3-41a382818859)


### 4. Configure CloudFront Origin Domain

* Go to CloudFront > Origins > Edit.

* Change the origin domain value by copying the S3 static website hosting URL (without http/).

* Save the changes.


![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/a38d84ff-7475-4442-9109-b0ee531fc590)


![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/3e3abf54-ec20-4ed3-a243-e1ae7811bc2a)


### 5. Redirect Domain to CloudFront

* Copy the URL of the CloudFront distribution.

* Create a CNAME record on Cloudflare or your domain registrar with the CloudFront URL as the value.

* After populating the value, your website will display the CloudFront content.

* Now, your static website is hosted on AWS S3, served through CloudFront, and secured with an ACM SSL certificate. 




![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/559e0e15-0509-4373-92f5-16c795fc8a5e)


![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/6922a3c0-54e0-4d0f-8fd0-1cbb5c05ca1a)




