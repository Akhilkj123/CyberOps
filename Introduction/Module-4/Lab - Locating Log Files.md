### Part 1: Log File Overview
#### Step 1: Web server log file example
a. Use the cat command below to list a web server sample log file. The sample file is located at /var/log:

[analyst@secOps ~]$ cat /var/log/logstash-tutorial.log

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/93f10422-4ace-4892-b410-645fccbd5a7e)

 Explain why the output of the cat command is in a different format than the single entry shown in item.
 - The 'cat' command if being given to a file it lists the contents of a file and if being given to a directory it lists the number of files present in the directory.

#### Step 2: Operating system log file example
a. [analyst@secOps ~]$ sudo more /var/log/messages

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/06b73327-49da-4ad9-ae8b-9a89147bb1ad)

Notice that the events listed above are very different from the web server events. Because the operating
system itself is generating this log, all recorded events are in relation to the OS itself.

b. If necessary, enter Ctrl + C to exit out of the previous command.

c. Log files are very important for troubleshooting. Assume that a user of that specific system reported that
all network operations were slow around 4:20 am on May 19.

Question:
Can you find evidence of that in the log entries shown above? If so, in what lines? Explain.

- To easily find the specific time mentioned, the below listed command can be given:

cat /etc/log/messages | grep "May 19 04:2"
- This command can help in finding the information of the specific time.

### Part 2: Locating Log Files in Unknown Systems
a. When working with new software, the first step is to look at the documentation. It provides important
information about the software, including information about its log files. Use the man command to display
the nginx manual page:

[analyst@secOps ~]$ man nginx

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/796d91db-4da9-4aa4-96b1-0dd04f6eb28f)

b. Scroll down the page to locate the nginx logging section. The documentation makes it clear that nginx
supports logging, with the location of its log files defined at compilation time.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/b6f0578f-a44d-483e-a82b-f68e0232ba70)

c. The manual page also contains information on the files used by nginx. Scroll down further to display the
nginx operating files under the Files section:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/1fd97d0d-b499-43a5-b802-632a121468f9)


