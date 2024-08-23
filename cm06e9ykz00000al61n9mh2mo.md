---
title: "Day 26 Tutorial: Using Jenkins Declarative Pipeline"
seoTitle: "Jenkins Declarative Pipeline Tutorial"
datePublished: Fri Aug 23 2024 07:33:06 GMT+0000 (Coordinated Universal Time)
cuid: cm06e9ykz00000al61n9mh2mo
slug: day-26-tutorial-using-jenkins-declarative-pipeline
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1724397895060/6340e50e-2986-40ab-b03d-d497055b03a6.png
tags: linux, jenkins, 90daysofdevops

---

## What is a Pipeline in Jenkins?☑️

A **Pipeline** is a series of automated steps or jobs linked together in a specific order to achieve continuous integration, continuous delivery, or continuous deployment in software development. Pipelines allow developers to automate building, testing, and deploying applications, ensuring a consistent and reliable workflow.

### Types of Jenkins Pipelines⚙️

* **Declarative Pipeline**:  
    The Declarative Pipeline is a newer and more organized way to write a pipeline as code in Jenkins. It has a simpler and clearer syntax, making it easier to understand and maintain. This style uses a set structure, making it more readable and ideal for most users, especially beginners.
    
* **Syntax:**
    
* ```javascript
    pipeline {
        agent any
        stages {
            stage('Build') {
                steps {
                    echo 'Building...'
                    // Insert build steps here
                }
            }
            stage('Test') {
                steps {
                    echo 'Testing...'
                    // Insert test steps here
                }
            }
            stage('Deploy') {
                steps {
                    echo 'Deploying...'
                    // Insert deploy steps here
                }
            }
        }
    }
    ```
    
* **Scripted Pipeline**:  
    The Scripted Pipeline is the older, more flexible way to define a pipeline. It uses a special language called DSL (Domain Specific Language) built with Groovy. While it offers more flexibility and control, it can be more complex and harder to maintain. Scripted Pipelines are useful when you need more complicated logic that the Declarative approach might not easily handle.
    
* **Syntax:**
    
* ```javascript
    node {
        // Define environment variables
        def myVar = 'Hello World!'
        // Checkout code from Git
        stage('Checkout') {
            echo 'Checking out code...'
            checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/example/repo.git']]])
        }
        // Build stage
        stage('Build') {
            echo 'Building the application...'
            sh 'echo "Building..."'
        }
        // Test stage
        stage('Test') {
            echo 'Running tests...'
            sh 'echo "Running tests..."'
        }
        // Deploy stage
        stage('Deploy') {
            echo 'Deploying the application...'
            sh 'echo "Deploying..."'
        }
        // Print environment variable
        echo "Message: ${myVar}"
    }
    ```
    

### Why We Should Use a Pipeline❓

* **Version Control Integration**:  
    The pipeline is defined in a text file called a **Jenkinsfile**, which can be added to a project's source control repository (e.g., Git). This allows versioning and tracking of changes over time. It also makes the pipeline part of the application's code, which can be reviewed and improved just like any other code.
    
* **Pipeline-as-Code**:  
    Pipeline definition as an integral part of the software project. This approach ensures that the deployment process is consistent, repeatable, and reliable. It allows the pipeline to be versioned, tested, and stored alongside the source code.
    
* **Automatic Builds for Branches and Pull Requests**:  
    Using a Jenkinsfile, Jenkins automatically sets up pipeline build processes for all branches and pulls requests in the repository. This makes sure that all changes, no matter the branch, are built, tested, and verified, which helps reduce integration problems.
    
* **Improved Collaboration**:  
    Having the pipeline definition in the same repository as the codebase encourages teamwork and communication among developers. Code reviews can include pipeline changes, and making sure all team members understand the CI/CD process.
    

# Task: 🎯

### ➤Create a New Job, this time select Pipeline instead of Freestyle Project.

### ➤Complete the example using the Declarative pipeline

### ➤Create a new Agent/Node for running the job

## Steps:📶

### ╰┈➤Open Master Machine & Copy public key:

```powershell
ubuntu@ip-172-31-45-42:~$ ssh-keygen
ubuntu@ip-172-31-45-42:~$ cd .ssh
ubuntu@ip-172-31-45-42:~/.ssh$ ls
authorized_keys  id_ed25519  id_ed25519.pub
ubuntu@ip-172-31-45-42:~/.ssh$ cat id_ed25519.pub
```

### ╰┈➤Paste the public key into the agent machine

```powershell
ubuntu@ip-172-31-26-86:~$ cd .ssh
ubuntu@ip-172-31-26-86:~/.ssh$ ls
authorized_keys
ubuntu@ip-172-31-26-86:~/.ssh$ vim authorized_keys
```

### ╰┈➤Update the package of the Agent Machine

```powershell
sudo apt-get update
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724334432334/d33caecc-c3fe-4527-bfdf-dbed7c38cb43.png align="center")

### ╰┈➤Install Java into the Agent Machine

```powershell
sudo apt install fontconfig openjdk-17-jre
```

### ╰┈➤Create a new node

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724334900643/7e8276d7-3155-4663-aa22-805d8c13bca5.png align="center")

### ╰┈➤Copy agent directory path

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724335113165/8b8be8af-3ef4-419d-a772-ec54f99ad519.png align="center")

### ╰┈➤Paste into Jenkin node

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724335172079/0a771c0e-0bb3-40b6-94e8-d5d6f30b3c11.png align="center")

### ╰┈➤Add the agent IP address

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724335430827/5dd640d2-508c-4d02-9aaa-d07217b6de8c.png align="center")

### ╰┈➤Add Credentials

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724335627892/c2f7fdfe-7b87-4003-b605-24e58a3169ee.png align="center")

### ╰┈➤Copy the private key from the master

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724335779118/cbca9a2f-31ac-482a-b831-a2c8a5597e13.png align="center")

### ╰┈➤Paste into Jenkins Node

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724335836523/7ee53733-15de-4f2f-985c-37d267471e90.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724336054987/0ed62c88-63b9-451b-a750-b9b700c456d9.png align="center")

### ╰┈➤Save the node configuration

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724336117486/fb444f8f-0228-46b6-8cbe-cd6ac41348c3.png align="center")

### ╰┈➤Now node is created and connected to the EC2 - Agent machine

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724336265336/d725b7e3-e3c7-4cb5-85cc-45a6d72fb0c1.png align="center")

### ╰┈➤Create a new Declarative pipeline

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724336458535/7c541aa3-e85a-4921-80f0-e05dfb9cdb83.png align="center")

### ╰┈➤Add description

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724336772750/3e67925b-940e-487c-9791-f36c48d9248a.png align="center")

### ╰┈➤Write a groovy script

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724336750005/662808c6-595f-4022-ac82-1aeca6c648d3.png align="center")

### ╰┈➤Click on Build to run the job

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724336824264/38d423c3-6eca-46be-a474-c644cebdcb41.png align="center")

### ╰┈➤The job runs successfully on the agent now by using the pipeline

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724336873672/02482ab2-d634-4ff8-a400-d0f38193a9ba.png align="center")

## Conclusion:💡

By following these steps, We can create a simple Jenkins pipeline using Declarative syntax. This example shows how easy and powerful Jenkins Pipelines are for automating the CI/CD process, ensuring consistent and reliable software delivery.