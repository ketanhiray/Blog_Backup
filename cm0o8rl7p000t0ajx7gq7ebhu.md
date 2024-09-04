---
title: "Understanding Kubernetes Architecture: Day 30"
seoTitle: "Kubernetes Architecture Deep Dive"
seoDescription: "Learn Kubernetes architecture, components, benefits, control plane roles, API server, kubelets, and kubectl for efficient container management"
datePublished: Wed Sep 04 2024 19:18:42 GMT+0000 (Coordinated Universal Time)
cuid: cm0o8rl7p000t0ajx7gq7ebhu
slug: understanding-kubernetes-architecture-day-30
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1725477418059/1c54fe3a-27d5-4337-b352-b1fe81735614.png
tags: kubernetes, 2articles1week, kubernetes-architecture, 90daysofdevops

---

## **Kubernetes Overview**

With the widespread use of containers, Kubernetes is now the main tool for managing and organizing containerized applications. It is a key part of the DevOps world, helping with the deployment, scaling, and management of applications. Originally created at Google and released as open-source in 2014, Kubernetes is based on 15 years of Google's experience in handling containerized workloads, with major help from the open-source community. Its design is inspired by Google's internal system, Borg.

# **What is Kubernetes?**

Kubernetes, or K8s, is an open-source platform that automates the deployment, scaling, and operation of application containers. The name K8s is a shorthand for Kubernetes, replacing the eight letters "ubernete" with the number 8. This platform makes it easier to manage containers in various environments, from development to production.

## What are the benefits of using k8s?

1. **Scalability**: Kubernetes lets applications scale easily based on demand. It automatically adjusts the number of running containers to match the current load, making sure resources are used efficiently.
    
2. **High Availability and Reliability**: By spreading applications across multiple containers and nodes, Kubernetes ensures high availability; if a container or node fails, Kubernetes automatically replaces or reschedules the workload, keeping the service running.
    
3. **Automated Rollouts and Rollbacks**: Kubernetes provides automated processes for updating applications without downtime. It can handle the rollout of new versions, check the application's health, and roll back if there are any issues.
    
4. **Self-Healing**: Kubernetes can automatically restart failed containers, replace them, kill unresponsive containers, and keep them out of service until they are ready.
    
5. **Efficient Resource Utilization**: Kubernetes makes the best use of resources by automatically scheduling containers based on their needs and the available resources in the cluster.
    
6. **Multi-Cloud and Hybrid Deployments**: Kubernetes offers a consistent platform across different environments, including on-premises, public, and private clouds, supporting multi-cloud and hybrid cloud strategies.
    

## Explain the architecture of Kubernetes.

### **Kubernetes Architecture**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1725385938744/661910ec-0bf1-4725-8c6d-39de8de5924f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1725386805729/36144962-c697-499f-8b4a-ed0f2174b401.png align="center")

Understanding the architecture of Kubernetes is key to using it well. The architecture is built around a cluster, which includes several worker machines called nodes that run containerized applications. The cluster is managed by the Kubernetes control plane, which handles all activities within the cluster, like scheduling applications, keeping them in their desired state, scaling them, and rolling out updates.

### **Components:**

* **Control Plane(Master Node)**: The control plane is the brain of the Kubernetes cluster, managing the worker nodes and the Kubernetes runtime. Key components of the control plane include the **<mark>API server, etcd</mark>** (a consistent and highly available key-value store), the **<mark>scheduler</mark>**, and the **<mark>controller manager</mark>**.
    
* **Worker Nodes**: Also known as worker machines, nodes are where the containerized applications run. Each node has a **<mark>Kubelet</mark>** (an agent that talks to the control plane), **<mark>a container runtime or pod</mark>** (like Docker), and a **<mark>kube-proxy or service proxy</mark>** (which manages network rules and enables communication).
    

## What is a Control Plane?

The control plane keeps the cluster in the desired state, managing which applications run and which container images they use. It makes decisions for the whole cluster, like scheduling, and reacts to events in the cluster, such as starting a new pod if the number of replicas is too low.

## Control Plane Components(Master Node)

**<mark>API Server</mark>:** This is the "front desk" of Kubernetes. Whenever we want to interact with our cluster, our request goes through the API Server. It checks and processes these requests to the backend components.

**<mark>etcd</mark>:** Think of etcd as the "database" of Kubernetes; it stores all the information about our cluster, including which nodes are part of the cluster, what pods are running, their statuses, and more.

**<mark>Scheduler</mark>:** The Scheduler is like the "event planner" for our containers. When we request a container to be run, the Scheduler decides which machine (Node) in our cluster should run it, taking into account resource availability and other constraints.

**<mark>Controller Manager: </mark>** Imagine a bunch of small robots that continuously monitor the cluster to make sure everything is running smoothly; if something goes wrong (e.g., a Pod crashes), they work to fix it, ensuring the cluster state matches our desired state..

**<mark>Cloud Controller Manager: </mark>** This is a specialized component that allows Kubernetes to interact with the underlying cloud provider, like AWS or Azure, helping with tasks such as setting up load balancers and persistent storage.

## Write the difference between kubectl and kubelets.

* **<mark>kubectl</mark>**: This is the command-line tool for interacting with the Kubernetes API server. It allows users to deploy applications, inspect and manage cluster resources, and view logs.
    
* **<mark>Kubelet</mark>**: This is an agent that runs on each node in the Kubernetes cluster. It ensures that containers are running in a pod. Kubelet gets instructions from the control plane to ensure the containers are running as expected.
    

## Role of the API Server

The API server is a key component of the Kubernetes control plane, exposing the Kubernetes API, which serves as the front end for the control plane. It handles requests from users, tools, and components, providing the means to manage all resources in the cluster. The API server processes REST operations, validates them, and updates the corresponding objects in etcd, enabling other components to interact with the data.

## Conclusion

Kubernetes has changed how we deploy, scale, and manage applications. Its strong architecture and features like self-healing, scalability, and automated rollouts make it essential for DevOps. Knowing its architecture and components like the control plane, kubectl, kubelets, and the API server is key to using it effectively.