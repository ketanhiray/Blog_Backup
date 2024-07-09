---
title: "Day 6 - Linux File Permissions and Access Control Lists"
seoTitle: "DevOps"
datePublished: Tue Jul 09 2024 08:12:03 GMT+0000 (Coordinated Universal Time)
cuid: clye4upvd000009kw2hxw77hu
slug: day-6-linux-file-permissions-and-access-control-lists
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720515447755/ffcd27fc-6ba2-4a4e-b781-065ddddc5d9b.png
tags: linux, devops, shell-script, 90daysofdevops

---

### **Understanding File Permissions 🛡️**

File permissions in Linux determine who can read, write, or execute a file. Understanding these permissions is crucial for securely managing your files and directories. Let's get started!

1. **Create and Check File Permissions✍**
    
    **Create a file**:
    
    ```powershell
    ubuntu@ip-172-31-45-42:~$ touch test.txt
    ```
    
    **List file details**:
    
    ```powershell
    ubuntu@ip-172-31-45-42:~$ ls -l
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720448840611/1daad316-5d1e-43e1-bb36-fc7239668825.png align="center")
    
    You'll see something like this:
    
    **<mark>-rw-rw-r--</mark>**
    
    **Categories of Users 👥**
    
    * **Owner**: The person who created the file.
        
        * **Change owner**: `chown newowner test.txt`
            
    * **Group**: Users in a specific group.
        
        * **Change group**: `chgrp newgroup test.txt`
            
    * **Others**: All other users with access.
        
        * **Change permissions**: `chmod o+w test.txt` (adds write permission for others)
            
    
    #### Changing Permissions 🛠️
    
    1. **Change user permissions**:
        
        ```powershell
        ubuntu@ip-172-31-45-42:~$ chmod 700 test.txt
        ubuntu@ip-172-31-45-42:~$ ls -l
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720449391054/05173342-81a8-4765-bc4c-8aa5a63d2456.png align="center")
        
    
    ### **Writing an Article:✍**
    
    **File Permissions in Linux**  
    File permissions are essential for system security. By using commands such as *chown*, *chgrp*, and *chmod*, you can control access to your files and directories. This helps protect sensitive data and ensures that users can only perform authorized actions.
    
    * **Basic Permissions**
        
        * Permissions in Linux are represented by a three-digit number, where each digit represents a different set of users: owner, group, and others.
            
        * **Highest Permission:**`7` (4+2+1)
            
        * **Maximum Permission:**`777`, but effectively `666` for files due to security reasons, meaning no user gets execute permission.
            
        * **Effective Permission for Directories:**`755`
            
        * **Lowest Permission:**`000` (not recommended)
            
        * **Minimum Effective Permission for Files:**`644` (default unmask value of `022`)
            
        * **Default Directory Permission:** Includes execute permission for navigation
            
    
    ### **Access Control Lists (ACL):⚙**
    
    **Check ACL**:
    
    ```powershell
    getfacl test.txt
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720449947773/bad042f3-9a97-4781-8d97-815be069dbd7.png align="center")
    
    **Set ACL**:
    
    ```powershell
    setfacl -m u:ubuntu:rwx test.txt
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720450189923/1eb1a24f-b685-4579-9007-75b12ac4f726.png align="center")
    
    ### **Additional Tasks:🎲**
    
    * **Task:** Create a script that changes the permissions of multiple files in a directory based on user input.
        
    * ```powershell
          vim multi_user_permissions.sh
        ```
        
    
    ```powershell
    #!/bin/bash
    read -p "Enter the directory path: " dir
    read -p "Enter the file type (e.g., txt, sh, etc.): " filetype
    read -p "Enter the permissions (e.g., 755, u+x, etc.): " permissions
    
    # Change permissions for each file in the specified directory and file type
    for file in "$dir"/*.$filetype; do
      if [ -e "$file" ]; then
        chmod "$permissions" "$file"
        echo "Changed permissions of $file to $permissions"
      else
        echo "No files of type $filetype found in $dir"
      fi
    done
    ```
    
    **Task:** Write a script that sets ACL permissions for a user on a given file, based on user input.
    
    ```powershell
    ubuntu@ip-172-31-45-42:~$ vim set_acl.sh
    ```
    
    ```powershell
    #!/bin/bash
    # Function to check if setfacl is installed
    check_setfacl_installed() {
      if ! command -v setfacl &> /dev/null; then
        echo "setfacl command not found. Please install the ACL package."
        exit 1
      fi
    }
    # Function to get user input
    get_user_input() {
      read -p "Enter the username: " username
      read -p "Enter the file path: " file_path
      read -p "Enter the ACL permission (e.g., rwx): " acl_permission
    }
    # Function to set ACL permission
    set_acl_permission() {
      setfacl -m u:$username:$acl_permission $file_path
      if [ $? -eq 0 ]; then
        echo "ACL permission set successfully."
      else
        echo "Failed to set ACL permission."
      fi
    }
    # Main script execution
    check_setfacl_installed
    get_user_input
    set_acl_permission
    ```
    
    ```powershell
    ubuntu@ip-172-31-45-42:~$ chmod +x set_acl.sh
    ubuntu@ip-172-31-45-42:~$ ./set_acl.sh
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720507554647/08f39465-198a-4438-a4da-84a651ea8351.png align="center")
    
    ### **Understanding Sticky Bit, SUID, and SGID:🤔**
    
    * **Sticky bit**: Used on directories to prevent users from deleting files they do not own. Only the file owner, the directory owner, or the root user can delete or rename the files.
        
        *<mark>drwxrwxr-t</mark>*
        
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720508267925/fe11e715-5e4a-40a4-9bb8-3c94dfecd85b.png align="center")
        
    * **SUID (Set User ID)**: Allows users to run an executable with the permissions of the executable's owner.
        
        *<mark>drwsrwxr-t</mark>*
        
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720508580656/bce11b92-8ee8-4005-bb1e-240cbd48be63.png align="center")
        
    * **SGID (Set Group ID)**: Allows users to run an executable with the permissions of the executable's group .
        
        *<mark>drwsrwsr-t</mark>*
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720508695313/fc54e554-0b0c-4272-8a4c-d58b73bfd1e7.png align="center")
        
    
    ### **Backup and Restore Permissions:💾**
    
    * **Task:** Create a script that backs up the current permissions of files in a directory to a file.
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720509710837/8aad1a9e-3712-4660-b242-271a9a4bdc11.png align="center")
    
    **Task:** Create another script that restores the permissions from the backup file.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720511178074/19451317-fa43-4574-8828-6071d04c7947.png align="center")
    

### **Conclusion**

In the blog post, you learned about Linux file permissions and how to view and change them using different methods. You also learned about special permissions and access control lists that allow you to fine-tune your file security.

Permissions are an essential part of Linux system administration and DevOps engineering. They help protect your data from unauthorized access, ensuring that only authorized users and processes can perform specific tasks on your files and directories.