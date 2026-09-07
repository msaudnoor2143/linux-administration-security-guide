# Lab 06 — Working with File Ownership

## Objective

In this lab, you will learn how Linux manages **file and directory ownership**.

You will learn how to:

- Identify the owner and group of a file
- Understand the relationship between ownership and permissions
- Inspect ownership using `ls -l` and `stat`
- Change file ownership with `chown`
- Change group ownership with `chgrp`
- Change both owner and group
- Understand why ownership matters for Linux security
- Verify ownership changes
- Apply ownership controls using practical exercises

---

## Prerequisites

Before starting this lab, you should be comfortable with:

- Navigating the Linux filesystem
- Creating files and directories
- Using `ls`
- Using `cat`
- Understanding Linux file permissions
- Understanding `r`, `w`, and `x`
- Understanding the `Owner | Group | Others` permission model
- Using `chmod`

> **Important:** Some ownership changes require administrator privileges. Commands using `sudo` may ask for your Linux account password.

---

# Pre-Tasks

Complete these tasks before starting the main exercises.

## Pre-Task 1 — Check Your Current User

Run:

```bash
whoami
```

Then:

```bash
id
```

Take note of:

- Your username
- Your user ID
- Your primary group
- Your supplementary groups

---

## Pre-Task 2 — Check Your Current Directory

Run:

```bash
pwd
```

Then:

```bash
ls -la
```

Observe the owner and group columns for the files and directories.

---

## Pre-Task 3 — Create the Lab Workspace

Create a dedicated directory:

```bash
mkdir -p ~/linux-labs/lab-06-ownership
cd ~/linux-labs/lab-06-ownership
```

Verify:

```bash
pwd
```

---

## Pre-Task 4 — Create a Practice File

Create a file:

```bash
echo "Linux ownership practice file" > ownership.txt
```

Verify:

```bash
cat ownership.txt
```

---

## Pre-Task 5 — Inspect the File

Run:

```bash
ls -l ownership.txt
```

You should see output similar to:

```text
-rw-r--r-- 1 user user 30 Sep 7 14:00 ownership.txt
```

The exact username, group, size, and timestamp will depend on your system.

Focus on these two fields:

```text
user user
```

The first is the **owner**.

The second is the **group**.

---

# Task 1 — Understanding File Ownership

Every file and directory in Linux has an associated:

- Owner
- Group

For example:

```text
-rw-r--r-- 1 saud saud 30 Sep 7 14:00 ownership.txt
```

The ownership section is:

```text
saud saud
```

which can be represented as:

```text
Owner → saud
Group → saud
```

Linux uses this information when deciding which permissions apply to a user.

---

# Task 2 — Understanding Ownership and Permissions Together

Run:

```bash
ls -l ownership.txt
```

You may see:

```text
-rw-r--r--
```

The permissions are divided into:

```text
rw- | r-- | r--
```

and correspond to:

```text
Owner | Group | Others
```

The owner and group information tells Linux **which users belong to each permission category**.

For example:

```text
-rw-r----- 1 alice developers ownership.txt
```

means:

```text
Owner  → alice
Group  → developers
Others → everyone else
```

The permissions are:

```text
Owner  → rw-
Group  → r--
Others → ---
```

Ownership and permissions therefore work together as an access-control mechanism.

---

# Task 3 — Inspect Ownership with ls

Run:

```bash
ls -l ownership.txt
```

For a directory, use:

```bash
ls -ld .
```

You can also inspect multiple files:

```bash
ls -l
```

Example:

```text
-rw-r--r-- 1 user user 30 Sep 7 14:00 ownership.txt
```

The important fields are:

```text
Permissions  Links  Owner  Group  Size  Date  Name
```

---

# Task 4 — Inspect Ownership with stat

Use:

```bash
stat ownership.txt
```

Look for information similar to:

```text
Uid: ( 1000/    user)
Gid: ( 1000/    user)
```

This provides additional information about the file's owner and group.

You can also use:

```bash
stat -c '%U %G %n' ownership.txt
```

Example:

```text
user user ownership.txt
```

This gives:

```text
Owner Group Filename
```

---

# Task 5 — Check Your Available Users

Linux stores information about local user accounts in:

```text
/etc/passwd
```

You can safely inspect usernames with:

```bash
cut -d: -f1 /etc/passwd
```

You can also check a particular user:

```bash
id "$(whoami)"
```

This shows the UID and group information associated with your current account.

---

# Task 6 — Check Available Groups

Display groups associated with your current user:

```bash
groups
```

You can also use:

```bash
id
```

To inspect local group definitions:

```bash
cut -d: -f1 /etc/group
```

This can help you understand the groups that exist on the system.

---

# Task 7 — Change File Ownership with chown

The command used to change ownership is:

```bash
chown
```

General syntax:

```bash
chown USER FILE
```

For example:

```bash
sudo chown anotheruser ownership.txt
```

However, you should only perform this operation using a real user account that exists on your system.

Check available users first:

```bash
cut -d: -f1 /etc/passwd
```

Then verify the result:

```bash
ls -l ownership.txt
```

> **Note:** Changing ownership usually requires administrator privileges.

---

# Task 8 — Change Group Ownership with chgrp

The command used to change the group associated with a file is:

```bash
chgrp
```

General syntax:

```bash
chgrp GROUP FILE
```

First check your available groups:

```bash
groups
```

Then, using a group that your account belongs to, you can change the file's group.

For example:

```bash
chgrp "$(id -gn)" ownership.txt
```

Verify:

```bash
ls -l ownership.txt
```

---

# Task 9 — Change Owner and Group Together

`chown` can also change both the owner and group.

The general syntax is:

```bash
chown USER:GROUP FILE
```

For example:

```bash
sudo chown USER:GROUP ownership.txt
```

Replace:

```text
USER
```

and:

```text
GROUP
```

with actual accounts and groups available on your system.

Verify:

```bash
ls -l ownership.txt
```

---

# Task 10 — Change Only the Group with chown

You can also use `chown` to change only the group:

```bash
chown :GROUP ownership.txt
```

For example:

```bash
chown :"$(id -gn)" ownership.txt
```

Verify:

```bash
ls -l ownership.txt
```

This changes the group while leaving the owner unchanged.

---

# Task 11 — Create a Directory for Ownership Practice

Create:

```bash
mkdir ownership-dir
```

Create a file inside it:

```bash
echo "Ownership test" > ownership-dir/test.txt
```

Inspect the directory:

```bash
ls -ld ownership-dir
```

Inspect the file:

```bash
ls -l ownership-dir/test.txt
```

You should see ownership information for both.

---

# Task 12 — Recursive Ownership

When working with directories containing multiple files, ownership can be changed recursively.

The general form is:

```bash
sudo chown -R USER:GROUP DIRECTORY
```

The `-R` means:

```text
recursive
```

This applies the ownership change to the directory and the contents beneath it.

> **Security caution:** Be extremely careful with recursive `chown`. Running it against the wrong directory can change ownership of many files and potentially affect system operation.

For this lab, inspect your directory before making recursive changes:

```bash
find ownership-dir -maxdepth 2 -printf '%u:%g %p\n'
```

---

# Practical Challenge 1 — Identify Ownership

Run:

```bash
cd ~/linux-labs/lab-06-ownership
```

Then:

```bash
ls -l
```

For every file, identify:

```text
Owner:
Group:
Permissions:
```

You should be able to determine all three directly from the output.

---

# Practical Challenge 2 — Create Multiple Files

Create three files:

```bash
touch file1.txt file2.txt file3.txt
```

Inspect them:

```bash
ls -l
```

Use:

```bash
stat -c '%U %G %A %n' file1.txt file2.txt file3.txt
```

This displays:

```text
Owner Group Permissions Filename
```

---

# Practical Challenge 3 — Practice Group Ownership

Create a file:

```bash
echo "Group ownership practice" > group-test.txt
```

Check your current primary group:

```bash
id -gn
```

Set the file's group to your current primary group:

```bash
chgrp "$(id -gn)" group-test.txt
```

Verify:

```bash
ls -l group-test.txt
```

---

# Practical Challenge 4 — Combine Ownership and Permissions

Create:

```bash
echo "Security configuration practice" > secure-config.txt
```

Set restrictive permissions:

```bash
chmod 640 secure-config.txt
```

Check:

```bash
ls -l secure-config.txt
```

You should see permissions similar to:

```text
-rw-r-----
```

Now inspect ownership:

```bash
stat -c '%U %G %A %n' secure-config.txt
```

Think about the relationship between:

```text
Owner
Group
Permissions
```

---

# Task 13 — Ownership Verification

After making any ownership change, verify it.

Use:

```bash
ls -l filename
```

or:

```bash
stat -c '%U %G %A %n' filename
```

For example:

```bash
stat -c '%U %G %A %n' ownership.txt
```

Expected format:

```text
OWNER GROUP PERMISSIONS FILENAME
```

This is a useful habit when troubleshooting Linux access problems.

---

# Security Perspective

File ownership is a fundamental part of Linux security.

Permissions alone are not enough. Linux also needs to know:

> Who owns this resource, and which group is associated with it?

For example, a sensitive configuration file might use:

```text
Owner  → root
Group  → application-group
Others → no access
```

with permissions such as:

```text
-rw-r-----
```

This allows the owner to modify the file while members of the appropriate group can read it.

---

# Ownership and the Principle of Least Privilege

Good Linux security follows the principle of least privilege.

Users should receive:

- Only the access they need
- Only the permissions they need
- Only the group memberships they need

Avoid changing ownership simply to make an access problem disappear.

Instead:

1. Identify the intended owner.
2. Identify the intended group.
3. Determine the required permissions.
4. Apply the smallest appropriate access level.
5. Verify the result.

---

# Common Mistakes

## Mistake 1 — Confusing Owner and Group

In:

```text
-rw-r--r-- 1 alice developers file.txt
```

the:

```text
alice
```

is the owner.

The:

```text
developers
```

is the group.

---

## Mistake 2 — Using a Nonexistent User

Before changing ownership, verify that the user exists:

```bash
id username
```

If the account does not exist, the command will not perform the intended ownership change.

---

## Mistake 3 — Using sudo Without Understanding the Change

Commands such as:

```bash
sudo chown
```

can make important changes to system files.

Always verify:

```bash
pwd
```

and:

```bash
ls -l
```

before making administrative changes.

---

## Mistake 4 — Using Recursive chown Carelessly

Be extremely cautious with:

```bash
sudo chown -R
```

A recursive operation can affect many files.

Always confirm the target directory before executing it.

---

# Useful Commands

Check current user:

```bash
whoami
```

Check user and groups:

```bash
id
```

Show group memberships:

```bash
groups
```

List files with ownership:

```bash
ls -l
```

Show directory ownership:

```bash
ls -ld directory
```

Show detailed metadata:

```bash
stat filename
```

Show owner, group, permissions, and name:

```bash
stat -c '%U %G %A %n' filename
```

Change owner:

```bash
sudo chown USER filename
```

Change group:

```bash
chgrp GROUP filename
```

Change owner and group:

```bash
sudo chown USER:GROUP filename
```

Change group using `chown`:

```bash
chown :GROUP filename
```

Recursively change ownership:

```bash
sudo chown -R USER:GROUP directory
```

List local users:

```bash
cut -d: -f1 /etc/passwd
```

List local groups:

```bash
cut -d: -f1 /etc/group
```

---

# Verification

Return to the lab directory:

```bash
cd ~/linux-labs/lab-06-ownership
```

List the files:

```bash
ls -la
```

Check ownership of the main file:

```bash
stat -c '%U %G %A %n' ownership.txt
```

Check the practice files:

```bash
stat -c '%U %G %A %n' file1.txt file2.txt file3.txt
```

Check the group practice:

```bash
stat -c '%U %G %A %n' group-test.txt
```

Check the secure configuration practice:

```bash
stat -c '%U %G %A %n' secure-config.txt
```

If you can correctly identify the owner, group, and permissions of each file, you have completed the verification stage.

---

# Knowledge Check

Before moving to the next lab, make sure you can answer:

1. What is file ownership in Linux?
2. What are the two ownership attributes associated with a file?
3. How can you see a file's owner and group?
4. What command changes file ownership?
5. What command changes group ownership?
6. What does `chown USER:GROUP file` do?
7. What does the `-R` option do?
8. Why should recursive ownership changes be used carefully?
9. How do ownership and permissions work together?
10. Why is the principle of least privilege important?
11. How can you verify a file's owner and group?
12. Why might a system administrator need to change file ownership?

---

# Key Concepts Learned

By completing this lab, you should now understand:

- Linux file ownership
- Linux groups
- Owner versus group
- Ownership and permissions
- `ls -l`
- `stat`
- `chown`
- `chgrp`
- Recursive ownership changes
- Ownership verification
- Least privilege
- Ownership as a security control

---

# Command Reference

| Command | Purpose |
|---|---|
| `whoami` | Display current username |
| `id` | Display user and group information |
| `groups` | Display group memberships |
| `ls -l` | Show permissions and ownership |
| `ls -ld` | Show directory permissions and ownership |
| `stat` | Display detailed file metadata |
| `chown` | Change file owner |
| `chgrp` | Change file group |
| `chown USER:GROUP` | Change owner and group |
| `chown -R` | Recursively change ownership |
| `cut -d: -f1 /etc/passwd` | List local usernames |
| `cut -d: -f1 /etc/group` | List local group names |

---

# Security Best Practices

- Always know who owns sensitive files.
- Use groups to manage shared access appropriately.
- Avoid unnecessary ownership changes.
- Use `sudo` only when administrative privileges are required.
- Verify the target before using `chown`.
- Be especially careful with `chown -R`.
- Combine ownership with appropriate `chmod` permissions.
- Follow the principle of least privilege.
- Regularly audit ownership of important system and application files.

---

# Completion Checklist

- [ ] Checked the current user with `whoami`
- [ ] Checked user and group information with `id`
- [ ] Created the Lab 06 workspace
- [ ] Created `ownership.txt`
- [ ] Inspected ownership with `ls -l`
- [ ] Inspected ownership with `stat`
- [ ] Learned the difference between owner and group
- [ ] Checked available users
- [ ] Checked available groups
- [ ] Practiced `chown`
- [ ] Practiced `chgrp`
- [ ] Practiced changing owner and group
- [ ] Practiced directory ownership
- [ ] Learned about recursive ownership
- [ ] Practiced combining ownership with permissions
- [ ] Verified ownership changes
- [ ] Reviewed ownership security principles

---

# Final Takeaways

Linux access control is based on multiple layers.

For every file or directory, it is important to understand:

```text
Owner
Group
Permissions
```

The most important commands from this lab are:

```bash
ls -l
stat
chown
chgrp
```

Remember:

```text
chmod → changes permissions
chown → changes ownership
chgrp → changes group
```

Together, these mechanisms allow Linux administrators to control who can access and modify system resources.

---

## Next Lab

**Lab 07 — SSH and File Transfer**

In the next lab, you will move from local Linux access control into secure remote administration using SSH and secure file-transfer concepts.
