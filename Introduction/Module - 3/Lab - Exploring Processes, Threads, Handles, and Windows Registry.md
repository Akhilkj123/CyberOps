### Explore an active process.
a. Navigate to the SysinternalsSuite folder with all the extracted files.

b. Open procexp.exe. Accept the Process Explorer License Agreement when prompted.

c. The Process Explorer displays a list of currently active processes.

d. To locate the web browser process, drag the Find Window's Process icon into the opened web browser
window. Microsoft Edge was used in this example.

![image](https://user-images.githubusercontent.com/65653010/236664653-0135a311-6a67-42fd-ae99-0cd49d0ba3f0.png)

e. The Microsoft Edge process can be terminated in the Process Explorer. Right-click the selected process
and select Kill Process. Click OK to continue

![image](https://user-images.githubusercontent.com/65653010/236664726-0a7789e3-059b-45f5-82ba-d2bcc32e7c11.png)

### Step 3: Start another process.
a. Open a Command Prompt. (Start > search Command Prompt > select Command Prompt)

b. Drag the Find Window's Process icon into the Command Prompt window and locate the highlighted
Command Prompt process in Process Explorer.

![image](https://user-images.githubusercontent.com/65653010/236665144-42ee9a95-63bc-41ba-a7eb-3f9279aa2c29.png)


c. The process for the Command Prompt is cmd.exe. Its parent process is explorer.exe process. The
cmd.exe has a child process, conhost.exe.

d. Navigate to the Command Prompt window. Start a ping at the prompt and observe the changes under the
cmd.exe process.

Question:
What happened during the ping process?

![image](https://user-images.githubusercontent.com/65653010/236665204-89b68128-5e48-44dc-b751-8ede0391f0d9.png)

e. As you review the list of active processes, you find that the child process conhost.exe may be suspicious.
To check for malicious content, right-click conhost.exe and select Check VirusTotal. When prompted,
click Yes to agree to VirusTotal Terms of Service. Then click OK for the next prompt.

f. Expand the Process Explorer window or scroll to the right until you see the VirusTotal column. Click the
link under the VirusTotal column. The default web browser opens with the results regarding the malicious
content of conhost.exe.
![image](https://user-images.githubusercontent.com/65653010/236665345-6884a74f-0f09-43d8-a958-a5a387945dd1.png)


g. Right-click the cmd.exe process and select Kill Process.Question:
What happened to the child process conhost.exe?

![image](https://user-images.githubusercontent.com/65653010/236665377-b97f0d78-cee4-464b-991f-a9fd9bec4e26.png)

conhost.exe all is being killed

### Part 2: Exploring Threads and Handles
In this part, you will explore threads and handles. Processes have one or more threads. A thread is a unit of
execution in a process. A handle is an abstract reference to memory blocks or objects managed by an
operating system. You will use Process Explorer (procexp.exe) in Windows SysInternals Suite to explore the
threads and handles.
Step 1: Explore threads.

a. Open a command prompt.

b. In Process Explorer window, right-click conhost.exe and Select Properties..... Click the Threads tab to
view the active threads for the conhost.exe process. Click OK to continue if prompted by a warning dialog
box.

c. Examine the details of the thread.
Question:
What type of information is available in the Properties window?

![image](https://user-images.githubusercontent.com/65653010/236666240-44c3bc40-fabc-40a2-ad27-ac82a949133b.png)

Start time,Kernel time,State

d) Click OK to continue.


