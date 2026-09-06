# Lab 04 — Text Editors

> Learn how to create, edit, save, and manage text files from the Linux command line using terminal-based text editors.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand text editors in Linux
- Understand the difference between graphical and terminal editors
- Use `nano` to edit text files
- Create and modify configuration-style files
- Save and exit a text editor
- Search within a text file
- Understand basic text-editing shortcuts
- Verify changes made to files
- Understand why text editors are important for Linux administration

---

## 📚 Prerequisites

Before starting this lab, you should have:

- A working Linux system
- Access to a terminal
- Basic Linux command-line knowledge
- Completion of:
  - **Lab 01 — Navigating the Linux Filesystem**
  - **Lab 02 — Working with Directories**
  - **Lab 03 — Managing Files**

> ⚠️ **Important:** Perform all exercises inside the dedicated lab directory. Do not edit important system configuration files until you understand the consequences of the changes.

---

# 1. Introduction to Text Editors

A text editor is a program used to create and modify text files.

Linux administrators frequently work with text files such as:

- Configuration files
- Shell scripts
- Log files
- Documentation
- Application settings
- Automation files

Many Linux systems provide both graphical and terminal-based text editors.

Common Linux text editors include:

```text
nano
vim
vi
emacs
```

In this lab, you will primarily work with **nano** because it is beginner-friendly and available on many Linux distributions.

---

# 2. Create a Lab Workspace

Create a dedicated directory:

```bash
mkdir -p ~/linux-lab-04
```

Move into it:

```bash
cd ~/linux-lab-04
```

Verify your location:

```bash
pwd
```

You should see something similar to:

```text
/home/your-user/linux-lab-04
```

List the directory:

```bash
ls -la
```

---

# 3. Check Whether nano Is Installed

Run:

```bash
nano --version
```

If `nano` is installed, you should see version information.

You can also check its location:

```bash
which nano
```

Example:

```text
/usr/bin/nano
```

> **Note:** The exact version and path may differ between Linux distributions.

---

# 4. Opening a File with nano

Create and open a file using:

```bash
nano notes.txt
```

If the file does not exist, `nano` will create it when you save it.

You should now see the nano editor.

At the bottom of the screen, nano displays keyboard shortcuts.

For example:

```text
^X
```

means:

```text
Ctrl + X
```

The `^` symbol represents the **Ctrl** key.

---

# 5. Entering Text

Inside nano, type:

```text
Linux administration is an important cybersecurity skill.
```

Add another line:

```text
This lab focuses on working with text editors.
```

Your file should contain something similar to:

```text
Linux administration is an important cybersecurity skill.
This lab focuses on working with text editors.
```

---

# 6. Saving a File in nano

To save the file, press:

```text
Ctrl + O
```

Nano will ask for the filename.

You should see something similar to:

```text
File Name to Write: notes.txt
```

Press:

```text
Enter
```

The file will be saved.

---

# 7. Exiting nano

To exit nano, press:

```text
Ctrl + X
```

You should return to the terminal.

Verify that the file exists:

```bash
ls -l
```

You should see:

```text
notes.txt
```

---

# 8. Viewing the File

Use:

```bash
cat notes.txt
```

Expected output:

```text
Linux administration is an important cybersecurity skill.
This lab focuses on working with text editors.
```

This confirms that the text was successfully saved.

---

# 9. Editing an Existing File

Open the file again:

```bash
nano notes.txt
```

Add another line:

```text
Linux text editors are useful for configuration management.
```

Save the file:

```text
Ctrl + O
```

Press:

```text
Enter
```

Exit:

```text
Ctrl + X
```

Verify:

```bash
cat notes.txt
```

---

# 10. Understanding the nano Interface

Nano provides a simple terminal-based interface.

The bottom section displays commonly used shortcuts.

Examples:

| Shortcut | Function |
|---|---|
| `Ctrl + O` | Write/save file |
| `Ctrl + X` | Exit nano |
| `Ctrl + W` | Search |
| `Ctrl + K` | Cut current line |
| `Ctrl + U` | Paste previously cut text |
| `Ctrl + G` | Display help |
| `Ctrl + C` | Display cursor position |

The exact interface may vary slightly depending on your nano version.

---

# 11. Moving Around the File

You can use the keyboard arrow keys to move around the file.

Common navigation keys include:

```text
↑
↓
←
→
```

You can also use:

```text
Home
End
Page Up
Page Down
```

These allow you to move around larger files more efficiently.

---

# 12. Searching Inside a File

Open the file:

```bash
nano notes.txt
```

Press:

```text
Ctrl + W
```

Nano will display a search prompt.

Enter:

```text
cybersecurity
```

Then press:

```text
Enter
```

Nano will search for the term.

This becomes especially useful when working with large configuration files.

---

# 13. Creating a Configuration-Style File

Create a practice configuration file:

```bash
nano server.conf
```

Enter:

```text
SERVER_NAME=linux-lab
ENVIRONMENT=development
LOG_LEVEL=info
SERVICE_STATUS=enabled
```

Save:

```text
Ctrl + O
```

Press:

```text
Enter
```

Exit:

```text
Ctrl + X
```

Verify:

```bash
cat server.conf
```

Expected:

```text
SERVER_NAME=linux-lab
ENVIRONMENT=development
LOG_LEVEL=info
SERVICE_STATUS=enabled
```

---

# 14. Understanding Configuration Files

Linux administrators frequently modify configuration files.

Examples include files associated with:

```text
/etc
```

Many Linux services rely on configuration files to determine how they should operate.

Examples of configuration tasks include:

- Setting service options
- Configuring network services
- Defining application behavior
- Configuring logging
- Managing authentication settings

> ⚠️ **Security note:** System configuration files can affect the operation and security of the entire machine. Always make backups and understand a change before applying it to a production system.

---

# 15. Editing Configuration-Style Data

Open the practice file:

```bash
nano server.conf
```

Change:

```text
LOG_LEVEL=info
```

to:

```text
LOG_LEVEL=debug
```

Save:

```text
Ctrl + O
```

Press:

```text
Enter
```

Exit:

```text
Ctrl + X
```

Verify:

```bash
cat server.conf
```

---

# 16. Creating a Security Notes File

Create:

```bash
nano security-notes.txt
```

Enter:

```text
Linux Security Notes

1. Keep systems updated.
2. Use strong access controls.
3. Review system logs.
4. Apply least privilege.
5. Protect sensitive configuration files.
```

Save:

```text
Ctrl + O
```

Press:

```text
Enter
```

Exit:

```text
Ctrl + X
```

Verify:

```bash
cat security-notes.txt
```

---

# 17. Appending Information Without Opening nano

Sometimes you do not need a text editor.

For example:

```bash
echo "Review file permissions regularly." >> security-notes.txt
```

Display the file:

```bash
cat security-notes.txt
```

This demonstrates an important Linux principle:

> Choose the simplest tool appropriate for the task.

For one-line additions, `echo` and redirection may be faster than opening an editor.

---

# 18. Understanding File Redirection

The following command:

```bash
echo "New line" > file.txt
```

creates or **overwrites** the file.

The following command:

```bash
echo "New line" >> file.txt
```

adds content to the end of the file.

The difference is important:

```text
>   = overwrite
>>  = append
```

For example:

```bash
echo "First line" > example.txt
```

Then:

```bash
echo "Second line" >> example.txt
```

View the result:

```bash
cat example.txt
```

Expected:

```text
First line
Second line
```

---

# 19. Comparing nano and Command-Line Redirection

There are multiple ways to create and modify text files.

### Using nano

```bash
nano file.txt
```

Useful when:

- Editing multiple lines
- Manually changing configuration
- Working interactively

### Using echo

```bash
echo "text" > file.txt
```

Useful when:

- Creating a simple file
- Adding a single line
- Automating file creation

### Using cat with a here-document

For larger blocks of text:

```bash
cat > example.txt <<'EOF'
Line one
Line two
Line three
EOF
```

This is particularly useful when creating files through scripts or automated lab setup.

---

# 20. Creating a Multi-Line File Automatically

Create a practice file without opening an editor:

```bash
cat > automation-notes.txt <<'EOF'
Linux Automation Notes

Automation can reduce repetitive administrative work.

Common automation tools include:
- Shell scripts
- Ansible
- Python
- Cron
EOF
```

View the file:

```bash
cat automation-notes.txt
```

This technique will become useful when working with automation labs later in the course.

---

# 21. Viewing Line Numbers

Use:

```bash
nl notes.txt
```

Example:

```text
     1  Linux administration is an important cybersecurity skill.
     2  This lab focuses on working with text editors.
     3  Linux text editors are useful for configuration management.
```

Line numbers are useful when troubleshooting configuration files and scripts.

---

# 22. Counting File Content

Use:

```bash
wc notes.txt
```

This displays:

- Number of lines
- Number of words
- Number of bytes

For example:

```text
3 17 143 notes.txt
```

You can also request specific information.

Count lines:

```bash
wc -l notes.txt
```

Count words:

```bash
wc -w notes.txt
```

Count bytes:

```bash
wc -c notes.txt
```

---

# 23. Searching Files from the Terminal

You can search for text without opening an editor.

For example:

```bash
grep "Linux" notes.txt
```

This displays lines containing:

```text
Linux
```

You can search for a configuration setting:

```bash
grep "LOG_LEVEL" server.conf
```

Expected:

```text
LOG_LEVEL=debug
```

This is extremely useful when working with configuration files.

---

# 24. Practical Challenge

Create a file called:

```text
admin-notes.txt
```

Use nano:

```bash
nano admin-notes.txt
```

Enter the following information:

```text
Linux Administration Practice

Filesystem:
Users:
Permissions:
Networking:
Processes:
Logs:
Security:
```

Save and exit.

Verify:

```bash
cat admin-notes.txt
```

---

# 25. Practical Challenge — Modify the File

Open:

```bash
nano admin-notes.txt
```

Add information after each category.

For example:

```text
Filesystem: Understand directories and storage.
Users: Manage accounts and groups.
Permissions: Control access to files.
Networking: Understand IP addresses and ports.
Processes: Monitor running programs.
Logs: Investigate system activity.
Security: Apply least privilege.
```

Save and exit.

Verify:

```bash
cat admin-notes.txt
```

---

# 26. Practical Challenge — Search the File

Search for:

```bash
grep "Security" admin-notes.txt
```

Then search for:

```bash
grep "Networking" admin-notes.txt
```

Then display line numbers:

```bash
grep -n "Security" admin-notes.txt
```

The `-n` option displays the matching line number.

---

# 27. Practical Challenge — Create a Configuration File

Create:

```bash
nano application.conf
```

Enter:

```text
APP_NAME=SecurityLab
APP_ENV=development
LOG_LEVEL=info
PORT=8080
DEBUG=false
```

Save and exit.

Verify:

```bash
cat application.conf
```

Search for the logging configuration:

```bash
grep "LOG_LEVEL" application.conf
```

Search for the port:

```bash
grep "PORT" application.conf
```

---

# 28. Security Perspective

Text editors are an important part of cybersecurity and Linux administration.

Security professionals frequently inspect and modify:

- Configuration files
- Firewall settings
- Service configurations
- Authentication settings
- Scripts
- Log-processing configurations
- Monitoring configurations

However, configuration changes should always be performed carefully.

Before changing an important file:

1. Know what the file does.
2. Make a backup when appropriate.
3. Change only what is necessary.
4. Verify the result.
5. Test the affected service.

---

# 29. Backing Up a Configuration File

Before modifying an important configuration file, a simple backup can be created with:

```bash
cp application.conf application.conf.bak
```

Verify:

```bash
ls -l application.conf*
```

You should see:

```text
application.conf
application.conf.bak
```

This provides a basic recovery copy.

---

# 30. Restoring a Backup

If necessary, the backup can be restored:

```bash
cp application.conf.bak application.conf
```

Verify:

```bash
cat application.conf
```

> **Note:** Always verify that the backup is actually the version you intend to restore before overwriting a configuration file.

---

# 31. Common Mistakes

## Mistake 1 — Forgetting to Save

If you edit a file in nano and exit without saving, your changes may not be written.

Use:

```text
Ctrl + O
```

before exiting.

---

## Mistake 2 — Accidentally Overwriting a File

This command:

```bash
echo "text" > file.txt
```

overwrites the existing contents.

Use:

```bash
echo "text" >> file.txt
```

when you intend to append.

---

## Mistake 3 — Editing the Wrong File

Always verify your current directory:

```bash
pwd
```

and inspect the file:

```bash
ls -l filename
```

before making important changes.

---

## Mistake 4 — Modifying System Configuration Without Understanding It

Avoid experimenting directly with files under:

```text
/etc
```

until you understand their purpose.

Use the lab directory for practice.

---

# 32. Useful Text-Editing Commands

Open a file with nano:

```bash
nano filename
```

Display a file:

```bash
cat filename
```

Display line numbers:

```bash
nl filename
```

Search for text:

```bash
grep "text" filename
```

Count lines:

```bash
wc -l filename
```

Count words:

```bash
wc -w filename
```

Create or overwrite a file:

```bash
echo "text" > filename
```

Append to a file:

```bash
echo "text" >> filename
```

Create a multi-line file:

```bash
cat > filename <<'EOF'
Line one
Line two
Line three
EOF
```

Create a backup:

```bash
cp filename filename.bak
```

---

# 33. Verification

Move into your lab directory:

```bash
cd ~/linux-lab-04
```

List all files:

```bash
ls -lah
```

Display the main practice files:

```bash
cat notes.txt
cat server.conf
cat security-notes.txt
cat automation-notes.txt
cat admin-notes.txt
cat application.conf
```

Check line numbers:

```bash
nl notes.txt
```

Search for configuration values:

```bash
grep "LOG_LEVEL" server.conf
```

Check file statistics:

```bash
wc notes.txt
```

---

# 34. Knowledge Check

### Q1. What is a text editor?

### Q2. Why are text editors important in Linux administration?

### Q3. What does `nano filename` do?

### Q4. What keyboard shortcut saves a file in nano?

### Q5. What keyboard shortcut exits nano?

### Q6. What does `Ctrl + W` do in nano?

### Q7. What is the difference between `>` and `>>`?

### Q8. What does `grep` do?

### Q9. What does `nl` do?

### Q10. What does `wc -l` display?

### Q11. Why should important configuration files be backed up before modification?

### Q12. Why should you avoid modifying system configuration files without understanding their purpose?

---

# 35. Key Concepts

### Text Editor

A program used to create and modify text files.

### nano

A beginner-friendly terminal-based text editor.

### Configuration File

A file containing settings used by a system, service, or application.

### Redirection

A shell mechanism used to send command output to files.

```text
>   = overwrite
>>  = append
```

### grep

A command used to search for matching text.

### Backup

A copy of a file that can be used for recovery.

---

# 36. Command Reference

| Command | Purpose |
|---|---|
| `nano file` | Open a file in nano |
| `cat file` | Display file contents |
| `nl file` | Display file with line numbers |
| `grep "text" file` | Search for text |
| `grep -n "text" file` | Search and display line numbers |
| `wc file` | Display lines, words, and bytes |
| `wc -l file` | Count lines |
| `wc -w file` | Count words |
| `echo "text" > file` | Create/overwrite a file |
| `echo "text" >> file` | Append to a file |
| `cp file file.bak` | Create a backup |
| `cat > file <<'EOF'` | Create a multi-line file |

---

# 37. Important nano Shortcuts

| Shortcut | Function |
|---|---|
| `Ctrl + O` | Save/write file |
| `Ctrl + X` | Exit |
| `Ctrl + W` | Search |
| `Ctrl + K` | Cut line |
| `Ctrl + U` | Paste cut text |
| `Ctrl + G` | Help |
| `Ctrl + C` | Show cursor position |

> **Tip:** Nano displays many of these shortcuts at the bottom of the screen, so you do not need to memorize all of them immediately.

---

# 38. Completion Checklist

Before considering this lab complete, make sure you can:

- [ ] Explain what a text editor is
- [ ] Explain why Linux administrators use text editors
- [ ] Open a file with `nano`
- [ ] Create a new text file
- [ ] Enter text into a file
- [ ] Save a file in nano
- [ ] Exit nano
- [ ] Edit an existing file
- [ ] Search within nano
- [ ] Use `cat`
- [ ] Use `grep`
- [ ] Use `nl`
- [ ] Use `wc`
- [ ] Explain `>`
- [ ] Explain `>>`
- [ ] Create multi-line files using a here-document
- [ ] Create configuration-style files
- [ ] Back up a configuration file
- [ ] Explain why configuration files must be handled carefully

---

# 39. Final Takeaways

Text editors are fundamental Linux administration tools.

The basic nano workflow is:

```bash
nano filename
```

Then:

```text
Ctrl + O
Enter
Ctrl + X
```

The most useful command-line text operations include:

```bash
cat
grep
nl
wc
```

File redirection is also important:

```text
>   = overwrite
>>  = append
```

For larger automated file creation, here-documents can be useful:

```bash
cat > file.txt <<'EOF'
Line one
Line two
EOF
```

Understanding these techniques will make later Linux administration and cybersecurity labs much easier.

---

# 40. Conclusion

In this lab, you learned how to work with text editors and text files from the Linux command line.

You practiced:

- Opening files with nano
- Creating and editing text files
- Saving and exiting nano
- Searching within files
- Creating configuration-style files
- Using `cat`
- Using `grep`
- Using `nl`
- Using `wc`
- Using output redirection
- Creating multi-line files
- Backing up files before modification
- Applying safe configuration-management practices

Text editing is a foundational Linux skill because administrators and security professionals frequently work with configuration files, scripts, logs, and system documentation.

---

# 🚀 Next Lab

Continue to:

**Lab 05 — File Permissions**

In the next lab, you will learn how Linux controls access to files and directories using users, groups, permissions, and the `chmod` command.
