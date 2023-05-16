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
  
  
