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

h. Once again, use the cat command to display the contents of the, now re-generated, message.enc file:

Is message.enc displayed correctly now? Explain.
- No it is displayed in base64 format

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/1b7d6fac-8e76-4cb7-baa9-dea861a1999c)

Can you think of a benefit of having message.enc Base64-encoded?
- Base64 encoding ensures data compatibility, text representation, and URL safety in various applications, making it useful for data transmission and storage.

## Part 2: Decrypting Messages with OpenSSL
a. Use the command below to decrypt message.enc:

b. OpenSSL will ask for the password used to encrypt the file. Enter the same password again.

c. When OpenSSL finishes decrypting the message.enc file, it saves the decrypted message in a text file
called decrypted_letter.txt. Use the cat display the contents of decrypted_letter.txt:


Was the letter decrypted correctly?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/a3aaa40c-81b2-4b5e-bc8c-f867864d0969)

The command used to decrypt also contains -a option. Can you explain?
- The -a option in the OpenSSL program is used to specify the input format when decrypting data.


