---
title: "Day 2 - Linux"
seoTitle: "DevOps"
seoDescription: "linux"
datePublished: Thu Jul 04 2024 06:27:52 GMT+0000 (Coordinated Universal Time)
cuid: cly6vxgv4000a0amg21po2al9
slug: day-2-linux
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719999121304/df0f7486-81bc-425e-9665-cff2d89945f8.jpeg
tags: devops, 90daysofdevops, shubhamlondhe, linux-for-devops, 90daysofdevops-chanllenge

---

* ### Listing commands
    
    *ls option\_flag arguments* --&gt; List the subdirectories and files available in the present directory
    
    * `ls -l`\--&gt; List the files and directories in long list format with extra information
        
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720017093746/513ba8b8-f69c-4a22-88e3-8aa2425f83b5.png align="center")
        
    * `ls -a` --&gt; List all including hidden files and directory
        
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720017132574/4600b08c-3f6c-49f1-8b28-e096960bec4b.png align="center")
        
    * `ls *.sh` --&gt; list all the files having .sh extension.
        
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720017215764/bbe42e1b-42ac-49f0-bd70-624b5005067f.png align="center")
        
    * `ls -i` --&gt; List the files and directories with index numbers Inodes
        
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720017534118/01920c3d-3f61-4e8d-b3d1-cb770e4f4794.png align="center")
        
    * `ls -d */` --&gt; list only directories.(we can also specify a pattern)
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720017590163/716d7e59-d2ca-46a6-a808-bcd911ac29ac.png align="center")
    
* ### Directory commands
    
    * `pwd` --&gt; Print work directory. Gives the present working directory.
        
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720017620333/760d88b0-40ed-42e1-8f84-6b52b8ad5699.png align="center")
        
    * `cd path_to_directory` --&gt; Change directory to the provided path
        
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720019157388/b11c968e-0a3c-46e8-aa25-e81d51451b37.png align="center")
        
    * `cd ~` or just `cd` --&gt; Change directory to the home directory
        
    * `cd -` --&gt; Go to the last working directory.
        
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720017744069/e01e7ebd-795f-429f-8acd-663cf860609b.png align="center")
        
    * `cd ..` --&gt; Change the directory to one step back.
        
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720017790227/3d40c0cf-a3ed-4676-ae0c-5a12671729c5.png align="center")
        
    * `cd ../..` --&gt; Change directory to 2 levels back.
        
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720017836640/abef8f1a-ce56-4866-9db2-548049e805af.png align="center")
        
    * `mkdir directoryName` --&gt; Use to make a directory in a specific location
        
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720019315908/aaf5581a-8a8c-4c15-8233-5a240cea197f.png align="center")
        
    
    **Examples:**
    
* ***mkdir newFolder*** # make a new folder 'newFolder'
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720018376043/0e2ddc6e-595e-4c73-858a-0343646563d1.png align="center")
    
    ***mkdir .NewFolder*** # make a hidden directory (also . before a file to make it hidden)
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720018549736/ee46aa67-5715-4d9d-9b08-0c2840c2d9db.png align="center")
    
    ***mkdir A B C D*** #make multiple directories at the same time
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720018660960/b42fc855-59e5-4a4a-b0c2-c1fda0ea8157.png align="center")
    
    ***mkdir /home/user/Mydirectory*** \# make a new folder in a specific location
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720018810624/b688bfde-d3f8-4a0e-a6e4-e58ea2c1bf64.png align="center")
    
    ***mkdir -p A/B/C/D*** # make a nested directory
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720019018508/dcb41536-6e6b-4b97-9a05-3eeab24d8cf3.png align="center")