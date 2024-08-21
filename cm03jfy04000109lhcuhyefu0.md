---
title: "Day 24 & 25  Jenkins CI/CD Project: To-Do List"
seoTitle: "Jenkins CI/CD: Day 24 To-Do List"
datePublished: Wed Aug 21 2024 07:34:25 GMT+0000 (Coordinated Universal Time)
cuid: cm03jfy04000109lhcuhyefu0
slug: day-24-25-jenkins-cicd-project-to-do-list
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1724225380826/3069ec2f-ed3e-4e21-93ca-9f2c4c58d7ae.png
tags: github, webhooks, jenkins, ci-cd, 90daysofdevops

---

## Task 1: Set up a connection between the Jenkins job and the GitHub repository.👨🏻‍💻

### ➤Steps:

### ╰┈➤Create Keys

```powershell
ssh-keygen 
cd .ssh 
cat <public key>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724162608876/ef6ee729-27be-41c0-b814-665ccf464008.png align="center")

### ╰┈➤Add the public key to the GitHub SSH keys section.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724162668227/4e1a3e15-f513-451a-81e4-2b278fe1a9c9.png align="center")

### ╰┈➤Add Key

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724162785108/a700e793-e50c-46a4-8ebf-ac7956adec31.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724162870272/d6ed1df7-adef-4c9e-8084-99035c25583a.png align="center")

### ╰┈➤Copy the GitHub repository URL and paste it into Jenkins' new *job &gt; Configuration &gt; GitHub Project.*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724163315955/1d889990-2981-4d9a-96b4-89c424e899e2.png align="center")

### ╰┈➤Paste the GitHub repository URL in the Source Code Management section.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724163343305/e0e6177c-138f-41b2-903a-c88471abe38b.png align="center")

### ╰┈➤Capy Private key

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724163552677/84f2a115-6374-4783-aa97-a6cb43054a8d.png align="center")

### ╰┈➤Paste the private key into the Jenkins job credentials section.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724163661805/d10da3c7-2578-4720-af73-6fdc3707605d.png align="center")

### ╰┈➤Select the created credential that we have created.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724163705916/7181e714-1109-45f2-838b-b06d84a567ce.png align="center")

### ╰┈➤Add Docker commands in the Build steps and save.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724163942198/0a0582d1-136d-4a41-bf6c-1df6372f314d.png align="center")

### ╰┈➤Run the Job

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724164176508/0d9f5ec6-a31e-4d1e-a277-2ee6ed4bddb0.png align="center")

### ╰┈➤Job Run Successfully

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724164219019/e6abce59-250c-40c6-9de6-49bb2d036848.png align="center")

### ╰┈➤Output- Check out `https://<ip>:8000`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724164318360/7c87c24d-d190-4916-9c0e-76563dfcd0b0.png align="center")

## Task 2: Set up a connection between the Jenkins job and the GitHub repository through <mark>GitHub Integration</mark>.🤖

### ➤Steps:

### ╰┈➤Kill the running Docker container

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724164558081/a2434905-af78-4c6e-bc7c-2b6c87b7b976.png align="center")

### ╰┈➤Navigate *Manage Jenkins&gt; Plugins &gt; Available plugins*

### ╰┈➤Search `GitHub Integration` and install

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724164638147/1726ead2-dac0-4b11-b38e-ed247630f3c3.png align="center")

### ╰┈➤Open the GitHub Navigate <mark>Webhooks</mark> and Add Jenkins URL

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724165305908/34dc9074-e9d8-4356-858f-553d2dda869f.png align="center")

### ╰┈➤After Adding wait for "✔️"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724165381634/739b7df1-e608-4bee-998e-69fd3b431bb1.png align="center")

### ╰┈➤Jenkins job configuration &gt; Check the Build Triggers

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724165520321/7ed41db5-bf41-46f8-b24b-eb278e321b73.png align="center")

### ╰┈➤When we make some Changes in the Code and commit the code

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724166174636/f8c2ab0e-fb9f-411f-aff0-81e01e183104.png align="center")

### ╰┈➤Then Jenkins's job will trigger automatically

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724166348741/3d6b5273-7c9f-459b-a509-02344c425f3f.png align="center")

### ╰┈➤Job Run Successfully

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724166243000/ef6ad77b-4834-4dac-920a-92603836cf56.png align="center")

### ╰┈➤Output after code changes

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724166300753/278ea616-f9cf-468b-86e5-3aaab85074af.png align="center")

## 🟣Conclusion :

We have completed our CI/CD project.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1724225265685/b5a7fdd0-7d17-47d6-8fb2-6fc9e008a39b.png align="center")