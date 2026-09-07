# Lab 10 — Understanding Shells

> Learn what a Linux shell is, identify the default shell, list available shells, and practice switching between shell environments.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand the concept and purpose of a shell
- Identify the default shell assigned to a user
- Check the current shell environment
- List available shells installed on a Linux system
- Switch between different shell environments
- Verify which shell is currently running
- Understand why shells are important for Linux administration and security

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Access to a Linux or Unix-like operating system
- A terminal
- Basic knowledge of command-line operations
- Basic understanding of environment variables
- Completion of **Lab 09 — Working with Links**

> **Note:** The exercises in this lab do not require root privileges.

---

# 1. Understanding the Shell

A **shell** is a command-line interface that allows users to interact with an operating system.

When you type a command into a terminal, the shell interprets the command and communicates with the operating system to perform the requested operation.

Common Linux shells include:

- `bash`
- `sh`
- `dash`
- `zsh`
- `fish`
- `ksh`

Different shells can provide different features, syntax, and behavior.

---

## 1.1 Why Shells Matter

Shells are important for:

- Running commands
- Managing files
- Starting programs
- Automating tasks
- Managing system resources
- Writing shell scripts
- Performing administrative operations

For Linux administrators and security professionals, command-line shell knowledge is an essential skill.

---

# 🧪 Practical Lab

## Task 1 — Check the Default Shell

### Objective

Determine the default shell assigned to the current user.

Run:

```bash
echo $SHELL
```

The `$SHELL` environment variable normally displays the path of the user's default shell.

Example output:

```text
/bin/bash
```

Another system may show something such as:

```text
/bin/zsh
```

The exact result depends on the system configuration.

---

## Task 2 — Identify the Current Shell

The `$SHELL` variable represents the user's default shell, but it does not necessarily tell you which shell process is currently running.

To inspect the current shell, run:

```bash
echo $0
```

For example:

```text
bash
```

This is useful when working with multiple shell environments.

---

## Task 3 — List Available Shells

Linux systems maintain a list of approved login shells in:

```text
/etc/shells
```

Display the file with:

```bash
cat /etc/shells
```

Example output may contain entries such as:

```text
/bin/sh
/bin/bash
/bin/dash
/bin/zsh
```

The exact list depends on which shells are installed on your system.

---

## Task 4 — Inspect `/etc/shells`

You can also inspect the file using:

```bash
less /etc/shells
```

If the file fits on the screen, you can simply use:

```bash
cat /etc/shells
```

The `/etc/shells` file is useful for determining which shells are configured as valid login shells on the system.

---

# 2. Switching to Another Shell

You can start another shell from your current shell.

For example:

```bash
sh
```

This starts a new `sh` shell inside your current terminal session.

---

## 2.1 Verify the Shell Switch

After running:

```bash
sh
```

check the current shell:

```bash
echo $0
```

You may see:

```text
sh
```

This indicates that the current command interpreter is now the `sh` shell.

---

## 2.2 Return to the Previous Shell

When you start another shell from your existing shell, the new shell runs as a child process.

To leave the current shell, run:

```bash
exit
```

You should return to the previous shell.

Verify:

```bash
echo $0
```

---

# 3. Understanding `$SHELL` vs `$0`

These two commands can provide different information.

### `$SHELL`

```bash
echo $SHELL
```

Usually shows the user's **default shell**.

### `$0`

```bash
echo $0
```

Shows the name or path associated with the **current shell process**.

For example, you might have:

```text
$ echo $SHELL
/bin/bash

$ echo $0
bash
```

After starting `sh`:

```text
$ sh

$ echo $0
sh
```

The distinction is useful when troubleshooting shell behavior or working with shell scripts.

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `echo $SHELL` | Display the user's default shell |
| `echo $0` | Display the current shell identifier |
| `cat /etc/shells` | List configured login shells |
| `less /etc/shells` | View the available shells interactively |
| `sh` | Start a `sh` shell |
| `exit` | Exit the current shell |

---

# 🧠 Key Concepts

## Shell

A shell is a command interpreter that provides an interface between the user and the operating system.

Example:

```text
User
  ↓
Shell
  ↓
Operating System
```

---

## Default Shell

The default shell is the shell configured for a user's normal login environment.

You can usually inspect it with:

```bash
echo $SHELL
```

For example:

```text
/bin/bash
```

---

## `/etc/shells`

The `/etc/shells` file contains paths to shells that are configured as valid login shells.

View it with:

```bash
cat /etc/shells
```

---

## Bash

`bash` is one of the most widely used shells on Linux systems.

It provides features such as:

- Command history
- Variables
- Command substitution
- Shell scripting
- Job control
- Command-line editing

---

## `sh`

`sh` refers to the traditional Bourne shell interface.

On modern Linux systems, `/bin/sh` may be provided by another shell implementation, such as `dash`.

Therefore, the exact behavior of `sh` can depend on the operating system.

---

## Child Shells

When you run:

```bash
sh
```

from another shell, you start a new shell process.

Conceptually:

```text
bash
 │
 └── sh
```

Running:

```bash
exit
```

from the `sh` session exits the child shell and returns you to the parent shell.

---

# 🛡️ Security Perspective

Understanding shells is important in cybersecurity because shells are frequently used for:

- System administration
- Automation
- Security monitoring
- Incident response
- Log analysis
- Configuration management
- Security scripting
- Troubleshooting

Security professionals may encounter different shells when examining systems.

Knowing how to identify the current shell helps avoid confusion when commands behave differently between environments.

The `/etc/shells` file can also provide useful information about which shells are configured on a system.

---

# ⚠️ Best Practices

### 1. Know which shell you are using

Check:

```bash
echo $0
```

This is particularly useful when troubleshooting shell-specific behavior.

---

### 2. Do not assume `$SHELL` always represents the current shell

Check both:

```bash
echo $SHELL
echo $0
```

when you need to distinguish the default shell from the current shell process.

---

### 3. Be careful when changing system shell configurations

This lab only requires temporarily starting another shell:

```bash
sh
```

Do not modify user or system login-shell settings unless you understand the consequences.

---

### 4. Use `exit` to leave nested shells

If you start another shell, use:

```bash
exit
```

to return to the previous shell.

---

### 5. Learn shell-specific syntax

Commands and scripting behavior can differ between shells.

A script written for one shell may not behave identically when executed by another.

---

# 📝 Questions

1. What is a shell?
2. Why is a shell important in Linux?
3. What does `echo $SHELL` display?
4. What does `echo $0` display?
5. What is the purpose of `/etc/shells`?
6. How can you list the available shells on a Linux system?
7. What happens when you execute `sh`?
8. How can you return to the previous shell?
9. What is the difference between a default shell and the current shell?
10. Why is shell knowledge important for cybersecurity professionals?
11. Why can commands behave differently between different shells?
12. Why should you avoid changing system shell configuration without understanding it?

---

# 🧩 Challenge

Perform the following sequence without changing any permanent system configuration.

### Step 1

Check your default shell:

```bash
echo $SHELL
```

### Step 2

Check your current shell:

```bash
echo $0
```

### Step 3

List the available shells:

```bash
cat /etc/shells
```

### Step 4

Start `sh`:

```bash
sh
```

### Step 5

Verify the new shell:

```bash
echo $0
```

### Step 6

Return to the previous shell:

```bash
exit
```

### Step 7

Verify your original shell again:

```bash
echo $0
```

Record your observations.

---

# 🧹 Cleanup

No permanent configuration changes are required for this lab.

If you started a child shell with:

```bash
sh
```

make sure you return to your original shell with:

```bash
exit
```

There is no practice directory that needs to be deleted.

---

# 📌 Lab Summary

In this lab, you learned about Linux shells and their role as command interpreters.

You learned how to:

- Identify the default shell with `echo $SHELL`
- Identify the current shell with `echo $0`
- List available shells with `cat /etc/shells`
- Start another shell with `sh`
- Return to the previous shell with `exit`

The most important distinction is:

```text
$SHELL
   ↓
Default shell for the user
```

while:

```text
$0
   ↓
Current shell/process context
```

Understanding shells provides an important foundation for Linux administration, shell scripting, automation, and cybersecurity.

---

# ✅ Lab Completion Checklist

- [ ] I understand what a shell is
- [ ] I understand the purpose of a shell
- [ ] I can identify my default shell
- [ ] I can identify my current shell
- [ ] I can list available shells
- [ ] I understand the purpose of `/etc/shells`
- [ ] I can start another shell
- [ ] I can return to the previous shell
- [ ] I understand the difference between `$SHELL` and `$0`
- [ ] I understand why shell knowledge is important in cybersecurity

---

## 🚀 Next Lab

**Lab 11 — Environment Variables**
