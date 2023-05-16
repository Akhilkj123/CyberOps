### Part 1: Exploring Filesystems in Linux
#### Step 1: Access the command line.
Launch the CyberOps Workstation VM and open a terminal window.
#### Step 2: Display the filesystems currently mounted.
a. Use the lsblk command to display all block devices:

[analyst@secOps ~]$ lsblk

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/53547431-ace3-485e-8611-8f6bff294ec6)

b. Use the mount command to display more detailed information on the currently mounted filesystems in the
CyberOps Workstation VM.

[analyst@secOps ~]$ mount

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/a7d34e7f-539c-4500-9747-f62955ec6613)

c. Run the mount command again, but this time, use the pipe | to send the output of mount to grep to filter
the output and display only the root filesystem:

[analyst@secOps ~]$ mount | grep sda1

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/a4b31deb-b4db-4d1e-aae6-8f2220c63027)

d. Issue the following two commands below on the CyberOps Workstation VM:

[analyst@secOps ~]$ cd /

[analyst@secOps /]$ ls -l

What is the meaning of the output? Where are the listed files physically stored?
- The listed files and directories are physically stored on the root filesystem, which, as determined earlier using the "mount" command, is located on the first partition of the sda block device (/dev/sda1). 

Why is /dev/sdb1 not shown in the output above?
- The output of the "ls -l" command in the root directory does not include the files and directories from the "/dev/sdb1" partition because the "/dev/sdb1" partition is not mounted on the root directory ("/").

#### Step 3: Manually mounting and unmounting filesystems
a. Use the ls -l command to verify that the directory second_drive is in the analyst's home directory.

[analyst@secOps /]$ cd ~

[analyst@secOps ~]$ ls –l

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/45d7cddb-a7ce-4c1e-930b-ddb48834f8cb)

b. Use ls -l again to list the contents of the newly created second_drive directory.

[analyst@secOps ~]$ ls -l second_drive/

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/c7bd34ed-1951-4ee3-a241-de528775c7c8)

c. Use the mount command to mount /dev/sdb1 on the newly created second_drive directory. The syntax
of mount is: mount [options] <device to be mounted> <mounting point>.

  [analyst@secOps ~]$ sudo mount /dev/sdb1 ~/second_drive/

 d. Now that the /dev/sdb1 has been mounted on /home/analyst/second_drive, use ls -l to list the contents
of the directory again.

  [analyst@secOps ~]$ ls -l second_drive/
  
  ![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/c5b4520d-b0d8-4299-94a9-ed2c7c7e2d18)

  Why is the directory no longer empty? Where are the listed files physically stored?
  - The directory is no longer empty because the files from /ddev/sdb1 are being mounted to ~/second_drive/
  
  e. Issue the mount command with no options again to display detailed information about the /dev/sdb1
partition. As before, use the grep command to display only the /dev/sdX filesystems:

  [analyst@secOps ~]$ mount | grep /dev/sd
  
  ![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/f832992a-425f-4e14-be6f-7468f45e706a)

  f. Unmounting filesystems is just as simple. Make sure you change the directory to something outside of the
mounting point and use the umount command, as shown below:

  [analyst@secOps ~]$ sudo umount /dev/sdb1
  
  ![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/db86dd45-d9d0-485c-a445-0e835ab5dc94)
 ![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/dbc81f3d-de91-4bc5-b05f-fef6f5328f75)

 ### Part 2: File Permission
#### Step 1: Visualize and Change the File Permissions.
  a. Navigate to /home/analyst/lab.support.files/scripts/.
  
[analyst@secOps ~]$ cd lab.support.files/scripts/

  ![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/cbf982fc-5336-43db-80be-dd347b4468ec)

  Consider the cyops.mn file as an example. Who is the owner of the file? How about the group?
  - User 'analyst' . Group 'analyst'
  
  The permissions for cyops.mn are –rw-r--r--. What does that mean?
  - It means that user has only read and write permission, while group and others have only read permission.
  
  c. The touch command is very simple and useful. It allows for the quick creation of an empty text file. Use
the command below to create an empty file in the /mnt directory:

  [analyst@secOps scripts]$ touch /mnt/myNewFile.txt
  
  [analyst@secOps ~]$ ls -ld /mnt
  
  ![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/1674d60a-65e3-4890-a3df-5c31a103777e)
  
  What can be done for the touch command shown above to be successful?
- Can add 'sudo' to the command to impersonate as user.
  
  d. The chmod command is used to change the permissions of a file or directory. As before, mount the
/dev/sdb1 partition on the /home/analyst/second_drive directory created earlier in this lab:

  [analyst@secOps ~]$ sudo mount /dev/sdb1 ~/second_drive/
  
e. Change to the second_drive directory and list the contents of it:
  
[analyst@secOps ~]$ cd ~/second_drive
  
[analyst@secOps second_drive]$ ls -l
  
  ![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/5f33d678-65f6-4377-a8d9-12cc61c720d2)

  What are the permissions of the myFile.txt file?
 - It means that user has only read and write permission, while group and others have only read permission.
  
f. Use the chmod command to change the permissions of myFile.txt.

[analyst@secOps second_drive]$ sudo chmod 665 myFile.txt

[analyst@secOps second_drive]$ ls -l
  
  ![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/5ffdc26f-cc31-494e-b12f-659083dbb578)
 
  Did the permissions change? What are the permissions of myFile.txt?
  - Yes now users and group has got write permission while others has got executable permission.
  
  What command would change the permissions of myFile.txt to rwxrwxrwx, granting any user in the
system full access to the file?
 - chmod 777 myFile.txt

  g. The chown command is used to change ownership of a file or directory. Issue the command below to
make root the owner of the myFile.txt:
  
[analyst@secOps second_drive]$ sudo chown analyst myFile.txt 

 ![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/5225cbc4-e6dc-4453-85f4-2b4e333eaa38)

  h. Now that analyst is the file owner, try appending the word ‘test’ to the end of myFile.txt.

  [analyst@secOps second_drive]$ echo test >> myFile.txt

[analyst@secOps second_drive]$ cat myFile.txt

  Question:
Was the operation successful? Explain
  
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/99b8d98c-44cc-4c0e-8b0a-6bc9240c0ee5)

  #### Step 2: Directory and Permissions
  
  a. Change back to the /home/analyst/lab.support.files directory and issue the ls -l command to list all the
files with details:

  [analyst@secOps second_drive]$ cd ~/lab.support.files/

  [analyst@secOps lab.support.files]$ ls -l
  
  ![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/6c67501d-ccbd-432a-b86e-3bb54df0ff4b)

  Question:Compare the permissions of the malware directory with the mininet_services file. What is the difference
between beginning part of the malware line and the mininet_services line?
- Malware is a directory and mininet_services is a file.
  
  ### Part 3: Symbolic Links and other Special File Types
  #### Step 1: Examine file types.
  a. Use the ls -l command to display the files in the /home/analyst folder. Notice the first characters of each
line are either a “–“ indicating a file or a “d” indicating a directory.

  [analyst@secOps ~]$ ls -l
  
  ![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/f261aecf-06ca-42e7-9788-6eb7ffe48e2b)

 b. Produce a listing of the /dev directory. Scroll to the middle of the output and notice how the block files
begin with a “b”, the character device files begin with a “c” and the symbolic link files begin with an “l”:

  [analyst@secOps ~]$ ls -l /dev/
  
  ![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/59816fc8-7c86-4b83-a0bf-8cbfdf9ac11c)
  
 c. Symbolic links in Linux are like shortcuts in Windows. There are two types of links in Linux: symbolic links
and hard links. The difference between symbolic links and a hard links is that a symbolic link file points to
the filename of another file and a hard link file points to the contents of another file. Create two files by
using echo:
[analyst@secOps ~]$ echo "symbolic" > file1.txt
[analyst@secOps ~]$ cat file1.txt
[analyst@secOps ~]$ echo "hard" > file2.txt
[analyst@secOps ~]$ cat file2.txt
  
  ![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/f4d0072d-7643-40da-880e-2162e062dd89)

  
  



  
