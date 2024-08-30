---
title: "Day 28 Tutorial for Configuring Jenkins Agents"
seoTitle: "Jenkins Agent Setup: Day 28 Guide"
datePublished: Thu Aug 29 2024 07:27:47 GMT+0000 (Coordinated Universal Time)
cuid: cm0eyq8fi000g08js2jjo9m98
slug: day-28-tutorial-for-configuring-jenkins-agents
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1724916305219/2c9b5dca-8cc9-4af5-97a0-18b22a696a1e.png
tags: docker, jenkins, 2articles1week, 90daysofdevops

---

## Master-Agent Architecture 🖧

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724744292076/e83e307d-dbb0-4559-8ca9-ecb29c2c6699.png align="center")

## Jenkins Master (Server)🗄️

The Jenkins master, also called the Jenkins server, is the main part of Jenkins. It handles:

* **Job Scheduling**: The master schedules jobs based on triggers like code changes, time intervals, or manual starts.
    
* **Workflow Orchestration**: It manages the execution of workflows defined in pipelines.
    
* **Monitoring**: The master tracks job statuses, and logs, and shows results on the Jenkins UI.
    
* **Configuration Management**: All job settings, credentials, and global settings are managed from the master.
    

The master provides the Jenkins user interface (UI) for creating, managing, and monitoring jobs, and it assigns job execution to agents to ensure efficient workload distribution.

## Jenkins Agent💼

A Jenkins agent is a separate machine or container that carries out the tasks defined in Jenkins jobs. Unlike the master, which handles orchestration and management, the agent focuses on doing the actual work. Agents are useful for:

* **Distributed Builds**: By running jobs on different agents, Jenkins can handle more jobs concurrently, improving performance.
    
* **Environment Isolation**: Agents can be configured with specific environments, such as different OS versions and software dependencies, allowing specialized jobs to run in the required settings.
    
* **Scalability**: As projects and teams grow, additional agents can be added to scale Jenkins’ job execution capacity.
    

Each agent is identified by a unique label, which can be used to target jobs to specific agents based on the required environment or capacity.

## 🎯Task -1

1. **Create an Agent:**
    
    * Set up a new node in Jenkins by creating an agent.
        
2. **AWS EC2 Instance Setup:**
    
    * Create a new AWS EC2 instance and connect it to the master (where Jenkins is installed).
        
3. **Master-Agent Connection:**
    
    * Establish a connection between the master and agent using SSH and a public-private key pair exchange.
        
    * Verify the agent's status in the "Nodes" section.
        

### ╰┈➤Create two AWS instances: one for the Master and one for the Agent.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724745938409/1de5afc1-8c1b-48e5-917a-f421231b2dc6.png align="center")

### ╰┈➤In the Master instance, install Java and Jenkins.

```powershell
##Java
sudo apt update
sudo apt install fontconfig openjdk-17-jre
java -version

##Jenkins
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt-get update
sudo apt-get install jenkins
sudo systemctl status jenkins
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724756896564/d56d5e23-09a4-4871-a7a7-5bc5eeaf557b.png align="center")

### ╰┈➤In the Agent instance, install Java and Docker.

```powershell
##Java
sudo apt update
sudo apt install fontconfig openjdk-17-jre
java -version

#Docker
sudo apt-get update
sudo apt-get install docker.io
sudo systemctl status docker
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724757790375/328e3354-c5a6-4dc3-9507-c30f5101dd00.png align="center")

### ╰┈➤Now, let's connect the master and agent.

**To connect the master and agent, you need to use SSH and exchange public-private key pairs.**

### ➤**<mark>On the master instance,</mark>**

```powershell
ssh-keygen
cd .ssh
ls
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724758735299/0364d327-cb9b-496e-9ce4-35ab8d0716fa.png align="center")

```powershell
cat <Public key>
```

### ╰┈➤Copy public key

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724759097514/bb2988e3-669a-46b7-98a2-4ea6d9674e6a.png align="center")

### ➤<mark>Now, on the agent,</mark>

```powershell
cd .ssh
ls
vim authorized_keys
```

### ╰┈➤Paste public key

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724759066631/f6ad55ec-75c2-4bde-987d-2613b1505f41.png align="center")

### ╰┈➤Open Master EC2:

### ╰┈➤Add Jenkins port:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724760363898/2097792c-2f1a-4c1a-a6d3-bab1e27c7a5c.png align="center")

### ╰┈➤Copy Jenkins' initial password from the master machine

```powershell
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

### ╰┈➤Paste

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724913772319/ba44d3ba-fcdf-4d7c-9f1b-dff1a03f856b.png align="center")

### ╰┈➤Create a username and password

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724760654632/19f95b2b-25c0-4328-b3d6-3a9084e12915.png align="center")

### ╰┈➤Install Suggested plugins

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724760475238/5a354874-2183-4b8a-9961-2820ab6b27e6.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724760813428/74994c45-8b94-4281-a1c2-cf6b21789a83.png align="center")

### ╰┈➤Now, let's set up a new node. Go to `Manage Jenkins` and click on `Set up a node`.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724760927249/3f6b7611-6418-4159-a504-815966f03ce6.png align="center")

### ╰┈➤ Enter all details. Here, when we use labels for the agent, your master server will trigger the builds for the agent server.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724761090184/e5ce06c7-f210-4c7c-9658-11213220c00e.png align="center")

### ╰┈➤For the launch method, select '`Launch agents via SSH`'. Enter the public IP of the Agent instance in the `Host` field.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724761576521/f3bfc89f-a993-4626-8fbd-30b5c6ec5e90.png align="center")

### ╰┈➤For Credentials, add new credentials (if you don't already have them saved in Jenkins). Select '`SSH username with private key`'. Fill in all required details, and in the private key area, add the `Private key` **from the master instance (id\_rsa).**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724761828688/de2ca420-aa39-4181-a4c4-f69ea86a17ec.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724761809727/65bb1225-dcb2-4b8f-a7f5-a93e62b57a5c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724761884606/a3ae3f04-6b1c-4264-9a8a-fa14b783de32.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724762899009/45adcf5d-cfc6-4218-be0a-b026173d7664.png align="center")

### ╰┈➤Save the configuration details. And you can verify that the Agent is up and running if set up properly.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724762975133/5d528634-6503-445f-bcfc-c73e479bb9b3.png align="center")

## 🎯**Task-2**

* **Run your previous Jobs on the new agent**
    
* **Use labels for the agent, your master server should trigger builds for the agent server.**
    

### ╰┈➤Let's create a freestyle project that we have deployed before and try to trigger the build on the agent node.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724763371806/01895d25-795c-4840-84c6-5528dddc0abf.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724763521606/c2166fd0-09f0-4682-88dd-b92372971030.png align="center")

### ╰┈➤Add the necessary details. Here, select "`Restrict where this project can be run`**"** and enter the label of the agent node.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724763739686/083b796f-3d0b-4f8d-b2fa-a639e9d8fba0.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724763833118/0c377125-8442-4a9c-983b-e59055660568.png align="center")

```powershell
docker build . -t node-todo:latest
docker run -d -p 8000:8000 --name todo-app node-todo:latest
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724764092138/987e2d00-7b27-4126-9d0f-f81c4d76c068.png align="center")

### 🔴Error- (`Read error details carefully` )

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724764219211/3adfd501-ca67-4581-956b-fbafb8734934.png align="center")

```powershell
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
docker run hello-world
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724764314045/dd01380b-e03d-4cf4-a4d0-16c7b1bbc4af.png align="center")

### ➡️Now, build the Jenkins job again.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724764901894/64289e7e-52bc-4a94-aeff-e3c8dba04355.png align="center")

### 🟢Job ran successfully

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724764953336/699d834f-136a-4d82-87a4-d71b927ab870.png align="center")

### 🔶Now, since we deployed the trigger build in the agent. Go to the `public IP of the agent instance` and port :8000 and you can verify that the docker container was deployed in the agent instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724765024750/af32bfb0-2293-42b6-9a75-8b049d969d18.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724765143064/2feb5a64-47da-4204-86e1-4500815a8f7c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724765277270/bce3a1af-f09d-410a-a024-9b6c7a56e4f0.png align="center")

### ◉Commands for Stop, Kill Docker Container

```powershell
docker ps
docker kill <id>
```

### ◉Command for Stop Docker and Jenkins

```powershell
Agent:
sudo systemctl status docker
 sudo systemctl stop docker.socket

Master:
sudo systemctl stop jenkins
sudo systemctl status jenkins
```

## Conclusion📌

By using Jenkins' master-agent architecture, teams can efficiently scale their CI/CD pipelines to manage growing workloads. Setting up a Jenkins agent involves creating a node, configuring an EC2 instance, and establishing a secure connection between the master and the agent. Once set up, jobs can be distributed across multiple agents, optimizing build times and resource use.