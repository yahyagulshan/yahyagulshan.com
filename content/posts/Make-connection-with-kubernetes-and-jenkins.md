---
title: "Make connection with kubernetes and jenkins"
date: 2024-02-12T04:06:22Z
author:
authorLink:
description:
tags:
- Kubernetes
- Jenkins
- Connection
- Ubuntu
categories:

draft: false
hiddenFromHomePage: true
---

# This document outlines the steps to connect Kubernetes and Jenkins on a Linux (Ubuntu) machine with Minikube running.

## Prerequisites: 

* Jenkins installed on a Linux (Ubuntu) machine.

* Minikube running on the same machine.


### Required Plugins:

* Docker

* Docker Pipeline

* Kubernetes

### Creating a Service Account and Secret for Kubernetes Plugin in Minikube

* Create a file named account.yaml with the following content:

---

![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/332a4a5a-5751-4954-8fc0-541cd1c0e455)

![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/f18a363a-edc0-4863-8f30-390a92c62ab1)


for file [file](https://yahyagulshan.com/posts/file-content-(account.yaml))

* Run the following command:

`kubectl apply -f account.yaml`

### Save the secret token data for configuring Kubernetes credentials in Jenkins:

* Run `kubectl get secrets` to list secrets.

* Run `kubectl describe secrets/jenkins-token` to get the token data .

*  Copy the token and store it securely.

### Adding Kubernetes Credentials to Jenkins

* Open Jenkins and navigate to Manage Jenkins > Manage Credentials.

* Click "Secret Text" and paste the copied token into the field.

* Create a Kubernetes ID named "my_kubernetes" with the token as credentials.

![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/f6148637-19c5-4349-9348-e907ab1157b8)


### Adding DockerHub Credentials to Jenkins


* Navigate to Manage Jenkins > Manage Credentials.

![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/6873ea53-690d-4529-9f65-e5035d05cc0a)



* Click "Username and Password" and provide your DockerHub credentials.

### Configuring Kubernetes Plugin in Jenkins

* Navigate to Manage Jenkins > Manage Nodes & Clouds.

* Scroll to the bottom and click "Add a new cloud". Select "Kubernetes".

### Convert the Minikube CA certificate to Base64 encoding:

**Bash**
`cat /home/devyan/.minikube/ca.crt | base64 -w 0; echo`

![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/b669f786-c427-43c1-ae46-0729a30e991e)


* Use Kubernetes Id(my_kubernetes) which was crated earlier.

* Paste the encoded certificate into the "Kubernetes server certificate key" field.

![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/175f251a-893a-4326-bc9b-f9546b1fc2e3)


* Save the configuration.

* Verification and Next Steps





                                               

