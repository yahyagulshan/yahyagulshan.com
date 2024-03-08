---
title: "How to install Jenkins on Ubuntu 22.04"
date: 2024-02-05T04:06:22Z
author:
authorLink:
description:
tags:
- Jenkins
- Java
- Ubuntu

categories:

draft: false
hiddenFromHomePage: true
---

## Prerequisites For Installation on Jenkins on ubuntu 📜

* Minimum hardware requirements:

* 256 MB of RAM

* 1 GB of drive space (although 10 GB is a recommended minimum if running Jenkins as a Docker container) 

* Software requirements:

* Java

### Installation steps ⚙️ 👣

* first update and upgrade the system 

   `sudo apt update && apt upgrade -y`

* Install Java usig this command 
   
   `sudo apt install openjdk-17-jre`

* Check Java version 

  `java --version`

* Then run below commands
   
   `sudo wget -O /usr/share/keyrings/jenkins-keyring.asc   https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key`
   
   ` echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]   https://pkg.jenkins.io/debian-stable binary/ | sudo tee   /etc/apt/sources.list.d/jenkins.list > /dev/null`

   `sudo apt-get update`

   `sudo apt-get install jenkins`

   `sudo systemctl enable jenkins`

   `sudo systemctl start jenkins`

   `sudo systemctl status jenkins`

* to get password for first time login to Jenkins

 `sudo cat /var/lib/jenkins/secrets/initialAdminPassword`

 {{< image src="/img/Jenkins/password.png" caption=" follow the instruction ">}}

 this command will provide us the password. copy this password in secure place this will need in next step

 * for open the Jenkins on browser copy the Ip of (ec2 server) or which machine we are using for example (http://34.207.143.141:8080/) with 8080 PORT.

   {{< image src="/img/Jenkins/browser.png" caption=" follow the instruction ">}}

* on browser Jenkins opens and need password for open this (here we need the password which we copy from previous step) 

 {{< image src="/img/Jenkins/unlock.png" caption=" follow the instruction ">}}

 * After give the password new page open and ask for which plugins we need choose the suiteable option and click next. installation process start

  {{< image src="/img/Jenkins/getting-started.png" caption=" follow the instruction ">}}

* After installation completed need to give new "user name" , "password" , "full name" , and "email id" . give that information .

  {{< image src="/img/Jenkins/username.png" caption=" follow the instruction ">}}

* Now give the instance configuration as per our requirement or go as it.

{{< image src="/img/Jenkins/configuration.png" caption=" follow the instruction ">}}

* Now jenkins is ready click on start using Jenkins

{{< image src="/img/Jenkins/ready.png" caption=" follow the instruction ">}}

* Start usig Jenkins

{{< image src="/img/Jenkins/Jenkins.png" caption=" follow the instruction ">}}

