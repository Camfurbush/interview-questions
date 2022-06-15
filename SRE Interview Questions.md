# SRE Interview Questions

This page covers some different questions and categories an SRE might be expected to know

- [SRE Interview Questions](#sre-interview-questions)
  - [SRE Specific](#sre-specific)
    - [How and why would you use error budgets?](#how-and-why-would-you-use-error-budgets)
    - [Explain Blue-Green Deployment Technique](#explain-blue-green-deployment-technique)
    - [What are some common deployment strategies?](#what-are-some-common-deployment-strategies)
      - [Blue/Green](#bluegreen)
      - [Canary](#canary)
      - [Rolling](#rolling)
    - [What is an SLA/SLI/SLO and how do they relate to each other](#what-is-an-slaslislo-and-how-do-they-relate-to-each-other)
    - [What are the differences between continuous integration, continuous delivery, and continuous deployment](#what-are-the-differences-between-continuous-integration-continuous-delivery-and-continuous-deployment)
  - [Ansible](#ansible)
    - [How does Ansible work?](#how-does-ansible-work)
    - [What is the difference between pull-based and push-based architecture](#what-is-the-difference-between-pull-based-and-push-based-architecture)
    - [Can you explain is idempotence is or what it means when something is idempotent](#can-you-explain-is-idempotence-is-or-what-it-means-when-something-is-idempotent)
    - [What is immutability](#what-is-immutability)
  - [Terraform](#terraform)
    - [Can you explain what Infrastructure as Code and why its important](#can-you-explain-what-infrastructure-as-code-and-why-its-important)
    - [Whats the first command you run when start a terraform project](#whats-the-first-command-you-run-when-start-a-terraform-project)
    - [What are the most useful Terraform commands?](#what-are-the-most-useful-terraform-commands)
    - [What is the terraform state file and why is it important](#what-is-the-terraform-state-file-and-why-is-it-important)
    - [How would you store your terraform state](#how-would-you-store-your-terraform-state)
    - [What is a terraform backend](#what-is-a-terraform-backend)
    - [What is State File Locking?](#what-is-state-file-locking)
    - [Linux](#linux)
    - [What is a “/proc” file system?](#what-is-a-proc-file-system)
    - [What is a Zombie Process?](#what-is-a-zombie-process)
    - [What is the load average?](#what-is-the-load-average)
    - [Commands](#commands)
      - [How do you view the files in the current directory?](#how-do-you-view-the-files-in-the-current-directory)
      - [How do you view the current kernel version?](#how-do-you-view-the-current-kernel-version)
      - [How do you view the current running processes?](#how-do-you-view-the-current-running-processes)
      - [Where are common log files located?](#where-are-common-log-files-located)
      - [How do you view available memory?](#how-do-you-view-available-memory)
      - [How do you view current CPU load?](#how-do-you-view-current-cpu-load)
      - [How do you view current disk usage](#how-do-you-view-current-disk-usage)
    - [Scenario Based Questions](#scenario-based-questions)
  - [Docker](#docker)
    - [What is Docker?](#what-is-docker)
    - [What are docker images?](#what-are-docker-images)
    - [What can you tell about Docker Compose?](#what-can-you-tell-about-docker-compose)
    - [Differentiate between COPY and ADD commands that are used in a Dockerfile?](#differentiate-between-copy-and-add-commands-that-are-used-in-a-dockerfile)
    - [Can you tell the difference between CMD and ENTRYPOINT?](#can-you-tell-the-difference-between-cmd-and-entrypoint)
    - [How would you download a remote docker image to your machine](#how-would-you-download-a-remote-docker-image-to-your-machine)
    - [How do you create a docker container from an image?](#how-do-you-create-a-docker-container-from-an-image)
    - [How would you connect to a running container](#how-would-you-connect-to-a-running-container)
    - [How do you list all running docker images](#how-do-you-list-all-running-docker-images)
    - [How would you build and deploy a custom docker image](#how-would-you-build-and-deploy-a-custom-docker-image)
    - [Dockerfile](#dockerfile)
    - [How do you keep docker images lightweight?](#how-do-you-keep-docker-images-lightweight)
    - [What is a multi-stage docker build and whats the benefit?](#what-is-a-multi-stage-docker-build-and-whats-the-benefit)
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
  - [Recommended Resources](#recommended-resources)
    - [Courses](#courses)
    - [Articles](#articles)
    - [Books](#books)
  - [References](#references)

## SRE Specific

### How and why would you use error budgets?

- An error budget is the amount of acceptable unreliability a service can have before customer happiness is impacted.
- If a service is well within its budget, the developers can take more risks in their releases.
- If not, developers need to make safer choices.

### Explain Blue-Green Deployment Technique

- Blue-green deployment is a technique that reduces downtime and risk by running two identical production environments called Blue and Green. At any time, only one of the environments is live, with the live environment serving all production traffic. For this example, Blue is currently live and Green is idle.
- As you prepare a new version of your software, deployment and the final stage of testing takes place in the environment that is not live: in this example, Green. Once you have deployed and fully tested the software in Green, you switch the router so all incoming requests now go to Green instead of Blue. Green is now live, and Blue is idle.
- This technique can eliminate downtime due to application deployment. In addition, blue-green deployment reduces risk: if something unexpected happens with your new version on Green, you can immediately roll back to the last version by switching back to Blue.

### What are some common deployment strategies?

#### Blue/Green

- Blue-green deployments are a pattern whereby we reduce downtime during production deployments by having two separate production environments ("blue" and "green").

#### Canary

- Canary deployments are a pattern for rolling out releases to a subset of users or servers.
- The idea is to first deploy the change to a small subset of servers, test it, and then roll the change out to the rest of the servers.
- The canary deployment serves as an early warning indicator with less impact on downtime: if the canary deployment fails, the rest of the servers aren't impacted.

#### Rolling

- Rolling deployments are a pattern whereby, instead of deploying a package to all servers at once, we slowly roll out the release by deploying it to each server one-by-one.
- In load balanced scenarios, this allows us to reduce overall downtime.

### What is an SLA/SLI/SLO and how do they relate to each other

- An SLA (service level agreement) is an agreement between provider and client about measurable metrics like uptime, responsiveness, and responsibilities.
- An SLO (service level objective) is an agreement within an SLA about a specific metric like uptime or response time
- An SLI (service level indicator) measures compliance with an SLO (service level objective).
  ![slaieou](https://wac-cdn.atlassian.com/dam/jcr:2c63228d-0dbd-4b8c-b44b-c8514c835905/slo-vs-sla-vs-sli-1.jpg?cdnVersion=322)

### What are the differences between continuous integration, continuous delivery, and continuous deployment

- Developers practicing continuous integration merge their changes back to the main branch as often as possible. By doing so, you avoid the integration hell that usually happens when people wait for release day to merge their changes into the release branch.
- Continuous delivery is an extension of continuous integration to make sure that you can release new changes to your customers quickly in a sustainable way. This means that on top of having automated your testing, you also have automated your release process and you can deploy your application at any point of time by clicking on a button.
- Continuous deployment goes one step further than continuous delivery. With this practice, every change that passes all stages of your production pipeline is released to your customers. There's no human intervention, and only a failed test will prevent a new change to be deployed to production

## Ansible

### How does Ansible work?

- Ansible is a combination of multiple pieces working together to become an automation tool. Mainly these are modules, playbooks, and plugins.
- Modules are small codes that will get executed. There are multiple inbuilt modules that serve as a starting point for building tasks.
- Playbooks contain plays which further is a group of tasks. This is the place to define the workflow or the steps needed to complete a process
- Plugins are special kinds of modules that run on the main control machine for logging purposes. There are other types of plugins also.

### What is the difference between pull-based and push-based architecture

- Pull Model: The nodes are dynamically updated by pulling the latest configuration from a centralized server.
- Push Model: Centralized server pushes the configurations to the nodes

### Can you explain is idempotence is or what it means when something is idempotent

- The term idempotence means that when changes are applied multiple times, the state is mutated (changed) just once. First, it already assumes that there are going to be changes applied which means that you cannot have something both immutable and have idempotent actions done to it (no actions are done to it by contract).

- In the use of configuration management tools, idempotence is used in some cases when applying the same change multiple times. Like adding the line that says localhost to the /etc/hosts file, you don't really need multiple such lines and if one already exists it is safe to not try to append again.

### What is immutability

- Immutability, which literally means "no mutations" or "no changes". In the DevOps sense, it means that once you created an artifact, be that a container image, or a VM image, or maybe a package from compiled code - you declare that you will never ever change it. Often if any changes are required, you declare that a new version of "thing" will be created instead.

## Terraform

### Can you explain what Infrastructure as Code and why its important

- Infrastructure as Code or IaC is a process that DevOps teams should follow to have a more organized way of managing the infra. Instead of some throwaway scripts or manually configuring any cloud component, there should be a code repo where all of these will lie and any change in configuration should be done through it. It is wise to put it under source control also. This improves speed, consistency, and accountability.

### Whats the first command you run when start a terraform project

- terraform init to download the state and any providers

### What are the most useful Terraform commands?

- terraform init - initializes the current directory
- terraform refresh - refreshes the state file
- terraform output - views Terraform outputs
- terraform apply - applies the Terraform code and builds stuff
- terraform destroy - destroys what has been built by Terraform
- terraform graph - creates a DOT-formatted graph
- terraform plan - a dry run to see what Terraform will do

### What is the terraform state file and why is it important

- Terraform must store state about your managed infrastructure and configuration. This state is used by Terraform to map real world resources to your configuration, keep track of metadata, and to improve performance for large infrastructures. This state is stored by default in a local file named "terraform.tfstate".
- This is how terraform knows what actions to perform

### How would you store your terraform state

- You can store your terraform state in the local repository by default, but you should store it somewhere remotely like a backend or github (not for prod)

### What is a terraform backend

- Each Terraform configuration can specify a backend, which defines two main things:
  - Where operations are performed (terraform cloud/enterprise)
  - Where the state is stored
- Preferred backends are Terraform Cloud/Enterprise or Amazon S3 and DynamoDB

### What is State File Locking?

- State file locking is Terraform mechanism in which operations on a specific state file are blocked to avoid conflicts between multiple users performing the same process. When one user releases the lock, then only the other one can operate on that state. This helps in preventing state file corruption. This is a backend operation.

### Linux

### What is a “/proc” file system?

- Proc file system is a pseudo or virtual file system that provides an interface to the kernel data structure. It generally includes useful information about processes that are running currently. It can also be used to change some kernel parameters at runtime or during execution. It is also regarded as a control and information center for the kernel. All files under this directory are named virtual files

### What is a Zombie Process?

- Zombie Process, also referred to as a defunct or dead process in Linux, is a process that has finished the execution, but its entry remains in the process table. It usually happens due to a lack of correspondence between parent and child processes.

### What is the load average?

- As the name suggests, is the average system load on Linux servers being calculated over a given period of time. The load average of Linux servers can be found using “top” and “uptime” commands. It is simply used to keep track of system resources. It is represented by a decimal number starting at 0.00. It tells you the load that the system has been under.
- This should be at roughly 1.0 per CPU.

### Commands

#### How do you view the files in the current directory?

- `ls`

#### How do you view the current kernel version?

- `uname -a`

#### How do you view the current running processes?

- ps aux

#### Where are common log files located?

- /var/log

#### How do you view available memory?

- `free`
- `top`

#### How do you view current CPU load?

- `top`

#### How do you view current disk usage

- df -h
- pvdisplay
- lvdisplay
- lsblk

### Scenario Based Questions

- Sometimes they will ask scenario based questions like:
  - A developer tells you the app server is reporting a 503, how do you investigate
  - Walk through how to resolve it
    - SSH to the server
    - Use systemctl to check the service
    - Check the application logs
    - Investigate error messages
    - etc
- Be comfortable navigating around linux

## Docker

### What is Docker?

- Docker is a containerization platform which packages your application and all its dependencies together in the form of containers so as to ensure that your application works seamlessly in any environment be it development or test or production.
- Docker containers, wrap a piece of software in a complete filesystem that contains everything needed to run: code, runtime, system tools, system libraries etc. anything that can be installed on a server.
- This guarantees that the software will always run the same, regardless of its environment.

### What are docker images?

They are executable packages(bundled with application code & dependencies, software packages, etc.) for the purpose of creating containers. Docker images can be deployed to any docker environment and the containers can be spun up there to run the application.

### What can you tell about Docker Compose?

- It is a YAML file consisting of all the details regarding various services, networks, and volumes that are needed for setting up the Docker-based application. So, docker-compose is used for creating multiple containers, host them and establish communication between them. For the purpose of communication amongst the containers, ports are exposed by each and every container.

### Differentiate between COPY and ADD commands that are used in a Dockerfile?

- Both the commands have similar functionality, but COPY is more preferred because of its higher transparency level than that of ADD.
- COPY provides just the basic support of copying local files into the container whereas ADD provides additional features like remote URL and tar extraction support.

### Can you tell the difference between CMD and ENTRYPOINT?

- CMD command provides executable defaults for an executing container. In case the executable has to be omitted then the usage of ENTRYPOINT instruction along with the JSON array format has to be incorporated.
- ENTRYPOINT specifies that the instruction within it will always be run when the container starts.
  - This command provides an option to configure the parameters and the executables. If the DockerFile does not have this command, then it would still get inherited from the base image mentioned in the FROM instruction.
  - The most commonly used ENTRYPOINT is /bin/sh or /bin/bash for most of the base images.
- As part of good practices, every DockerFile should have at least one of these two commands

### How would you download a remote docker image to your machine

- `docker pull <image_name>`

### How do you create a docker container from an image?

- `docker run -it -d <image_name>`

### How would you connect to a running container

- `docker exec -it <container id> bash`

### How do you list all running docker images

- `docker ps`

### How would you build and deploy a custom docker image

- Open a terminal in the same folder as your Dockerfile

```sh
docker login
docker build .
docker images # get the id of the docker image
docker tag IMAGE_ID NEW_IMAGE_NAME:latest
docker push NEW_IMAGE_NAME:latest
```

### Dockerfile

- Know the components of a Dockerfile and how to make your own
- This uses the ubuntu docker image and installs python and an python app

```Dockerfile
FROM ubuntu
RUN apt-get update && apt-get install curl python
COPY main.py /app/main.py
WORKDIR /app
ENTRYPOINT ["python /app/main.py"]
```

### How do you keep docker images lightweight?

- Disable caching in commands
- Reduce the amount of layers
- Use multi-stage builds
- Run multiple commands on the same line

### What is a multi-stage docker build and whats the benefit?

- A multi-stage docker build is a technique used to keep dockerfiles small.
- An example, use a dockerfile to build the application, then copy the compiled application and place on a lightweight image like alpine to serve the compiled app.

```Dockerfile
# syntax=docker/dockerfile:1

FROM golang:1.16 AS builder
WORKDIR /go/src/github.com/alexellis/href-counter/
RUN go get -d -v golang.org/x/net/html
COPY app.go ./
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o app .

FROM alpine:latest
RUN apk --no-cache add ca-certificates
WORKDIR /root/
COPY --from=builder /go/src/github.com/alexellis/href-counter/app ./
CMD ["./app"]
```

## Kubernetes

### How are Kubernetes and Docker related

- Docker is an open-source platform used to handle software development. Its main benefit is that it packages the settings and dependencies that the software/application needs to run into a container, which allows for portability and several other advantages.
- Kubernetes allows for the manual linking and orchestration of several containers, running on multiple hosts that have been created using Docker.

### What are the main components of a Kubernetes cluster

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

### What does the master node do?

- The master node dignifies the node that controls and manages the set of worker nodes. This kind of resembles a cluster in Kubernetes.
- The nodes are responsible for the cluster management and the API used to configure and manage the resources within the collection.
- The master nodes of Kubernetes can run with Kubernetes itself, the asset of dedicated pods.

### What is a node in Kubernetes?

- A node is the smallest fundamental unit of computing hardware.
- It represents a single machine in a cluster, which could be a physical machine in a data center or a virtual machine from a cloud provider.
- Each machine can substitute any other machine in a Kubernetes cluster.
- The master in Kubernetes controls the nodes that have containers.

### What process runs on Kubernetes Master Node?

- The Kube-api server process runs on the master node and serves to scale the deployment of more instances.

### What is a pod in Kubernetes?

- In this Kubernetes interview question, try giving a thorough answer instead of a one-liner.
- Pods are high-level structures that wrap one or more containers. This is because containers are not run directly in Kubernetes.
- Containers in the same pod share a local network and the same resources, allowing them to easily communicate with other containers in the same pod as if they were on the same machine while at the same time maintaining a degree of isolation.

### What is the job of the kube-scheduler?

The kube-scheduler assigns nodes to newly created pods.

### What are Daemon sets?

A Daemon set is a set of pods that runs only once on a host. They are used for host layer attributes like a network or for monitoring a network, which you may not need to run on a host more than once.

### What is Minikube?

- With the help of Minikube, users can Kubernetes locally.
- This process lets the user run a single-node Kubernetes cluster on your personal computer, including Windows, macOS, and Linus PCs.
- With this, users can try out Kubernetes also for daily development work.

### What is a Namespace in Kubernetes?

- Namespaces are used for dividing cluster resources between multiple users.
- They are meant for environments where there are many users spread across projects or teams and provide a scope of resources.

### What is an Ingress?

- Ingress is a collection of routing rules that decide how the external services access the services running inside a Kubernetes cluster.
- Ingress provides load balancing, SSL termination, and name-based virtual hosting.
- This is typically managed outside of the cluster, nginx is EXTREMELY common

### How do we control the resource usage of POD?

With the use of limit and request resource usage of a POD can be controlled.

### Troubleshooting Scenario

- Need to be familiar with investigating kubernetes cluster and some of the components using kubectl
  - A developer has a pod that won't deploy/update/work, how would you troubleshoot it?
  - How do you get all your running pods
  - How to tell why a container is failing

### Guides

- <https://www.simplilearn.com/tutorials/kubernetes-tutorial?source=sl_frs_nav_playlist_video_clicked>
- <https://kubernetes.io/docs/tasks/debug/debug-application/debug-pods/>
- <https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

## Recommended Resources

### Courses

- <https://kodekloud.com/>

### Articles

- <https://roadmap.sh/devops>
- <https://www.srepath.com/site-reliability-engineering-glossary/>

### Books

- <https://www.amazon.com/Practice-Cloud-System-Administration-Practices/dp/032194318X>
- <https://sre.google/books/>
- <https://www.amazon.com/Accelerate-Software-Performing-Technology-Organizations/dp/1942788339>
- <https://www.amazon.com/Phoenix-Project-DevOps-Helping-Business/dp/0988262592>

## References

- <https://www.interviewbit.com/ansible-interview-questions/>
- <https://www.simplilearn.com/tutorials/kubernetes-tutorial?source=sl_frs_nav_playlist_video_clicked>
- <https://www.simplilearn.com/terraform-interview-questions-and-answers-article>
- <https://www.interviewbit.com/docker-interview-questions/>
