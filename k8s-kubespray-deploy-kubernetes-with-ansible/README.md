Deploy kubernetes with kubespray
===

Learning by doing

##### Update

2018/03/28 Azure Meetup #12

# Prerequisites

If you're interested in building your own Kubernetes. Install the following tools we use.

[virtualbox 5.1+](https://www.virtualbox.org/wiki/Downloads) to create VMs, on which we deploy our Kubernetes.

[vagrant 2.0.x+](https://www.vagrantup.com/downloads.html) to control virtualbox to build and manage vms.

[ansible-playbook](http://docs.ansible.com/ansible/latest/intro_installation.html) to run Kubespray playbook to deploy Kuberentes

[kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) to control Kubernetes cluster

```
# Ubuntu
apt-add-repository ppa:ansible/ansible \
  && apt-get update \
  && apt-get install -y python3 ansible
  && pip install netaddr

# Mac
pip install ansible netaddr

# netaddr is required by Kubespray
```

# Kubespay

Clone Kubespray
```
clone https://github.com/kubernetes-incubator/kubespray.git
```

cd kubespray

### Vagrant up VMs

vagrant up

That's it!

### Kubectl

```
kubectl config use-context

kubectl get po
```

# Get to the details

vagrant 

virtualbox vm

generate inventory

ansible-playbook

# More about Kubernetes

Why k8s

### Use case 1: when data scientist wants GPU

Workflow dispatching and resouce management

### Use case 2: when your site grows bigger

Scalibility

[FYI](https://kubernetes.io/docs/concepts/)

# End

