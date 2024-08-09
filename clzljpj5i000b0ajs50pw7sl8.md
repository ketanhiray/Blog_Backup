---
title: "Day 22 Jenkins Tutorial: Key Lessons"
seoTitle: "Jenkins Tutorial: Essential Day 22 Highlights"
datePublished: Thu Aug 08 2024 17:22:01 GMT+0000 (Coordinated Universal Time)
cuid: clzljpj5i000b0ajs50pw7sl8
slug: day-22-jenkins-tutorial-key-lessons
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1723188428911/cb00e79e-06d5-4f61-a065-f5e9186528af.png
tags: ec2, linux, aws, jenkins, 90daysofdevops, 90daysofdevopschallenge

---

# 🔶What is Jenkins?

Jenkins is an open-source automation server that streamlines the processes of building, testing, and deploying software. It is written in Java and is a pivotal tool in the DevOps ecosystem. Jenkins is known for implementing Continuous Integration (CI) and Continuous Delivery/Deployment (CD) workflows, often called pipelines.

### 💠Integrating Jenkins into the DevOps Lifecycle

In the DevOps lifecycle, Jenkins plays a crucial role by enabling continuous integration and delivery. Here's how Jenkins integrates into the various stages of DevOps:

1. **Source Code Management**: Jenkins integrates with Git to pull the latest code from repositories whenever changes are committed.
    
2. **Build Automation**: Jenkins automates code compilation and packaging using build tools like Maven or Gradle.
    
3. **Automated Testing**: Jenkins runs automated tests to check for code changes that could affect the existing functionality, helping to maintain code quality and reliability.
    
4. **Deployment Automation**: Once the code is built and tested, Jenkins can automatically deploy the application to different environments, reducing manual intervention and human error.
    
5. **Monitoring and Feedback**: Jenkins provides real-time feedback and monitoring of the build and deployment processes, enabling developers to address issues promptly.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723125417826/713cb8d9-b328-4374-b3f9-440c2aa2161b.png align="center")
    

### 💠Benefits of Using Jenkins

* **Automation**: Jenkins automates repetitive tasks, freeing up developers to focus on more critical aspects of development.
    
* **Efficiency**: With Jenkins, the time taken to build, test, and deploy code is significantly reduced, leading to faster release cycles.
    
* **Scalability**: Jenkins supports distributed builds, allowing multiple build agents to run simultaneously, thus handling large projects efficiently.
    
* **Extensibility**: The vast library of plugins available for Jenkins allows it to integrate with numerous tools and services, enhancing its functionality.
    

#### ᯽Role of Jenkins in Automating Build, Test, and Deployment Processes

Jenkins is instrumental in automating the entire software development lifecycle:

* **Build**: Jenkins pulls the latest code from the repository, compiles it, and packages it into a deployable format.
    
* **Test**: It runs automated tests to verify the integrity of the code. This includes unit tests, integration tests, and even performance tests.
    
* **Deploy**: Jenkins can deploy the built application to different environments, ensuring that the application is always in a deployable state.
    

By automating these processes, Jenkins ensures that software development is faster, more reliable, and more consistent.

# ☑️**Task 1: Jenkins Installation on Linux(**`Ubuntu`**)**

## Step 1: Installations of Java

```powershell
sudo apt update
sudo apt install openjdk-17-jre
java -version
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723126031145/7bc8a1b5-68c0-461f-8afc-40d823fd7102.png align="center")

## Step 2: Installations of Jenkins

```powershell
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```

## Step 3: Enable, Start and View Status

```powershell
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723127006711/564961c7-b61c-49fb-a4bc-3f567bc94788.png align="center")

## Step 4: Open Browser and Search

## `https://<IP>:8080`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723127079500/bcc20cae-b914-4533-968f-5659d738afbd.png align="center")

## Step 5: Command for view default Password

```powershell
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

## Step 6: Select `Install suggested plugins`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723127158046/67991db2-9fe9-4221-8f2a-0eed7f7e1730.png align="center")

## Step 7: Plugins are getting installing

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723127753322/7f6f210b-020e-480e-89bb-2966563e1422.png align="center")

## Step 8: Jenkins set-up is ready for use

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723127857185/45b6d782-7c6f-4dec-99ed-eca98ebecb64.png align="center")

## Step 9: Jenkins Dashboard

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723127905999/08250299-57fe-470e-9866-8645307b8ca1.png align="center")

# ☑️**Task 2: Create a freestyle pipeline to print "Hello World!!"**

## Step 1: Click on `New Item` to create a pipeline

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723128025265/56091153-8f43-4e24-9811-490ef9d3c974.png align="center")

## Step 2: Give the pipeline name & Choose `Freestyle Project`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723128119396/83c8e330-7f62-4367-a3c1-bc8d53c10b29.png align="center")

## Step 3: Give a description(optional)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723128206105/1b813e10-8e7f-4870-8ef6-5f0f3784a359.png align="center")

## Step 4: Add a build step - Execute shell.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723128625948/70d650d8-6ef3-4245-bc83-32f887dd6b2e.png align="center")

## Step 5: Make the status of the node `Online`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723128734256/dd376dd7-be1a-487c-85be-ad6f0e644645.png align="center")

## Step 6: Now click on `Build Now` to run the Job.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723128423289/b2f3a8a8-24e9-4f8a-8263-8c843769fdc3.png align="center")

## Step 7: Click on `Console output` to see the result.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723129583184/90b846e2-a00e-4950-bed1-84dea1ba5015.png align="center")

## Step 8: After the execution is done `stop` the Jenkins

```powershell
sudo systemctl stop jenkins 
sudo systemctl status jenkins
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723129911503/bf850d74-0f33-4511-813c-8eedf23ca126.png align="center")

# 🎯Conclusion

By following these steps, we have successfully created a `Freestyle Pipeline` in Jenkins that prints `"Hello World,"`.This pipeline is a simple example of how Jenkins can automate tasks, making it a valuable tool for DevOps engineers.