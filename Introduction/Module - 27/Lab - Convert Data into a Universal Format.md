## Part 1: Normalize Timestamps in a Log File
a. Launch the CyberOps Workstation VM and then launch a terminal window.

b. Use the cd command to change to the /home/analyst/lab.support.files/ directory. A copy of the file
shown above is stored there.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/dfc8eeeb-080a-4c38-9850-1df721af462d)

c. Issue the following AWK command to convert and print the result on the terminal:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/fb1bbe1d-1d3b-42be-8026-9c64379408e6)

Were the Unix Epoch timestamps converted to Human Readable format? Were the other fields modified?
Explain.
- Yes it is in human readable format. Other fields, such as codes and numeric values, remain largely unchanged. The double line is a seperator where the last line is not in the records.

 d. Use nano (or your favorite text editor) to remove the extra empty line at the end of the file and run the
AWK script again by using the up-arrow to find it in the command history buffer.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/f238f0d9-ef8a-45af-ae1a-5d1450b13372)

Is the output correct now? Explain.

e. While printing the result on the screen is useful for troubleshooting the script, analysts will likely need to
save the output in a text file. Redirect the output of the script above to a file named
applicationX_in_human.log to save it to a file:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/97d419b2-89f0-4c93-bd1f-3e47859cc6bd)

What was printed by the command above? Is this expected?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/2f75f463-5daf-45bb-a05a-507e8b3ceb9c)

f. Use cat to view the applicationX_in_human.log. Notice that the extra line is now removed and the
timestamps for the log entries have been converted to human readable format.
