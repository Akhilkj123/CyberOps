## Part 1: Encrypting Messages with OpenSSL
### Step 1: Encrypting a Text File
a. Log into CyberOPS Workstation VM.

b. Open a terminal window.

c. Because the text file to be encrypted is in the /home/analyst/lab.support.files/ directory, change to that
directory:

d. Type the command below to list the contents of the encrypted letter_to_grandma.txt text file on the
screen:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/d6377d46-36dc-42dc-944e-bdb07c15b0b7)

e. From the same terminal window, issue the command below to encrypt the text file. The command will use
AES-256 to encrypt the text file and save the encrypted version as message.enc. OpenSSL will ask for a
password and for password confirmation. Provide the password as requested and be sure to remember
the password.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/60b9eab1-1b95-434d-a632-1bdd4010f361)

f. When the process is finished, use the cat command again to display the contents of the message.enc
file. 

Did the contents of the message.enc file display correctly? What does it look like? Explain.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/61a15614-bea7-485b-8fc0-6cf98293084e)

g. To make the file readable, run the OpenSSL command again, but this time add the -a option. The -a
option tells OpenSSL to encode the encrypted message using a different encoding method of Base64
before storing the results in a file.

![Uploading image.png…]()

