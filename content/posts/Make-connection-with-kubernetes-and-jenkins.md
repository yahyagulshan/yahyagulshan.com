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


                                               

