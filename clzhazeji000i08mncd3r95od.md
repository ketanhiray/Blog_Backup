---
title: "Day 21: Essential Docker Interview Questions for DevOps Engineers"
seoTitle: "Top Docker Questions for DevOps Interviews"
datePublished: Mon Aug 05 2024 18:06:40 GMT+0000 (Coordinated Universal Time)
cuid: clzhazeji000i08mncd3r95od
slug: day-21-essential-docker-interview-questions-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1722870365254/62115b7b-5e3c-4011-a8d1-81b64572a7fa.png
tags: docker, devops, dockerfile, 90daysofdevops

---

Docker is essential for DevOps engineers to containerise applications for consistent deployment. Understanding key Docker concepts is crucial for interviews. Here's a guide to essential Docker interview questions.

### 1\. What is the difference between an Image, Container, and Engine?

* **Docker Image**:
    
* A lightweight, standalone, and executable software package that includes everything needed to run a piece of software, including the code, runtime, libraries, and settings.
    
* Built using a `Dockerfile`.
    
* Example: `nginx:latest` is an image that can be used to run an NGINX server
    
* **Docker Container**:
    
* A runtime instance of a Docker image. Containers are isolated environments where applications run. They share the host system's kernel but maintain isolated processes, networking, and file systems.
    
* Containers can be started, stopped, moved, and deleted.
    
* Example: Running an NGINX container:
    
    ```powershell
    docker run -d -p 8080:80 nginx:latest
    ```
    
* **Docker Engine**: The core component of Docker, responsible for creating, managing, and running Docker containers. It consists of a server (the Docker daemon), a REST API, and a command-line interface (CLI).
    
* Docker Engine consists of:
    
    * Docker Daemon: Runs on the host machine.
        
    * Docker CLI: Used to communicate with the Docker Daemon.
        

### 2\. What is the difference between the Docker command COPY vs ADD?

* **COPY**: Copies files or directories from the host file system into the Docker image. It is simple and predictable.
    
* Syntax:
    
    ```dockerfile
    COPY <src> <dest>
    ```
    
* **ADD**: Extends COPY by allowing the addition of remote files (via URLs) and the automatic extraction of compressed files (e.g., .tar, .gz). It has more functionality but can be unpredictable if not used carefully.
    
* Syntax:
    
    ```dockerfile
    ADD <src> <dest>
    ```
    

### 3\. What is the difference between the Docker command CMD vs RUN?

* **CMD**: Specifies the default command to run when a container starts, which can be overridden at runtime.
    
* Syntax:
    
    ```dockerfile
    CMD ["executable", "param1", "param2"]
    ```
    
* **RUN**: Executes a command during the build process of a Docker image, creating a new layer in the image.
    
* Used for installing software packages.
    
* Syntax:
    
    ```dockerfile
    RUN <command>
    ```
    

### 4\. How will you reduce the size of a Docker image?

* Use multi-stage builds.
    
* Minimize the number of layers by combining commands.
    
* Use `.dockerignore` file to exclude unnecessary files and directories.
    
* Choose a smaller base image.
    
* Clean up unnecessary files and dependencies.
    
* Example of a multi-stage build:
    
    ```dockerfile
    FROM golang:1.16 as builder
    WORKDIR /app
    COPY . .
    RUN go build -o myapp
    
    FROM alpine:latest
    WORKDIR /root/
    COPY --from=builder /app/myapp .
    CMD ["./myapp"]
    ```
    

### 5\. Why and when should you use Docker?

* **Consistency**: Ensures the application runs the same way everywhere eg. QA, PROD.
    
* **Isolation**: Isolates applications and their dependencies.
    
* **Portability**: Easily move applications between environments.
    
* **Scalability**: Quickly scale up or down.
    

### 6\. Explain the Docker components and how they interact with each other.

* **Docker Client**: The user interface for interacting with Docker is usually through the command line.
    
* **Docker Daemon (dockerd)**: Runs on the host machine, and manages Docker objects (images, containers, networks, volumes).
    
* **Docker Image**: A read-only template to create Docker containers.
    
* **Docker Container**: A lightweight, standalone, and executable package of software.
    
* **Docker Registry**: Stores Docker images. Docker Hub is a public registry, but private registries can also be used.
    

### 7\. Explain the terminology: Docker Compose, Dockerfile, Docker Image, Docker Container.

* **Docker Compose**: A tool for defining and running multi-container Docker applications using a YAML file called `docker-compose.yml`.
    
* ```yaml
    version: '3'
    services:
      web:
        image: nginx
        ports:
          - "80:80"
    ```
    
* **Dockerfile**: A text file containing instructions to build a Docker image.
    
* ```dockerfile
    FROM node:20-alpine
    WORKDIR /app
    COPY package*.json ./
    ```
    
* **Docker Image**: A template for creating Docker containers.
    
* **Docker Container**: A runnable instance of a Docker image.
    

### 8\. In what real scenarios have you used Docker?

* Deploying microservices.
    
* Running CI/CD pipelines.
    
* Isolating development environments.
    
* Automating testing processes.
    

### 9\. Docker vs Hypervisor?

* **Docker**: Uses containerization, sharing the host OS kernel, resulting in lightweight and faster environments.
    
* **Hypervisor**: Uses virtualization, providing complete VMs with separate OS instances, more resource-intensive.
    

### 10\. What are the advantages and disadvantages of using Docker?

* **Advantages**:
    
    * Consistency across environments
        
    * Efficient resource utilization
        
    * Faster deployment and scaling
        
    * Isolation and security
        
* **Disadvantages**:
    
    * Complexity in managing large-scale containerized applications
        
    * Performance overhead in some scenarios
        
    * Potential security vulnerabilities
        

### 11\. What is a Docker namespace?

A namespace is a feature that provides isolation of resources like process IDs, user IDs, file systems, and network interfaces, ensuring each container operates independently.

Types: PID, NET, IPC, MNT, UTS, and USER.

### 12\. What is a Docker registry?

A storage and distribution system for Docker images. Public registries like Docker Hub and private registries can be used to store and share Docker images.

Examples: Docker Hub, AWS ECR, and Google Container Registry.

### 13\. What is an entry point?

An ENTRYPOINT instruction in a Dockerfile sets the default application to be run when a container starts, providing more flexibility compared to CMD.

Syntax:

```dockerfile
ENTRYPOINT ["executable", "param1", "param2"]
```

### 14\. How to implement CI/CD in Docker?

* Use Docker to create consistent build environments.
    
* Integrate with CI/CD tools like Jenkins, GitLab CI, or CircleCI.
    
* Automate testing and deployment processes using Docker containers.
    
* Example with Jenkins:
    
    ```javascript
    pipeline {
      agent any
      stages {
        stage('Build') {
          steps {
            script {
              docker.build('myapp:latest')
            }
          }
        }
        stage('Test') {
          steps {
            script {
              docker.image('myapp:latest').inside {
                sh 'npm test'
              }
            }
          }
        }
        stage('Deploy') {
          steps {
            script {
              docker.image('myapp:latest').push()
            }
          }
        }
      }
    }
    ```
    

### 15\. Will data on the container be lost when the Docker container exits?

Yes, unless data is stored in volumes or bind mounts, which persist data outside the container's lifecycle.

```powershell
docker run -v /host/<path>:/<container_id>/<path> myapp
```

### 16\. What is a Docker swarm?

A native clustering and orchestration tool for Docker, enabling the management of a cluster of Docker nodes as a single system.

Manages a group of Docker engines.

### 17\. What are the Docker commands for the following:

* **Viewing running containers**:
    
* ```powershell
    docker ps
    ```
    
* **Running a container under a specific name**:
    
* ```powershell
    docker run --name <container_name/id> <image>
    ```
    
* **Exporting a Docker image**:
    
* ```powershell
    docker save -o <file.tar> <image>
    ```
    
* **Importing an existing Docker image**:
    
* ```powershell
    docker load -i <file.tar>
    ```
    
* **Deleting a container**:
    
* ```powershell
    docker stop <container>
    docker rm <container>
    ```
    
* **Removing all stopped containers, unused networks, build caches, and dangling images**:
    
* ```powershell
    docker system prune
    ```
    

### 18\. What are the common Docker practices to reduce the size of Docker images?

* Use multi-stage builds.
    
* Select minimal base images.
    
* Avoid installing unnecessary packages.
    
* Combine RUN commands to reduce layers.
    
* Clean up temporary files and caches.
    
* Use `.dockerignore` to exclude unnecessary files.
    

### 19\. How do you troubleshoot a Docker container that is not starting?

* Check container logs:
    
* ```powershell
    docker logs <container_id>
    ```
    
* Inspect the container:
    
* ```powershell
    docker inspect <container_id>
    ```
    
* Verify configuration and environment variables.
    
* Review the `Dockerfile` for errors.
    

### 20\. Can you explain the Docker networking model?

Docker provides different networking modes: bridge, host, overlay, and none.

* **Bridge**: Default network, containers on the same bridge can communicate.
    
* **Host**: Shares the host's networking namespace.
    
* **Overlay**: For Swarm services, connects multiple Docker daemons.
    

### 21\. How do you manage persistent storage in Docker?

Use Docker volumes or bind mounts to store data outside the container’s lifecycle, ensuring data persists even when containers are removed.

```powershell
docker run -v /host/<path>:/<container_id>/<path> myapp
```

### 22\. How do you secure a Docker container?

* Use minimal base images.
    
* Regularly update images.
    
* Run containers with the least privilege.
    
* Use Docker Bench for security checks.
    
* Keep Docker and container images updated.
    
* Enable Docker Content Trust (DCT) for image signing.
    

### 23\. What is Docker overlay networking?

A networking mode used by Docker Swarm to connect containers across multiple hosts, allowing them to communicate securely.

* Allows containers running on different Docker daemons to communicate.
    
* Useful for Swarm services.
    

### 24\. How do you handle environment variables in Docker?

* Use the `-e` flag with `docker run` to set environment variables.
    
* Define environment variables in a Dockerfile using `ENV`.
    
* Use a `.env` file with Docker Compose.
    
* ```powershell
    docker run -e MY_VAR=value myapp
    ```
    

These questions and answers can assist you in preparing for your next DevOps interview. Demonstrating a clear understanding of these concepts can effectively showcase your Docker knowledge.