## Part 1: Open Wireshark and load the PCAP file.
a. Start the CyberOps Workstation VM.

b. Click Applications > CyberOPS > Wireshark on the desktop and browse to the Wireshark application.

c. In the Wireshark application, click Open in the middle of the application under Files.

d. Browse through the /home/analyst/ directory and search for lab.support.files. In the lab.support.files
directory and open the SQL_Lab.pcap file.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/ec9dac3d-33bd-47fd-acbd-46c0a4d28f2d)

e. The PCAP file opens within Wireshark and displays the captured network traffic. This capture file extends
over an 8-minute (441 second) period, the duration of this SQL injection attack.

What are the two IP addresses involved in this SQL injection attack based on the information displayed?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/7ea8b442-f495-4538-abf9-5bb632676afe)

## Part 2: View the SQL Injection Attack.
a. Within the Wireshark capture, right-click line 13 and select Follow > HTTP Stream. Line 13 was chosen
because it is a GET HTTP request. This will be very helpful in following the data stream as the application
layers sees it and leads up to the query testing for the SQL injection.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/9ce19e34-a488-4e5b-a660-79f037845702)

b. In the Find field, enter 1=1. Click Find Next.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/bef3dc1e-ec48-488a-8c56-f1b60cf7a2f2)

c. The attacker has entered a query (1=1) into a UserID search box on the target 10.0.2.15 to see if the
application is vulnerable to SQL injection. Instead of the application responding with a login failure
message, it responded with a record from a database. The attacker has verified they can input an SQL
command and the database will respond. The search string 1=1 creates an SQL statement that will be
always true. In the example, it does not matter what is entered into the field, it will always be true.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/a8847cd5-d5d6-40bd-87fc-81cdb8f4b504)

d. Close the Follow HTTP Stream window.

e. Click Clear display filter to display the entire Wireshark conversation.

## Part 3: The SQL Injection Attack continues...
a. Within the Wireshark capture, right-click line 19, and click Follow > HTTP Stream.

b. In the Find field, enter 1=1. Click Find Next.

c. The attacker has entered a query (1’ or 1=1 union select database(), user()#) into a UserID search box on
the target 10.0.2.15. Instead of the application responding with a login failure message, it responded with
the following information:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/6a50024a-91c3-49b7-af46-f1f65a8010a3)

d. Close the Follow HTTP Stream window.

e. Click Clear display filter to display the entire Wireshark conversation.

## Part 4: The SQL Injection Attack provides system information.
a. Within the Wireshark capture, right-click line 22 and select Follow > HTTP Stream. In red, the source
traffic is shown and is sending the GET request to host 10.0.2.15. In blue, the destination device is
responding back to the source.

b. In the Find field, enter 1=1. Click Find Next.

c. The attacker has entered a query (1’ or 1=1 union select null, version ()#) into a UserID search box on the
target 10.0.2.15 to locate the version identifier. Notice how the version identifier is at the end of the output
right before the </pre>.</div> closing HTML code.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/f045c602-9d89-42b4-9401-013595ca341f)

What is the version?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/dba52f59-239e-4a43-b7bb-0189bf69504d)

d. Close the Follow HTTP Stream window

e. Click Clear display filter to display the entire Wireshark conversation.

## Part 5: The SQL Injection Attack and Table Information
a. Within the Wireshark capture, right-click on line 25 and select Follow > HTTP Stream. The source is
shown in red. It has sent a GET request to host 10.0.2.15. In blue, the destination device is responding
back to the source.

b. In the Find field, enter users. Click Find Next.

c. The attacker has entered a query (1’or 1=1 union select null, table_name from
information_schema.tables#) into a UserID search box on the target 10.0.2.15 to view all the tables in the database. This provides a huge output of many tables, as the attacker specified “null” without any further specifications.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/85d564eb-d74b-44cc-a4b5-cb8c7296c85d)


What would the modified command of (1' OR 1=1 UNION SELECT null, column_name FROM
INFORMATION_SCHEMA.columns WHERE table_name='users') do for the attacker?
- It lists the name of all the users from the user table.

d. Close the Follow HTTP Stream window.
e. Click Clear display filter to display the entire Wireshark conversation

## Part 6: The SQL Injection Attack Concludes.
a. Within the Wireshark capture, right-click line 28 and select Follow > HTTP Stream. The source is shown
in red. It has sent a GET request to host 10.0.2.15. In blue, the destination device is responding back to
the source.

b. Click Find and type in 1=1. Search for this entry. When the text is located, click Cancel in the Find text
search box.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/cc56b1ba-1181-4d9f-95b1-db5df24ae2ce)

Which user has the password hash of 8d3533d75ae2c3966d7e0d4fcc69216b?
- 1337

Using a website such as https://crackstation.net/, copy the password hash into the password hash
cracker and get cracking.

What is the plain-text password?
- charley

d. Close the Follow HTTP Stream window. Close any open windows.

### Reflection Questions

1. What is the risk of having platforms use the SQL langauge?
- The primary risk of using SQL in software applications is SQL injection attacks, which can occur if user inputs are not properly validated and sanitized, potentially leading to unauthorized access or data manipulation. Additionally, SQL code can become complex and challenging to maintain, increasing the risk of errors and performance issues in the long term.

2. Browse the internet and perform a search on “prevent SQL injection attacks”. What are 2 methods or steps
that can be taken to prevent SQL injection attacks?
- **Parameterized Statements:** Use parameterized queries or prepared statements provided by your database or programming language.
- **Input Validation and Sanitization:** Implement strong input validation and sanitization practices. Validate and sanitize user inputs to ensure they conform to expected formats and do not contain malicious code. 
