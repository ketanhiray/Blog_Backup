---
title: "Day 7 Tutorial: Understanding Package Managers and Systemctl Basics"
seoTitle: "DevOps"
datePublished: Thu Jul 11 2024 09:20:22 GMT+0000 (Coordinated Universal Time)
cuid: clyh269si000008ma063shnht
slug: day-7-tutorial-understanding-package-managers-and-systemctl-basics
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720685489301/42518068-b1e2-461b-9248-3e11ad261bca.png
tags: linux, devops, 90daysofdevops

---

### What is a Package Manager in Linux?

Simply put, a package manager is a tool that enables users to install, remove, upgrade, configure, and manage software packages on an operating system. The package manager can be a graphical application like a software centre or a command-line tool like apt-get or Pacman.

### What is a Package?📦

A package is typically known as an application, but it can also be a GUI application, command line tool, or a software library needed by other software programs. Essentially, a package is an archive file that includes the binary executable, configuration file, and sometimes information about the dependencies.

### Different Kinds of Package Managers

There are many different package managers available for Linux. Some of the most popular package managers include:

* APT (Advanced Packaging Tool) is the default package manager for Debian-based distributions, such as Ubuntu and Mint.
    
* YUM (Yellowdog Update Manager) is the default package manager for Red Hat-based distributions, such as CentOS and Fedora.
    
* DNF (Dandified YUM) is a newer package manager that is based on YUM.
    
* Pacman is the default package manager for Arch Linux.
    

## Tasks📝

### **Install Docker:**

```powershell
# Update the package index
sudo apt update
# Install Docker
sudo apt install docker.io

sudo systemctl status docker
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720682554567/c7945136-1de8-4ab9-a7e6-2e50522d6baf.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720682783303/2216e430-9f10-421b-aa9c-a695167e964d.png align="center")

**Check Docker Service Status:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720683479722/f4b7a8f1-321a-4884-b52a-77a58cd62de8.png align="center")

**Analyze Logs:**

```powershell
journalctl -u docker
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720684933849/0543d933-7ddc-43bd-a2b4-3e83cac1fc08.png align="center")

### **Install Jenkins:**

```powershell
sudo apt install openjdk-11-jdk
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update
sudo apt install default-jre
sudo apt install jenkins
sudo systemctl start jenkins
sudo systemctl enable jenkins
sudo systemctl status jenkins
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720683043618/0974ef9c-b99e-4d9f-a787-779701727c32.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720683250201/56ea12c1-4f4c-44d1-8fd3-2f57dfed76e6.png align="center")

**Manage Jenkins Service:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720684320449/c3d73ee4-4ae9-4341-90c3-caf7f0c871c1.png align="center")

**Analyze Logs:**

```powershell
journalctl -u jenkin
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720685094133/7ea61242-672c-4c7e-840b-e38337c5e285.png align="center")

### Systemctl and Systemd🛅

Systemd is the init system and service manager for most Linux distributions. It is responsible for starting and stopping system services, such as the Docker daemon and the Jenkins service.

Systemctl is a command-line tool used to control and monitor the systemd system and service manager. Some common tasks with systemctl include starting, stopping, restarting, reloading, enabling, disabling, masking, unmasking, and checking the status of units.

* Understanding the `systemctl` and `service` Commands
    
    * Both `systemctl` and `service` commands are used to manage system services in Linux, but they differ in terms of usage, functionality, and the system architectures they support.
        
    * `systemctl` Command
        
        * `systemctl` is a command used to introspect and control the state of the `systemd` system and service manager. It is more modern and is used in systems that use `systemd` as their init system, which is common in many contemporary Linux distributions.
            
        * Examples:
            
            * Check the status of the Docker service:
                
                ```powershell
                   sudo systemctl status docker
                ```
                
            * Start the Jenkins service:
                
                ```powershell
                   sudo systemctl start jenkins
                ```
                
            * Stop the Docker service:
                
                ```powershell
                   sudo systemctl stop docker
                ```
                
            * Enable the Jenkins service to start at boot:
                
                ```powershell
                   sudo systemctl enable jenkins
                ```
                
    * `service` Command
        
        * 'service' is a command that works with the older 'init' systems (like SysVinit). It provides a way to start, stop, and check the status of services. While it is still available on systems using 'systemd' for backward compatibility, its usage is generally discouraged in favor of 'systemctl'.
            
        * Examples:
            
            * Check the status of the Docker service:
                
                ```powershell
                   sudo service docker status
                ```
                
            * Start the Jenkins service:
                
                ```powershell
                   sudo service jenkins start
                ```
                
            * Stop the Docker service:
                
                ```powershell
                   sudo service docker stop
                ```
                
    * **Key Differences**
        
        * System Architecture:
            
            * `systemctl` works with `systemd`.
                
            * `service` works with SysVinit and is compatible with `systemd` for backward compatibility.
                
        * Functionality:
            
            * Remember: systemctl offers advanced control over services, including managing service state, enabling/disabling services at boot, and querying detailed service status.
                
                Meanwhile, service provides basic functionality for managing services, such as starting, stopping, and checking their status.
                
        * Syntax and Usage:
            
            * `systemctl` uses a more unified syntax for managing services.
                
            * `service` has a simpler and more traditional syntax.