---
title: "Day 16: Using Docker for DevOps Engineering"
seoTitle: "Docker in DevOps: Day 16 Insights"
datePublished: Thu Jul 25 2024 12:50:27 GMT+0000 (Coordinated Universal Time)
cuid: clz19udj600040akz5io91ivw
slug: day-16-using-docker-for-devops-engineering
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1721911611676/ff6b799d-6e1a-48aa-83e0-847d18f4729c.png
tags: docker, devops, 90daysofdevops

---

## 🐳Docker

Docker is a platform that allows you to rapidly build, test, and deploy applications, and scale them into any environment with confidence in your code's performance.

Docker revolutionises application development by packaging apps into containers, ensuring consistent performance across different environments. This guide'll explore essential Docker commands for efficient container and image management.

## ✅Task:

* ### 1️⃣Use the `docker run` command to start a new container and interact with it through the command line. \[Hint: `docker run hello-world`\]
    
* Running the *hello-world* image executes a command that confirms Docker is working correctly.
    
* ```dockerfile
    docker run hello-world
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721902926828/0000690c-ae37-4ab4-86ad-3009926d7981.png align="center")
    
* ### 2️⃣Use the `docker inspect` command to view detailed information about a container or image.
    
* View Detailed Information About a Container or Image
    
* ```dockerfile
    docker inspect hello-world
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721903231036/15312342-4b30-4df8-ac8b-d6f90f73754f.png align="center")
    
* ### 3️⃣Use the `docker port` command to list the port mappings for a container.
    
* This command maps *port* *8282* on the host to *port* *82* in the container and lists the port mappings.
    
* ```dockerfile
    docker run -d -p 8282:82 --name my_container3 nginx
    docker port my_container3
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721904383899/fac8608f-8f7a-4527-9904-233e36fb18c2.png align="center")
    
* ### 4️⃣Use the `docker stats` command to view resource usage statistics for one or more containers.
    
* This command provides a live stream of resource usage statistics for all running containers.
    
* ```dockerfile
    docker stats
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721904587895/0f8087e7-1b5e-4163-8abd-1634ec358e39.png align="center")
    
* ### 5️⃣Use the `docker top` command to view the processes running inside a container.
    
    This command lists the processes running inside the *my\_container3* container.
    
* ```dockerfile
    docker top my_container3
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721904871589/4475d18a-6f8a-48c6-8595-e361496ea579.png align="center")
    
* ### 6️⃣Use the `docker save` command to save an image to a tar archive.
    
    This command saves the *nginx* image to a tar archive named *my\_image.tar.*
    
* ```dockerfile
    docker save -o my_image.tar nginx
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721905608827/3796b49d-5444-4935-ab87-3481d60953a7.png align="center")
    
    ### 7️⃣Use the `docker load` command to load an image from a tar archive.
    
    This command loads the image from the *my\_image.tar* archive into Docker.
    
    ```dockerfile
    docker load -i my_image.tar
    ```
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721905840319/52d4d87e-1f71-4e24-87f9-74b2f7ba0be1.png align="center")
    
    ## 🎯Conclusion
    
    Mastering these Docker commands will provide a solid foundation to manage your environment, from small web apps to complex microservices.