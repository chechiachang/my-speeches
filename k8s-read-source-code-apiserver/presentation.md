autoscale: true
footer: Che-Chia David Chang, 2018,  [https://github.com/chechiachang](https://github.com/chechiachang)
slidenumbers: true

# Read Source Code: Kubernetes API server

---

David Chang
Back-End Developer, Kuberentes admin, DevOps

![inline](../images/davidchang.jpg)

---

# Ways to Read Source Code

[https://github.com/kubernetes/kubernetes](https://github.com/kubernetes/kubernetes)

1. Read everything line by line. Never done before :P
2. Read some interesting part like:
  - How to access with client
  - Authentication and Authorization
  - Big picture (Architecture)
  - Go through workflow for one API

--- 

# Outline

1. Let's use kube-apiserver
2. Let's read api code
  - How to run apiserver

![inline](../images/kubernetes.png)

---

# Kube-apiserver The Easy Way

[Official Tutorial: Access API](https://kubernetes.io/docs/tasks/administer-cluster/access-cluster-api)

[What happens when k8s](https://github.com/jamiehannaford/what-happens-when-k8s)

Need a running kubernetes? Use This:
[Katacoda](https://www.katacoda.com/courses/kubernetes/playground)

---

# First API call

Kubectl
```
kubectl proxy --port=8080 &
curl http://localhost:8080/api/
```

Curl
```
APISERVER=$(kubectl config view | grep server | cut -f 2- -d ":" | tr -d " ")
TOKEN=$(kubectl describe secret $(kubectl get secrets | grep default | cut -f1 -d ' ') | grep -E '^token' | cut -f2 -d':' | tr -d '\t')
curl $APISERVER/api --header "Authorization: Bearer $TOKEN" --insecure
```

---

# Go client

Programmatic access to the API with libraries
- Suport Go and Python

```
go get https://github.com/kubernetes/client-go

import (
   "k8s.io/client-go/1.4/kubernetes"
   "k8s.io/client-go/1.4/pkg/api/v1"
   "k8s.io/client-go/1.4/tools/clientcmd"
)
   // uses the current context in kubeconfig
   config, _ := clientcmd.BuildConfigFromFlags("", "path to kubeconfig")
   // creates the clientset
   clientset, _:= kubernetes.NewForConfig(config)
   // access the API to list pods
   pods, _:= clientset.CoreV1().Pods("").List(v1.ListOptions{})
```
---

# Kubectl

1. Ensure client-side fail fast
2. Authentication

---

# How to run a apiserver

Source code

https://github.com/kubernetes/kubernetes/blob/master/cmd/kube-apiserver/apiserver.go

---

# Check a running kube-apiserver

```
kubectl describe po kube-apiserver-master -n kube-system
```

---

# What happens when kube-apiserver run

