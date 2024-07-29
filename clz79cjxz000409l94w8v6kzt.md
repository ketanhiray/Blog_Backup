---
title: "Docker Project Day 17: Todo-List Task 
(Using Linux)"
seoTitle: "Linux Docker Tutorial: Todo-List Task"
datePublished: Mon Jul 29 2024 17:23:13 GMT+0000 (Coordinated Universal Time)
cuid: clz79cjxz000409l94w8v6kzt
slug: docker-project-day-17-todo-list-task-using-linux
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1722273675791/142801bb-d1cd-4b03-912f-af86918a4732.png
tags: linux, docker, devops, 90daysofdevops

---

# 🐳Docker

Docker is a tool that simplifies running applications in containers, and self-contained packages are created using a Dockerfile.

A Dockerfile is a set of instructions for creating a container. It specifies the base image, commands, and files to include. For example, it can tell Docker to use a web server image, add website files, and start the web server.

## 1️⃣Copy the code from GitHub Repository

```dockerfile
git clone <URL>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1722262341198/c227bebf-f767-4e21-9e9f-64ddaa07c4c8.png align="center")

## 2️⃣Start the docker

```dockerfile
sudo su
systemctl start docker
service docker start
docker ps
systemctl status docker
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1722262516177/7193baee-5762-4403-879b-2a3f068e11a7.png align="center")

## 3️⃣Create "Dockerfile"

```dockerfile
# Use an official Node.js runtime as a parent image
FROM node:20 AS build
# Set the working directory in the container
WORKDIR /app
# Copy the package.json and package-lock.json files to the container
COPY package*.json ./
# Install the dependencies
RUN npm install
# Copy the rest of the application's source code to the container
COPY . .
# Build the React application
RUN npm run build
# Use an official Nginx image to serve the build
FROM nginx:alpine
# Copy the build output to the Nginx HTML directory
COPY --from=build /app/build /usr/share/nginx/html
# Expose the port Nginx runs on
EXPOSE 8383
# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
```

## 4️⃣Build Docker Image

```dockerfile
docker build -t todo-app .
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1722271160927/6659c777-354d-49cf-840b-445b8114bff4.png align="center")

## 5️⃣Run the application

```dockerfile
docker run -d -p 8383:80 --name todo-list todo-app
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1722271229740/14e52bce-ed27-479e-811f-81cae1ece99e.png align="center")

```dockerfile
sudo docker ps
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1722271763981/af65441f-95d0-4d71-b5ff-bbb40943ad0e.png align="center")

## 6️⃣Output: *https://localhost:&lt;port&gt;*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1722271554598/2ef13aed-a936-45bb-be5b-8eee210b2a2c.png align="center")

## 7️⃣Stop and Remove the docker container

```dockerfile
docker stop <container_id_or_name>
docker rm <container_id_or_name>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1722272148182/0bf0eb46-8ea4-48a6-b515-6ca4a2017be7.png align="center")

# 💡Conclusion:

In this blog, we created a To-Do list app using React.js and Docker. We covered setting up the app, containerizing it with Docker, addressing build issues, and managing Docker containers. This process showcased Docker's power in ensuring consistent environments and streamlining deployment.