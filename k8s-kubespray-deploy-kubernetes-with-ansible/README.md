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
pip install ansible

port install py27-netaddr

# netaddr is required by Kubespray
```

# Let's get started

```
clone https://github.com/kubernetes-incubator/kubespray.git

cd kubespray
vagrant up
```

That's it! 

This gonna take a while. Let's get to some details.

### Virtualbox

Install [virtualbox 5.1+](https://www.virtualbox.org/wiki/Downloads).

Disadvantage about vbox GUI:

1. Clicking is time-consuming and engineers are lazy. 
2. Bad for automation. 
3. Lack of Scalibility
4. Manual operation could cause mistakes.

A good practice is to Write shell script with VBoxManage, the client of virtualbox

Or even better, use Vagrant
 
### Vagrant

[vagrant 2.0.x+](https://www.vagrantup.com/downloads.html)

Create you VMs with (ruby based) script. 

Bring VMs up & down within only one command

Check the Vagrantfile

### Ansible playbook

Ansible is a IT automation tools

Basically, ansible playbook ssh and execute bash command on servers.

1. Reduce manual efforts. Deliver and deploy faster
2. Install K8s components to each servers and check components status on each step
3. Come with lots of handy tools (like native array supports)
4. Automation is everything

### Kubespay

Deploy k8s with ansible-playbook

Available on AWS, GCE, or baremetal

High Available cluster

Generate inventory file with inventory.py
```
cp -rfp inventory/sample inventory/mycluster

declare -a IPS=(10.10.1.3 10.10.1.4 10.10.1.5)
CONFIG_FILE=inventory/mycluster/hosts.ini python3 contrib/inventory_builder/inventory.py ${IPS[@]}
```

(Optional) Change parameters

deploy
```
ansible-playbook -i inventory/myCluster/hosts.ini cluster.yml
```

### Kubectl

```
kubectl config use-context

kubectl get po
```

### Destroy

Remember to suspend / destroy VMs 
```
vagrant suspend
vagrant destroy
```

# More about Kubernetes

Why k8s

### Use case 1: when data scientist wants GPU

Workflow dispatching and resouce management

### Use case 2: when your site grows bigger

Scalibility

[FYI](https://kubernetes.io/docs/concepts/)

# End


VBoxManage list vms
