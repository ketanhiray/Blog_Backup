---
title: "Day 31 : Easy Steps to Launch a Kubernetes Cluster and Install Nginx"
seoTitle: "Launch Kubernetes Cluster & Install Nginx Easily"
seoDescription: "Learn to set up a local Kubernetes cluster with Minikube and deploy Nginx, effortlessly. Start mastering Kubernetes today!"
datePublished: Mon Sep 09 2024 08:00:10 GMT+0000 (Coordinated Universal Time)
cuid: cm0upq9ap001809mmddmu7xi1
slug: day-31-easy-steps-to-launch-a-kubernetes-cluster-and-install-nginx
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1725868118856/1136bcf7-7ac8-4712-a4c1-c5a4c783bcf2.png
tags: docker, kubernetes, 2articles1week, minikube, 90daysofdevops

---

## Setting Up Kubernetes Locally with Minikube

Minikube is a great tool for anyone wanting to learn Kubernetes. It lets us set up a local Kubernetes cluster, making it perfect for learning, testing, and development.

## What is Minikube?🧊

Minikube is a lightweight version of Kubernetes that lets us run a Kubernetes cluster on our local machine. It works on macOS, Linux, and Windows, and provides all the features of a full Kubernetes cluster in a simpler and faster setup.

#### Key Features:

1. **Cross-Platform**: Works on Linux, macOS, and Windows.
    
2. **Multiple Container Runtimes**: Supports containerd, CRI-O, and Docker.
    
3. **Direct API Endpoints**: Allows quick image loads and builds.
    
4. **Advanced Features**: LoadBalancer, filesystem mounts, network policy.
    
5. **Addons**: Easily install Kubernetes applications like dashboards and metrics servers.
    
6. Supports common CI environments
    
7. Supports the latest Kubernetes release (+6 previous minor versions)
    

## Let's understand the concept **pod**📚

In Kubernetes, **Pods** are the smallest units we can deploy. They contain one or more containers that share network and storage resources. A pod can run a single container, but more complex apps can run multiple containers within the same pod. Essentially, a Pod is a group of containers that share storage and network resources and have a plan for how to run them. The containers in a Pod always run together in the same context, acting as a "logical host" for our application.

## Task-01: Install Minikube on Our Local Machine💻

### ➤To install Minikube, please refer to the official [Minikube Installation Documentation](https://minikube.sigs.k8s.io/docs/start/?arch=%2Fwindows%2Fx86-64%2Fstable%2F.exe+download)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1725720021170/d4c60ad8-f2be-407f-87f9-0b0c95950e4a.png align="center")

### ➤After the installation, let's start Minikube.

```bash
minikube start
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1725721352639/5e43ecb6-2765-4c29-8981-98703013ed70.png align="center")

### ➤check the minikube status

```bash
minikube status
```

### ➤minikube is running

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1725721460717/19afabe1-aeeb-4312-ae70-0d8eaa056963.png align="center")

### ➤We can also start minikube from Docker.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1725722138457/bbc43f2b-cc6a-4dfb-9d3b-31eeb17d4fa3.png align="center")

## Task-02: Create the first pod on Kubernetes through Minikube.📟

### ➤create yaml file for nginx

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80
```

### ➤Apply the configuration to create the pod:

```bash
kubectl apply -f pod.yaml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1725865969064/38cb2f90-fa1a-4e50-83c2-bd5fdca81078.png align="center")

### ➤Verify that the pod is running:

```bash
kubectl get pods
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1725866047208/b2b0745e-bd15-4095-b1d7-b327f4989588.png align="center")

### ➤To access the nginx pod, we can forward the port:

```bash
kubectl port-forward nginx 8080:80
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1725866464952/f34cf3ca-221e-4618-bf62-541ca8a4fdc6.png align="center")

### ➤Visit [`http://localhost:8080`](http://localhost:8080) in our browser to see the nginx welcome page.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1725866431700/1173cc38-9b83-4a8b-b038-1a3148b53d42.png align="center")

### ➤To stop the container, use the following command:

```bash
minikube stop 
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1725866580354/7e5363a4-40f1-4d11-beab-0ce775251592.png align="center")

## Conclusion📝

Kubernetes has changed container management by offering a strong platform for deploying, scaling, and managing containerized apps, making it essential in DevOps. Minikube provides an easy way to try out Kubernetes locally, helping developers and engineers learn and test Kubernetes features like Pods and deployments. By working with Minikube, we've started our journey to mastering Kubernetes, which will help us build and manage scalable, reliable apps in real-world settings.