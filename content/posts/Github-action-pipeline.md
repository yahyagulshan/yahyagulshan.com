---
title: "Github-action pipeline deploy code on EC2"
date: 2024-02-22T04:06:22Z
author:
authorLink:
description:
tags:
- Github-action
- EC2
- Code
- Auto-deploy
categories:
- Pipeline
draft: false
hiddenFromHomePage: true
---
# Github-action pipeline deploy code on EC2

* This blog will guide you through setting up a GitHub Actions pipeline to automatically deploy your code to an EC2 instance upon changes in your repository.

### Before you begin:

* Ensure you have an EC2 instance with a public IP address.

* Note the security group name associated with your EC2 instance.

* Obtain AWS access keys with necessary permissions and their corresponding secret access keys.

* Have your SSH private key ready for connecting to the EC2 instance.

### Steps

**Create Secrets**

* Go to your GitHub repository `settings` > `Secrets` > `Actions`.

![Screenshot from 2024-02-22 01-38-57](https://github.com/yahyagulshan/linuxnotes/assets/59036269/32d36363-9c51-4b53-b9d7-2d536a307c7f)



![image](https://github.com/yahyagulshan/linuxnotes/assets/59036269/07538e69-8031-4180-a124-ad3d0f4e1c40)



![image](https://github.com/yahyagulshan/linuxnotes/assets/59036269/210d416b-90ce-4a3a-ab6e-59f1076e50db)



![image](https://github.com/yahyagulshan/linuxnotes/assets/59036269/3bc23717-f512-4779-ab32-740087ac3250)



![image](https://github.com/yahyagulshan/linuxnotes/assets/59036269/4be5d963-6185-4d29-b27e-388bd444b9e6)

**1- Create new secrets for:**

* AWS_ACCESS_KEY_ID

* AWS_SECRET_ACCESS_KEY

* EC2_Private_key (store the private key content)

* EC2_HOST (public IP address of your EC2 instance)

* EC2_USER (username for SSH access)

**2- Clone Sample Repository:**

* Clone the sample GitHub repository that you need to follow:

      `git clone https://github.com/yahyagulshan/github-aws-ec2.git`

**3- Configure Workflow** (.github/workflows/ec2.yml):

* Open ec2.yml and update:

* `region:` Your AWS region (line 21)

* `sg-name:` Your EC2 instance's security group name (line 22)

![image](https://github.com/yahyagulshan/linuxnotes/assets/59036269/be93ab52-03d2-4ee0-82b0-4bd96961483b)

* Edit source and target paths (lines 37 and 40): 

* `source:` Directory in your repository to deploy

* `target:` Location on your EC2 instance to deploy to



![image](https://github.com/yahyagulshan/linuxnotes/assets/59036269/82113076-e0aa-4928-a0db-57323bcf03a2)

* Commit the changes.

**4- Push Changes:**

* Push your changes to the repository.

**5- Deployment:**

The GitHub Actions pipeline will automatically run and deploy your code to the specified EC2 instance based on the configured workflow.

![image](https://github.com/yahyagulshan/linuxnotes/assets/59036269/cce8361d-e95d-4c48-a9b4-fcd61ce46303)

**Benefits:**

* Streamlined deployment process.

* Automatic updates upon code changes.

* Reduced manual intervention.

* Improved collaboration and development cycle.

**Additional Notes:**

* This is a basic example. Customize the workflow based on your needs.

* Ensure proper security measures and access control for your EC2 instance.

* Explore advanced features like environment variables and custom scripts in the workflow.

* By following these steps and leveraging the power of GitHub Actions, you can achieve automated and efficient deployments of your code to your EC2 instance, ensuring your application stays up-to-date and readily accessible.

