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

<span style="color:blue">apiVersion: v1</span>


<span style="color:red">kind: ServiceAccount</span>

<span style="color:red">metadata:</span>