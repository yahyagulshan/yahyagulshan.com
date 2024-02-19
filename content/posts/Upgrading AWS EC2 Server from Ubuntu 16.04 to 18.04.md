---
title: "Upgrading AWS EC2 Server from Ubuntu 16.04 to 18.04"
date: 2023-09-09T04:06:22Z
author:
authorLink:
description:
tags:
- Update
- Ubuntu 16.04
- Ubuntu 18.04
categories:
- Tutorial
draft: false
hiddenFromHomePage: true
---

# Safely Upgrading Your AWS EC2 Server 16.04 to Ubuntu 18.04: A Step-by-Step Guidee

### Before Proceeding with the Upgrade

* Before embarking on the upgrade journey for your AWS EC2 server, it is crucial to take the necessary precautions to avoid potential data loss. Follow these steps diligently to ensure a smooth and secure upgrade process.

### Step 1: Backup Your Server
* Before proceeding with the upgrade, ensure that you have taken a backup of your server. This critical step acts as a safety net, protecting your data in case of any unforeseen issues during the upgrade.
### Upgrading Process
### Step 2: Login to the AWS Console

* Access your AWS account and navigate to the EC2 dashboard.

***

### Step 3: Create an AMI (Amazon Machine Image)

* 1- Select the EC2 instance that you plan to upgrade.

* 2- Click on the "Actions" button and choose "Image" > "Create Image."

* 3- Follow the prompts to create an AMI of your EC2 instance. This AMI serves as your backup image, preserving the current state of your server.

***


### Step 4: SSH into the Server

* Once the AMI creation is completed, SSH into your EC2 server using your preferred terminal.

### Step 5: Check Available Disk Space

* Before proceeding with the upgrade, it is essential to assess the available disk space on your server. Run the following command to check disk space:

      `df -lh`

### Step 6: Perform the Upgrade

Run the following commands to smoothly upgrade your Ubuntu server:

Update package lists:

    `sudo apt-get update`

Perform a distribution upgrade:

    `sudo apt-get dist-upgrade`

Install the update manager core:

    `sudo apt-get install update-manager-core`

Initiate the release upgrade:

    `sudo do-release-upgrade`

Follow all instructions provided during the upgrade procedure and carefully monitor each step.

### Step 7: Restart the Server

* 1- After the upgrade is complete, a system restart is required.

* 2- Confirm the restart by pressing "yes" to complete the procedure.

* 3- Once the server restarts, your Ubuntu upgrade is complete.


### Step 8: Check the Ubuntu Version

* To verify that the upgrade was successful and your system is now running Ubuntu 18.04, run the following command:

      `cat /etc/os-release`

* By meticulously following these steps, you can confidently and securely upgrade your AWS EC2 server from Ubuntu 16.04 to Ubuntu 18.04. Always remember to back up your data and exercise caution during the upgrade to prevent any potential data loss or service interruption. Your server's smooth transition to the latest Ubuntu version is now complete!
