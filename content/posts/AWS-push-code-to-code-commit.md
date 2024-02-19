---
title: "Push code on AWS-Code-Commit"
date: 2023-02-19T04:06:22Z
author:
authorLink:
description:
tags:
- AWS
- Code-Commit
- IAM

categories:
- Credentials
draft: false
hiddenFromHomePage: true
---

# Securely Pushing Changes to AWS CodeCommit: A Step-by-Step Guide

* When working with AWS CodeCommit, a secure and straightforward version control service, ensuring the correct setup of credentials is paramount.

* Below, we'll guide you through the process of creating IAM (Identity and Access Management) credentials, obtaining HTTPS Git credentials, and pushing changes to your AWS CodeCommit repository.

### Step 1: Create IAM User for CodeCommit

* 1-  Open the AWS IAM console.

* 2- Navigate to the "Users" section and click on "Add user."

* 3- Provide a meaningful username and check the "Programmatic access" option.

* 4- Attach the necessary permissions for CodeCommit (e.g., AWSCodeCommitFullAccess).

* 5- Complete the user creation process.

### Step 2: Obtain HTTPS Git Credentials

* 1-Open the IAM user you just created and navigate to the "Security credentials" tab.

* 2-Drop down the page and locate the "HTTPS Git credentials for AWS CodeCommit (1)" section.

* 3-Click on "Generate credentials."

* 4- AWS will provide a username and password for accessing the CodeCommit repository.

### Step 3: Push Changes to AWS CodeCommit

* Now that you have your credentials, follow these steps to push changes to your AWS CodeCommit repository.

**3.1 Check the Git Status**

Before making any changes, check the status of your Git repository:

    `git status`

**3.2 Add and Commit Changes**

Add all changes and commit them with a descriptive message:

    `git add --all && git commit -am "Add new file"`

**3.3 Push Changes to the CodeCommit Repository**

Use the following command to push changes to the CodeCommit repository:

    `git push origin master`

**3.4 Enter Username and Password**

When prompted, enter the AWS CodeCommit username and password provided in Step 2.


---

By following these steps, you can securely push your changes to AWS CodeCommit. This ensures that your version-controlled projects on AWS are up-to-date and accessible while maintaining the highest security standards. Make sure to keep your IAM credentials secure, and regularly rotate passwords for enhanced security. Happy coding!