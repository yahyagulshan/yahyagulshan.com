---
title: "Service File (Account.yaml)"
date: 2024-02-13T04:06:22Z
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
<p>---</p>

<p>apiVersion: v1 </p>
<p>kind: ServiceAccount</p>
<p>metadata:</p>
  <p>name: jenkins</p>
  <p>namespace: default</p>

<p>---</p>

<p>kind: Role</p>
<p>apiVersion: rbac.authorization.k8s.io/v1</p>
<p>metadata:</p>
  <p>name: jenkins</p>
  <p>namespace: default</p>
<p>rules:</p>
<p>- apiGroups: [""]</p>
  <p>resources: ["pods","services"]</p>
  <p>verbs: ["create","delete","get","list","patch","update","watch"]</p>
<p>- apiGroups: ["apps"]</p>
  <p>resources: ["deployments"]</p>
  <p>verbs: ["create","delete","get","list","patch","update","watch"]</p>
<p>- apiGroups: [""]</p>
  <p>resources: ["pods/exec"]</p>
  <p>verbs: ["create","delete","get","list","patch","update","watch"]</p>
<p>- apiGroups: [""]</p>
 <p> resources: ["pods/log"]</p>
  <p>verbs: ["get","list","watch"]</p>
<p>- apiGroups: [""]</p>
  <p>resources: ["secrets"]</p>
 <p> verbs: ["get"]</p>
<p>- apiGroups: [""]</p>
  <p>resources: ["persistentvolumeclaims"]</p>
  <p>verbs: ["create","delete","get","list","patch","update","watch"]</p>
 
<p>---</p>
<p>apiVersion: v1</p>
<p>kind: Secret</p>
<p>metadata:</p>
  <p>name: jenkins-token</p>
  <p>annotations:</p>
    <p>kubernetes.io/service-account.name: jenkins</p>
<p>type: kubernetes.io/service-account-token</p>

<p>---</p>
<p>apiVersion: rbac.authorization.k8s.io/v1</p>
<p>kind: RoleBinding</p>
<p>metadata:</p>
  <p>name: jenkins</p>
  <p>namespace: default</p>
<p>roleRef:</p>
  <p> apiGroup: rbac.authorization.k8s.io <p>
  <p>kind: Role<p>
 <p> name: jenkins<p>
<p>subjects:<p>
<p>- kind: ServiceAccount
  name: jenkins<p>
---
<p>### Allows jenkins to create persistent volumes
### This cluster role binding allows anyone in the "manager" group to read secrets in any namespace.
kind: ClusterRoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: jenkins-crb
subjects:
- kind: ServiceAccount
  namespace: default
  name: jenkins
roleRef:
  kind: ClusterRole
  name: jenkinsclusterrole
  apiGroup: rbac.authorization.k8s.io
---
kind: ClusterRole
apiVersion: rbac.authorization.k8s.io/v1
metadata:
### "namespace" omitted since ClusterRoles are not namespaced
  name: jenkinsclusterrole
rules:
- apiGroups: [""]
  resources: ["persistentvolumes"]
  verbs: ["create","delete","get","list","patch","update","watch"]<p>