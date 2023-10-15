## Part 1: Hashing a Text File with OpenSSL
a. In the CyberOps Workstation virtual machine, open a terminal window.
 
b. Because the text file to hash is in the /home/analyst/lab.support.files/ directory, change to that directory:

c. Type the command below to list the contents of the letter_to_grandma.txt text file on the screen:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/8bd95db5-1e45-42b9-870f-6f03a3eec68a)

d. From the terminal window, issue the command below to hash the text file. The command will use SHA-2-
256 as the hashing algorithm to generate a hash of the text file. The hash will be displayed on the screen
after OpenSSL has computed it.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/5439ca21-512f-42bf-af5a-168f99c596b5)

e. Hash functions are useful for verifying the integrity of the data regardless of whether it is an image, a
song, or a simple text file. The smallest change results in a completely different hash. Hashes can be
calculated before and after transmission, and then compared. If the hashes do not match, then data was
modified during transmission.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/ba93fa84-6b5d-4aca-a498-5e65156d4965)
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/06a90178-7de3-4c9d-8fc8-435845abd8d4)

Is the new hash different that hash calculated in item (d)? How different?
- Yes it is completely different

g. A hashing algorithm with longer bit-length, such as SHA-2-512, can also be used. To generate a SHA-2-
512 hash of the letter_to_grandma.txt file, use the command below:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/605fc765-821c-473e-8136-5825df96f35d)

h. Use sha256sum and sha512sum to generateSHA-2-256 and SHA-2-512 hash of the
letter_to_grandma.txt file:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/fe4b760b-2676-4e35-8fd2-0cbee916fca7)
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/ef19cb3c-cfb3-4002-bd82-10bc5c3381e9)

Do the hashes generated with sha256sum and sha512sum match the hashes generated in items (f) and
(g), respectively? Explain.
- Yes, both are same hash as in items (f) and (g)

## Part 2: Verifying Hashes
a. Along with sample.img, sample.img_SHA256.sig was also downloaded. sample.img_SHA256.sig is a file
containing the SHA-2-256 hash that wascomputed by the website. First, use the cat command to display
the contents of the sample.img_SHA256.sig file:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/ea4e9cd3-f591-496d-8b48-ea67bdb0d074)

b. Use SHA256sum to calculate the SHA-2-256 hash of the sample.img file:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/c9f24ae4-d6b3-4c6d-a226-8651c20a6cb1)

Was the sample.img downloaded without errors? Explain.
- Yes, as the samples have the same hash
