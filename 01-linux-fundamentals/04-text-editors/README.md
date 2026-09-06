Lab 04 — Using Text Editors

Learn how to create, open, edit, save, and manage text files using terminal-based text editors in Linux.

🎯 Objective

By completing this lab, you will learn how to:

Understand the role of text editors in Linux
Open and create files using nano
Edit files using nano
Save and exit nano
Understand the basic interface of nano
Open and edit files using vi
Understand Normal Mode and Insert Mode
Enter Insert Mode in vi
Return to Normal Mode
Save and exit files using vi
Understand common vi commands
Compare nano and vi
Understand why terminal text editors are important for Linux administration
📚 Prerequisites

Before starting this lab, you should have:

Access to a Linux system
A working terminal
Basic knowledge of Linux commands
Completion of Lab 01 — Navigating the Linux Filesystem
Completion of Lab 02 — Working with Directories
Completion of Lab 03 — Managing Files

Check whether nano and vi are installed:

command -v nano
command -v vi

If installed, these commands should return paths such as:

/usr/bin/nano
/usr/bin/vi
1. Introduction to Linux Text Editors

A text editor is a program used to create and modify plain-text files.

Linux relies heavily on text files for system administration.

Examples include:

Configuration files
Shell scripts
Service configuration
Network configuration
Security configuration
User configuration
Application settings
Documentation

Many Linux servers do not have a graphical desktop environment.

Instead, administrators connect through tools such as SSH and perform their work entirely from the command line.

For this reason, knowing how to use terminal-based text editors is an important Linux administration skill.

Two editors you will learn in this lab are:

Editor	Description
nano	Simple and beginner-friendly terminal editor
vi	Powerful modal editor commonly available on Linux and Unix systems
2. Create a Lab Workspace

Create a dedicated directory for this lab:

mkdir -p ~/linux-lab-04

Move into the directory:

cd ~/linux-lab-04

Verify your location:

pwd

You should see a path similar to:

/home/your-user/linux-lab-04

List the directory:

ls -la

At this point, the directory should be empty or contain only files from previous practice.

3. Understanding nano

nano is a simple terminal-based text editor.

It is particularly useful for beginners because its most common keyboard shortcuts are displayed at the bottom of the screen.

Unlike vi, Nano does not use separate Normal and Insert modes for ordinary text entry.

You can open a file and immediately begin typing.

4. Creating a File for nano

Create a basic text file using echo:

echo "Hello, World!" > example.txt

Verify the file:

cat example.txt

Expected output:

Hello, World!

Check the file:

ls -l example.txt
5. Opening a File with nano

Open the file:

nano example.txt

The file will open inside the Nano editor.

You can now edit the contents directly.

Add the following lines:

Hello, World!
This is a Linux text editor lab.
I am learning how to edit files using nano.
6. Saving a File in nano

To save the file, press:

Ctrl + O

Nano will display a prompt asking for the filename.

Press:

Enter

to confirm the filename.

The file is now saved.

7. Exiting nano

To exit Nano:

Ctrl + X

You should return to the terminal.

Verify the contents:

cat example.txt
8. Important nano Shortcuts
Shortcut	Function
Ctrl + O	Save/write the file
Ctrl + X	Exit Nano
Ctrl + W	Search for text
Ctrl + K	Cut the current line
Ctrl + U	Paste previously cut text
Ctrl + G	Display help
Understanding the ^ Symbol

Nano often displays shortcuts like:

^O Write Out
^X Exit

The ^ symbol represents the Ctrl key.

Therefore:

^O

means:

Ctrl + O

and:

^X

means:

Ctrl + X
9. Practical nano Exercise

Create another file:

echo "Linux Administration" > nano-practice.txt

Open it:

nano nano-practice.txt

Add the following content:

Linux text editors are important for system administration.
Nano provides a simple interface for editing text files.
Terminal editors are useful when working with remote servers.
Linux administrators frequently work with configuration files.

Save the file:

Ctrl + O

Press:

Enter

Exit Nano:

Ctrl + X

Verify the file:

cat nano-practice.txt
10. Understanding vi

vi is a powerful text editor that is commonly available on Linux and Unix systems.

Unlike Nano, vi uses a modal editing system.

This means that the same keyboard keys can perform different actions depending on the current mode.

This is one of the most important concepts to understand when learning vi.

11. Opening a File with vi

Open the example file:

vi example.txt

The file will open inside vi.

At first, you will be in Normal Mode.

12. Understanding vi Modes

The three important concepts for beginners are:

Normal Mode

Normal Mode is used for:

Navigation
Commands
Deleting text
Copying text
Moving around the file
Insert Mode

Insert Mode is used for:

Entering text
Adding text
Editing text
Command-Line Mode

Command-Line Mode is accessed using : from Normal Mode.

It is used for commands such as:

Saving
Quitting
Searching
Other editor operations

A simplified workflow is:

Normal Mode
     |
     | i
     v
Insert Mode
     |
     | Esc
     v
Normal Mode
     |
     | :
     v
Command-Line Mode
13. Entering Insert Mode

With example.txt open in vi, press:

i

You are now in Insert Mode.

Add the following lines:

Editing files with vi is different from nano.
vi uses different modes for editing and commands.
Learning vi is useful for Linux administration.

You can now type normally.

14. Returning to Normal Mode

After finishing your changes, press:

Esc

You are now back in Normal Mode.

Remember:

i

means:

Enter Insert Mode.

And:

Esc

means:

Return to Normal Mode.

If you are ever unsure which mode you are in, pressing Esc is a useful way to return to Normal Mode.

15. Saving and Exiting vi

From Normal Mode, type:

:wq

Then press:

Enter

The command consists of:

w = write/save
q = quit

Therefore:

:wq

means:

Save the file and exit vi.

Verify your changes:

cat example.txt
16. Important vi Commands
Command	Function
i	Enter Insert Mode
Esc	Return to Normal Mode
:w	Save the file
:q	Quit
:wq	Save and quit
:q!	Quit without saving
dd	Delete the current line
yy	Copy the current line
p	Paste
/text	Search for text
17. Practical vi Exercise

Create a practice file:

echo "Linux Security" > vi-practice.txt

Open it:

vi vi-practice.txt

Press:

i

Add:

Linux security requires strong system administration skills.
Text editors are commonly used to manage configuration files.
vi provides powerful keyboard-based editing capabilities.
Linux administrators should understand terminal-based editors.

Press:

Esc

Save and exit:

:wq

Press:

Enter

Verify the file:

cat vi-practice.txt
18. Understanding :q!

Another important vi command is:

:q!

This means:

Quit without saving changes.

For example:

Esc
:q!
Enter

This will exit the editor and discard any unsaved changes.

⚠️ Warning: Use :q! only when you intentionally want to discard your changes.

19. Testing :q!

Create a test file:

echo "Original text" > discard-test.txt

Open it:

vi discard-test.txt

Press:

i

Change the text.

For example, add:

This change should not be saved.

Press:

Esc

Then use:

:q!

Press:

Enter

Check the file:

cat discard-test.txt

The unsaved changes should not be present.

20. nano vs vi
Feature	nano	vi
Beginner friendly	Very	Requires practice
Modal editing	No	Yes
Basic editing	Easy	More complex
Keyboard commands	Simple	Extensive
Linux server usage	Common	Very common
Learning curve	Low	Higher
Advanced editing	Limited	Powerful

Neither editor is universally better.

Nano is usually easier for beginners and quick edits.

vi has a steeper learning curve but provides a powerful keyboard-driven editing workflow.

21. Real-World Linux Administration Scenario

Imagine you connect to a remote Linux server using SSH.

The server has no graphical desktop environment.

You need to modify a configuration file.

A typical workflow could look like this:

SSH
 |
 v
Linux Terminal
 |
 v
Text Editor
 |
 v
Configuration File
 |
 v
Save Changes
 |
 v
Test Configuration
 |
 v
Restart/Reload Service

Terminal text editors are therefore important for:

Linux administration
Cybersecurity
DevOps
Cloud engineering
Server management
System administration
22. Configuration Files and Text Editors

Linux stores many system settings in text-based configuration files.

Examples include configuration related to:

Users
Networking
Services
SSH
Logging
Security
Applications
System startup

Administrators may need to inspect or modify these files.

However, configuration files should not be changed randomly.

Always understand what a file does before modifying it.

23. Security Perspective

Text editors are not security tools themselves, but they are frequently used when managing security-related configuration.

Examples include:

SSH configuration
Firewall configuration
User configuration
Service configuration
Logging configuration
Network configuration
Access-control settings
System-hardening configuration

Before modifying an important configuration file:

Understand what the file controls.
Make a backup when appropriate.
Modify only what is necessary.
Check the configuration syntax when applicable.
Test the changes.
Keep track of what was changed.

For example:

cp configuration.conf configuration.conf.backup

This creates a backup before modification.

Important: Only modify system configuration files when you have the appropriate permissions and understand the possible consequences.

24. Common Mistakes
Mistake 1 — Trying to type in vi while in Normal Mode

If you cannot enter text normally, you may still be in Normal Mode.

Press:

i

to enter Insert Mode.

Mistake 2 — Forgetting Esc

Before entering commands such as:

:wq

press:

Esc

to return to Normal Mode.

Mistake 3 — Forgetting to press Enter

After entering:

:wq

you must press:

Enter

to execute the command.

Mistake 4 — Accidentally discarding changes

The command:

:q!

exits without saving changes.

Use it carefully.

Mistake 5 — Editing important system files without understanding them

Do not experiment randomly with critical Linux configuration files.

Use your practice directory:

~/linux-lab-04

for learning and experimentation.

25. Verification

List the files created during this lab:

ls -lh ~/linux-lab-04

You should have files similar to:

example.txt
nano-practice.txt
vi-practice.txt
discard-test.txt

Display the contents:

cat ~/linux-lab-04/example.txt
cat ~/linux-lab-04/nano-practice.txt
cat ~/linux-lab-04/vi-practice.txt
cat ~/linux-lab-04/discard-test.txt

Check the number of lines:

wc -l ~/linux-lab-04/example.txt
wc -l ~/linux-lab-04/nano-practice.txt
wc -l ~/linux-lab-04/vi-practice.txt
wc -l ~/linux-lab-04/discard-test.txt
26. Useful File Inspection Commands

After editing files, you can use several commands to inspect them.

Display the complete file:

cat example.txt

Display the file with line numbers:

cat -n example.txt

Display the first lines:

head example.txt

Display the last lines:

tail example.txt

Count lines, words, and characters:

wc example.txt

These commands will become increasingly useful in later labs.

27. Practical Challenge

Create a file called:

linux-editor-challenge.txt

Start by creating it:

echo "Linux Editor Challenge" > linux-editor-challenge.txt

Open it using Nano:

nano linux-editor-challenge.txt

Add information about:

Your Linux learning goals
Why Linux administrators need text editors
One advantage of Nano
One advantage of vi

Save and exit Nano.

Then reopen the same file using:

vi linux-editor-challenge.txt

Enter Insert Mode:

i

Add one more line.

Press:

Esc

Save and exit:

:wq

Press:

Enter

Finally verify the file:

cat linux-editor-challenge.txt
28. Knowledge Check

Answer the following questions after completing the lab.

Q1. What is the purpose of a text editor in Linux?
Q2. Why is Nano considered beginner-friendly?
Q3. What does the i command do in vi?
Q4. How do you return from Insert Mode to Normal Mode?
Q5. What does :w do?
Q6. What does :wq do?
Q7. What does :q! do?
Q8. What is the main difference between Nano and vi?
Q9. Why are terminal-based text editors important on Linux servers?
Q10. Why should you avoid experimenting directly with important system configuration files?
29. Key Concepts
Text Editor

A program used to create and modify plain-text files.

Nano

A simple terminal-based editor suitable for beginners and quick edits.

vi

A powerful modal text editor commonly available on Linux and Unix systems.

Normal Mode

The default vi mode used for navigation and commands.

Insert Mode

The vi mode used for entering and editing text.

Command-Line Mode

The vi mode used to execute commands such as saving and quitting.

:wq

Save and quit.

:q!

Quit without saving.

🔎 Command Reference
Command / Shortcut	Purpose
nano file.txt	Open a file with Nano
Ctrl + O	Save in Nano
Ctrl + X	Exit Nano
Ctrl + W	Search in Nano
Ctrl + K	Cut a line in Nano
Ctrl + U	Paste in Nano
vi file.txt	Open a file with vi
i	Enter Insert Mode
Esc	Return to Normal Mode
:w	Save
:q	Quit
:wq	Save and quit
:q!	Quit without saving
dd	Delete current line
yy	Copy current line
p	Paste
/text	Search for text
🛡️ Best Practices

When working with text editors on Linux:

1. Practice in a dedicated directory

Use:

~/linux-lab-04

for experimentation.

2. Understand the file before editing it

Do not modify configuration files blindly.

3. Back up important configuration files

When appropriate:

cp file.conf file.conf.backup
4. Verify your changes

After editing:

cat file.txt

or use other appropriate inspection commands.

5. Be careful with destructive operations

Commands such as:

:q!

can discard changes.

Understand a command before executing it.

✅ Lab Completion Checklist
 I understand what Linux text editors are used for.
 I can open a file using nano.
 I can edit a file using nano.
 I can save a file using Ctrl + O.
 I can exit nano using Ctrl + X.
 I understand the basic modes of vi.
 I can enter Insert Mode using i.
 I can return to Normal Mode using Esc.
 I can save using :w.
 I can save and exit using :wq.
 I understand what :q! does.
 I can perform basic editing with vi.
 I completed the Nano exercise.
 I completed the vi exercise.
 I completed the practical challenge.
 I verified my files.
 I understand why terminal text editors are important for Linux administration.
🧠 Final Takeaways

The most important commands from this lab are:

nano file.txt
Ctrl + O
Ctrl + X
vi file.txt
i
Esc
:w
:wq
:q!

Remember the basic vi workflow:

Open file
   ↓
Normal Mode
   ↓
i
   ↓
Insert Mode
   ↓
Edit text
   ↓
Esc
   ↓
Normal Mode
   ↓
:wq
   ↓
Enter
   ↓
Exit
Conclusion

In this lab, you learned how to work with two important Linux text editors: nano and vi.

You learned how to:

Create text files
Open files
Edit files
Save files
Exit text editors
Use Nano shortcuts
Understand vi modes
Enter Insert Mode
Return to Normal Mode
Save and exit using :wq
Exit without saving using :q!
Verify edited files
Apply safe text-editing practices

Text-editor skills are a fundamental part of Linux administration and will become increasingly important as you work with shell scripting, system configuration, networking, automation, and cybersecurity.
