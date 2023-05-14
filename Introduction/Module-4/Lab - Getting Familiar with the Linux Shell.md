### Part 1: Shell Basics
The shell is the term used to refer to the command interpreter in Linux. Also known as Terminal, Command
Line and Command Prompt, the shell is very powerful way to interact with a Linux computer.
#### Step 1: Access the Command Line
a. Log on to the CyberOps Workstation VM as the analyst using the password cyberops. The account
analyst is used as the example user account throughout this lab.
b. To access the command line, click the terminal icon located in the Dock, at the bottom of VM screen. The
terminal emulator opens.
#### Step 2: Display Manual Pages from the command line.
You can display command line help using the man command. A man page, short for manual page, is a built-
in documentation of the Linux commands. A man page provides detailed information about a given command
and all its available options.
a. To learn more about the man page, type:
[analyst@secOps ~]$ man man
Question:
Name a few sections that are included in a man page.
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/5900cf2b-0715-4137-b465-7280b7b2eb05)
b. Type q to exit the man page.

c. Use the man command to learn more about the cp command:
[analyst@secOps ~]$ man cp
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/f05503b4-c14a-4f95-a7a8-4890753d6ac4)

What is the function of the cp command?
- Files and Directories

What command would you use to find out more information about the pwd command? What is the
function of the pwd command?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/6f8ef7f8-690a-4ae1-9834-5eb53a318218)

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/52b724f5-93cc-47b5-bb44-81b9c5481360)

Step 3: Create and change directories.
In this step, you will use the change directory (cd), make directory (mkdir), and list directory (ls) commands.
Note: A directory is another word for folder. The terms directory and folder are used interchangeably
throughout this lab.
a. Type pwd at the prompt.
[analyst@secOps ~]$ pwd
/home/analyst

Question:
What is the current directory?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/7872ff94-8630-4512-b1b2-e52b7cfe224b)

b. Navigate to the /home/analyst directory if it is not your current directory. Type cd /home/analyst

[analyst@secOps ~]$ cd /home/analyst
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/23f428be-6fb9-4696-9f40-d2eb3b6fc2b2)

c. Type ls -l at the command prompt to list the files and folders that are in the current folder. Standing for
list, the -l option displays file size, permissions, ownership, date of creation and more.
[analyst@secOps ~]$ ls -l

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/88d13010-6afd-4d33-a1a5-204de8455f27)

d. In the current directory, use the mkdir command to create three new folders: cyops_folder1,
cyops_folder2, and cyops_folder3. Type mkdir cyops_folder1 and press Enter. Repeat these steps to
create cyops_folder2 and cyops_folder3.

e. Type ls -l to verify that the folders have been created:
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/34565c0c-4854-4589-b230-22a174859e1e)

f. Type cd /home/analyst/cyops_folder3 at the command prompt and press Enter.
[analyst@secOps ~]$ cd /home/analyst/cyops_folder3
[analyst@secOps cyops_folder3]$
Question:
Which folder are you in now?
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/3b1480bc-0feb-494d-afe5-adb99a7ff8f3)

Challenge: Type the command cd ~ and describe what happens.

Question:
Why did this happen?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/87fd7508-1347-4259-bff0-98d0127c25ae)
- '~' represents our home directory.

g. Use the mkdir command to create a new folder named cyops_folder4 inside the cyops_folder3 folder:
[analyst@secOps ~]$ mkdir /home/analyst/cyops_folder3/cyops_folder4
[analyst@secOps ~]$

h. Use the ls -l command to verify the folder creation.
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/16c75145-bd46-4d1f-93ff-1b3db29fd11c)

i. Up to this point, we have been using full or absolute paths. Absolute path is the term used when referring
to paths that always start at the root (/) directory. It is also possible to work with relative paths. Relative
paths reduce the amount of text to be typed. To understand relative paths, we must understand the . and
.. (dot and double dot) directories. From the cyops_folder3 directory, issue a ls –la:
[analyst@secOps ~]$ ls –la /home/analyst/cyops_folder3

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/3c653976-0ed4-4cb4-b5db-f75304219366)

j. Change the current directory to /home/analyst/cyops_folder3:
[analyst@secOps ~]$ cd /home/analyst/cyops_folder3
[analyst@secOps cyops_folder3]$

k. Type cd .
[analyst@secOps cyops_folder3]$ cd .
[analyst@secOps cyops_folder3]$
Question:
What happens?
- It remains in the same folder as '.' represnts the current directory.

l. Changing the directory to the .. directory, will change to the directory that is one level up. This directory is
also known as parent directory. Type cd ..
[analyst@secOps cyops_folder3]$ cd ..
[analyst@secOps ~]$

Question:
What happens?
- It goes to the parent directory.

What would be the current directory if you issued the cd .. command at [analyst@secOps ~]$?
Type your answers here.
What would be the current directory if you issued the cd .. command at [analyst@secOps home]$?
Type your answers here.
What would be the current directory if you issued the cd .. command at [analyst@secOps /]$?
