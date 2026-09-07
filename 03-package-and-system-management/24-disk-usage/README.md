# Lab 24 — Disk Usage and File Size

Learn how to inspect disk usage and file sizes in Linux using the `du` command. This lab focuses on identifying how much storage directories and files consume, finding large directories, and analyzing disk usage efficiently.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Determine the size of directories in Linux.
- Check the sizes of files and subdirectories.
- Identify directories consuming the most storage.
- Sort disk usage results from largest to smallest.
- Perform a deeper recursive disk usage analysis.
- Use disk usage information for storage management and troubleshooting.

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Basic knowledge of the Linux command line.
- Access to a Linux system with terminal access.
- Familiarity with the Linux filesystem hierarchy.
- Basic knowledge of directories and files.

---

# 1. Understanding Disk Usage

Linux provides several commands for monitoring storage.

The `du` command is primarily used to estimate the amount of disk space used by files and directories.

Basic syntax:

```bash
du [options] [path]
```

For example:

```bash
du -sh /home
```

The command displays the amount of disk space consumed by `/home`.

---

# 2. Checking the Size of a Single Directory

## Command

```bash
du -sh /path/to/directory
```

### Options

| Option | Meaning |
|---|---|
| `-s` | Display only a summary |
| `-h` | Display sizes in human-readable format |

For example:

```bash
du -sh /home
```

Possible output:

```text
5.2G    /home
```

The exact result will depend on the contents of your system.

### Why this is useful

This provides a quick way to determine how much storage a particular directory is consuming.

---

# 3. Checking the Size of Subdirectories

To examine the contents of a directory individually:

```bash
du -sh /path/to/directory/*
```

For example:

```bash
du -sh /home/*
```

This allows you to compare the storage consumed by individual files and directories.

Example output:

```text
1.2G    /home/user/Documents
850M    /home/user/Downloads
420M    /home/user/Pictures
```

The actual values will vary between systems.

---

# 4. Finding the Largest Directories

When a system starts running low on storage, identifying large directories is useful.

You can combine `du` with `sort`:

```bash
du -sh /path/to/directory/* | sort -hr
```

For example:

```bash
du -sh /home/* | sort -hr
```

### Understanding the command

```text
du -sh
```

Calculates the size of each item.

```text
|
```

Pipes the output into another command.

```text
sort -hr
```

Sorts the results.

### `sort` options

| Option | Meaning |
|---|---|
| `-h` | Understand human-readable sizes |
| `-r` | Reverse the sorting order |

Using `-hr` places the largest items first.

Example:

```text
5.2G    /home/user
1.8G    /home/shared
750M    /home/test
120M    /home/temp
```

This makes it easier to immediately identify large storage consumers.

---

# 5. Performing a Deep Disk Usage Analysis

For a more detailed analysis, use:

```bash
du -ah /path/to/directory | sort -hr
```

For example:

```bash
du -ah /home | sort -hr
```

### What `-a` does

The `-a` option includes files as well as directories.

Without `-a`, `du` primarily reports directory usage.

With:

```bash
du -ah
```

you can examine individual files and directories.

The complete pipeline:

```bash
du -ah /home | sort -hr
```

can help identify the largest storage-consuming objects under `/home`.

---

# 🧪 Practical Lab

## Task 1 — Check a Directory's Size

Check the size of your home directory:

```bash
du -sh ~
```

Record the result.

---

## Task 2 — Analyze Home Directory Contents

Run:

```bash
du -sh ~/*
```

Observe the storage used by the directories and files inside your home directory.

---

## Task 3 — Sort Storage Usage

Run:

```bash
du -sh ~/* 2>/dev/null | sort -hr
```

Identify the largest items.

### Question

Which directory or file is consuming the most space?

---

## Task 4 — Perform a Detailed Analysis

Run:

```bash
du -ah ~ 2>/dev/null | sort -hr | head -20
```

This displays the largest 20 files/directories found under your home directory.

### What to observe

Look for:

- Large directories.
- Large downloaded files.
- Large project directories.
- Cached data.
- Unexpectedly large files.

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `du -sh /path` | Show total size of a directory |
| `du -sh /path/*` | Show sizes of items inside a directory |
| `du -sh /path/* \| sort -hr` | Sort items by size |
| `du -ah /path` | Show files and directories recursively |
| `du -ah /path \| sort -hr` | Recursively analyze and sort usage |
| `du -ah /path \| sort -hr \| head -20` | Display the largest 20 items |

---

# 🧠 Key Concepts

## Disk Usage

Disk usage refers to the amount of storage space currently consumed by files and directories.

---

## `du`

`du` stands for **disk usage**.

It is useful for investigating how storage is being consumed.

---

## Human-Readable Output

The `-h` option makes sizes easier to understand.

Instead of displaying only raw values, Linux can show values such as:

```text
KB
MB
GB
```

---

## Summary Mode

The `-s` option provides a summary rather than displaying every item underneath a directory.

Example:

```bash
du -sh ~
```

---

## Recursive Analysis

Using:

```bash
du -a
```

allows individual files to be included in the output.

This makes it possible to perform a more detailed storage investigation.

---

## Sorting Disk Usage

Combining:

```bash
du
```

with:

```bash
sort -hr
```

makes it much easier to identify the largest storage consumers.

---

# 🛡️ Security & Administration Perspective

Disk usage monitoring is an important part of Linux system administration.

Administrators can use these techniques to:

- Detect unexpectedly large directories.
- Investigate storage shortages.
- Monitor server storage consumption.
- Identify unnecessary files.
- Troubleshoot systems approaching full disk capacity.
- Reduce the risk of services failing because required storage is unavailable.

A full filesystem can cause applications and system services to behave unexpectedly, so storage monitoring should be part of routine system administration.

---

# ⚠️ Best Practices

- Investigate large files before deleting anything.
- Do not delete system files simply because they are large.
- Be careful when analyzing directories belonging to other users.
- Use `sudo` only when you actually need elevated permissions.
- Always verify a file's purpose before removing it.
- Monitor important server filesystems regularly.

---

# 📝 Questions

1. What does the `du` command do?
2. What does the `-h` option provide?
3. What is the purpose of `du -sh`?
4. What does the `-a` option do?
5. Why is `sort -hr` useful when analyzing disk usage?
6. How can you find the largest items inside your home directory?
7. Why is disk usage monitoring important for Linux servers?
8. What problems can occur when a filesystem becomes completely full?

---

# 🚀 Challenge

Perform a disk usage investigation of your home directory.

Use:

```bash
du -ah ~ 2>/dev/null | sort -hr | head -20
```

Then identify:

- The largest directory.
- The largest individual file.
- Approximately how much storage they consume.
- Whether the results are expected on your system.

Do not delete anything as part of this challenge.

---

# 📋 Summary

In this lab, you learned how to analyze Linux disk usage using `du`.

You practiced:

- Checking the size of a directory.
- Checking the sizes of its contents.
- Sorting directories by size.
- Performing recursive disk usage analysis.
- Identifying large files and directories.

The main commands from this lab are:

```bash
du -sh /path/to/directory
du -sh /path/to/directory/*
du -sh /path/to/directory/* | sort -hr
du -ah /path/to/directory | sort -hr
```

These commands provide a practical foundation for storage management and Linux troubleshooting.

---

# ✅ Lab Completion Checklist

- [ ] Checked the size of a directory using `du -sh`
- [ ] Checked the sizes of directory contents
- [ ] Sorted disk usage using `sort -hr`
- [ ] Performed recursive disk usage analysis
- [ ] Identified large files/directories
- [ ] Completed the challenge
- [ ] Answered the review questions

---

# 🚀 Next Lab

**Lab 25 — Creating Users**

In the next lab, you will move from storage management into Linux user administration and learn the fundamentals of creating and managing user accounts.
