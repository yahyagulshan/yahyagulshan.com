---
title: "AWS Connect-private-ec2-instance-without-public-ip"
date: 2024-02-22T04:06:22Z
author:
authorLink:
description:
tags:
- EC2
- Private subnet
- without Public Ip
- VPC ec2 instance endpoint


categories:

draft: false
hiddenFromHomePage: true
---

# How to Connect-private-ec2-instance-without-public-ip or Nat gateway in private subnet in AWS

### Before you begin: ✍️

* We must have EC2 instance running (which has no public ip and in private subnet)

* we have I am user (AWS_ACCESS_KEY_ID & AWS_SECRET_ACCESS_KEY_ID)

* User have permission on EC2.

**Step 1** 🔨

* Open AWS VPC console

* and click on Endpoints .

![image](https://github.com/yahyagulshan/linuxnotes/assets/59036269/d617765c-29b9-4d82-b2b7-63d9b35c729a)

* Click on create endpoint.

![image](https://github.com/yahyagulshan/linuxnotes/assets/59036269/d4eb9b9e-63f0-436b-afc9-3316748d1595)

* Now give the name choose service category select VPC

![image](https://github.com/yahyagulshan/linuxnotes/assets/59036269/aa19dde7-577f-4fa7-8234-6e4a8cacff8f)

* Select Security group and Subnet and press on create end point

![image](https://github.com/yahyagulshan/linuxnotes/assets/59036269/6c02ccd7-7022-496e-b743-0691cf944826)

* it will take some time to create.

**Step 2** 🔨
### Connect to your Linux instance using the Amazon EC2 console

* Open the Amazon EC2 console

* Select the instance, choose Connect, and then do the following:

![image](https://github.com/yahyagulshan/linuxnotes/assets/59036269/0fc40daa-63b1-444d-b621-f812219c3cb1)

* Choose the EC2 Instance Connect tab.

* For Connection type, choose Connect using EC2 Instance Connect Endpoint.

* For User name, verify the user name.

* For Max tunnel duration (seconds), enter the maximum allowed duration for the SSH connection.

* The duration must comply with the maxTunnelDuration condition specified in the IAM policy. If you don't have access to the IAM policy, ask your administrator to verify it. If maxTunnelDuration is not specified in the IAM policy, enter the default, which is 3600 seconds (1 hour).

* For EC2 Instance Connect Endpoint, choose the EC2 Instance Connect Endpoint in the instance’s VPC.

* Choose Connect to open a terminal window.

### Connect to your Linux instance using SSH 💻

**Single connection**

* To allow only a single connection to an instance using SSH and the open-tunnel command

      ssh -i my-key-pair.pem ec2-user@i-0123456789example \
      -o ProxyCommand='aws ec2-instance-connect open-tunnel --instance-id i-0123456789example'

* For:

* -i – Specify the key pair that was used to launch the instance.

* ec2-user@i-0123456789example – Specify the username of the AMI that was used to launch the instance, and the instance ID.

* --instance-id – Specify the ID of the instance to connect to. Alternatively, specify %h, which extracts the instance ID from the user.

**Multi-connection**

* 1- Run the following command to start listening for new TCP connections on the specified port on your local machine.

      aws ec2-instance-connect open-tunnel \
      --instance-id i-0123456789example \
      --local-port 8888

👇: Expected output  👇  

    Listening for connections on port 8888.

* In a new terminal window, run the following ssh command to create a new TCP connection and a private  tunnel to your instance.

      ssh -i my-key-pair.pem ec2-user@localhost -p 8888


👇: Expected output  👇

    Accepted new tcp connection, opening websocket tunnel.

You might also see the following:🥸

Closing tcp connection.