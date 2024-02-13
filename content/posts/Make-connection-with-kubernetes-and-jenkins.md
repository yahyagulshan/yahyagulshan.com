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

{{< image src="/img/Connection/file.png" caption=" follow the instruction ">}}
{{< image src="/img/Connection/file2.png" caption=" follow the instruction ">}}

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

{{< image src="/img/Connection/Jenkins-page.png" caption=" follow the instruction ">}}

### Adding DockerHub Credentials to Jenkins


* Navigate to Manage Jenkins > Manage Credentials.

{{< image src="/img/Connection/docker-credentials.png" caption=" follow the instruction ">}}


* Click "Username and Password" and provide your DockerHub credentials.

### Configuring Kubernetes Plugin in Jenkins

* Navigate to Manage Jenkins > Manage Nodes & Clouds.

* Scroll to the bottom and click "Add a new cloud". Select "Kubernetes".

### Convert the Minikube CA certificate to Base64 encoding:

**Bash**
`cat /home/devyan/.minikube/ca.crt | base64 -w 0; echo`

{{< image src="/img/Connection/pic.png" caption=" follow the instruction ">}}

* Use Kubernetes Id(my_kubernetes) which was crated earlier.

* Paste the encoded certificate into the "Kubernetes server certificate key" field.

{{< image src="/img/Connection/id.png" caption=" follow the instruction ">}}

* Save the configuration.

* Verification and Next Steps





                                               

