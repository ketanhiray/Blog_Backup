---
title: "Day 20 Docker Cheat-Sheet: Key Commands and Tips"
seoTitle: "Essential Docker Commands and Tips"
datePublished: Sun Aug 04 2024 14:05:35 GMT+0000 (Coordinated Universal Time)
cuid: clzfmxi5x000f09jx80qo03dt
slug: day-20-docker-cheat-sheet-key-commands-and-tips
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1722780263804/e4272453-c06f-4e36-b059-290d30fa6228.png
tags: docker, 90daysofdevops

---

## 🐳Docker Commands

### 🔶Basic Commands

* **docker --version:** Display the Docker version
    
* **docker info:** Show detailed information about the Docker installation.
    

### 🔶Container Management

* **docker run &lt;*options*&gt; &lt;port&gt; &lt;image\_name&gt;:** Run a new container from a Docker image.
    
* **docker ps:** List running containers.
    
* **docker ps -a:** List all containers (including dead ones).
    
* **docker stop &lt;container\_id/name&gt;:** Stop a running container.
    
* **docker start &lt;container\_id/name&gt;:** Start a stopped container.
    
* **docker restart &lt;container\_id/name&gt;:** Restart a container.
    
* **docker rm &lt;container\_id/name&gt;:** Remove a stopped container.
    
* **docker rmi &lt;image\_id&gt;:** Remove a Docker image.
    

### 🔶Image Management

* **docker images:** List all Docker images.
    
* **docker pull &lt;image\_id&gt;:** Pull an image from a Docker registry.
    
* **docker build -t &lt;image\_id&gt;:** Build a Docker image from a Dockerfile
    
* **docker tag &lt;source\_img&gt; &lt;destination\_img&gt;:** Tag an image with a new name
    
* **docker push &lt;img&gt;:** Push an image to a Docker registry.
    

### 🔶Viewing Logs and Executing Commands

* **docker logs &lt;container\_id/name&gt;:** View the logs of a container.
    
* **docker exec -it &lt;container\_id/name&gt; /bin/bash:** Run a command in a running container.
    
* **docker inspect &lt;container\_id/name&gt;:** Return low-level information about a container.
    

### 🔶Network Management

* **docker network ls:** List all networks.
    
* **docker network create &lt;network\_name&gt;:** Create a new network.
    
* **docker network rm &lt;network\_name&gt;:** Remove a network.
    

### 🔶Volume Management

* **docker volume ls:** List all volumes.
    
* **docker volume create &lt;volume\_name&gt;:** Create a new volume.
    
* **docker volume rm &lt;volume\_name&gt;:** Remove a volume.
    

## 📦Docker Compose Commands

### 🔷Basic Commands

* **docker-compose --version:** Display the Docker Compose version installed
    
* **docker-compose up:** Create and start containers defined in the docker-compose.yml file.
    
* **docker-compose down:** Stop and remove containers, networks, and volumes defined in the docker-compose.yml file.
    

### 🔷Service Management

* **docker-compose ps:** List containers defined in the docker-compose.yml file.
    
* **docker-compose start:** Start services defined in the docker-compose.yml file.
    
* **docker-compose stop:** Stop services defined in the docker-compose.yml file.
    
* **docker-compose restart:** Restart services defined in the docker-compose.yml file.
    
* **docker-compose rm:** Remove stopped service containers.
    

### 🔷Logs and Configuration

* **docker-compose logs &lt;service&gt;:** View logs for a service.
    
* **docker-compose config:** Validate and view the Compose file configuration.
    

### 🔷Scaling Services

* **docker-compose scale &lt;service&gt;=&lt;number&gt;:** Scale a service to the specified number of instances.
    

### 🔷Running Commands in Services

* **docker-compose exec &lt;service&gt; &lt;command&gt;:** Execute a command in a running service container.
    

## ✨Conclusion

With this comprehensive cheat sheet, we're well-equipped to efficiently handle Docker and Docker Compose commands. This will help us to build, deploy, and manage containerised applications.