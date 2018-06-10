Kubernetes Network
===

Build our network service from Pod step by step

[kubernetes service](https://kubernetes.io/docs/concepts/services-networking/service/)

[Flannel](https://github.com/coreos/flannel)

# Docker 
Docker uses host-private networking, so containers can talk to other containers only if they are on the same machine

# Node
- Has IP before kubernetes cluster
- Kubernetes provide hostname dns in cluster with kube-dns

telnet a node's name
test a kube-dns with debug mode

# Pod
- Assign with an IP when created. Pod IP is an existing IP on a network device(real/virtual), maitained by flannel.
- Mortal.
- Deployment / Replica Set to revive Pod. IP changed after Pod died. -> this is bad

telnet a Pod's ip
telnet a Pod's name
telnet a Pod's dns
a pod with IP 1.2.3.4 in the namespace default with a DNS name of cluster.local would have an entry: 1-2-3-4.default.pod.cluster.local

# Service
A Kubernetes Service is an abstraction which defines a logical set of Pods and a policy by which to access them - sometimes called a micro-service.
- label selector 
- service.dns -> Pod(s) with label
- assigned an IP address, cluster IP. Cluster IP setup by kube-proxy and load balance to Pod. It is not a actual IP on any device.

Unlike Pod IP addresses, which actually route to a fixed destination, Service IPs are not actually answered by a single host. Instead, we use iptables (packet processing logic in Linux) to define virtual IP addresses 

my-svc.my-namespace.svc.cluster.local

# Access Pod
https://kubernetes.io/docs/concepts/services-networking/connect-applications-service/

### Type of Service
- ClusterIP: Exposes the service on a cluster-internal IP. Choosing this value makes the service only reachable from within the cluster. This is the default ServiceType.
- NodePort: Exposes the service on each Node’s IP at a static port (the NodePort). A ClusterIP service, to which the NodePort service will route, is automatically created. You’ll be able to contact the NodePort service, from outside the cluster, by requesting <NodeIP>:<NodePort>.
- LoadBalancer: Exposes the service externally using a cloud provider’s load balancer. NodePort and ClusterIP services, to which the external load balancer will route, are automatically created.
- ExternalName: Maps the service to the contents of the externalName field (e.g. foo.bar.example.com), by returning a CNAME record with its value. No proxying of any kind is set up. This requires version 1.7 or higher of kube-dns

### Kube-proxy
The Kubernetes network proxy runs on each node, and reflects services as defined in the Kubernetes API on each node and can do simple TCP and UDP stream forwarding or round robin TCP and UDP forwarding across a set of backends.

[Kube-proxy](https://kubernetes.io/docs/reference/command-line-tools-reference/kube-proxy/)
https://vitalflux.com/quick-glance-at-kubernetes-architectural-building-blocks/

- --service-cluster-ip-range=10.0.0.0/1
- Proxy-mode: userspace
- Proxy-mode: iptables

- Cluster IP is inside cluster. To access from outside, type it as a NodePort
- NodePort is a port open on every node

 In Kubernetes v1.1, the Ingress API was added (beta) to represent “layer 7”(HTTP) services

### Services Discovering

domain -> IP is work. How am I find what service domain is on?

Environment variables
DNS

kube-dns 
https://kubernetes.io/docs/concepts/services-networking/dns-pod-service/

# Debug

Enjoy

iptables in pod
iptables in node - unlikely. but it happens

busybox inside cluster and ping/telnet
diff your error yaml with a working yaml set
