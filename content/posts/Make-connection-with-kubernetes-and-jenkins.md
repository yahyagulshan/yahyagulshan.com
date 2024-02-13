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

# For make connection between Kubernetes and Jenkins

## Prerequset 

* Jenkins is installed on Linux(ubuntu) machine and minikube is running .

### Plugins required 

* Docker

* Docker Pipeline

* Kubernetes

### Creating a service account with secret for kubernetes-plugin in minikube

* Create a file called `account.yaml` .

---

{{< image src="/img/Connection/file.png" caption=" follow the instruction ">}}
{{< image src="/img/Connection/file2.png" caption=" follow the instruction ">}}

for file [file](https://yahyagulshan.com/posts/file-content-(account.yaml))

* Now run the below command

`kubectl apply -f account.yaml`

### Save secret token data, we need it while configure Kubernetes credentials in Jenkins

* to get secret token

`kubectl get secrets`

* get secret data run below command

`kubectl describe secrets/jenkins-token`

*  copy the token and save it in secure place

* now open Jenkins (In Jenkins click on Manage Jenkins → Manage Credentials)

* Secret: token string , Paste token data in a secret field

* create Kubernetes Id (my_kubernetes)with token data(token string )

{{< image src="/img/Connection/Jenkins-page.png" caption=" follow the instruction ">}}

* Save DockerHub credentials in a Jenkins

{{< image src="/img/Connection/docker-credentials.png" caption=" follow the instruction ">}}

* Configuring Kubernetes plugin 

`Jenkins — manage Jenkins — Manage Nodes & Clouds`  (Configure system scroll to bottom and in Add a new cloud, select Kubernetes)

* Convert certificate info into base64 encoding and paste it in a field ( Kubernetes server certificate key)

`cat /home/devyan/.minikube/ca.crt | base64 -w 0; echo`

{{< image src="/img/Connection/pic.png" caption=" follow the instruction ">}}

* Use Kubernetes Id(my_kubernetes) which was crated earlier.

{{< image src="/img/Connection/id.png" caption=" follow the instruction ">}}

* Now our connection is establish





                                               

