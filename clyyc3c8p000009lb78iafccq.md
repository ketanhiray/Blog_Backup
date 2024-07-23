---
title: "Day 14: Essential Linux and Git-GitHub Cheat Sheet"
seoTitle: "DevOps, Linux ,Git , GitHub"
datePublished: Tue Jul 23 2024 11:30:06 GMT+0000 (Coordinated Universal Time)
cuid: clyyc3c8p000009lb78iafccq
slug: day-14-essential-linux-and-git-github-cheat-sheet
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1721729958157/e5a82c7e-5559-49d1-a016-57a46ab17fb6.png
tags: linux, github, git, devops, 90daysofdevops

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721730376145/a28f1640-cb3f-4ec4-90d0-ebb95215147f.png align="center")

### File and Directory Management🗂️

* `ls`: List directory contents.
    
    * `ls -l`: List in long format.
        
    * `ls -a`: List all files including hidden files (those starting with a dot).
        
    * `ls -lh`: Long format with human-readable file sizes
        
* `cd`: Change the current directory.
    
    * Change the directory to `[dir]`. Use `cd ..` to go up one level.
        
* `pwd`: Print the current working directory.
    
* `mkdir` : Create a new directory. `mkdir new_folder`
    
* `rmdir` : Remove an empty directory. `rmdir old_folder`
    
* `rm` : Remove files or directories.
    
    * `rm -r [dir]`: Remove the directory and its contents recursively.
        
    * `rm -i [file]`: Remove with a prompt before every removal.
        

### File Permissions and Ownership🛡️

* `chmod` : Change file permissions.
    
    * Example: `chmod 755` [`script.sh`](http://script.sh)
        
    * `chmod 755 [file_name]`: Set permissions to rwxr-xr-x.
        
    * `chmod u+x [file_name]`: Add execute permission for the owner.
        
* `chown` : Change file owner and group.
    
    * Example: `chown user:group file.txt`
        
* `chgrp` : Change group ownership.
    
    * Example: `chgrp groupname file.txt`
        

### **File Permissions Symbols**🔑

* `r`: Read permission.
    
* `w`: Write permission.
    
* `x`: Execute permission.
    
* `-`: No permission.
    

### Viewing and Editing Files📖

* `cat` : Concatenate and display file contents.
    
    * Example: `cat file.txt`
        
* `less` : View file contents one screen at a time.
    
    * Example: `less file.txt`
        
* `nano` : Simple text editor.
    
    * Example: `nano file.txt`
        
* `vi` or `vim` : Advanced text editor.
    
    * Example: `vim file.txt`
        

### Process Management⏳

* `ps`: Display current processes.
    
    * Example: `ps aux` - Display detailed information about all running processes.
        
* `top`: Display and manage processes in real-time.
    
    * Example: `top`
        
* `htop`: Enhanced version of `top` (needs to be installed).
    
* `kill`: Terminate a process.
    
    * Example: `kill 1234` (terminate the process with PID 1234)
        
* `killall [process_name]`: Terminate all processes with the specified name.
    
* `bg`: Resume a suspended job in the background.
    
* `fg`: Bring a background job to the foreground.
    
* `jobs`: List all background jobs.
    
* `systemctl` : Manage system services.
    
    * Example: `systemctl start nginx` (start nginx service), `systemctl status nginx` (check status of nginx service)
        

### Networking🌐

* `ifconfig`: Display or configure network interfaces.
    
    * Example: `ifconfig eth0`
        
* `ping [host]`: Check the network connection to a server.
    
    * Example: `ping` [`google.com`](http://google.com)
        
* `netstat`: Network statistics.
    
    * Example: `netstat -tuln` (List all listening ports.)
        
* `wget [url]`: Download files from the web.
    
* `curl [url]`: Transfer data from or to a server.
    
* `ip addr`: Show IP addresses and network interfaces.
    

### Disk Usage💾

* `df`: Display disk space usage.
    
    * Example: `df -h` human-readable format.
        
* `du`: Estimate file space usage.
    
    * Example: `du -sh [file/dir]`: Display summary in human-readable format.
        

### Archive and Compression📦

* `tar`: Archive files.
    
    * Example: `tar -cvf archive.tar folder/` (create), `tar -xvf archive.tar` (extract)
        
* `gzip`: Compress files.
    
    * Example: `gzip file.txt`
        
* `gunzip`: Decompress files.
    
    * Example: `gunzip file.txt.gz`
        
* `zip [`[`archive.zip`](http://archive.zip)`]` [`[file/dir]`](http://archive.zip/): Create a zip file archive.
    
* `unzip [`[`archive.zip`](http://archive.zip)[`]`:](http://archive.zip/) Extract zip file archive.
    

### **Access Control Lists (ACL)**🔐

* `getfacl [file]`: Get the ACL of a file.
    
* `setfacl -m u:[user]:[permissions] [file]`: Set ACL for a user.
    
* `setfacl -m g:[group]:[permissions] [file]`: Set ACL for a group.
    
* `setfacl -x u:[user] [file]`: Remove ACL for a user.
    

### **Searching**🕵🏻

* `grep [pattern] [file]`: Search for a pattern in a file.
    
* `grep -r [pattern] [dir]`: Recursively Search in a directory.
    
* `grep -i [pattern] [file]`: Search Case-insensitive file name .
    
* `find [dir] -name [pattern]`: Find files by name.
    
* `locate [name]`: Find files by name (uses a database, needs to be updated with `updatedb`).
    

### **Package Management**🛒

* `apt update`: Update package lists but it does not install or upgrade any packages.
    
* `apt upgrade`: Installed or upgraded packages.
    
* `apt install [package]`: Install a package.
    
* `apt remove [package]`: Remove a package.
    
* `apt autoremove`: Remove unnecessary packages.
    

### **Service Management**🛠️

* `systemctl start [service]`: Start a service.
    
* `systemctl stop [service]`: Stop a service.
    
* `systemctl restart [service]`: Restart a service.
    
* `systemctl status [service]`: Check the status of a service.
    
* `systemctl enable [service]`: Enable a service to start on boot.
    
* `systemctl disable [service]`: Disable a service from starting on boot.
    

### **User Management**👨🏻‍💻

* `adduser [username]`: Add a new user.
    
* `passwd [username]`: Change the user password.
    
* `deluser [username]`: Remove a user.
    
* `usermod -aG [group] [username]`: Add a user to a group.
    
* `groups [username]`: Display list the groups a user is in.
    

### **Shell Scripting**📜

**Structure:**

```powershell
  #!/bin/bash
  echo "Hello"
```

**Variables Use:**

```powershell
  #!/bin/bash
  NAME="Ketan"
  echo "Hello, $NAME"
```

**Conditional Statements- If & else:**

```powershell
  if [ condition ]; then
    # Commands
  elif [ condition ]; then
    # Commands
  else
    # Commands
  fi
```

**Loops- For and While:**

```powershell
  for i in {1..5}; do
    echo "Iteration $i"
  done

  while [ condition ]; do
    # Commands
  done
```

### Other Commands 📑

* `echo [text]`: Display the text.
    
* `date`: Display or set the system date and time.
    
* `uptime`: Show how long the system has been running.
    
* `who`: Show who is logged on.
    
* `history`: Show command history.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721730157825/f3badc22-e119-447e-b0e2-9c9270de780c.png align="center")

### Configuration🔧

* `git config`: Set configuration values.
    
    * Example: `git config --global` [`user.name`](http://user.name) `"Your Name"`,
        
    * `git config --global` [`user.email`](http://user.email) `"`[`you@example.com`](mailto:you@example.com)`"`
        

### Repository Management📂

* `git init`: Initialize a new Git repository.
    
* `git clone`: Clone a repository into a new directory.
    
    * Example: `git clone` [`https://github.com/user/repo.git`](https://github.com/user/repo.git)
        

### Basic Snapshotting⚙️

* `git add`: It will move all the files to the staging.
    
    * Example: `git add file.txt`
        
* `git commit`: It is used to create a new commit with a specific commit message
    
    * Example: `git commit -m "Initial commit"`
        
* `git status`: Show the working tree status.
    
* `git log`: It will display a list of commits.
    
* `git diff`: Show changes between two commit IDs and working tree, etc.
    

### Branching and Merging🎋

* `git branch`: List, create, or delete branches.
    
    * Example: `git branch` (list), `git branch new-branch` (create), `git branch -d old-branch` (delete)
        
* `git checkout`: Switch branches or restore working tree files.
    
    * Example: `git checkout new-branch` (switch), `git checkout -b new-branch` (create and switch)
        
* `git merge`: Join two or more development histories together.
    
    * Example: `git merge new-branch`
        

### Remote Repositories🍃

* `git remote`: Manage a set of tracked repositories.
    
    * Example: `git remote -v` (list), `git remote add origin` [`https://github.com/user/repo.git`](https://github.com/user/repo.git) (add remote)
        
* `git fetch`: Download objects and refs from another repository.
    
    * Example: `git fetch origin`
        
* `git pull`: It will pull the changes from the remote repository to the local.
    
    * Example: `git pull origin main`
        
* `git push`: Update the remote references along with their associated objects.
    
    * Example: `git push origin main`
        

### Rewriting History⌛

* `git reset`: Reset current HEAD to the specified state.
    
    * Example: `git reset --hard HEAD~1` (delete all commit)
        
    * `git reset --soft HEAD~1`(remove from history but store in file system/staging area)
        
* `git revert`: Create a new commit that undoes the changes by creating/adding new commits.
    
    * Example: `git revert HEAD`
        
* `git rebase`: Reapply commits on top of another base tip and it will maintain in a linear format.
    
    * Example: `git rebase main`
        

### Additional Tips👀

* `.gitignore`: Text file used in Git repositories to specify which files and directories should be ignored and not tracked by Git.
    
    * Example: Add `node_modules/` to `.gitignore` to ignore all files in the `node_modules` directory.
        

### Conclusion🎯

It provides quick and concise information to help manage files, processes, permissions, and version control efficiently, thereby streamlining workflows and improving the productivity of DevOps Engineers.