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

