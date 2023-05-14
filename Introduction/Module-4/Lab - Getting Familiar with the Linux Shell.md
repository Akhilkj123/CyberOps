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

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/2136e46f-45ed-4869-a0b2-231fc88eef07)

What would be the current directory if you issued the cd .. command at [analyst@secOps home]$?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/00b01318-76b0-4e0a-8002-51709a9ffb7f)

What would be the current directory if you issued the cd .. command at [analyst@secOps /]$?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/79f13b01-8e0c-43ac-aab8-f1229ff098ca)

#### Step 4: Redirect Outputs.
a. Use the cd command to change to the /home/analyst/ (~) directory:

b. Use the echo command to echo a message. Because no output was defined, echo will output to the
current terminal window:
[analyst@secOps ~]$ echo This is a message echoed to the terminal by echo.
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/b02a0f2a-e234-4360-a23a-fccfb1dc9292)

c. Use the > operator to redirect the output of echo to a text file instead of to the screen:
analyst@secOps ~]$ echo This is a message echoed to the terminal by echo. >
some_text_file.txt
No output was shown.

Question:
Is that expected? Explain.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/be698580-500b-4ad6-8821-6a1efb13a630)

d. Notice, that even though the some_text_file.txt file did not exist, prior to the echo command, it was
automatically created to receive the output generated by echo. Use the ls -l command to verify if the file
was really created:
[analyst@secOps ~]$ ls –l some_text_file.txt

e. Use the cat command to display the contents of the some_text_file.txt text file:
[analyst@secOps ~]$ cat some_text_file.txt

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/83ac1cd0-a8ff-4e69-a64f-48c81186179b)

f. Use the > operator again to redirect a different echo output of echo to the some_text_file.txt text file:
analyst@secOps ~]$ echo This is a DIFFERENT message, once again echoed to the terminal by echo. > some_text_file.txt

g. Once again, use the cat command to display the contents of the some_text_file.txt text file:
[analyst@secOps ~]$ cat some_text_file.txt
This is a DIFFERENT message, once again echoed to the terminal by echo.

Question:
What happened to the text file? Explain.
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/eabf43d8-ff6b-4e40-8a83-9359a56608e3)
- It got replaced.

#### Step 5: Redirect and Append to a Text File.

a. Similar to the > operator, the >> operator also allows for redirecting data to files. The difference is that >>
appends data to the end of the referred file, keeping the current contents intact. To append a message to
the some_text_file.txt, issue the command below:
[analyst@secOps ~]$ echo This is another line of text. It will be APPENDED to the output file. >> some_text_file.txt

b. Use the cat command to display the contents of the some_text_file.txt text file yet again:
[analyst@secOps ~]$ cat some_text_file.txt
This is a DIFFERENT message, once again echoed to the terminal by echo.
This is another line of text. It will be APPENDED to the output file.

Question:
What happened to the text file? Explain.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/8391377f-8cb4-496c-96fd-af0423e2e06d)

#### Step 6: Work with hidden files in Linux.
a. In Linux, files with names that begin with a ‘.’ (single dot) are not shown by default. While dot-files have
nothing else special about them, they are called hidden files because of this feature. Examples of hidden
files are .file5, .file6, .file7.

Note: Do not confuse dot-files with the current directory indicator “.” symbol. Hidden file names begin with
a dot (period), followed by more characters while the dot directory is a hidden directory comprised of only
a single dot.

b. Use ls -l to display the files stored in the analyst home directory.
[analyst@secOps ~]$ ls –l
Question:
How many files are displayed?
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/4eed84d4-a38c-4905-aade-7d8efc0cdf16)

c. Use the ls -la command to display all files in the home directory of analyst, including the hidden files.
[analyst@secOps ~]$ ls –la

Questions:

Is it possible to hide entire directories by adding a dot before its name as well? Are there any directories
in the output of ls -la above?
- Yes, it is possible to hide entire directories by adding a dot before its name. Directories with a dot before their name are considered "hidden" directories in Linux, and they are not displayed by default in directory listings.

Give three examples of hidden files shown in the output of ls -la above.
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/54c32c81-6933-4e2a-b9a2-80942becb046)

d. Type the man ls command at the prompt to learn more about the ls command.
[analyst@secOps ~]$ man ls

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/296ee32d-bc68-4682-ac85-6aa33a523bc7)

e. Use the down arrow key (one line at a time) or the space bar (one page at a time) to scroll down the page
and locate the -a option used above and read its description to familiarize yourself with the ls -a
command.

### Part 2: Copying, Deleting, and Moving Files
#### Step 1: Copying Files
a. The cp command is used to copy files around the local file system. When using cp, a new copy of the file
is created and placed in the specified location, leaving the original file intact. The first parameter is the
source file and the second is the destination. Issue the command below to copy some_text_file.txt from
the home directory to the cyops_folder2 folder:
[analyst@secOps ~]$ cp some_text_file.txt cyops_folder2/

Identify the parameters in the cp command above.

Question:
What are the source and destination files?
- The source file is some_text_file.txt and the destination directory is cyops_folder2/.

b. Use the ls command to verify that some_text_file.txt is now in cyops_folder2:
[analyst@secOps ~]$ ls cyops_folder2/


c. Use the ls command to verify that some_text_file.txt is also in the home directory:
[analyst@secOps ~]$ ls -l

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/acffc03b-07aa-4772-a5b2-728bc0928e9f)

#### Step 2: Deleting Files and Directories
a. Use the rm command to remove files. Issue the command below to remove the file some_text_file.txt
from the home directory. The ls command is then used to show that the file some_text_file.txt has been
removed from the home directory:
[analyst@secOps ~]$ rm some_text_file.txt

[analyst@secOps ~]$ ls -l

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/8710bb74-18f8-439d-81f4-4a601a035de1)

b. In Linux, directories are seen as a type of file. As such, the rm command is also used to delete directories
but the -r (recursive) option must be used. Notice that all files and other directories inside a given
directory are also deleted when deleting a parent directory with the -r option. Issue the command below to
delete the cyops_folder1 folder and its contents:
[analyst@secOps ~]$ rm –r cyops_folder1
[analyst@secOps ~]$ ls -l

#### Step 3: Moving Files and Directories
a. Moving files works similarly to copying files. The difference is that moving a file removes it from its original
location. Use the mv commands to move files around the local filesystem. Like the cp commands, the mv
command also requires source and destination parameters. Issue the command below to move the
some_text_file.txt from /home/analyst/cyops_folder2 back to the home directory:
[analyst@secOps ~]$ mv cyops_folder2/some_text_file.txt .

[analyst@secOps ~]$ ls –l cyops_folder2/
