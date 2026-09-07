# Lab 18 — Archiving with `tar`

> Learn how to create, inspect, and extract compressed `tar` archives in Linux.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand the purpose of archiving
- Create a compressed `tar` archive
- Compress archives using gzip
- List the contents of a `tar` archive
- Extract files from a compressed archive
- Understand the most common `tar` options
- Apply `tar` to basic backup and data-management tasks

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Basic knowledge of navigating the Linux command line
- Access to a Linux environment
- A terminal
- The `tar` command available on the system

You can check whether `tar` is available with:

```bash
tar --version
```

---

# 1. Understanding Archiving

**Archiving** is the process of combining multiple files and directories into a single archive.

Linux commonly uses the `tar` command for this purpose.

For example, instead of transferring several files individually, you can combine them into one archive:

```text
project/
├── file1
├── file2
├── file3
└── file4
```

into:

```text
project_archive.tar
```

A `tar` archive can also be compressed to reduce its size.

---

# 2. Understanding `tar`

The name `tar` comes from **Tape Archive**.

The `tar` command is widely used to:

- Combine files into archives
- Preserve directory structures
- List archive contents
- Extract archived files
- Work with compression formats

A common compressed archive format is:

```text
.tar.gz
```

Here:

- `.tar` represents the archive
- `.gz` indicates gzip compression

---

# 3. Creating a Compressed `tar` Archive

The basic command from this lab is:

```bash
tar -czf archive.tar.gz /path/to/folder
```

### Understanding the options

| Option | Meaning |
|---|---|
| `-c` | Create a new archive |
| `-z` | Use gzip compression |
| `-f` | Specify the archive filename |

The general structure is:

```text
tar -czf archive.tar.gz folder
```

---

# 4. Creating a Practice Directory

For this lab, create a safe practice directory in your home directory:

```bash
mkdir -p ~/tar-lab/project
```

Create a few sample files:

```bash
touch ~/tar-lab/project/file1.txt
touch ~/tar-lab/project/file2.txt
touch ~/tar-lab/project/file3.txt
```

Add some sample content:

```bash
echo "This is file 1." > ~/tar-lab/project/file1.txt
echo "This is file 2." > ~/tar-lab/project/file2.txt
echo "This is file 3." > ~/tar-lab/project/file3.txt
```

Check the directory:

```bash
ls -l ~/tar-lab/project
```

---

# 5. Create the Compressed Archive

Move into the practice directory:

```bash
cd ~/tar-lab
```

Create a gzip-compressed archive of the `project` directory:

```bash
tar -czf project_archive.tar.gz project
```

This creates:

```text
project_archive.tar.gz
```

Check that the archive exists:

```bash
ls -lh project_archive.tar.gz
```

---

# 6. Understanding the Archive Command

The command:

```bash
tar -czf project_archive.tar.gz project
```

can be understood as:

```text
tar
│
├── -c   Create archive
├── -z   Compress using gzip
├── -f   Specify archive filename
│
├── project_archive.tar.gz
│
└── project
```

The original `project` directory remains unchanged.

The command creates an additional compressed archive containing its contents.

---

# 7. Listing Archive Contents

You can inspect an archive without extracting it.

Use:

```bash
tar -tzf project_archive.tar.gz
```

### Understanding the options

| Option | Meaning |
|---|---|
| `-t` | List archive contents |
| `-z` | Handle gzip compression |
| `-f` | Specify the archive file |

The command allows you to see what is inside the archive without extracting anything.

---

# 8. Extracting the Archive

The `-x` option is used to extract files.

The basic command is:

```bash
tar -xzf project_archive.tar.gz
```

### Understanding the options

| Option | Meaning |
|---|---|
| `-x` | Extract files |
| `-z` | Handle gzip compression |
| `-f` | Specify the archive file |

---

# 9. Testing Extraction

To safely test extraction, create a separate extraction directory:

```bash
mkdir ~/tar-lab/extracted
```

Move into it:

```bash
cd ~/tar-lab/extracted
```

Extract the archive:

```bash
tar -xzf ../project_archive.tar.gz
```

Check the extracted directory:

```bash
ls -l
```

You should see:

```text
project
```

Inspect its contents:

```bash
ls -l project
```

---

# 🧪 Practical Lab

Complete the following tasks.

## Task 1 — Verify `tar`

Run:

```bash
tar --version
```

Confirm that `tar` is available.

---

## Task 2 — Create the Practice Directory

Run:

```bash
mkdir -p ~/tar-lab/project
```

---

## Task 3 — Create Sample Files

Run:

```bash
touch ~/tar-lab/project/file1.txt
touch ~/tar-lab/project/file2.txt
touch ~/tar-lab/project/file3.txt
```

---

## Task 4 — Add Sample Content

Run:

```bash
echo "This is file 1." > ~/tar-lab/project/file1.txt
echo "This is file 2." > ~/tar-lab/project/file2.txt
echo "This is file 3." > ~/tar-lab/project/file3.txt
```

---

## Task 5 — Verify the Files

Run:

```bash
ls -l ~/tar-lab/project
```

---

## Task 6 — Create the Compressed Archive

Run:

```bash
cd ~/tar-lab
tar -czf project_archive.tar.gz project
```

---

## Task 7 — Verify the Archive

Run:

```bash
ls -lh ~/tar-lab/project_archive.tar.gz
```

---

## Task 8 — List the Archive Contents

Run:

```bash
tar -tzf ~/tar-lab/project_archive.tar.gz
```

Verify that the three sample files appear in the archive.

---

## Task 9 — Create an Extraction Directory

Run:

```bash
mkdir -p ~/tar-lab/extracted
```

---

## Task 10 — Extract the Archive

Run:

```bash
cd ~/tar-lab/extracted
tar -xzf ../project_archive.tar.gz
```

---

## Task 11 — Verify Extraction

Run:

```bash
ls -l ~/tar-lab/extracted/project
```

The original files should now be present.

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `tar --version` | Display the installed `tar` version |
| `tar -czf archive.tar.gz folder` | Create a gzip-compressed archive |
| `tar -tzf archive.tar.gz` | List archive contents |
| `tar -xzf archive.tar.gz` | Extract a gzip-compressed archive |
| `ls -lh archive.tar.gz` | Display archive information |

---

# 🧠 Key Concepts

## Archive

An archive combines multiple files and directories into a single file.

Example:

```text
project_archive.tar
```

---

## Compression

Compression reduces the amount of storage space required by data.

Gzip compression can be used with `tar`:

```bash
tar -czf project_archive.tar.gz project
```

---

## `.tar.gz`

A `.tar.gz` file represents:

1. A `tar` archive
2. Compressed using gzip

---

## `-c`

Creates a new archive:

```bash
tar -czf archive.tar.gz project
```

---

## `-z`

Uses gzip compression:

```bash
tar -czf archive.tar.gz project
```

---

## `-f`

Specifies the archive filename:

```bash
tar -czf archive.tar.gz project
```

Here:

```text
archive.tar.gz
```

is the filename.

---

## `-t`

Lists the contents of an archive:

```bash
tar -tzf archive.tar.gz
```

---

## `-x`

Extracts an archive:

```bash
tar -xzf archive.tar.gz
```

---

# 🛡️ Security & Administration Perspective

Archiving is an important Linux administration skill.

Administrators may use archives for:

- Backups
- Data transfer
- Software distribution
- Project storage
- Log management
- System maintenance

Before extracting an archive, especially one obtained from an untrusted source, inspect its contents first:

```bash
tar -tzf archive.tar.gz
```

This lets you see what the archive contains before extracting it.

When handling important data, verify that the archive contains the expected files and that extraction is performed into an appropriate location.

---

# ⚠️ Best Practices

### 1. Inspect archives before extracting

Use:

```bash
tar -tzf archive.tar.gz
```

before extracting unfamiliar archives.

### 2. Keep backups separate

Do not rely on a single copy of important data.

### 3. Use meaningful archive names

For example:

```text
project_backup.tar.gz
```

is easier to understand than:

```text
archive1.tar.gz
```

### 4. Check available storage

Large archives can require significant disk space.

Check available storage with:

```bash
df -h
```

### 5. Extract archives carefully

Make sure you know where the archive contents will be extracted.

### 6. Preserve important data

Do not delete the original files simply because they have been archived unless you have verified the archive and have an appropriate backup strategy.

---

# 📋 Archive Workflow

A common archive workflow is:

```text
Create
  ↓
Inspect
  ↓
Store / Transfer
  ↓
Extract when required
  ↓
Verify
```

Example:

```bash
tar -czf project_archive.tar.gz project
```

Then:

```bash
tar -tzf project_archive.tar.gz
```

Then:

```bash
tar -xzf project_archive.tar.gz
```

---

# 📝 Questions

1. What is the purpose of the `tar` command?
2. What does the name `tar` originally refer to?
3. What does the `-c` option do?
4. What does the `-z` option do?
5. What does the `-f` option do?
6. What does the `-t` option do?
7. What does the `-x` option do?
8. What does the `.tar.gz` extension indicate?
9. How can you inspect an archive without extracting it?
10. Why should you inspect an unfamiliar archive before extracting it?
11. What are some common administrative uses for `tar`?
12. What is the difference between archiving and compression?

---

# 🧩 Challenge

Create your own directory containing several files:

```bash
mkdir -p ~/tar-lab/challenge
```

Create sample files:

```bash
touch ~/tar-lab/challenge/file1.txt
touch ~/tar-lab/challenge/file2.txt
touch ~/tar-lab/challenge/file3.txt
touch ~/tar-lab/challenge/file4.txt
```

Create a compressed archive:

```bash
cd ~/tar-lab
tar -czf challenge_archive.tar.gz challenge
```

List its contents:

```bash
tar -tzf challenge_archive.tar.gz
```

Create a separate extraction directory:

```bash
mkdir -p ~/tar-lab/challenge-extracted
```

Extract the archive:

```bash
cd ~/tar-lab/challenge-extracted
tar -xzf ../challenge_archive.tar.gz
```

Finally, verify:

```bash
ls -l challenge
```

---

# 📁 Case Study — Weekly Project Archives

Consider a software development team that needs to archive its project directories every week.

Manually handling many individual files can become inconvenient.

The team can create a compressed archive of its project directory:

```bash
tar -czf project_archive.tar.gz project
```

The resulting archive can then be stored as part of the team's backup process.

Before using an archive, administrators can inspect it:

```bash
tar -tzf project_archive.tar.gz
```

When the files are required again, they can extract the archive:

```bash
tar -xzf project_archive.tar.gz
```

This provides a simple foundation for organizing and managing project backups.

---

# 🧹 Cleanup

After completing the practical lab, you can remove the practice files and archives created specifically for this lab:

```bash
rm -rf ~/tar-lab
```

> **Warning:** Only run this command if `~/tar-lab` contains the practice material created for this lab and does not contain anything you want to keep.

---

# 📌 Summary

In this lab, you learned the fundamentals of Linux archiving with `tar`.

You practiced:

- Creating directories and sample files
- Creating gzip-compressed `tar` archives
- Listing archive contents
- Extracting archives
- Understanding common `tar` options
- Using archives for basic backup and storage workflows
- Inspecting archives before extraction

The key commands from this lab are:

```bash
tar -czf archive.tar.gz folder
```

```bash
tar -tzf archive.tar.gz
```

```bash
tar -xzf archive.tar.gz
```

Understanding these commands provides an important foundation for Linux administration, backup management, and data handling.

---

# ✅ Lab Completion Checklist

- [ ] I understand what archiving means
- [ ] I understand the purpose of `tar`
- [ ] I can create a compressed `tar` archive
- [ ] I understand the `-c` option
- [ ] I understand the `-z` option
- [ ] I understand the `-f` option
- [ ] I can list archive contents
- [ ] I understand the `-t` option
- [ ] I can extract a compressed archive
- [ ] I understand the `-x` option
- [ ] I can inspect an archive before extracting it
- [ ] I understand how `tar` can be used for backups
- [ ] I completed the practical lab
- [ ] I completed the challenge

---

## 🚀 Next Lab

**Lab 19 — Compressing with gzip**
