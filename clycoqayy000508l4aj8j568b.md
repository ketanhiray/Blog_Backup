---
title: "Day 5 - Advanced Linux Shell Scripting for DevOps Engineers with User Management"
seoTitle: "DevOps"
datePublished: Mon Jul 08 2024 07:52:57 GMT+0000 (Coordinated Universal Time)
cuid: clycoqayy000508l4aj8j568b
slug: day-5-advanced-linux-shell-scripting-for-devops-engineers-with-user-management
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720278095121/2c66908a-3770-40dc-a662-a2aa74181019.jpeg
tags: linux, devops, 90daysofdevops

---

1. **Create Directories Using Shell Script:**
    
    ```powershell
    ubuntu@ip-172-31-45-42:~/devops/ketan$ vim create_folders.sh
    ```
    
    ```powershell
    #!/bin/bash
    if [ $# -ne 3 ]; then
      echo "Usage: $0 <string> <start_day> <end_day>"
      exit 1
    fi
    
    string="$1"
    start_day=$2
    end_day=$3
    
    if ! [[ "$start_day" =~ ^[0-9]+$ ]] || ! [[ "$end_day" =~ ^[0-9]+$ ]]; then
      echo "Start and end day should be integers."
      exit 1
    fi
    
    if [ "$start_day" -gt "$end_day" ]; then
      echo "Start day should be less than or equal to the end day."
      exit 1
    fi
    
    for ((i=start_day; i<=end_day; i++)); do
      directory_name="${string}-${i}"
      mkdir "$directory_name"
      echo "Created directory: $directory_name"
    done
    echo "Directories created successfully."
    ```
    
    ```powershell
    ubuntu@ip-172-31-45-42:~/devops/ketan$ chmod 700 create_folders.sh
    ```
    
    ```powershell
    ubuntu@ip-172-31-45-42:~/devops/ketan$ ./create_folders.sh "Day" 1 90
    Created directory: Day-1
    Created directory: Day-2
    Created directory: Day-3
    Created directory: Day-4
    Created directory: Day-5
    
    Directories created successfully.
    ```
    
2. **Create a Script to Backup All Your Work:**
    
    ```powershell
    #!/bin/bash
    if [$# -ne 2]; then
            echo "Usage: $0 <source_directory> <target_directory>"
            exit 1
    fi
    
    source_dir="$1"
    target_dir="$2"
    # Validate if the source directory exists
    if [ ! -d "$source_dir" ]; then
            echo "Error: Source directory does not exist."
            exit 1
    
    fi
    # Validate if the target directory exists
    if [! -d "$target_dir" ]; then
            echo "Error: Target directory does not exist."
            exit 1
    fi
    
    # Create backup with current time stamp
    backup_file="$target_dir/backup_$(date +'%Y%m%d_%H%M%S').tar.gz"
    
    # Create the backup archive
    tar -cvf "$backup_file" -C "$source_dir" .
    echo "Backup created successfully at : $backup_file"
    ```
    
    ```powershell
    ./create_backup.sh /path/to/source_directory /path/to/target_directory
    ```
    
    ```powershell
    ubuntu@ip-172-31-45-42:~/devops$ mkdir backupfolder
    ubuntu@ip-172-31-45-42:~/devops$ ls
    backfolder  backupfolder  create_backup.sh  create_bakup.sh  ketan
    ubuntu@ip-172-31-45-42:~/devops$ ./create_backup.sh ketan backupfolder
    
    ./Day-22/
    ./Day-79/
    ./Day-84/
    ./Day-24/
    
    Backup created successfully at: backupfolder/backup_20240706_142339.tar.gz
    ```
    
3. **Read About Cron and Crontab to Automate the Backup Script:**
    
    To add a cron job to execute the shell script at 11:00 PM every day, you must open the crontab file for the user that will run the cron job. Follow these steps to add the cron job:
    
    1. Open the crontab file for editing `crontab -e`
        
    2. ```powershell
          0 23  * /path/to/your/shell/script.sh /path/to/source_directory /path/to/target_directory
        ```
        
        Replace "/path/to/your/shell/[script.sh](http://script.sh)" with the actual path to your shell script file. Also, replace "/path/to/source\_directory" and "/path/to/target\_directory" with the actual paths of the source and target directories.
        
    3. Save the crontab file and exit the editor.
        
        The cron job will now run the shell script at 11:00 PM every day. It will create a backup with the current timestamp in the specified target directory.
        
4. **Read About User Management:**
    
    Linux includes a built-in user management system to create, modify, and delete users.
    
    1. To create a user, we can use the following command:
        
        ```powershell
         sudo useradd username
        ```
        
        ```powershell
        ubuntu@ip-172-31-45-42:~/devops$ sudo useradd ketanhiray
        ubuntu@ip-172-31-45-42:~/devops$ cat /etc/passwd
        
        ketanhiray:x:1005:1007::/home/ketanhiray:/bin/sh
        ```
        
    2. To modify user permissions, we can use the following command:
        
        ```powershell
        ubuntu@ip-172-31-45-42:~/devops$ chmod 700 ketan
        ```
        
        This command will give the user `username` read, write, and execute permissions to the directory `directory`.
        
    3. To delete a user, we can use the following command:
        
        ```powershell
         sudo userdel username
        ```
        
5. **Post Your Progress:**
    
    Mastering Advanced Linux Shell Scripting opens up a world of possibilities for DevOps engineers. Automating repetitive tasks and efficiently managing users can enhance productivity and streamline operations. I'm thrilled to have honed these skills and am eager to put them into practice in real-world projects!
    
    Remember to like, comment, and share this post if you find it helpful, so we can inspire and support each other in our DevOps journey!