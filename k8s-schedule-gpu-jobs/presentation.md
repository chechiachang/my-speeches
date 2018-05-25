Manage and Schedule GPU Computing Tasks on Kubernetes
===

# 

Begin with a not-so-basic user scenario...

GPU

# Our user story

Data scientists want GPUs

Data processing job consumes:
- CPU, Memory for OS and routine operations
- GPU, as the main computing power
- Time, "Uh...not sure how long it takes..."
- Storage, a lot of "fast" storage

CPU and Memory, we have OS take care of that

It's hard to share GPU resource between (data processing) jobs

# Our goal

Job queue
Prioritize
Maximize production

More automation, less munual labor

# How kubernetes deal with our problem

# (Optional) A simple intro about docker

# A simple intro about k8s

Kubernetes in one-line: 
  an automated container deployment, scaling, and management orchestration

https://kubernetes.io/

# Picture about Architeture

Scheduler
APIserver

# Back to our case: a simple GPU job

put GPU job (your tensorflow code maybe) into a Pod spec
Kubernetes will find suitable (with GPU) node to run this Pod

# Workflow about how to use it

Let's deploy a mongo db
- apply a Pod

Let's deploy a mongo db cluster
- load balancer
- health check
- auto scaling

# Back to our case: GPU workflow

Scheduling

# Back to our case: a more complicated GPU job

# Back to our case: GPU job a real business case

A user interface to schedule job | for data scientists
A server provides user interface, addtional services, resource management | engineer
- Network Storage System
A kuberentes cluster | Kubernetes admin
Bare metal servers with GPU | System admin

# A big picture of Solution based on kubernetes

Efforts
- deploy a kubernetes cluster
- [Enable GPU] (https://kubernetes.io/docs/tasks/manage-gpus/scheduling-gpus/)
- Schedule job
- Get results

