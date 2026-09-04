# Lab 02 — Working with Directories

> Learn how to create, remove, rename, and move directories using the Linux command line.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Create directories with `mkdir`
- Create nested directory structures
- Remove empty directories with `rmdir`
- Understand recursive directory removal
- Rename directories with `mv`
- Move directories between locations
- Verify directory operations
- Understand the importance of safe filesystem management

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Access to a Linux system
- A terminal
- Basic knowledge of `pwd`
- Basic knowledge of `ls`
- Completion of **Lab 01 — Navigating the Linux Filesystem**

> **Note:** The exercises in this lab can be completed without root privileges.

---

# 1. Creating Directories with `mkdir`

The `mkdir` command means **make directory**.

It creates a new directory at the specified location.

### Basic syntax

```bash
mkdir directory_name
```

### Example

Create a directory named `my_new_directory`:

```bash
mkdir my_new_directory
```

Verify that it was created:

```bash
ls
```

You can also verify it directly:

```bash
ls -ld my_new_directory
```

The `-d` option tells `ls` to display information about the directory itself rather than its contents.

---

## 1.1 Creating Multiple Directories

You can create multiple directories with one command:

```bash
mkdir directory1 directory2 directory3
```

Verify:

```bash
ls
```

---

## 1.2 Creating Nested Directories

You can create a directory inside another directory.

For example:

```bash
mkdir parent_directory
mkdir parent_directory/sub_directory
```

The resulting structure is:

```text
parent_directory/
└── sub_directory/
```

### Using `-p`

The `-p` option allows you to create an entire directory path at once.

```bash
mkdir -p parent_directory/sub_directory
```

For example:

```bash
mkdir -p projects/linux/labs
```

This creates:

```text
projects/
└── linux/
    └── labs/
```

even if the parent directories do not already exist.

---

# 2. Removing Empty Directories with `rmdir`

The `rmdir` command removes **empty directories**.

### Basic syntax

```bash
rmdir directory_name
```

Create a test directory:

```bash
mkdir my_new_directory
```

Remove it:

```bash
rmdir my_new_directory
```

Verify:

```bash
ls
```

The directory should no longer appear.

---

## 2.1 Why `rmdir` Only Removes Empty Directories

Suppose a directory contains a file:

```text
example/
└── notes.txt
```

Running:

```bash
rmdir example
```

will fail because the directory is not empty.

This behavior provides an additional safety mechanism against accidentally removing directory contents.

---

# 3. Removing Directories Containing Content

The `rm` command can remove files and directories.

To recursively remove a directory and its contents:

```bash
rm -r directory_name
```

The `-r` option means **recursive**.

For example:

```bash
rm -r directory_with_contents
```

This can remove the directory and everything underneath it.

---

## ⚠️ Important Safety Warning

Be extremely careful with recursive deletion.

Before using:

```bash
rm -r
```

verify:

1. Your current location
2. The exact directory you are targeting
3. The contents of that directory

Useful checks include:

```bash
pwd
```

and:

```bash
ls -la
```

Never experiment with destructive commands on important system directories.

---

# 4. Renaming a Directory with `mv`

The `mv` command can be used to **rename** a directory.

### Syntax

```bash
mv old_name new_name
```

Create a test directory:

```bash
mkdir old_directory
```

Rename it:

```bash
mv old_directory new_directory
```

Verify:

```bash
ls
```

You should now see:

```text
new_directory
```

instead of:

```text
old_directory
```

---

# 5. Moving a Directory

The same `mv` command can move a directory to another location.

Create two directories:

```bash
mkdir new_directory
mkdir parent_directory
```

Move `new_directory` into `parent_directory`:

```bash
mv new_directory parent_directory/
```

Verify:

```bash
ls parent_directory/
```

You should see:

```text
new_directory
```

---

# 6. Understanding `mv`

The `mv` command performs two common operations.

### Rename

```bash
mv old_directory new_directory
```

Result:

```text
old_directory
    ↓
new_directory
```

### Move

```bash
mv directory destination/
```

Result:

```text
destination/
└── directory/
```

The command determines whether the operation is a rename or a move based on the destination.

---

# 🧪 Practical Lab

Perform the following exercise in your **home directory**.

First return home:

```bash
cd ~
```

Verify:

```bash
pwd
```

---

## Task 1 — Create a Lab Workspace

Create the following structure:

```text
linux-directory-lab/
└── practice/
```

Use:

```bash
mkdir -p linux-directory-lab/practice
```

Verify:

```bash
ls -R linux-directory-lab
```

---

## Task 2 — Create Additional Directories

Inside `practice`, create:

```text
documents/
scripts/
backups/
```

Run:

```bash
mkdir linux-directory-lab/practice/documents linux-directory-lab/practice/scripts linux-directory-lab/practice/backups
```

Verify:

```bash
ls linux-directory-lab/practice
```

---

## Task 3 — Rename a Directory

Rename:

```text
scripts
```

to:

```text
linux-scripts
```

Run:

```bash
mv linux-directory-lab/practice/scripts linux-directory-lab/practice/linux-scripts
```

Verify:

```bash
ls linux-directory-lab/practice
```

---

## Task 4 — Move a Directory

Move `linux-scripts` into `documents`:

```bash
mv linux-directory-lab/practice/linux-scripts linux-directory-lab/practice/documents/
```

Verify:

```bash
ls linux-directory-lab/practice/documents
```

---

## Task 5 — Remove an Empty Directory

Remove the `backups` directory:

```bash
rmdir linux-directory-lab/practice/backups
```

Verify:

```bash
ls linux-directory-lab/practice
```

---

## Task 6 — Inspect the Final Structure

Run:

```bash
ls -R linux-directory-lab
```

The final structure should look similar to:

```text
linux-directory-lab/
└── practice/
    └── documents/
        └── linux-scripts/
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `mkdir directory` | Create a directory |
| `mkdir -p path` | Create nested directories |
| `rmdir directory` | Remove an empty directory |
| `rm -r directory` | Recursively remove a directory |
| `mv old new` | Rename a directory |
| `mv directory destination/` | Move a directory |
| `ls` | List directory contents |
| `ls -la` | Detailed listing including hidden files |
| `ls -R` | Recursively list directory contents |
| `pwd` | Display the current working directory |

---

# 🧠 Key Concepts

### `mkdir`

Creates directories.

```bash
mkdir example
```

### `mkdir -p`

Creates an entire directory path when required.

```bash
mkdir -p project/src/scripts
```

### `rmdir`

Removes an empty directory.

```bash
rmdir example
```

### `mv`

Renames or moves directories.

```bash
mv old_name new_name
```

or:

```bash
mv directory destination/
```

### `rm -r`

Recursively removes directories and their contents.

```bash
rm -r directory
```

Use this command carefully.

---

# 🛡️ Security Perspective

Directory management is important in Linux security because system administrators and security professionals regularly organize:

- Application data
- Configuration files
- Logs
- Backups
- Scripts
- User data
- Security tools
- Temporary files

Poor directory organization can make systems harder to administer and audit.

More importantly, incorrect use of commands such as:

```bash
rm -r
```

can cause significant data loss.

Understanding the filesystem before performing administrative operations is therefore an important security and system-administration skill.

---

# ⚠️ Best Practices

Before modifying directories:

### 1. Check where you are

```bash
pwd
```

### 2. Check what exists

```bash
ls -la
```

### 3. Use precise paths

Avoid deleting or moving something when you are unsure about its location.

### 4. Prefer safe testing environments

Practice filesystem operations inside a dedicated directory such as:

```text
~/linux-directory-lab
```

rather than inside system directories.

---

# 📝 Questions

1. What does `mkdir` do?
2. What is the purpose of the `-p` option?
3. What is the difference between `rmdir` and `rm -r`?
4. How can `mv` be used to rename a directory?
5. How can `mv` be used to move a directory?
6. Why is `rm -r` potentially dangerous?
7. Why should you check `pwd` before performing filesystem operations?
8. What is the purpose of a dedicated practice directory?

---

# ✅ Lab Completion Checklist

- [ ] I can create directories with `mkdir`
- [ ] I can create nested directories with `mkdir -p`
- [ ] I can remove empty directories with `rmdir`
- [ ] I understand recursive directory removal
- [ ] I can rename directories using `mv`
- [ ] I can move directories using `mv`
- [ ] I can verify directory structures
- [ ] I understand the risks of recursive deletion
- [ ] I can safely organize a Linux filesystem

---

## 🚀 Next Lab

**Lab 03 — Managing Files**
