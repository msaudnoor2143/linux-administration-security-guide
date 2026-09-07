# Lab 09 — Working with Links

> Learn how to create and compare hard links and symbolic links using the Linux command line.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand the difference between hard links and symbolic links
- Create hard links using `ln`
- Create symbolic links using `ln -s`
- Inspect file information using `ls -l`
- Compare inode numbers using `ls -i`
- Understand how links relate to Linux inodes
- Compare the structural differences between hard links and symbolic links
- Understand practical uses of links in Linux system administration

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Access to a Linux system
- A terminal
- Basic knowledge of navigating the Linux filesystem
- Basic knowledge of creating files
- Basic understanding of files and directories
- Basic understanding of Linux inodes
- Completion of **Lab 08 — Viewing File Contents**

> **Note:** The exercises in this lab can be completed without root privileges.

---

# 1. Understanding Linux Links

A Linux link provides another way to access a file.

There are two important types of links:

1. **Hard links**
2. **Symbolic links (soft links)**

Although both provide another name or reference for a file, they work differently.

---

## 1.1 Hard Links

A hard link is another directory entry that points to the same inode as the original file.

For example:

```bash
ln original.txt hardlink.txt
```

The original file and the hard link refer to the same underlying inode.

This means they represent the same file data from the filesystem's perspective.

---

## 1.2 Symbolic Links

A symbolic link is a special file that stores a path to another file or directory.

It can be created with:

```bash
ln -s original.txt symlink.txt
```

Unlike a hard link, the symbolic link has its own inode.

The symbolic link simply points to the path of the target.

---

# 2. Hard Links vs Symbolic Links

| Feature | Hard Link | Symbolic Link |
|---|---|---|
| Created with | `ln` | `ln -s` |
| Shares inode with target | Yes | No |
| Has its own inode | No | Yes |
| Points directly to file inode | Yes | No |
| Stores target path | No | Yes |
| Can link to directories | Generally no | Yes |
| Works across filesystems | No | Yes |
| Can become broken if target is removed | No | Yes |

> The exact behavior of hard links can depend on filesystem and operating-system restrictions, but the inode relationship is the key concept to understand.

---

# 🧪 Practical Lab

## Task 1 — Create a Practice Directory

Create a dedicated directory for this lab:

```bash
mkdir -p ~/link-lab
cd ~/link-lab
```

Verify your current location:

```bash
pwd
```

List the directory:

```bash
ls -la
```

Your directory should currently be empty apart from `.` and `..`.

---

## Task 2 — Create the Original File

Create a sample file named `original.txt`:

```bash
echo "This is the original file." > original.txt
```

Verify the file:

```bash
ls -l original.txt
```

Display its contents:

```bash
cat original.txt
```

Expected output:

```text
This is the original file.
```

---

## Task 3 — Create a Hard Link

Create a hard link named `hardlink.txt`:

```bash
ln original.txt hardlink.txt
```

List both files:

```bash
ls -l original.txt hardlink.txt
```

You should see both filenames referring to the same underlying file.

Now display their inode numbers:

```bash
ls -i original.txt hardlink.txt
```

The inode numbers should be the **same**.

Example:

```text
123456 original.txt
123456 hardlink.txt
```

> Your inode number will be different. The important point is that both filenames show the same inode number.

---

## Task 4 — Create a Symbolic Link

Create a symbolic link named `symlink.txt`:

```bash
ln -s original.txt symlink.txt
```

List the files:

```bash
ls -l
```

The symbolic link should appear similar to:

```text
symlink.txt -> original.txt
```

This indicates that `symlink.txt` points to `original.txt`.

---

## Task 5 — Compare the Links

Display detailed information:

```bash
ls -l original.txt hardlink.txt symlink.txt
```

Now display inode numbers:

```bash
ls -i original.txt hardlink.txt symlink.txt
```

Observe the results.

### Expected relationship

```text
original.txt    → same inode as hardlink.txt
hardlink.txt    → same inode as original.txt
symlink.txt     → different inode
```

The exact inode numbers depend on your filesystem.

---

## Task 6 — Compare File Sizes

Use:

```bash
ls -l original.txt hardlink.txt symlink.txt
```

The original file and hard link normally show the same file size because they reference the same underlying file.

The symbolic link normally has a small size corresponding to the length of the path it stores.

For example:

```text
original.txt
hardlink.txt
symlink.txt -> original.txt
```

The symbolic link's size may therefore be different from the target file's size.

---

## Task 7 — Verify the Symbolic Link

Use:

```bash
readlink symlink.txt
```

Expected output:

```text
original.txt
```

You can also use:

```bash
readlink -f symlink.txt
```

This resolves the symbolic link to the target's absolute path.

---

## Task 8 — Inspect the Link Count

Run:

```bash
ls -l original.txt
```

Look at the number immediately after the permissions.

For example:

```text
-rw-r--r-- 2 user user ...
```

The `2` represents the number of hard links to the inode.

After creating `hardlink.txt`, the original file's hard-link count should normally increase.

You can compare:

```bash
ls -l original.txt hardlink.txt
```

Both directory entries refer to the same inode.

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `ln source target` | Create a hard link |
| `ln -s source target` | Create a symbolic link |
| `ls -l` | Display detailed file information |
| `ls -i` | Display inode numbers |
| `readlink file` | Display the target of a symbolic link |
| `readlink -f file` | Resolve a symbolic link to its final path |
| `pwd` | Display the current directory |
| `cat file` | Display file contents |
| `echo "text" > file` | Create or overwrite a text file |

---

# 🧠 Key Concepts

## `ln`

The `ln` command creates links.

Basic syntax:

```bash
ln source target
```

Example:

```bash
ln original.txt hardlink.txt
```

This creates a hard link.

---

## `ln -s`

The `-s` option creates a symbolic link.

Example:

```bash
ln -s original.txt symlink.txt
```

The symbolic link stores a reference to the target path.

---

## Inodes

An inode is a filesystem data structure that stores information about a file.

It contains metadata such as:

- File type
- Permissions
- Ownership
- File size
- Timestamps
- Links to the file's data blocks

The filename itself is associated with the inode through a directory entry.

You can display inode numbers with:

```bash
ls -i
```

---

## Hard Links and Inodes

A hard link points to the same inode as the original file.

For example:

```text
original.txt
      │
      ▼
   inode 1234
      ▲
      │
hardlink.txt
```

Therefore:

```bash
ls -i original.txt hardlink.txt
```

should show the same inode number.

---

## Symbolic Links and Inodes

A symbolic link has its own inode and contains a path to the target.

Conceptually:

```text
symlink.txt
     │
     ▼
  target path
     │
     ▼
original.txt
     │
     ▼
 target inode
```

Therefore:

```bash
ls -i original.txt symlink.txt
```

should show different inode numbers.

---

# 🛡️ Security Perspective

Understanding links is important for Linux security and system administration.

Links are commonly encountered in:

- System configuration
- Application installations
- Software versions
- Log management
- Shared resources
- Administrative scripts
- Filesystem organization

Security professionals should understand where links point before modifying or deleting files.

Symbolic links are particularly important when reviewing filesystem behavior because a link may point somewhere different from what its filename initially suggests.

Always inspect a symbolic link with:

```bash
ls -l
```

or:

```bash
readlink link_name
```

before performing administrative operations.

---

# ⚠️ Best Practices

### 1. Inspect links before modifying them

Use:

```bash
ls -l
```

to see whether an entry is a symbolic link.

---

### 2. Check inode numbers when investigating hard links

Use:

```bash
ls -i
```

This helps determine whether multiple filenames refer to the same inode.

---

### 3. Use a dedicated practice directory

Practice link operations inside:

```text
~/link-lab
```

rather than important system directories.

---

### 4. Be careful when deleting files involved in links

Deleting a symbolic link does not normally delete its target.

However, removing one hard-link name does not necessarily remove the underlying file data if another hard link still exists.

---

### 5. Avoid modifying system links while learning

System directories may contain important symbolic links used by applications and operating-system components.

Practice inside your own lab directory instead.

---

# 📝 Questions

1. What is a hard link?
2. What is a symbolic link?
3. Which command creates a hard link?
4. Which command creates a symbolic link?
5. What is an inode?
6. Why do a file and its hard link normally have the same inode number?
7. Why does a symbolic link have a different inode?
8. What does `ls -i` show?
9. What does `readlink` do?
10. What happens to a symbolic link if its target is removed?
11. Why can symbolic links work across filesystems while hard links generally cannot?
12. Why is understanding links useful for system administrators and security professionals?

---

# 🧩 Challenge

Create the following structure:

```text
~/link-lab/
├── original.txt
├── hardlink.txt
└── symlink.txt -> original.txt
```

Then run:

```bash
cd ~/link-lab
ls -li
```

Your goal is to identify:

- Which two entries share the same inode
- Which entry has a different inode
- Which entry is the symbolic link
- The hard-link count of the original file
- The size of each entry

Finally run:

```bash
readlink symlink.txt
```

and verify that it points to:

```text
original.txt
```

---

# 🧹 Cleanup

After completing the lab, you can remove the practice environment with:

```bash
rm -rf ~/link-lab
```

> **Warning:** Only use this command if `~/link-lab` is the dedicated practice directory created for this lab. Always verify the path before using recursive deletion.

You can verify that it was removed with:

```bash
ls ~
```

---

# 📌 Lab Summary

In this lab, you learned how Linux uses links to provide different ways of accessing files.

You created:

- A hard link using `ln`
- A symbolic link using `ln -s`

You then compared:

- File sizes
- Inode numbers
- Link counts
- Symbolic-link targets

The key difference is:

```text
Hard link
    ↓
Same inode
    ↓
Same underlying file
```

while:

```text
Symbolic link
    ↓
Different inode
    ↓
Points to a target path
```

Understanding this distinction is an important foundation for Linux filesystem administration and security.

---

# ✅ Lab Completion Checklist

- [ ] I can explain what a hard link is
- [ ] I can explain what a symbolic link is
- [ ] I can create hard links with `ln`
- [ ] I can create symbolic links with `ln -s`
- [ ] I can inspect links using `ls -l`
- [ ] I can display inode numbers using `ls -i`
- [ ] I can inspect symbolic-link targets using `readlink`
- [ ] I understand the relationship between links and inodes
- [ ] I understand the difference between hard and symbolic links
- [ ] I can safely practice link operations inside a dedicated directory

---

## 🚀 Next Lab

**Lab 10 — Understanding Shells**
