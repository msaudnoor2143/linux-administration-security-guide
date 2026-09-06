# Lab 05 — File Permissions

## Objective

In this lab, you will learn how Linux controls access to files and directories using **file permissions**.

You will learn how to:

- Read and understand Linux permission strings
- Identify file owners and groups
- Check permissions using `ls -l` and `stat`
- Modify permissions using `chmod`
- Use symbolic and numeric permission notation
- Understand permissions for files versus directories
- Apply the principle of least privilege
- Verify that permission changes work as expected

---

## Prerequisites

Before starting this lab, you should be comfortable with:

- Navigating the Linux filesystem
- Creating directories
- Creating and removing files
- Using `ls`
- Using `cat`
- Using basic terminal commands
- Understanding absolute and relative paths

If you have completed **Labs 01–04**, you have everything required.

---

# Pre-Tasks

Complete these tasks before starting the main exercises.

## Pre-Task 1 — Check Your Current User

Run:

```bash
whoami
```

Then check your user ID and group memberships:

```bash
id
```

### Why?

Linux permissions are applied according to the relationship between:

- The current user
- The file owner
- The user's groups
- Everyone else

---

## Pre-Task 2 — Check Your Current Directory

Run:

```bash
pwd
```

Then list its contents:

```bash
ls -la
```

Observe the permission information displayed for existing files and directories.

---

## Pre-Task 3 — Create a Lab Workspace

Create a dedicated directory for this lab:

```bash
mkdir -p ~/linux-labs/lab-05-permissions
cd ~/linux-labs/lab-05-permissions
```

Verify:

```bash
pwd
```

You should now be inside:

```text
~/linux-labs/lab-05-permissions
```

---

## Pre-Task 4 — Create a Practice File

Create a file:

```bash
echo "Linux permissions practice file" > example.txt
```

Verify its contents:

```bash
cat example.txt
```

---

## Pre-Task 5 — Inspect the Initial Permissions

Run:

```bash
ls -l example.txt
```

You should see output similar to:

```text
-rw-r--r-- 1 user user 32 Sep 6 15:00 example.txt
```

The exact owner, group, size, and timestamp will depend on your system.

Pay particular attention to:

```text
-rw-r--r--
```

You will learn how to interpret this in the next section.

---

# Task 1 — Understanding Linux File Permissions

Linux permissions determine who can access a file and what they are allowed to do with it.

Run:

```bash
ls -l example.txt
```

A permission string may look like:

```text
-rw-r--r--
```

It can be divided into four parts:

```text
- rw- r-- r--
│ │   │   │
│ │   │   └── Others
│ │   └────── Group
│ └────────── Owner
└──────────── File type
```

### File Type

The first character represents the file type.

Common values include:

| Character | Meaning |
|---|---|
| `-` | Regular file |
| `d` | Directory |
| `l` | Symbolic link |

For example:

```text
-rw-r--r--
```

The first character:

```text
-
```

means it is a regular file.

---

# Task 2 — Understanding Read, Write, and Execute

Linux uses three basic permission types:

| Permission | Symbol | Meaning for a File |
|---|---|---|
| Read | `r` | View/read contents |
| Write | `w` | Modify contents |
| Execute | `x` | Execute the file as a program/script |

Consider:

```text
-rw-r--r--
```

The permissions are:

```text
rw-
r--
r--
```

These correspond to:

```text
Owner   → rw-
Group   → r--
Others  → r--
```

Therefore:

- Owner can read and write
- Group can read
- Others can read
- Nobody except the owner has write permission

---

# Task 3 — Understanding Owner, Group, and Others

Run:

```bash
ls -l example.txt
```

Example:

```text
-rw-r--r-- 1 saud saud 32 Sep 6 15:00 example.txt
```

The ownership information appears after the link count:

```text
saud saud
```

The first value is the **owner**.

The second value is the **group**.

Linux therefore evaluates permissions in this order:

```text
Owner → Group → Others
```

This distinction is extremely important in multi-user Linux systems.

---

# Task 4 — Inspect Detailed File Information

Use `stat`:

```bash
stat example.txt
```

You will see information including:

- File size
- Permissions
- Owner
- Group
- Access time
- Modification time
- Change time

Look for a line similar to:

```text
Access: (0644/-rw-r--r--) 
```

The `0644` portion is the numeric representation of the permissions.

---

# Task 5 — Modify Permissions with chmod

The command used to change permissions is:

```bash
chmod
```

The general syntax is:

```bash
chmod [permissions] [file]
```

---

## Task 5.1 — Add Write Permission to the Group

Run:

```bash
chmod g+w example.txt
```

Check the result:

```bash
ls -l example.txt
```

The group should now have write permission.

For example:

```text
-rw-rw-r--
```

### Explanation

```text
g
```

means group.

```text
+w
```

means add write permission.

Therefore:

```bash
chmod g+w example.txt
```

means:

> Add write permission for the group.

---

# Task 6 — Symbolic chmod Notation

Symbolic permissions use:

### Permission targets

```text
u = user/owner
g = group
o = others
a = all
```

### Permission types

```text
r = read
w = write
x = execute
```

### Operators

```text
+ = add permission
- = remove permission
= = set exact permissions
```

Examples:

```bash
chmod u+x example.txt
```

Add execute permission for the owner.

```bash
chmod g+w example.txt
```

Add write permission for the group.

```bash
chmod o-r example.txt
```

Remove read permission from others.

```bash
chmod a+r example.txt
```

Add read permission for everyone.

---

# Task 7 — Remove Permissions

First inspect the current permissions:

```bash
ls -l example.txt
```

Remove write permission from the group:

```bash
chmod g-w example.txt
```

Verify:

```bash
ls -l example.txt
```

Remove read permission from others:

```bash
chmod o-r example.txt
```

Verify:

```bash
ls -l example.txt
```

---

# Task 8 — Set Exact Symbolic Permissions

You can use `=` to explicitly define permissions.

Run:

```bash
chmod u=rw,g=r,o=r example.txt
```

Verify:

```bash
ls -l example.txt
```

The result should resemble:

```text
-rw-r--r--
```

This means:

```text
Owner  → rw-
Group  → r--
Others → r--
```

---

# Task 9 — Numeric Permissions

Linux also supports numeric permission notation.

Each permission has a numerical value:

| Permission | Value |
|---|---:|
| Read (`r`) | 4 |
| Write (`w`) | 2 |
| Execute (`x`) | 1 |

These values are added together.

### Examples

Read only:

```text
4
```

Write only:

```text
2
```

Execute only:

```text
1
```

Read + Write:

```text
4 + 2 = 6
```

Read + Execute:

```text
4 + 1 = 5
```

Read + Write + Execute:

```text
4 + 2 + 1 = 7
```

---

# Task 10 — Use chmod 764

Run:

```bash
chmod 764 example.txt
```

Then:

```bash
ls -l example.txt
```

You should see:

```text
-rwxrw-r--
```

The numeric value:

```text
764
```

is divided into three sections:

```text
7   6   4
│   │   │
│   │   └── Others
│   └────── Group
└────────── Owner
```

### Owner — 7

```text
4 + 2 + 1 = 7
```

Therefore:

```text
rwx
```

### Group — 6

```text
4 + 2 = 6
```

Therefore:

```text
rw-
```

### Others — 4

```text
4 = 4
```

Therefore:

```text
r--
```

So:

```text
764
```

means:

```text
Owner  → rwx
Group  → rw-
Others → r--
```

---

# Task 11 — Practice Common Permission Modes

Experiment with these permission settings.

## 644 — Standard Readable File

```bash
chmod 644 example.txt
ls -l example.txt
```

Expected:

```text
-rw-r--r--
```

Meaning:

```text
Owner  → read + write
Group  → read
Others → read
```

---

## 600 — Private File

```bash
chmod 600 example.txt
ls -l example.txt
```

Expected:

```text
-rw-------
```

Meaning:

```text
Owner  → read + write
Group  → no permissions
Others → no permissions
```

This is useful when a file should only be accessible by its owner.

---

## 640 — Owner and Group Access

```bash
chmod 640 example.txt
ls -l example.txt
```

Expected:

```text
-rw-r-----
```

Meaning:

```text
Owner  → read + write
Group  → read
Others → no permissions
```

---

# Task 12 — Understand Directory Permissions

Create a directory:

```bash
mkdir permissions-dir
```

Check its permissions:

```bash
ls -ld permissions-dir
```

Notice that the permission string begins with:

```text
d
```

For example:

```text
drwxr-xr-x
```

The `d` indicates that the object is a directory.

Directory permissions behave slightly differently from file permissions.

For directories:

| Permission | Meaning |
|---|---|
| `r` | List directory contents |
| `w` | Create/delete entries |
| `x` | Enter/traverse the directory |

This distinction is important when securing Linux systems.

---

# Task 13 — Practice Directory Permissions

Set the directory to:

```bash
chmod 750 permissions-dir
```

Check:

```bash
ls -ld permissions-dir
```

The result should resemble:

```text
drwxr-x---
```

This means:

```text
Owner  → rwx
Group  → r-x
Others → ---
```

---

# Task 14 — Recursive Permission Inspection

Return to your lab directory:

```bash
cd ~/linux-labs/lab-05-permissions
```

List everything:

```bash
ls -la
```

For a directory and its contents, you can inspect permissions recursively with:

```bash
find . -printf '%M %u %g %p\n'
```

This displays:

```text
Permissions Owner Group Path
```

Example:

```text
-rw-r--r-- saud saud ./example.txt
drwxr-x--- saud saud ./permissions-dir
```

---

# Practical Challenge 1 — Create a Private File

Create:

```bash
echo "Private Linux data" > private.txt
```

Set its permissions so that:

- Owner can read and write
- Group has no permissions
- Others have no permissions

Use:

```bash
chmod 600 private.txt
```

Verify:

```bash
ls -l private.txt
```

Expected:

```text
-rw-------
```

---

# Practical Challenge 2 — Create a Shared File

Create:

```bash
echo "Shared Linux information" > shared.txt
```

Set its permissions so that:

- Owner can read and write
- Group can read
- Others can read

Use:

```bash
chmod 644 shared.txt
```

Verify:

```bash
ls -l shared.txt
```

Expected:

```text
-rw-r--r--
```

---

# Practical Challenge 3 — Create an Executable Script

Create a simple script:

```bash
echo '#!/bin/bash' > test-script.sh
echo 'echo "Linux permissions lab"' >> test-script.sh
```

Inspect:

```bash
ls -l test-script.sh
```

Add execute permission for the owner:

```bash
chmod u+x test-script.sh
```

Verify:

```bash
ls -l test-script.sh
```

Run it:

```bash
./test-script.sh
```

You should see:

```text
Linux permissions lab
```

---

# Security Perspective

File permissions are one of the fundamental security mechanisms in Linux.

Incorrect permissions can expose:

- Configuration files
- Application data
- Logs
- Scripts
- Credentials
- Private user files
- System resources

A common security principle is:

> Give users and processes only the permissions they actually need.

This is known as the **principle of least privilege**.

---

# Why chmod 777 Should Be Avoided

You may encounter:

```bash
chmod 777 file
```

This gives:

```text
Owner  → rwx
Group  → rwx
Others → rwx
```

Although it may appear convenient for troubleshooting, granting unrestricted permissions can create unnecessary security exposure.

Instead, determine exactly which users need access and assign the minimum required permissions.

For example:

```bash
chmod 640 file.txt
```

may be more appropriate than:

```bash
chmod 777 file.txt
```

---

# Common Mistakes

## Mistake 1 — Confusing File and Directory Permissions

Remember:

For a file:

```text
r = read contents
w = modify contents
x = execute
```

For a directory:

```text
r = list contents
w = create/delete entries
x = enter/traverse
```

---

## Mistake 2 — Forgetting the Three Permission Groups

Always remember:

```text
Owner | Group | Others
```

For:

```text
-rwxr-xr--
```

the groups are:

```text
rwx | r-x | r--
```

---

## Mistake 3 — Miscalculating Numeric Permissions

Remember:

```text
r = 4
w = 2
x = 1
```

Therefore:

```text
rwx = 7
rw- = 6
r-x = 5
r-- = 4
-wx = 3
-w- = 2
--x = 1
--- = 0
```

---

# Useful Commands

Check permissions:

```bash
ls -l
```

Check a specific file:

```bash
ls -l example.txt
```

Show hidden files:

```bash
ls -la
```

Show detailed metadata:

```bash
stat example.txt
```

Change permissions symbolically:

```bash
chmod g+w example.txt
```

Change permissions numerically:

```bash
chmod 644 example.txt
```

Check directory permissions:

```bash
ls -ld permissions-dir
```

Find files and display permissions:

```bash
find . -printf '%M %u %g %p\n'
```

---

# Permission Reference

| Symbol | Meaning | Numeric Value |
|---|---|---:|
| `r` | Read | 4 |
| `w` | Write | 2 |
| `x` | Execute | 1 |
| `-` | No permission | 0 |

Common combinations:

| Numeric | Symbolic |
|---:|---|
| `7` | `rwx` |
| `6` | `rw-` |
| `5` | `r-x` |
| `4` | `r--` |
| `3` | `-wx` |
| `2` | `-w-` |
| `1` | `--x` |
| `0` | `---` |

---

# Common Permission Modes

| Mode | Owner | Group | Others | Typical Use |
|---:|---|---|---|---|
| `777` | `rwx` | `rwx` | `rwx` | Generally avoid |
| `755` | `rwx` | `r-x` | `r-x` | Executable/program directories |
| `750` | `rwx` | `r-x` | `---` | Restricted shared directories |
| `744` | `rwx` | `r--` | `r--` | Less common |
| `700` | `rwx` | `---` | `---` | Private directories |
| `644` | `rw-` | `r--` | `r--` | Common regular files |
| `640` | `rw-` | `r--` | `---` | Group-readable private files |
| `600` | `rw-` | `---` | `---` | Private files |

---

# Security Best Practices

When managing Linux permissions:

- Use the minimum permissions required.
- Avoid unnecessary `777` permissions.
- Protect sensitive configuration files.
- Protect private user data.
- Regularly inspect permissions on important files.
- Understand who owns a file before changing its permissions.
- Verify permission changes after using `chmod`.
- Be especially careful with recursive permission changes.
- Separate users and groups according to their responsibilities.

---

# Verification

Run the following commands:

```bash
cd ~/linux-labs/lab-05-permissions
```

Check your files:

```bash
ls -la
```

Inspect the main practice file:

```bash
stat example.txt
```

Check the private file:

```bash
ls -l private.txt
```

Check the shared file:

```bash
ls -l shared.txt
```

Check the script:

```bash
ls -l test-script.sh
```

Run the script:

```bash
./test-script.sh
```

If everything works correctly, you have successfully completed the lab.

---

# Knowledge Check

Before moving on, make sure you can answer these questions:

1. What does the first character in `-rw-r--r--` represent?
2. What are the three permission categories?
3. What does `r` mean?
4. What does `w` mean?
5. What does `x` mean?
6. What is the difference between `644` and `600`?
7. What does `chmod g+w file.txt` do?
8. What does `chmod u+x script.sh` do?
9. What does `764` mean?
10. Why should unrestricted permissions such as `777` generally be avoided?
11. How do directory permissions differ from file permissions?
12. Which command can you use to inspect detailed file metadata?

---

# Key Concepts Learned

By completing this lab, you should now understand:

- Linux permission strings
- File types
- Owner/group/others
- Read, write, and execute permissions
- Symbolic `chmod`
- Numeric `chmod`
- Permission values
- Common permission modes
- Directory permissions
- File ownership information
- Permission verification
- Least privilege
- Basic Linux file security

---

# Completion Checklist

- [ ] Checked the current user with `whoami`
- [ ] Checked user/group information with `id`
- [ ] Created the lab workspace
- [ ] Created `example.txt`
- [ ] Used `ls -l`
- [ ] Read a Linux permission string
- [ ] Used `stat`
- [ ] Changed permissions symbolically
- [ ] Removed permissions
- [ ] Used exact symbolic permissions
- [ ] Used numeric permissions
- [ ] Practiced `644`
- [ ] Practiced `600`
- [ ] Practiced `640`
- [ ] Practiced directory permissions
- [ ] Created a private file
- [ ] Created a shared file
- [ ] Created an executable script
- [ ] Verified the final permissions
- [ ] Reviewed the security implications of file permissions

---

# Final Takeaways

Linux file permissions provide a fundamental layer of access control.

The most important pattern to remember is:

```text
Owner | Group | Others
```

And the three basic permissions are:

```text
r = 4
w = 2
x = 1
```

For example:

```text
764
```

means:

```text
Owner  → rwx
Group  → rw-
Others → r--
```

Understanding permissions is essential for Linux administration, system hardening, server management, and cybersecurity.

---

## Next Lab

**Lab 06 — Working with File Ownership**

In the next lab, you will build on Linux permissions by learning how file ownership and groups affect access control.
