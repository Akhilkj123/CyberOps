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

Step 2: Explore handles.
a. In the Process Explorer, click View > select Lower Pane View > Handles to view the handles associated
with the conhost.exe process.
Question:
Examine the handles. What are the handles pointing to?
Type your answers here.

![image](https://user-images.githubusercontent.com/65653010/236666410-b10e8605-d15a-454d-9e98-44e8d238ccaa.png)

b. Close the Process Explorer when finished.

### Part 3: Exploring Windows Registry
The Windows Registry is a hierarchical database that stores most of the operating systems and desktop
environment configuration settings.

a. To access the Windows Registry, click Start > Search for regedit and select Registry Editor. Click Yes
when asked to allow this app to make changes.

The Registry Editor has five hives. These hives are at the top level of the registry.
- HKEY_CLASSES_ROOT is actually the Classes subkey of HKEY_LOCAL_MACHINE\Software\. It
stores information used by registered applications like file extension association, as well as a
programmatic identifier (ProgID), Class ID (CLSID), and Interface ID (IID) data.
- HKEY_CURRENT_USER contains the settings and configurations for the users who are currently
logged in.
- HKEY_LOCAL_MACHINE stores configuration information specific to the local computer.
- HKEY_USERS contains the settings and configurations for all the users on the local computer.
HKEY_CURRENT_USER is a subkey of HKEY_USERS.
- HKEY_CURRENT_CONFIG stores the hardware information that is used at bootup by the local
computer.

b. In a previous step, you had accepted the EULA for Process Explorer. Navigate to the EulaAccepted
registry key for Process Explorer.
Click to select Process Explorer in HKEY_CURRENT_USER > Software > Sysinternals > Process
Explorer. Scroll down to locate the key EulaAccepted. Currently, the value for the registry key
EulaAccepted is 0x00000001(1).


![image](https://user-images.githubusercontent.com/65653010/236666856-de967c2b-ba15-4fda-9cb5-b2c7bfb1ceb8.png)

c. Double-click EulaAccepted registry key. Currently the value data is set to 1. The value of 1 indicates that
the EULA has been accepted by the user.

d. Change the 1 to 0 for Value data. The value of 0 indicates that the EULA was not accepted. Click OK to
continue.

Question:
What is value for this registry key in the Data column?

![image](https://user-images.githubusercontent.com/65653010/236666954-6e123430-4f45-4dee-a0c8-397649c4d96b.png)

e. Open the Process Explorer. Navigate to the folder where you have downloaded SysInternals. Open the
folder SysInternalsSuite > Open procexp.exe.

Question:When you open the Process Explorer, what did you see?



