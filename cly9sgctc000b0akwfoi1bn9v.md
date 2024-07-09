---
title: "Day 4 - Basic Linux Shell Scripting for DevOps Engineers💻"
seoTitle: "Linux,DevOps"
datePublished: Sat Jul 06 2024 07:13:53 GMT+0000 (Coordinated Universal Time)
cuid: cly9sgctc000b0akwfoi1bn9v
slug: day-4-basic-linux-shell-scripting-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720188021223/1601a9ed-8497-46fe-9c53-be03f3826db9.jpeg
tags: linux, devops, 90daysofdevops, 90daysofdevops-chanllenge

---

### 🌟What is Kernel?

The kernel is the heart of a computer's operating system, managing all interactions between software and hardware. It controls functions like CPU scheduling, memory management, and device communication. By efficiently managing system resources, the kernel ensures smooth operation and stability, making it a crucial component in any computing environment.

### 🌟What is Shell?

A shell is a command-line tool that lets users interact with the operating system. It takes text commands and turns them into actions performed by the system. Think of the shell as a link between you and the complex processes running in the background.🖥️➡️💻

#### 🔑Key Functions of a Shell

1. **Command Execution:**
    
    * The shell allows you to execute commands to manage files, run applications, and control the system.
        
    * Example: `ls` to list files, `cd` to change directories.📂
        
2. **Scripting:**
    
    * Shells can execute scripts, which are collections of commands saved in a file, to automate tasks.
        
    * Example: A script to back up important files daily.📜
        
3. **Customisation:**
    
    * Users can customize their shell environment with variables, aliases, and functions to enhance productivity.
        
    * Example: Setting the `PATH` variable to include custom directories.🛠️
        
4. **Job Control:**
    
    * The shell can manage multiple tasks, allowing you to run processes in the foreground or background.
        
    * Example: Running a long process in the background using `&`.🔄
        

### 🌟What is Linux Shell Scripting?

Linux shell scripting is a powerful tool that lets users automate tasks, manage systems, and streamline workflows using the shell. It's an important skill for anyone working in Linux environments, especially in system administration, DevOps, and development. 🐧💻

### **What is Linux Shell Scripting for DevOps? 🤖**

Linux shell scripting is a powerful tool for DevOps engineers, allowing them to automate tasks and streamline their workflows. By writing scripts, DevOps engineers can automate repetitive tasks, such as deploying code or managing infrastructure, saving time and increasing efficiency.

### What is #!/bin/bash? Can we write #!/bin/sh as well? 🤔

`#!/bin/bash` is known as a shebang or hashbang. It specifies which interpreter should be used to execute the script. In this case, it specifies that the script should be run using the `bash` shell. Yes, you can also write `#!/bin/sh`, which specifies that the script should be run using the `sh` shell.

### Example 1: Write a Shell Script that prints “I will complete #90DaysOfDevOps challenge” 📝

Here’s an example of a simple shell script that prints “I will complete #90DaysOfDevOps challenge”:

```powershell
#!/bin/bash
echo "I will complete #90DaysOfDevOps challenge"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720423220128/ea505eaa-c1e6-4975-8b0c-0d7bb08a5bc7.png align="center")

### **Example 2: Write a Shell Script to take user input, input from arguments, and print the variables**

```powershell
#!/bin/bash
echo "Enter your name:"
read name
echo "Hello $name!"
echo "You entered $# arguments: $@"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720423343231/729c5f17-acef-4a20-a515-5d25141f0a30.png align="center")

### **Example 3: Write an Example of If-else in Shell Scripting by comparing 2 numbers**

```powershell
#!/bin/bash
num1=5
num2=10
if [ $num1 -gt $num2 ]
then
    echo "$num1 is greater than $num2"
else
    echo "$num1 is less than $num2"
fi
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720423490609/6a9664c1-70f7-4fef-b690-d758d1af58b5.png align="center")

"Today, we hope you enjoyed learning about basic Linux shell scripting for DevOps engineers".💻