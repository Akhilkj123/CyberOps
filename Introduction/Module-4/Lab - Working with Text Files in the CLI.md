
### Step 1: Open SciTE from the GUI

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
