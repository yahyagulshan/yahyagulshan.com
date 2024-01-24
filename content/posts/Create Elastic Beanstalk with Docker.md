---
title: "Create Elastic Beanstalk with Docker"
date: 2024-01-24-T04:06:22Z
author:
authorLink:
description:
tags:
- Elastic Beanstalk
- Docker
- Ec2
- Load Balancer

categories:

draft: false
hiddenFromHomePage: true
---

# Create Elastic Beanstalk

* Open AWS console and search elastic beanstalk

* Open elastic beanstalk and click on “create envoirnment”

{{< image src="/img/beanstalk/Create.png" caption=" follow the instruction ">}}

* Step 2 
- New page open click on webserver
- Give the suitable Application name
- Environment name its automatically select
- And give the domain name

{{< image src="/img/beanstalk/configure-env.png" caption=" follow the instruction ">}}

* Step 3
- And scroll down the page
- In Plateform
- Select platform “Docker”
- Platform branch “Docker running on 64bi Amazon linux 2023”
- Platform version “Recommended”
- And for Application code “Sample application” and then click Next.


{{< image src="/img/beanstalk/plateform.png" caption=" follow the instruction ">}}

* Step 4 
- Then for Configure service access
- For service role if we are first time use elastic beanstalk and no role already created for it.
- Then select “create and use new service role”
- And if we already use elasticbeanstalk service the role is there then we select 2nd option.
- For ec2 key pair select our key pair
- And last option in this page is “ec2 instance profile”
- Here we select the role which we need to create first . and give all the permission for this role which is required for our ec2. And select the role. - - Then press next


{{< image src="/img/beanstalk/Configure-service.png" caption=" follow the instruction ">}}

* Step 5 


- This page is for networking
- Here we select our vpc
- If we give our ec2 public ip then select the option
- And which subnets which we need for our ec2 instance

{{< image src="/img/beanstalk/setup-networking.png" caption=" follow the instruction ">}}

* Step 6

- Scroll down the page
- And next option is for database
- If we need to create database with the help of beanstalk then we select the subnets for our database and click the option “enable databse”
- And fill the required option. Then press next

{{< image src="/img/beanstalk/databases.png" caption=" follow the instruction ">}}

* Step 7

- Next options are configure the instance and scaling here select the root volume type.
- By default value is “container default”.
- For amazon cloudwatch monitoring. Default value is 5 minutes.


{{< image src="/img/beanstalk/configure-instance.png" caption=" follow the instruction ">}}

* Step 8

- Next select security group

{{< image src="/img/beanstalk/instance-meta-data.png" caption=" follow the instruction ">}}

* Step 9

- Next option is autoscaling for our environment 
- For environment type select “loadbalanced”
- And select minimum and maximum instance.

{{< image src="/img/beanstalk/capacity.png" caption=" follow the instruction ">}}

* Step 10

- Then select architecture
- Default is “s86_64”
- Next option is ec2 instance type
- Select required option
- And AMI ID Is select by automatically

{{< image src="/img/beanstalk/architecture.png" caption=" follow the instruction ">}}

* Step 11

- Next option is scaling triggers
- Go as default

{{< image src="/img/beanstalk/scalling-triggers.png" caption=" follow the instruction ">}}

* Step 12

- In this page next option is load blancer select visibility and subnets for loadbalancer


{{< image src="/img/beanstalk/loadbalancer-networking.png" caption=" follow the instruction ">}}

* Step 13

- Then select load balancer type
- And add listener if we need it.

{{< image src="/img/beanstalk/load-type.png" caption=" follow the instruction ">}}

* Step 14

- Then as default
- And press next

{{< image src="/img/beanstalk/rules.png" caption=" follow the instruction ">}}

* Step 15

- Next page opens
- In this page select monitoring and logging
- In system select “enhanced”
- And select the “cloudwatch custom metrics-instance”
- And next option is “cloudwatch custom metrics-environment”


{{< image src="/img/beanstalk/Configure-updates.png" caption=" follow the instruction ">}}

* Step 16

- If we need managed update then click on that option other wise leave it.
- Next option in SNS if we need notification on our email id then give the email id.

{{< image src="/img/beanstalk/manage-plateform-updates.png" caption=" follow the instruction ">}}

* Step 17

- Then leave all the next option as default


{{< image src="/img/beanstalk/rolling-updates.png" caption=" follow the instruction ">}}

* Step 18

- Next option is platform software
- Here select the proxy server as “nginx” or none

{{< image src="/img/beanstalk/plateform-update.png" caption=" follow the instruction ">}}

* Step 19

- Next option are if we need logs storage on s3 then select the option .
- And if we need to give some credentials then we gave here with name and value option.

{{< image src="/img/beanstalk/S3-log-storage.png" caption=" follow the instruction ">}}

* Step 20

- Then press next.
- And read all the detail carefully and press submit. 
- After created the environment click on upload and deploy and click on “choose file” and select “project.zip” to upload the code.
- After successfully deployed the code our webpage should be working


