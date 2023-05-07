### Part 1: Access PowerShell console.
a. Click Start. Search and select powershell.

b. Click Start. Search and select command prompt.
### Part 2: Explore Command Prompt and PowerShell commands.
a. Enter dir at the prompt in both windows.

Question:
What are the outputs to the dir command?
![image](https://user-images.githubusercontent.com/65653010/236669914-659d5b85-8b73-4db5-890f-aa40a24fa15e.png)

b. Try another command that you have used in the command prompt, such as ping, cd, and ipconfig.

Question:What are the results?

![image](https://user-images.githubusercontent.com/65653010/236670025-9bf75b92-5464-4970-aac4-42aaa1f9b1b6.png)

### Part 3: Explore cmdlets.
a. PowerShell commands, cmdlets, are constructed in the form of verb-noun string. To identify the
PowerShell command to list the subdirectories and files in a directory, enter Get-Alias dir at the
PowerShell prompt.

What is the PowerShell command for dir?

![image](https://user-images.githubusercontent.com/65653010/236670145-35bf88a5-093c-4456-8504-7774f7a2fd11.png)

In PowerShell, the command equivalent to the "dir" command in the command prompt is "Get-ChildItem". The "Get-ChildItem" command lists the files and folders in the specified directory or location.

b. For more detailed information about cmdlets, perform an internet search for Microsoft powershell
cmdlets.

c. Close the Command Prompt window when done.

### Part 4: Explore the netstat command using PowerShell.
a. At the PowerShell prompt, enter netstat -h to see the options available for the netstat command.

![image](https://user-images.githubusercontent.com/65653010/236670590-2e7d88cf-ff21-4cd5-9062-17c5b0c842ce.png)

b. To display the routing table with the active routes, enter netstat -r at the prompt.
![image](https://user-images.githubusercontent.com/65653010/236670639-02ff5dd5-9771-4c89-b372-9cdf29e5e9c5.png)

c. Open and run a second PowerShell with elevated privileges. Click Start. Search for PowerShell and right-
click Windows PowerShell and select Run as administrator. Click Yes to allow this app to make
changes to your device.

d. The netstat command can also display the processes associated with the active TCP connections. Enter
the netstat -abno at the prompt.

![image](https://user-images.githubusercontent.com/65653010/236671780-0e4d0b30-2cde-4369-b9a1-243f6fd3250c.png)

e. Open the Task Manager. Navigate to the Details tab. Click the PID heading so the PID are in order.

f. Select one of the PIDs from the results of netstat -abno. PID 756 is used in this example.

![image](https://user-images.githubusercontent.com/65653010/236672142-0bafe9d7-8cf0-4598-aca1-0588e169445f.png)

PID 4940(vmware-authd.exe)

g. Locate the selected PID in the Task Manager. Right-click the selected PID in the Task Manager to open
the Properties dialog box for more information.
![image](https://user-images.githubusercontent.com/65653010/236672203-13aaf7f3-aadb-46e0-bed4-1e877e5e2832.png)

### Part 5: Empty recycle bin using PowerShell.
PowerShell commands can simplify management of a large computer network. For example, if you wanted to
implement a new security solution on all servers in the network you could use a PowerShell command or
script to implement and verify that the services are running. You can also run PowerShell commands to
simplify actions that would take multiple steps to execute using Windows graphical desktop tools

a. Open the Recycle Bin. Verify that there are items that can be deleted permanently from your PC. If not,
restore those files.

b. If there are no files in the Recycle Bin, create a few files, such as text file using Notepad, and place them
into the Recycle Bin.

c. In a PowerShell console, enter clear-recyclebin at the prompt.

![image](https://user-images.githubusercontent.com/65653010/236672475-d90ef351-22e1-40d3-b170-3a3b714f6eb2.png)
![image](https://user-images.githubusercontent.com/65653010/236672503-976ee1e7-3b70-4622-9a71-84aa85739521.png)





