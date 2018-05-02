Deploy High Availability Kubernetes Cluster On Cloud 
===

# Components of Kubernetes

kubelet

etcd

kube-apiserver

kube-controller-manager

kube-proxy

kube-scheduler


### Kubelet

A node agent runs on each node

Takes PodSpecs (mostly from apiserver) and create pod.

https://kubernetes.io/docs/reference/generated/kubelet/

### kube-apiserver

kubectl -> (api requests) -> kube-apiserver -> kubelet

### kube-proxy

iptables -> 
dns

### Kube-scheduler

policy, topology, workload -> availibility, performance, capacity

### etcd

persistent data about Kubernetes cluster

# Components for High Availibility Kubernetes
