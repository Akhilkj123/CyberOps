![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/73796fcb-67fa-416f-85db-765b689852c2)![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/31128e0f-c925-4138-807f-05172cf28655)## Part 1: Certificates Trusted by Your Browser
### Step 1: Display the Root Certificates in Chrome.

a. Open the Chrome web browser on your PC.

b. Click the three-dot icon on the far right of the address bar to display Chrome’s options. Click Settings.

c. Scroll down to Privacy and security and click More.

d. Scroll down and select Manage certificates.

e. In the Certificate window, select Trusted Root Certification Authorities tab to show all certificates and
certificate authorities trusted by Chrome.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/71ad0dec-cbf4-42e0-94e5-0b883ac60daf)
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/6142d1d0-81a5-4f7f-8f59-4aac6ca0e06a)

### Step 2: Display the Certificates in the CA Store in Firefox.
a. Open Firefox and click the Menu icon. The Menu icon is located on the far right of the Firefox window,
next to the address bar. Click Preferences.

b. Click Privacy & Security in the left panel.

c. Scroll down to the Security section and click View Certificates.

d. A window opens that shows the certificates and certification authorities trusted by Firefox.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/777a4347-b370-4be8-94cc-e142eef91ef2)

## Part 2: Checking for Man-In-Middle
### Step 1: Gathering the correct and unmodified certificate fingerprint.

The first step is to gather a few site fingerprints. This is important because these will be used for comparison
later. The table below contains a few site certificate fingerprints from popular sites.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/7a46e51f-d2a0-4d9e-913c-6bb0b493404d)
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/2a56185f-47e0-4e93-b6fd-01fb530e4a6f)

What are the fingerprints? Why are they important?
- SHA-1 fingerprints are cryptographic checksums derived from digital certificates to verify their authenticity and integrity. They are essential for security by ensuring the legitimacy of digital certificates and protecting against man-in-the-middle attacks.

Who calculates fingerprints? How to find them?
- Fingerprints are calculated by the issuer of the digital certificate, typically a Certificate Authority (CA) or the organization responsible for the server. 
 
### Step 2: Gather the certificate fingerprint in use by the CyberOps Workstation VM.
a. Use the three piped commands below to fetch the fingerprint for Cisco.com. The line below uses
OpenSSL to connect to cisco.com on port 443 (HTTPS), request the certificate and store it on a text file
named cisco.pem. The output is also shown for context.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/48512cf2-0062-4608-b3a7-5dfa3e8e3582)

b. Optionally, use the cat command to list the contents of the fetched certificate and stored in the
cisco.pem text file:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/0da0197c-2e87-4e4a-bdeb-0725f827138a)

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/df0bc89f-593d-4f96-bc08-b127bc1390a6)

c. Now that the certificate is saved in the cisco.pem text file, use the command below to extract and display
its fingerprint:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/819dc731-19d7-4322-8f8b-e43edff358bc)

What hash algorithm was used by OpenSSL to calculate the fingerprint?
- OpenSSL typically uses the SHA-1 hash algorithm to calculate fingerprints of X.509 certificates. 

Why was that specific algorithm chosen? Does it matter?
- The choice of SHA-1 for fingerprints was historical, but it now matters for security because SHA-1 is weak and susceptible to attacks. Stronger algorithms like SHA-256 or SHA-3 are recommended for better security in modern practices.

### Step 3: Compare the Fingerprints
Use Table 1 to compare the certificate fingerprint acquired directly from the Cisco HTTPS site with the one
acquired from within your network. Recall, fingerprints may change over time.

Do the fingerprints match?
- No

What does it mean?
- Somethings have been changed

What would be necessary for the HTTPS proxy to work?
- To make an HTTPS proxy work, you'll need a configured proxy server, SSL/TLS certificates for secure connections, and client settings that route traffic through the proxy. 
