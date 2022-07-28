# Kubernetes

- [Kubernetes](#kubernetes)
  - [How are Kubernetes and Docker related](#how-are-kubernetes-and-docker-related)
  - [What are the main components of a Kubernetes cluster](#what-are-the-main-components-of-a-kubernetes-cluster)
  - [What does the master node do?](#what-does-the-master-node-do)
  - [What is a node in Kubernetes?](#what-is-a-node-in-kubernetes)
  - [What process runs on Kubernetes Master Node?](#what-process-runs-on-kubernetes-master-node)
  - [What is a pod in Kubernetes?](#what-is-a-pod-in-kubernetes)
  - [What is the job of the kube-scheduler?](#what-is-the-job-of-the-kube-scheduler)
  - [What are Daemon sets?](#what-are-daemon-sets)
  - [What is Minikube?](#what-is-minikube)
  - [What is a Namespace in Kubernetes?](#what-is-a-namespace-in-kubernetes)
  - [What is an Ingress?](#what-is-an-ingress)
  - [How do we control the resource usage of POD?](#how-do-we-control-the-resource-usage-of-pod)
  - [Troubleshooting Scenario](#troubleshooting-scenario)
  - [Guides](#guides)

## How are Kubernetes and Docker related

- Docker is an open-source platform used to handle software development. Its main benefit is that it packages the settings and dependencies that the software/application needs to run into a container, which allows for portability and several other advantages.
- Kubernetes allows for the manual linking and orchestration of several containers, running on multiple hosts that have been created using Docker.

## What are the main components of a Kubernetes cluster

- Master Node

  - ETCD
    - Stores the configuration details and essential values
  - Scheduler
    - Scheduler assigns the tasks to the worker nodes
  - API Server
    - Kubernetes uses the API server to perform all operations on the cluster
    - It is a central management entity that receives all REST requests for modifications, serving as a frontend to the cluster
  - Kubectl
    - CLI tool to control the Kubernetes cluster manager
  - Controller Manager(s)
    - endpoints controller
    - service accounts controller
    - namespace controller
    - node controller
    - token controller
    - replication controller

- Worker Node
  - Pod
    - A pod is one or more containers controlled as a single application
  - Docker
    - It helps run the applications in an isolated, but lightweight operating environment. It runs the configured pods
    - It is responsible for pulling down and running containers from Docker images
  - Kubelet
    - Service responsible for conveying information to and from to the control plane service
    - The kubelet process is responsible for maintaining the work status and the node server
  - Kubernetes Proxy
    - Acts as a load balancer and network proxy to perform service on a single worker node
    - Manages pods on nodes, volumes, secrets, the creation of new containers, health check-ups, etc.
    - A proxy service that runs on every node that makes services available to the external host

## What does the master node do?

- The master node dignifies the node that controls and manages the set of worker nodes. This kind of resembles a cluster in Kubernetes.
- The nodes are responsible for the cluster management and the API used to configure and manage the resources within the collection.
- The master nodes of Kubernetes can run with Kubernetes itself, the asset of dedicated pods.

## What is a node in Kubernetes?

- A node is the smallest fundamental unit of computing hardware.
- It represents a single machine in a cluster, which could be a physical machine in a data center or a virtual machine from a cloud provider.
- Each machine can substitute any other machine in a Kubernetes cluster.
- The master in Kubernetes controls the nodes that have containers.

## What process runs on Kubernetes Master Node?

- The Kube-api server process runs on the master node and serves to scale the deployment of more instances.

## What is a pod in Kubernetes?

- In this Kubernetes interview question, try giving a thorough answer instead of a one-liner.
- Pods are high-level structures that wrap one or more containers. This is because containers are not run directly in Kubernetes.
- Containers in the same pod share a local network and the same resources, allowing them to easily communicate with other containers in the same pod as if they were on the same machine while at the same time maintaining a degree of isolation.

## What is the job of the kube-scheduler?

The kube-scheduler assigns nodes to newly created pods.

## What are Daemon sets?

A Daemon set is a set of pods that runs only once on a host. They are used for host layer attributes like a network or for monitoring a network, which you may not need to run on a host more than once.

## What is Minikube?

- With the help of Minikube, users can Kubernetes locally.
- This process lets the user run a single-node Kubernetes cluster on your personal computer, including Windows, macOS, and Linus PCs.
- With this, users can try out Kubernetes also for daily development work.

## What is a Namespace in Kubernetes?

- Namespaces are used for dividing cluster resources between multiple users.
- They are meant for environments where there are many users spread across projects or teams and provide a scope of resources.

## What is an Ingress?

- Ingress is a collection of routing rules that decide how the external services access the services running inside a Kubernetes cluster.
- Ingress provides load balancing, SSL termination, and name-based virtual hosting.
- This is typically managed outside of the cluster, nginx is EXTREMELY common

## How do we control the resource usage of POD?

With the use of limit and request resource usage of a POD can be controlled.

## Troubleshooting Scenario

- Need to be familiar with investigating kubernetes cluster and some of the components using kubectl
  - A developer has a pod that won't deploy/update/work, how would you troubleshoot it?
  - How do you get all your running pods
  - How to tell why a container is failing

## Guides

- <https://www.simplilearn.com/tutorials/kubernetes-tutorial?source=sl_frs_nav_playlist_video_clicked>
- <https://kubernetes.io/docs/tasks/debug/debug-application/debug-pods/>
- <https://kubernetes.io/docs/reference/kubectl/cheatsheet/>
