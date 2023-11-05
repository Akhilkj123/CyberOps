## Part 1: Review Aerts in Sguil
a. Launch the Security Onion VM and log in. Log in with the user analyst and password cyberops

b. Open Sguil and log in. Click Select All to select the interfaces and then Start SGUIL.

c. Review the events listed in the Event Message column. One of these messages is GPL
ATTACK_RESPONSE id check returned root. This message indicates that root access may have been
gained during an attack. The host at 209.165.200.235 returned root access to 209.165.201.17. The alert
ID 5.1 is used as an example in this lab.


![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/2f660f9b-2a85-4a10-8191-df0ec90be9bd)

d. Select the Show Packet Data and Show Rule checkboxes to view each alert in more detail.


![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/8a349c90-5c75-465e-a8f1-512fffdc8ed5)

e. Right-click the alert ID 5.1 and select Transcript.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/bdff5893-5d50-422b-af45-b2e447d0ed23)

f. Review the transcripts for the alert. The transcript displays the transactions between the threat actor
source (SRC) and the target (DST) during the attack. The threat actor is executing Linux commands on
the target.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/ed061ce8-3fba-4b81-9108-da88ca02149b)


![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/809bae1b-4aaa-44d5-ba60-e04552ea9aac)

What kind of transactions occurred between the client and the server in this attack?
- The attacker from 209.165.201.17 gained root access to 209.165.200.235. The attacker proceeds to browse the file system, copy the shadow file and edited /etc/shadow and /etc/passwd.

## Part 2: Pivot to Wireshark
a. Select the alert that provided you with the transcript from the previous step. Right-click the alert ID 5.1
and select Wireshark. The Wireshark main window displays three views of a packet.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/7989f93f-9ef2-4909-9fe2-0965aaea9954)

b. To view all packets that are assembled in a TCP conversation, right-click any packet and select Follow >
TCP Stream.


![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/86259ed7-79ac-4524-b071-8a9d68115018)

What did you observe? What do the text colors red and blue indicate?
- The TCP stream shows the transaction between threat actor displayed in red text and the target in blue text.

The attacker issues the whoami command on the target. What does this show about the attacker role on
the target computer?
- The attacker has full root privileges on the target computer.

Scroll through the TCP stream. What kind of data has the threat actor been reading?
- user account information

## Part 3: Pivot to Kibana
a. Return to Sguil. Right-click either the source or destination IP for the alert ID 5.1 and select Kibana IP
Lookup > SrcIP. Enter username analyst and password cyberops if prompted by Kibana.


![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/1f66488c-1fb5-4031-b616-545bb64aa700)

b. If the time range is the last 24 hours, change it to June 2020 so June 11 is included in the time range.
Use the Absolute tab to change the time range

c. In the displayed results, there is a list of different data types. You were told that the file confidential.txt is no longer accessible. In the Sensors – Sensors and Services (Pie Chart), ftp and ftp-data are present in the list, as shown in the figure. We will determine if FTP was used to steal the file.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/e78b9ef7-89f3-481d-82da-b8b063db4469)

d. Let's filter for bro_ftp. Hover over the empty space next to the count of bro_ftp data types. Select + to
filter for only FTP related traffic as shown in the figure.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/19a5ca93-07a0-45b0-a82c-e726e3aad28c)

e. Scroll down to the All Logs section. There are two entries listed.

What are the source and destination IP addresses and port numbers for the FTP traffic?
- The source IP address and port number 192.168.0.11:52776. The destination IP address and port number is 209.165.200.235:21.

f. Expand and review both log entries. In one of these entries, the ftp_argument has an entry of
ftp://209.165.200.235/./confidential.txt. Also review the message in the log entry to learn more about this
event.

g. Within the same log entry, scroll up back to the alert _id field and click the link.

h. Review the transcript for the transactions between the attacker and the target. If desired, you can download the pcap and review the traffic using Wireshark.

What are the user credentials to access the FTP site?
- Username analyst and password cyberops

i. Now that you have verified that the attacker has used FTP to copy the content of the file confidential.txt
and then deleted it from the target. So what is the content of the file? Remember one of the services
listed in the pie chart is ftp_data.

j. Navigate to the top of the dashboard. Select Files under the Zeek Hunting heading in the left panel, as
shown in the figure. This will allow you to review the types of the files that were logged.


![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/4f061b5c-c89b-494f-8503-babf77e97a50)

What are the different types of files? Look at the MIME Type section of the screen.
- The file types are text and different types of image files in this example.

Scroll to the Files - Source heading. What are the file sources listed?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/bd0185d3-c247-4afa-882a-95405ef7a856)

k. Filter for FTP_DATA by hovering over the empty space next to the Count for FTP_DATA and click +.

l. Scroll down to review the filtered results.

What is the MIME type, source and destination IP address associated with the transfer of the FTP data?
- - HTTP and FTP
  - 
When did this transfer occur?
- The file is a plain text file that were transfer from 192.168.0.11 to 209.165.200.235. The file was transferred on June 11, 2020 at 3:53.


m. In the File logs, expand the entry associated with FTP data. Click the link associated with alert _id.
- CONFIDENTIAL DOCUMEN  DO NOT SHARE This document contains information about the last security breach.

What is the text content of the file that was transferred using FTP?
- The file is a plain text file that were transfer from 192.168.0.11 to 209.165.200.235. The file was transferred on June 11, 2020 at 3:53.

With all the information has gathered so far, what is your recommendation for stopping further
unauthorized access?
- At a minimum, the password for the username analyst should be changed throughout the network (209.165.200.235 and 192.168.0.11)
