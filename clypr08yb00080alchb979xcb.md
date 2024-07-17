---
title: "Effective Error Handling Techniques in Shell Scripting – Day 11"
seoTitle: "DevOps"
datePublished: Wed Jul 17 2024 11:17:41 GMT+0000 (Coordinated Universal Time)
cuid: clypr08yb00080alchb979xcb
slug: effective-error-handling-techniques-in-shell-scripting-day-11
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1721214761897/9b6c6adf-46fd-4371-9487-a04c3bf2c8f3.png
tags: linux, devops, shell-script, 90daysofdevops

---

## Objectives🎯

Handling errors in shell scripts is crucial for creating reliable scripts. Today, we will learn effective error-handling techniques in bash scripts.

## Topics to Cover🗂

1. **Understanding Exit Status**: Every command returns an exit status (0 for success and non-zero for failure). Learn how to check and use exit statuses.
    
2. **Using if Statements for Error Checking**: Learn how to use if statements to handle errors.
    
3. **Using trap for Cleanup**: Understand how to use the trap command to handle unexpected errors and perform cleanup.
    
4. **Redirecting Errors**: Learn how to redirect errors to a file or /dev/null.
    
5. **Creating Custom Error Messages**: Understand how to create meaningful error messages for debugging and user information.
    

## Tasks📝

### Task 1: Checking Exit Status

* Write a script that attempts to create a directory and checks if the command was successful. If not, print an error message.
    
    ```powershell
    
    ubuntu@ip-172-31-45-42:~$ mkdir day11
    ubuntu@ip-172-31-45-42:~$ cd day11/
    ubuntu@ip-172-31-45-42:~/day11$ pwd
    /home/ubuntu/day11
    ubuntu@ip-172-31-45-42:~/day11$ vim create_directory.sh
    ubuntu@ip-172-31-45-42:~/day11$ cat create_directory.sh
    ubuntu@ip-172-31-45-42:~/day11$ ./create_directory.sh
    -bash: ./create_directory.sh: Permission denied
    ubuntu@ip-172-31-45-42:~/day11$ chmod +x create_directory.sh
    ubuntu@ip-172-31-45-42:~/day11$ ./create_directory.sh
    ```
    
    ```powershell
    #!/bin/bash
    #Create directory
    mkdir /home/ubuntu/day11/directory1
    
    #Check the status
    if [ $? -ne 0 ]; then
            echo "Fail to create directory /home/ubuntu/day11/"
    else
            echo "Directory created successfully.!!!! "
    
    fi
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721198964756/abc33e37-b683-429a-8a2c-ea8d488bb97a.png align="center")
    

### Task 2: Using `if` Statements for Error Checking

* Modify the script from Task 1 to include more commands (e.g., creating a file inside the directory) and use `if` statements to handle errors at each step.
    
* ```powershell
    ubuntu@ip-172-31-45-42:~/day11$ vim create_directory2.sh
    ubuntu@ip-172-31-45-42:~/day11$ cat create_directory2.sh
    ubuntu@ip-172-31-45-42:~/day11$ chmod +x create_directory2.sh
    ubuntu@ip-172-31-45-42:~/day11$ ./create_directory2.sh
    ```
    
* ```powershell
     #!/bin/bash
    #create a directory
    mkdir /home/ubuntu/day11/directory3
    
    if [ $? -ne 0 ]; then
       echo "Error: Fail to create directory /home/ubuntu/day11"
       exit 1
    fi
    
    #create file inside the directory
    touch /home/ubuntu/day11/directory3/task2.txt
    
    if [ $? -ne 0 ]; then
       echo "Error: Fail to create file /home/ubuntu/day11/directory3/task2.txt"
       exit 1
    fi
    
    echo "Directory and File created Successfully"
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721202794997/918fc911-e51c-4a71-ae03-7c3225e85ab6.png align="center")

### Task 3: Using `trap` for Cleanup

* Write a script that creates a temporary file and sets a `trap` to delete the file if the script exits unexpectedly.
    
* ```powershell
    ubuntu@ip-172-31-45-42:~/day11$ ls
    create_directory.sh  create_directory2.sh  directory3  trap.sh
    ubuntu@ip-172-31-45-42:~/day11$ cat trap.sh
    ubuntu@ip-172-31-45-42:~/day11$ chmod +x trap.sh
    ubuntu@ip-172-31-45-42:~/day11$ ./trap.sh
    ```
    
    ```powershell
    #!/bin/bash
    #Create a temp file
    temp_file="/home/ubuntu/day11/temp_file_$$.txt"
    touch "$temp_file"
    echo "Temporary file created at $temp_file"
    
    #set up a trap to delete the temporary file
    trap 'echo "Deleting temporary file"; rm -f "$temp_file"' EXIT
    
    #Timer
    echo "Script is running...."
    sleep 10
    
    #Normal exit
    echo "Script completed successfully.....!"
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721212220611/f0683e93-3f72-47b5-babe-dc7267f08233.png align="center")
    

### Task 4: Redirecting Errors

* Write a script that tries to read a non-existent file and redirects the error message to a file called `error.log`.
    
* ```powershell
    ubuntu@ip-172-31-45-42:~/day11$ ls
    create_directory.sh  create_directory2.sh  directory3  trap.sh
    ubuntu@ip-172-31-45-42:~/day11$ vim reditect_errors.sh
    ubuntu@ip-172-31-45-42:~/day11$ cat reditect_errors.sh
    ubuntu@ip-172-31-45-42:~/day11$ chmod +x reditect_errors.sh
    ubuntu@ip-172-31-45-42:~/day11$ ./reditect_errors.sh
    ```
    
    ```powershell
    #!/bin/bash
    #
    
    #Read a non-exitent file and redirect the error
    cat non_existent_file.txt 2> error.log
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721212816793/461ae707-e1d6-464e-8c83-a6d9bbf5cbb5.png align="center")
    

### Task 5: Creating Custom Error Messages

* Modify one of the previous scripts to include custom error messages that provide more context about what went wrong.
    
* ```powershell
    ubuntu@ip-172-31-45-42:~/day11$ vim custom_error_msg.sh
    ubuntu@ip-172-31-45-42:~/day11$ cat custom_error_msg.sh
    ubuntu@ip-172-31-45-42:~/day11$ chmod +x custom_error_msg.sh
    ubuntu@ip-172-31-45-42:~/day11$ ./custom_error_msg.sh
    ```
    
    ```powershell
    #!/bin/bash
    #create a directory
    mkdir /home/ubuntu/day11/directory5
    
    if [ $? -ne 0 ]; then
       echo "Error: Directory /home/ubuntu/day11 could not be create.Please check t                                                                         he permissions.!"
       exit 1
    fi
    
    #create file inside the directory
    touch /home/ubuntu/day11/directory5/task5.txt
    
    if [ $? -ne 0 ]; then
       echo "Error: File /home/ubuntu/day11/directory5/task5.txt could not be creat                                                                         ed. please check directory is created or not "
       exit 1
    fi
    
    echo "Directory and File created Successfully"
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721213715489/5136bfb8-fe32-470f-8b3d-2dd7ed2be75c.png align="center")
    

## Conclusion💻🚀

Errors handling and ensuring proper cleanup in scripts is crucial for robust and reliable script execution. Here’s a summary of the tasks and the key points:

1. **Checking Exit Status**: Use `$?` to check the exit status of commands. If a command fails (i.e., returns a non-zero status), you can handle the error accordingly.
    
2. **Using if Statements for Error Checking**: Incorporate `if` statements to check the success of each command step-by-step. This helps in pinpointing exactly where a script might fail.
    
3. **Using** `trap` for Cleanup: Set up a `trap` to clean up resources (like temporary files) if the script exits unexpectedly. This ensures that resources are not left in an inconsistent state.
    
4. **Redirecting Errors**: Redirect error messages to a file using `2>` to capture and log errors for further analysis.
    
5. **Creating Custom Error Messages**: Enhance error handling by providing custom error messages. This gives more context about what went wrong, making debugging easier.