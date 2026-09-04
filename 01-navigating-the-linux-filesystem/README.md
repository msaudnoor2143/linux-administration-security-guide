# Lab 01 — Navigating the Linux Filesystem

> Learn how to identify your location, inspect directories, and move through the Linux filesystem using the command line.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Identify your current working directory
- Understand absolute filesystem paths
- List files and directories
- Display hidden files
- Navigate using relative paths
- Navigate using absolute paths
- Move to a parent directory
- Understand the basic Linux filesystem hierarchy

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Access to a Linux system
- Basic command-line knowledge
- A terminal
- A user account with normal permissions

> **Note:** These exercises do not require root privileges.

---

## 1. Understanding Your Current Location

Linux maintains a **current working directory** for every shell session.

To display your current location, use:

```bash
pwd
```

`pwd` means **Print Working Directory**.

### Example

```bash
pwd
```

Possible output:

```text
/home/saud
```

The output is an **absolute path**.

An absolute path begins from the root directory:

```text
/
```

---

## 2. Listing Directory Contents

Use `ls` to display the contents of your current directory:

```bash
ls
```

Example:

```text
Desktop
Documents
Downloads
Pictures
Videos
```

The exact output depends on your Linux system.

---

## 2.1 Detailed Directory Listing

Use the `-l` option to display detailed information:

```bash
ls -l
```

This can show:

- File permissions
- Number of links
- Owner
- Group
- File size
- Modification time
- File or directory name

Example:

```text
drwxr-xr-x 2 user user 4096 Sep 4 Documents
-rw-r--r-- 1 user user  250 Sep 4 notes.txt
```

---

## 3. Hidden Files

Linux treats filenames beginning with `.` as hidden files.

Examples include:

```text
.bashrc
.profile
```

A normal:

```bash
ls
```

does not display hidden files.

Use:

```bash
ls -a
```

to display them.

---

## 3.1 Detailed Listing Including Hidden Files

You can combine the options:

```bash
ls -la
```

This displays:

- Detailed file information
- Hidden files
- File permissions
- Ownership
- File sizes
- Modification information

Example:

```text
drwxr-xr-x 1 user user 4096 Sep 4 .
drwxr-xr-x 3 user user 4096 Sep 4 ..
-rw-r--r-- 1 user user  220 Sep 4 .bashrc
```

### Important

Two special directory entries commonly appear:

```text
.
..
```

`.` represents the **current directory**.

`..` represents the **parent directory**.

---

## 4. Changing Directories

The `cd` command is used to change your current working directory.

```bash
cd directory
```

For example:

```bash
cd Documents
```

After changing directories, verify your location:

```bash
pwd
```

---

## 5. Relative Paths

A relative path describes a location based on your current directory.

For example, if you are currently in:

```text
/home/saud
```

and there is a directory:

```text
/home/saud/Documents
```

you can enter it using:

```bash
cd Documents
```

You do not need to specify the complete path.

---

## 6. Absolute Paths

An absolute path starts from the root directory:

```text
/
```

For example:

```bash
cd /home/saud/Documents
```

This tells Linux exactly where you want to go regardless of your current directory.

> Replace `/home/saud/Documents` with a path that actually exists on your system.

---

## 7. Moving to the Parent Directory

To move one level upward:

```bash
cd ..
```

For example, if your current location is:

```text
/home/saud/Documents
```

running:

```bash
cd ..
```

moves you to:

```text
/home/saud
```

Verify your location:

```bash
pwd
```

---

## 8. Returning to Your Home Directory

The `~` symbol represents the current user's home directory.

You can return to your home directory using:

```bash
cd ~
```

You can also simply use:

```bash
cd
```

Verify:

```bash
pwd
```

---

# 🧪 Practical Exercise

Complete the following tasks on your Linux system.

### Task 1 — Identify Your Location

Run:

```bash
pwd
```

Record the directory returned by your system.

---

### Task 2 — Inspect the Directory

Run:

```bash
ls
```

Then:

```bash
ls -la
```

Compare the two outputs.

**Question:** What additional entries or files appear when using `ls -la`?

---

### Task 3 — Navigate to Documents

If your system has a `Documents` directory:

```bash
cd Documents
```

Then verify:

```bash
pwd
```

---

### Task 4 — Move Back

Return to the parent directory:

```bash
cd ..
```

Verify:

```bash
pwd
```

---

### Task 5 — Use an Absolute Path

Return to your home directory:

```bash
cd ~
```

Then:

```bash
pwd
```

Copy the path displayed by `pwd`.

Use that path with `cd`.

For example:

```bash
cd /home/saud
```

Replace the example path with the path shown on your own system.

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `pwd` | Display the current working directory |
| `ls` | List directory contents |
| `ls -l` | Display a detailed directory listing |
| `ls -a` | Show hidden files |
| `ls -la` | Detailed listing including hidden files |
| `cd directory` | Enter a directory |
| `cd ..` | Move to the parent directory |
| `cd ~` | Go to the user's home directory |
| `cd` | Go to the user's home directory |

---

# 🧠 Understanding Linux Paths

### Absolute Path

An absolute path begins at the root directory `/`.

Example:

```text
/home/saud/Documents
```

### Relative Path

A relative path is interpreted from your current location.

Example:

```text
Documents
```

### Current Directory

The current directory is represented by:

```text
.
```

### Parent Directory

The parent directory is represented by:

```text
..
```

### Home Directory

The current user's home directory is represented by:

```text
~
```

---

# 🛡️ Security Perspective

Filesystem navigation is a fundamental Linux security skill.

Security professionals frequently need to locate:

- Configuration files
- System logs
- User directories
- Application data
- SSH configuration
- System binaries
- Temporary files
- Security-related files

Common locations include:

```text
/etc
/var/log
/home
/tmp
/usr/bin
```

Understanding filesystem paths becomes especially important when performing:

- Security auditing
- Log analysis
- Incident investigation
- Permission reviews
- System troubleshooting
- Malware analysis
- Server administration

---

# ⚠️ Safety Notes

Most commands in this lab are read-only.

However, Linux contains commands that can modify or delete system data. Always understand a command before executing it, particularly commands involving:

- `/`
- `/etc`
- `/var`
- `/home`
- Permissions
- Ownership
- Disk devices

Do not experiment with destructive commands on a production system.

---

# ✅ Lab Completion Checklist

- [ ] I can identify my current directory using `pwd`
- [ ] I can list files using `ls`
- [ ] I can display hidden files
- [ ] I understand `.` and `..`
- [ ] I can navigate using `cd`
- [ ] I understand relative paths
- [ ] I understand absolute paths
- [ ] I can return to my home directory
- [ ] I understand the basic Linux filesystem structure
- [ ] I understand why filesystem navigation matters in cybersecurity

---

# 📝 Questions

1. What does `pwd` display?
2. What is the difference between `ls` and `ls -la`?
3. What does `.` represent?
4. What does `..` represent?
5. What does `~` represent?
6. What is the difference between an absolute path and a relative path?
7. Why is understanding Linux filesystem navigation important for cybersecurity?

---

## 🚀 Next Lab

**Lab 02 — Working with Directories**
