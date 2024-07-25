---
title: "Day 12: Essential Git & GitHub Skills for DevOps Engineers"
seoTitle: "Git & GitHub Skills for DevOps Engineers"
datePublished: Thu Jul 18 2024 17:54:02 GMT+0000 (Coordinated Universal Time)
cuid: clyrkltm6000409jwhdqlbwxu
slug: day-12-essential-git-github-skills-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1721325048008/eafb3578-6abb-46a8-80a8-13acdf313c40.png
tags: github, git, devops, 90daysofdevops

---

* ### What is Git and why is it important?🤔
    
    * "**Git** is a distributed version control system that enables multiple developers to collaborate on a project simultaneously without overwriting each other's code changes. It helps to track changes in source code during software development, allowing for efficient management and version control of code changes."
        
    * **Importance of Git:**
        
        * **Version Control:** Keep track of changes so that you can revert to previous versions if needed.
            
        * **Collaboration:** Multiple developers can work on the same project at the same time.
            
        * **Branching:** Allows you to work on different features or fixes in isolation by creating multiple branches.
            
        * **Merging**: branches can be merged back into the main codebase.
            
        * **Backup::** Acts as a backup of your codebase.
            
        * **Performance:** Git is optimised for speed, handling large projects efficiently.
            
    
* ### What is the difference between the Main Branch and the Master Branch?🌳
    
    Before Microsoft acquired GitHub, the platform used "master" as its default branch name. However, due to concerns about the term's association with "master-slave," GitHub changed the default branch name to "Main" after the acquisition.
    

| **Feature** | Main Branch | Master Branch |
| --- | --- | --- |
| Default Usage | New branch | Old branch |
| Purpose | The primary branch of stable code | The primary branch of stable code |
| Functionality | Identical to "master" | Identical to the "main" |
| Usage in New Projects | Recommended for new projects | Used in old projects |

* ### Explain the difference between Git and GitHub.
    
* Git is the tool you use to manage your code locally, GitHub is like a social network for developers that use Git under the hood. Here’s a simple breakdown:
    
    * **Git:** A command-line tool for version control. You use it on your computer to manage your project’s history.
        
    * **GitHub:** A cloud-based platform that hosts Git repositories and adds extra features like issue tracking, pull requests, and team collaboration.
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721312872354/1f9bda5d-22ad-4bab-aac9-55cafd702b8f.png align="center")
    
* ### How do to create a new repository on GitHub?🆕
    
* **Log in to GitHub:** Open GitHub and log in to your account.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721313348012/3256fbd0-a179-4b15-8ae3-7129fc833f38.png align="center")
    
* **New Repository:** Click the "New" button from the repositories section on your dashboard.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721313293221/8de9d664-c1ca-4f44-9da6-a511474fbbdb.png align="center")
    
* **Repository Details:** Fill in the repository name, description (optional), and choose whether the repository should be public or private.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721313404002/c155b9f8-feec-4432-a0ed-fa4174ac8b1e.png align="center")
    
* **Initialize Repository:** You can initialize the repository with a README, .gitignore file, and choose a license.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721313506334/a8e7fa27-99b1-4c2f-8f18-bcd97b3d66b9.png align="center")
    
* **Create Repository:** Click the "Create repository" button.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721313548958/fbfc3ac0-5979-462a-bbae-76c9c8f9b62d.png align="center")
    
* ### What is the difference between a local & remote repository? How to connect local to remote?🌐
    
    * Local Repository:
        
        * Stored on your local machine.
            
        * Contains your working directory and Git database.
            
    * Remote Repository:
        
        * Hosted on a server (e.g., GitHub).
            
        * Allows collaboration with other developers.
            
    * Connecting Local to Remote:
        
        1. Initialize a local repository: `git init`
            
        2. Add a remote: `git remote add origin <URL>`
            
    
    ```powershell
    
    ubuntu@ip-172-31-45-42:~/day12$ git config --global user.email "<email>"                                                                         @gamil.com"
    ubuntu@ip-172-31-45-42:~/day12$ git config --global user.name "ketanhiray"
    ubuntu@ip-172-31-45-42:~/day12$ git config --list
    ```
    
* ```powershell
    ubuntu@ip-172-31-45-42:~/day12$ mkdir github
    ubuntu@ip-172-31-45-42:~/day12$ cd github/
    ubuntu@ip-172-31-45-42:~/day12/github$ git init
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721322097923/32f44ab3-39a6-4984-acf4-f3b8ef2ea17e.png align="center")
    

```powershell
ubuntu@ip-172-31-45-42:~/day12/github$ git remote add origin https://github.com/ketanhiray/DevOps.git
```

```powershell
ubuntu@ip-172-31-45-42:~/day12/github$ mkdir -p Devops/Git
ubuntu@ip-172-31-45-42:~/day12/github$ echo "Hello this is test text for git demo." > Devops/Git/Demo-day12.txt
ubuntu@ip-172-31-45-42:~/day12/github$ git add Devops/Git/Demo-day12.txt
ubuntu@ip-172-31-45-42:~/day12/github$ git commit -m "Text is addded in file"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721322646384/26dc479f-3d74-4e25-a79e-1c1c407f1761.png align="center")

<mark>Create Personal Access Token on GitHub</mark>

From your GitHub account, go to **Settings** → **Developer Settings** → **Personal Access Token** → **Tokens (classic)** → **Generate New Token** (Give your password) → **Fillup the form** → click **Generate token** → **Copy the generated Token**, it will be something like `ghp_sFhFsSHhTzMDreGRLjmks4Tzuzgthdvfsrta`

```powershell
ubuntu@ip-172-31-45-42:~/day12/github$ git remote set-url origin https://<TOKEN>@github.com/ketanhiray/Devops
ubuntu@ip-172-31-45-42:~/day12/github$ git push origin master
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721324565485/a25e9ff4-404c-4b80-a621-59eb13740a1e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721324596273/a7c23eb8-1a5f-4efa-9d78-7fbee0365c41.png align="center")

### Conclusion 🎉

Understanding Git and GitHub is vital for modern software development. Git helps manage project history, while GitHub streamlines collaboration. Mastering these tools enables efficient work, team collaboration, and project management. Happy coding! 💻