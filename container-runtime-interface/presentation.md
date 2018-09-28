Kubernetes Container Runtime Interface
===

# Session Objective

1. How to run Kubernetes without Docker

2. Understand the following terms and their relations
- Container Runtime
- CRI
- CRI-O

# CRI
Container Runtime Interface
https://kubernetes.io/blog/2016/12/container-runtime-interface-cri-in-kubernetes/

# Projects to 'Run' container

- Docker - application container runtime
- rkt - containers runtime runs on Pod level
- LXC/LXD - Linux container
- runC - low level cmd tool to spawn CRI standard container
- containerd - daemon to control runC
- OpenVZ - run full system containers
- systemd-nspawn - run full system containers
- machinectl - run full system containers
- qemu-kvm, lkvm - user namespaces control tool

Those projects are not exclusive. They work together. 
ex. Docker has runC and containerd. LXC was Docker's default execution environment.

# What's wrong with Docker

From rkt to compare other container
https://coreos.com/rkt/docs/latest/rkt-vs-other-projects.html

Dockerd is bind to socket and always need sudo. Check this 
https://askubuntu.com/questions/477551/how-can-i-use-docker-without-sudo

And Docker official docs about security
https://docs.docker.com/engine/security/security/

Watch out privileged in your docker run / yaml file
--privileged -> container run as root user

# CRI stack

Kubernetes 
kubelet - a k8s agent to run on each server to 'control' container runtime
CRI
Container Runtimes - 

# RKT (Rocket)


# RKT Stack

# OCI & CRI-O

OCI - Open Container Initiative

CRI-O - based implementation for Container Runtime Interface

http://cri-o.io/
https://github.com/kubernetes-sigs/cri-o

My-Container-Runtime + CRI-O plugin = Kubernetes

# New Stack

Kubernetes
Kubelet
OCI
Docker / OCI-daemon
Container
Linux

# Sum

- Container Runtime
- CRI
- CRI-O

# References

https://kubernetes.io/blog/2017/11/containerd-container-runtime-options-kubernetes/
https://xuxinkun.github.io/2017/12/12/docker-oci-runc-and-kubernetes/
https://www.kubernetes.org.cn/1079.html
https://jimmysong.io/posts/kubernetes-open-interfaces-cri-cni-csi/
