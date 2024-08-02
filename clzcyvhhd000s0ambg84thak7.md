---
title: "Day 18: Understanding Docker Compose"
seoTitle: "Learning Docker Compose Basics"
datePublished: Fri Aug 02 2024 17:16:37 GMT+0000 (Coordinated Universal Time)
cuid: clzcyvhhd000s0ambg84thak7
slug: day-18-understanding-docker-compose
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1722618421721/4ca8e80c-58ea-4b79-941c-faaba7aa0540.png
tags: docker, devops, yml, 90daysofdevops

---

## 🐋Docker Compose

Docker Compose is a tool for managing complex applications with multiple containers. It uses a YAML file to specify services, networks, volumes, and more. We can build, run, and scale the entire application with a single command.

Docker Compose helps develop, test, and deploy multi-component applications or microservices. For instance, it can be used to create a web application with a web server, a database, and a cache, and to manage communication and dependencies between components.

## 📑What is YAML?

YAML stands for "Yet Another Markup Language" or "YAML Ain’t Markup Language" (a recursive acronym). It is a data serialization language designed to be easy to read and write for humans, commonly used for configuration files and data storage/transmission in applications.

YAML has a simple syntax that uses indentation, colons, dashes, and brackets to represent the structure and values of data. YAML supports scalars (such as strings, numbers, and booleans), lists (or sequences), and maps (or dictionaries). YAML also allows you to define custom data types and aliases for reusing data.

## ☑️Tasks

## #️⃣Task 1: Understanding *docker-compose.yml*

To effectively use Docker Compose, start by learning how to work with the *docker-compose.yml* file. This file allows us to:

* **Set up the environment:** Define the configuration for your services.
    
* **Configure services:** Specify how each service will run and interact with others.
    
* **Use environment variables:** Easily manage dynamic configurations
    

```yaml
version: '3.3'
services:
  web:
    image: nginx:latest
    ports:
      - "8181:80"
  database:
    image: mysql:latest
    environment:
      MYSQL_ROOT_PASSWORD:root
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1722611217683/f2557245-ca25-44a9-95c7-34b45c107bd0.png align="center")

## #️⃣Task 2: Running Docker Commands

### 1️⃣Pull a Docker Image:

```powershell
docker pull nginx:latest
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1722611356574/a6145464-601d-4f9d-9fe3-130b7e99df9d.png align="center")

### 2️⃣Run the Container as a Non-Root User:

```powershell
sudo usermod -a -G docker $USER
sudo reboot
docker run -d --name my_nginx nginx:latest
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1722611530040/f09e16a3-4591-4f64-a6bd-8133fc1a4993.png align="center")

### 3️⃣Inspect the Container:

```powershell
docker inspect my_nginx
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1722611615621/cf6b0163-4b5f-4ef8-9215-c9f35c301211.png align="center")

### 4️⃣View Container Logs:

```powershell
docker logs my_nginx
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1722611720861/6d43397a-b19e-4dc3-9838-a3009c529b3c.png align="center")

### 5️⃣Stop and Start the Container:

```powershell
docker stop my_nginx
docker start my_nginx
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1722611846588/99a25aa1-75ad-4d21-9d82-3166d3054b5d.png align="center")

### 6️⃣Remove the Container:

```powershell
docker stop <container_id/name>
docker rm <container_id/name>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1722611943520/27d6d6b1-62a2-48d7-bc0f-dac4a8d45862.png align="center")

## 💥How to Run Docker Commands Without Sudo?

```powershell
 sudo usermod -a -G docker $USER
```

### 🟢Reboot the machine.

```powershell
sudo reboot
```

## 🎯Conclusion

Mastering Docker Compose and understanding YAML configuration files are crucial for modern DevOps. Docker Compose simplifies the management of multi-container applications, allowing you to define, configure, and control your services with ease. By completing hands-on tasks like setting up *docker-compose.yml*, pulling and running Docker images, and managing containers without root access, we can efficiently deploy and maintain containerized applications.