
### Step 1: Open SciTE from the GUI
#### Part 1: Graphical Text Editors

a. Log on to the CyberOps VM as the user analyst using the password cyberops. The account analyst is
used as the example user account throughout this lab.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/6e44cd89-e743-40e7-88dc-01e8cb01cd1b)

b. On the top bar, navigate to Applications > CyberOPS > SciTE to launch the SciTE text editor.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/8cc6c75d-7955-440e-9eaa-5e82151e6094)


c. SciTE is simple but includes a few important features: tabbed environment, syntax highlighting and more.
Spend a few minutes with SciTE. In the main work area, type or copy and paste the text below:
“Space, is big. Really big. You just won't believe how vastly, hugely, mindbogglingly big it is. I mean, you
may think it's a long way down the road to the chemist, but that's just peanuts to space.”
― Douglas Adams, The Hitchhiker’s Guide to the Galaxy

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/bd7b5499-4d25-4292-ba35-b22215b481aa)

d. Click File > Save to save the file. Notice that SciTE attempts to save the file to the current user’s home
directory, which is analyst, by default. Name the file space.txt and click Save.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/ccd44344-0d77-4e8d-a7b7-34c1c05775b5)

e. Close SciTE by clicking the X icon on the upper right side of the window and then reopen SciTE.

f. Click File > Open... and search for the newly saved file, space.txt.

g. Even though SciTE is looking at the correct directory (/home/analyst), space.txt is not displayed. This is
because SciTE is looking for known extensions and .txt is not one of them. To display all files, click the
dropdown menu at the bottom of the Open File window and select All Files (*).

h. Select space.txt to open it.
Note: While the Linux file systems do not rely on extensions, some applications such as SciTE may
attempt to use them to identify file types.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/88d99077-ac05-47e9-84f8-ddceaec61a32)

i. Close space.txt when finished.

Question:
Could you immediately find space.txt?
- Yes when the 'all sources' was changed to 'all files' the txt file is opened.


### Step 2: Open SciTE from the Terminal.
a. Alternatively, you can also open SciTE from the command line. Click the terminal icon located in the
Dock at the bottom of the desktop. The terminal emulator opens.
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/145c63ad-cf29-499d-9ae9-028fec0991cf)


b. Type ls to see the contents of the current directory. Notice space.txt is listed. This means you do not
have to provide path information to open the file.
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/ed6dce76-1d25-4aaa-afb2-cff77bb5bf40)

c. Type scite space.txt to open SciTE. Note that this will not only launch SciTE in the GUI, but it will also
automatically load the space.txt text file that was previously created.

[analyst@secOps ~]$ scite space.txt

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/95bf6b44-64bb-45ba-b936-d7f77cad12d7)

d. Notice that while SciTE is open on the foreground, the terminal window used to launch it is still open in
the background. In addition, notice that the terminal window used to launch SciTE no longer displays the
prompt.
Question:
Why is the prompt not shown in the terminal?
- When the SciTE programs is launched, it runs in foreground and the terminal goes in backgorund. The terminal only shows the prompt when it is ready to accept any input, as it goes to backgorund it no longer receives any input.

e. Close this instance of SciTE by either clicking the X icon as before, or by switching the focus back to the
terminal window that launched SciTE and stopping the process. You can stop the process by pressing
CTRL+C.
Note: Starting SciTE from the command line is helpful when you want to run SciTE as root. Simply
precede scite with the sudo command, sudo scite.
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/927b9448-bd5a-46b3-93ed-174aecd22e2e)

f. Close SciTE and move on to the next section.

#### Part 2: Command Line Text Editors
a. In the terminal window, type nano space.txt to open the text file created in Part 1.
[analyst@secOps ~]$ nano space.txt
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/a727e936-b063-45fa-91b7-d10bd017f5df)

b. nano will launch and automatically load the space.txt text file. While the text may seem to be truncated
or incomplete, it is not. Because the text was created with no return characters and line wrapping is not
enabled, by default, nano is displaying one long line of text.
Use the Home and End keyboard keys to quickly navigate to the beginning and to the end of a line,
respectively.
What character does nano use to represent that a line continues beyond the boundaries of the screen?


c. As shown on the bottom shortcut lines, CTRL+X can be used to exit nano. nano will ask if you want to
save the file before exiting (‘Y’ for Yes, or N for ‘No’). If ‘Y’ is chosen, you will be prompted to press enter
to accept the given file name, or change the file name, or provide a file name if it is a new unnamed
document.

d. To control nano, you can use CTRL, ALT, ESCAPE or the META keys. The META key is the key on the
keyboard with a Windows or Mac logo, depending on your keyboard configuration.
Navigation in nano is very user friendly. Use the arrows to move around the files. Page Up and Page
Down can also be used to skip forward or backwards entire pages. Spend some time with nano and its
help screen. To enter the help screen, press CTRL+G. Press q to quit the help screen and return to
document editing in nano.
