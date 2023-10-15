## Part 1: Create and Encrypt Files
### Step 1: Create text files
a. Start the CyberOps Workstation VM.

b. Open a terminal window. Verify that you are in the analyst home directory. Otherwise, enter cd ~ at the
terminal prompt.

c. Create a new folder called Zip-Files using the mkdir Zip-Files command.

d. Move into that directory using the cd Zip-Files command.

e. Enter the following to create three text files.

f. Verify that the files have been created, using the ls command.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/c5bd00ee-14cf-4f2d-b194-b53d59ab1cab)

### Step 2: Zip and encrypt the text files.
a. Create an encrypted zip file called file-1.zip containing the three text files using the following command:

b. When prompted for a password, enter a one-character password of your choice. In the example, the letter B was entered. Enter the same letter when prompted to verify.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/9a2ad58f-2088-4c87-833a-817751f4ec4c)

c. Repeat the procedure to create the following 4 other files

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/3ccc7e78-87f0-479e-bfca-96c07b391b70)

d. Verify that all zipped files have been created using the ls -l f* command.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/683925f1-b708-4dc9-8d9d-284189e3145a)

e. Attempt to open a zip using an incorrect password as shown.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/082cc468-00f0-44ae-ad07-d60148622c71)

## Part 2: Recover Encrypted Zip File Passwords
### Step 1: Introduction to fcrackzip
### Step 2: Recovering Passwords using fcrackzip
a. Now attempt to recover the password of the file-1.zip file. Recall, that a one-character password was
used to encrypt the file. Therefore, use the following fcrackzip command:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/cb8cedcf-f991-4e8e-b465-994c8e832e53)

How long does it take to discover the password?
- 20 seconds

b. Now attempt to recover the password of the file-2.zip file. Recall, that a two-character password was
used to encrypt the file. Therefore, use the following fcrackzip command:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/2ccfe789-e9ab-4524-939b-10156d86f93b)

How long does it take to discover the password?
- 2 seconds

c. Repeat the procedure and recover the password of the file-3.zip file. Recall, that a three-character
password was used to encrypt the file. Time to see how long it takes to discover a 3-letter password. Use
the following fcrackzip command:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/a69def71-e0f9-4e76-9750-50c7021fd398)

How long does it take to discover the password?
- 2 seconds

d. How long does it take to crack a password of four characters? Repeat the procedure and recover the
password of the file-4.zip file. Time to see how long it takes to discover the password using the following
fcrackzip command:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/361ae226-d377-4cd8-97b5-4af327504c64)

How long does it take to discover the password?
- 10 seconds

e. How long does it take to crack a password of five characters? Repeat the procedure and recover the
password of the file-5.zip file. The password length is five characters, so we need to set the -l command
option to 1-5. Again, time to see how long it takes to discover the password using the following fcrackzip
command:

How long does it take to discover the password?
- It takes more minutes
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/244ca4d5-15ca-4fd1-bc1f-cc45ad234f7e)
f. Recover a 6 Character Password using fcrackzip

It appears that longer passwords take more time to discover and therefore, they are more secure.
However, a 6 character password would not deter a cybercriminal.
Question:
How long do you think it would take fcrackzip to discover a 6-character password?

g. Repeat the procedure to recover the password of the file-6.zip file using the following fcrackzip
command:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/61680911-1b98-492f-9a28-bbaab0d1dfbc)

How long does it take to discover the password?
- It takes more hours to complete
