# Lab 12 — Basic Shell Scripting

> Learn how to create, make executable, and run a simple Bash shell script.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand the basics of shell scripting
- Create a simple Bash shell script
- Understand the shebang (`#!/bin/bash`)
- Use `echo` inside a shell script
- Change file permissions with `chmod`
- Make a shell script executable
- Execute a shell script from the terminal
- Understand how shell scripts can automate command-line operations

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Access to a Linux system
- A terminal
- Basic understanding of the Linux operating system
- Familiarity with basic terminal commands
- Basic knowledge of `echo`
- Basic knowledge of `chmod`
- Basic understanding of `./`
- Completion of **Lab 11 — Environment Variables**

> **Note:** This lab can be completed without root privileges.

---

# 1. Understanding Shell Scripts

A shell script is a text file containing commands that can be executed by a shell.

Instead of entering commands individually, multiple commands can be placed inside a script and executed together.

Shell scripts are commonly used for:

- Automating repetitive tasks
- System administration
- File management
- System maintenance
- Configuration tasks
- Security automation
- Command-line workflows

A Bash script commonly begins with:

```bash
#!/bin/bash
```

This is called the **shebang**.

---

# 2. Understanding the Shebang

The first line of a Bash script is commonly:

```bash
#!/bin/bash
```

The shebang tells the system which interpreter should be used to execute the script.

In this lab, Bash is used as the shell interpreter.

---

# 3. Writing a Simple Shell Script

The original exercise creates a script named:

```text
hello_world.sh
```

The script contains:

```bash
#!/bin/bash
echo "Hello World!"
```

The first line specifies Bash as the interpreter.

The second line uses `echo` to display a message.

---

# 🧪 Practical Lab

Perform the following exercise in your Linux terminal.

First return to your home directory:

```bash
cd ~
```

Verify your location:

```bash
pwd
```

---

## Task 1 — Create a Shell Script

Create a file named:

```text
hello_world.sh
```

You can use a text editor such as `nano`, `vi`, or `gedit`.

For example:

```bash
nano hello_world.sh
```

Add the following contents:

```bash
#!/bin/bash
echo "Hello World!"
```

Save the file and exit the editor.

> **Alternative:** If you prefer not to use an interactive editor, you can create the same file with:

```bash
echo '#!/bin/bash' > hello_world.sh
echo 'echo "Hello World!"' >> hello_world.sh
```

Verify the file exists:

```bash
ls -l hello_world.sh
```

---

## Task 2 — Inspect the Script

Display the contents of the script:

```bash
cat hello_world.sh
```

You should see:

```text
#!/bin/bash
echo "Hello World!"
```

The script contains two commands:

1. The Bash interpreter declaration
2. The `echo` command

---

## Task 3 — Make the Script Executable

A newly created file may not have execute permission.

Change its permissions with:

```bash
chmod +x hello_world.sh
```

The `+x` option adds execute permission.

Verify the permissions:

```bash
ls -l hello_world.sh
```

You should see an `x` in the permission information.

For example:

```text
-rwxr--r-- 1 user user ... hello_world.sh
```

The exact permissions may differ depending on your system's default settings.

---

# 4. Understanding File Permissions

Linux uses permissions to control what users can do with files.

Common permissions include:

| Permission | Meaning |
|---|---|
| `r` | Read |
| `w` | Write |
| `x` | Execute |

For a shell script, execute permission allows the file to be run directly as a program.

The command:

```bash
chmod +x hello_world.sh
```

adds execute permission to the file.

---

# 5. Running the Shell Script

Once the script has execute permission, run it using:

```bash
./hello_world.sh
```

The output should be:

```text
Hello World!
```

The `./` means that the script is located in the current directory.

---

# 6. Understanding `./`

When you execute:

```bash
./hello_world.sh
```

the shell is being told to run the file named `hello_world.sh` from the current directory.

The current directory is represented by:

```text
.
```

Therefore:

```text
./hello_world.sh
```

means:

```text
run hello_world.sh from the current directory
```

---

# 7. Running the Script Through Bash

A script can also be executed by explicitly invoking Bash:

```bash
bash hello_world.sh
```

This is different from:

```bash
./hello_world.sh
```

The first command explicitly starts Bash to interpret the script.

The second executes the script directly and relies on its executable permission and interpreter declaration.

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `echo` | Display text |
| `cat` | Display file contents |
| `chmod +x file` | Add execute permission |
| `ls -l` | Display detailed file permissions |
| `./script.sh` | Execute an executable script from the current directory |
| `bash script.sh` | Run a script using Bash |
| `pwd` | Display the current directory |

---

# 🧠 Key Concepts

## Shell Script

A shell script is a file containing a sequence of shell commands.

Example:

```bash
#!/bin/bash
echo "Hello World!"
```

---

## Shebang

The shebang specifies the interpreter used for the script.

Example:

```bash
#!/bin/bash
```

---

## `echo`

The `echo` command displays text.

Example:

```bash
echo "Hello World!"
```

---

## `chmod`

The `chmod` command changes file permissions.

Example:

```bash
chmod +x hello_world.sh
```

The `+x` adds execute permission.

---

## Execute Permission

A script normally needs execute permission when you want to run it directly with:

```bash
./hello_world.sh
```

---

## `./`

The `./` notation refers to the current directory.

Example:

```bash
./hello_world.sh
```

---

# 🛡️ Security Perspective

Shell scripting is an important skill in Linux administration and cybersecurity.

Scripts can automate tasks such as:

- System checks
- Log processing
- File management
- Configuration verification
- Security monitoring
- Administrative workflows

However, scripts should be written and executed carefully.

A script can perform many commands automatically, so administrators should understand what a script does before running it.

### Important practice

Before executing an unfamiliar script:

```bash
cat script.sh
```

or:

```bash
less script.sh
```

Review its contents first.

Avoid blindly executing scripts from unknown sources.

---

# ⚠️ Best Practices

### 1. Inspect scripts before executing them

Use:

```bash
cat script.sh
```

to understand what the script contains.

### 2. Use clear script names

For example:

```text
backup.sh
system_check.sh
log_analysis.sh
```

### 3. Use the appropriate interpreter

For Bash scripts:

```bash
#!/bin/bash
```

### 4. Check permissions

Use:

```bash
ls -l script.sh
```

### 5. Practice in a safe directory

Use your home directory or a dedicated laboratory directory rather than modifying important system files.

### 6. Avoid unnecessary privileges

Do not use `sudo` unless the task actually requires administrative privileges.

---

# 📝 Questions

1. What is a shell script?
2. What is the purpose of the shebang?
3. What does `#!/bin/bash` specify?
4. What does the `echo` command do?
5. What does `chmod +x` do?
6. Why does a script need execute permission when using `./script.sh`?
7. What does `./` represent?
8. What is the difference between `./hello_world.sh` and `bash hello_world.sh`?
9. How can you inspect a script before executing it?
10. Why can shell scripting be useful for system administration and security?

---

# 🧪 Challenge

Create another script named:

```text
system_info.sh
```

Make it display:

```text
System Information
```

Your script should contain:

```bash
#!/bin/bash
echo "System Information"
```

Make it executable:

```bash
chmod +x system_info.sh
```

Run it:

```bash
./system_info.sh
```

Expected output:

```text
System Information
```

Then inspect the file:

```bash
cat system_info.sh
```

---

# 🧹 Cleanup

The files created during this lab are:

```text
hello_world.sh
system_info.sh
```

If you want to remove the practice files after completing the lab:

```bash
rm hello_world.sh system_info.sh
```

> **Warning:** Only run the removal command if you are sure these files are the practice files created for this lab.

---

# 📌 Summary

In this lab, you learned the fundamentals of Bash shell scripting.

You practiced:

- Creating a shell script
- Using the Bash shebang
- Using `echo`
- Inspecting script contents
- Changing file permissions with `chmod`
- Adding execute permission
- Running scripts with `./`
- Running scripts with `bash`
- Understanding the importance of reviewing scripts before execution

Shell scripting provides an important foundation for Linux administration, automation, and cybersecurity.

---

# ✅ Lab Completion Checklist

- [ ] I understand what a shell script is
- [ ] I understand the Bash shebang
- [ ] I can create a basic shell script
- [ ] I can use `echo` inside a script
- [ ] I can inspect a script with `cat`
- [ ] I understand Linux execute permissions
- [ ] I can use `chmod +x`
- [ ] I can verify permissions with `ls -l`
- [ ] I can execute a script with `./script.sh`
- [ ] I can execute a script with `bash script.sh`
- [ ] I understand what `./` means
- [ ] I understand why scripts should be reviewed before execution
- [ ] I can create and execute a basic Bash script

---

## 🚀 Next Lab

**Lab 13 — Using Piping and Command-Line Combinations**
