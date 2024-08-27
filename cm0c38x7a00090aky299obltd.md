---
title: "Day 27: Mastering Jenkins Declarative Pipeline and Docker Integration"
seoTitle: "Jenkins Declarative Pipeline & Docker Integration"
datePublished: Tue Aug 27 2024 07:10:59 GMT+0000 (Coordinated Universal Time)
cuid: cm0c38x7a00090aky299obltd
slug: day-27-mastering-jenkins-declarative-pipeline-and-docker-integration
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1724690908641/a7735877-6707-4b0c-a0f0-287328378873.png
tags: docker, github, devops, jenkins, 90daysofdevops

---

# Task:📋

## Steps:✅

### ╰┈➤Create a Docker-integrated Jenkins declarative pipeline

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724431851672/45a56008-05a3-47a6-958f-42fddeccd91d.png align="center")

### ╰┈➤Check the GitHub trigger for the auto-run job.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724432038383/19688896-9ea0-4645-8aea-a75e941e1af2.png align="center")

### ╰┈➤Grant permissions for Docker.

```bash
sudo usermod -aG docker jenkins
or
sudo usermod -aG docker $USER
```

### ╰┈➤Login to DockerHub

```bash
docker login
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724434153785/c6a09f1f-db23-4ad6-ae31-40a119a258c7.png align="center")

### ╰┈➤Add DockerHub credentials

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724434463050/658a8c55-93d4-4cdb-94cb-d45b08ebbdd7.png align="center")

### ╰┈➤Selected credentials

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724434639143/f5dccc74-450c-420a-acd0-0a23406765dc.png align="center")

### ╰┈➤Create a Jenkins pipeline Groovy script.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724741020666/2e778324-dccf-4119-a42b-29c235123bbc.png align="center")

### ╰┈➤Groovy script

```javascript
pipeline {
    
    agent{
        node{
            
            label "DEV"
        }
    }
    
    stages{
        
        stage("Clone Code"){
            
            steps{
                 echo "Cloning code from Git Repo."
                git url: "https://github.com/ketanhiray/django-notes-app.git", branch: "main"
               
                 echo "Cloning done"
            }
            
        }
        
        stage("Build"){
            
             steps{
                sh "docker build . -t notes-app-jenkins:latest1"
            }
            
        }
        
         stage("Push to DockerHub"){
            steps{
                withCredentials(
                    [usernamePassword(
                        credentialsId:"dockerHub",
                        passwordVariable:"dockerHubPass", 
                        usernameVariable:"dockerHubUser"
                        )
                    ]
                ){
                sh "docker image tag notes-app-jenkins:latest1 ${env.dockerHubUser}/notes-app-jenkins:latest1"
                sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                sh "docker push ${env.dockerHubUser}/notes-app-jenkins:latest1"
                }
            }
        }
        
        stage("Deploy"){
            steps{
                sh "docker compose up -d"
            }
        }
    }
    
}
```

### ╰┈➤After running the job, we can check the console output for errors and background processes.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724684285410/81f8307c-b47b-4a63-8933-dfbfdd10410e.png align="center")

### ╰┈➤Our job ran successfully.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724684324048/5b995ef6-7ff0-4908-a14f-f01ecf8ed8b9.png align="center")

### ╰┈➤Check the output on port *8000*.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724684472104/a4b09e15-a053-45b1-be87-5a5a8e42f489.png align="center")

### ╰┈➤Check DockerHub to see if the project image is uploaded.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724684507201/e974c192-5982-4ccd-8f21-b3699dc2a46c.png align="center")

### ╰┈➤Command to stop and remove the container

```bash
sudo aa-remove-unknown
or
docker container stop
docker rm -f <container id>
```

## Summary:📝

* This blog Shows an easy way to build and run Docker containers using shell commands in a Jenkins Declarative Pipeline. It's simple but might have problems if the same container is already running.
    
* Jenkins' Docker Groovy efficiently manages Docker tasks, ideal for repetitive jobs and preventing container name conflicts. Using Jenkins' built-in Docker support creates more dependable, error-free pipelines.