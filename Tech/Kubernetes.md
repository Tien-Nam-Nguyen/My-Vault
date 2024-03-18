---
type:
  - Tech
tags:
  - Container
  - Docker
  - Kubernetes
published: true
created: 2023-10-24 23:36
modified: 2023-10-25T11:13:00
folder: Tech
---
# What is Kubernetes?
	Kubernetes(K8s), orchestrates containerized applications to run on a cluster of hosts. The K8s system automates the deployment and management of cloud native application. It distributes application across K8s cluster and automates dynamic container networking needs. K8s also allocates storage and persistent volumes.

# Kubernetes features
- **Auto-scaling**: scale containerized applications and their resources up or down based on usage.
- **Lifecycle management**: automate deployments and updates with ability: rollback to previous versions and pause/continue deployment
- **Declarative model**: declare the desired state, K8s works in the background to maintain that state and recover from any failures
- **Resilence and self-healing**: auto placement, auto restart, auto replication and auto scaling provide application self-healing.
- **Persistent storage**: ability to mount and add storage dynamically.
- **Load balancing**: K8s supports a varitety of internal and external load balancing options to address diverse needs.

# Architecture
>[!node]
> One master node can one or many worker nodes.
> ![Imgur](https://i.imgur.com/q0vVnBr.png)
## Master node

![Imgur| 230](https://i.imgur.com/3LXWOqD.png)
### API server
API server is an entrypoint to K8s cluster. It use CLI (KubeCtl) to interact cluster.
### Controller manager
Keeps track of whats happening in the cluster.
### Scheduler
Ensures pods placement based on the available resources and workloads .
### Etcd
Hold the current state of a cluster, includes all the configuration data and status data. The backup and restore process is made from the snapshots stored in etcd.

## Worker node
![Imgur](https://i.imgur.com/imXisCE.png)
### Kubelet
A node agent that runs on each node. It register the node with api server, managing pods and their containers. It deals with pods specifications which are defined in YAML. It also checks whether the pods are healthy or not.
### Pod
Pod is an abstraction of a container. One pod can contain many container, but in practice one pod just contain one container. A worker node can have many pods interacting with each other. Pod can have many replicas.
### Service
All pods interact with each other through service. Service is like static ip address. Many pod replicas shares the same service. When a pod is down, service is still there. Service also works like a load balancer.
### Ingress
Ingress is used to route external connections to different services of pods.  
### Volume
Volume is like a outside hard drive which service connects to it to persist the data. 
### Kube Proxy
Kube proxy is a network proxy that runs on each node, implementing part of the K8s service concept. It maintains network rules on nodes. These networks rules allow network communication to pods from network sessions inside or outside of cluster.


# References
<iframe width="560" height="315" src="https://www.youtube.com/embed/s_o8dwzRlu4?si=otWtHpgVrqf-l9Az" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>