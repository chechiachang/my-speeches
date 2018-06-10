Kubernetes Network
===

[kubernetes service](https://kubernetes.io/docs/concepts/services-networking/service/)

[Flannel](https://github.com/coreos/flannel)

Node
- Has IP before kubernetes cluster
- Kubernetes provide hostname dns in cluster with kube-dns

telnet a node's name
test a kube-dns with debug mode

Pod
- Assign with an IP when created. 
- Mortal.
- Deployment / Replica Set to revive Pod. IP changed after Pod died. -> this is bad

telnet a pod's name

Service
A Kubernetes Service is an abstraction which defines a logical set of Pods and a policy by which to access them - sometimes called a micro-service.
- label selector 
- service.dns -> Pod(s) with label
-  assigned an IP address, cluster IP
