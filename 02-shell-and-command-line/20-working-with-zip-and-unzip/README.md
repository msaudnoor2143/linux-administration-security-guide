# Lab 20 — Working with `zip` and `unzip`

> Learn how to create, inspect, and extract ZIP archives using the `zip` and `unzip` commands in Linux.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Check whether `zip` and `unzip` are installed
- Install the `zip` and `unzip` utilities when necessary
- Create compressed ZIP archives
- Compress multiple files into a single archive
- Inspect the contents of a ZIP archive
- Extract files from a ZIP archive
- Verify extracted files
- Understand common uses of ZIP archives

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Basic familiarity with the Linux command line
- Access to a Unix-like operating system
- A terminal
- Basic knowledge of creating and listing files

> **Note:** This lab can be completed on Linux, macOS, or another Unix-like system with the appropriate utilities installed.

---

# 1. Understanding `zip` and `unzip`

`zip` and `unzip` are command-line utilities used to create and extract ZIP archives.

A ZIP archive can contain:

- Multiple files
- Directories
- Compressed data

For example, instead of transferring:

```text
file1.txt
file2.txt
file3.txt
```

individually, they can be combined into:

```text
myarchive.zip
```

---

# 2. Checking Whether `zip` Is Installed

First check whether the `zip` utility is available:

```bash
zip -v
```

If the command returns version information, `zip` is installed.

---

# 3. Checking Whether `unzip` Is Installed

Check the `unzip` utility:

```bash
unzip -v
```

If version information is displayed, `unzip` is installed.

---

# 4. Installing `zip` and `unzip`

If either utility is unavailable, install the required packages.

## Debian / Ubuntu

On Debian-based systems such as Ubuntu:

```bash
sudo apt-get update
sudo apt-get install zip unzip
```

---

## Red Hat-Based Systems

On systems using `yum`:

```bash
sudo yum install zip unzip
```

> Package-management commands can vary between Linux distributions and versions. Use the package manager appropriate for your operating system.

---

## macOS

If Homebrew is installed, the original lab provides:

```bash
brew install zip
```

and:

```bash
brew install unzip
```

---

# 5. Creating Practice Files

For this lab, create a dedicated practice directory:

```bash
mkdir -p ~/zip-lab
```

Move into it:

```bash
cd ~/zip-lab
```

Create the first sample file:

```bash
echo "This is file 1" > file1.txt
```

Create the second sample file:

```bash
echo "This is file 2" > file2.txt
```

Verify the files:

```bash
ls -l
```

You should see:

```text
file1.txt
file2.txt
```

---

# 6. Creating a ZIP Archive

Use the `zip` command to compress both files into one archive:

```bash
zip myarchive.zip file1.txt file2.txt
```

This creates:

```text
myarchive.zip
```

The archive contains:

```text
file1.txt
file2.txt
```

---

# 7. Understanding the `zip` Command

The basic syntax is:

```bash
zip archive.zip file1 file2
```

In our example:

```bash
zip myarchive.zip file1.txt file2.txt
```

The components are:

```text
zip
│
├── myarchive.zip
│
├── file1.txt
└── file2.txt
```

The first argument specifies the archive name.

The remaining arguments specify the files to include.

---

# 8. Verifying the ZIP Archive

The `unzip` command can display the contents of a ZIP archive without extracting it.

Run:

```bash
unzip -l myarchive.zip
```

The `-l` option lists the contents of the archive.

You should see the files:

```text
file1.txt
file2.txt
```

---

# 9. Extracting a ZIP Archive

To extract the archive, use:

```bash
unzip myarchive.zip
```

The files contained in the archive will be extracted into the current directory.

---

# 10. Verifying Extracted Files

After extraction, list the directory:

```bash
ls
```

You should see:

```text
file1.txt
file2.txt
myarchive.zip
```

You can verify the contents of the files:

```bash
cat file1.txt
```

and:

```bash
cat file2.txt
```

Expected content:

```text
This is file 1
```

and:

```text
This is file 2
```

---

# 🧪 Practical Lab

Complete the following tasks.

## Task 1 — Check `zip`

Run:

```bash
zip -v
```

Confirm that the utility is available.

---

## Task 2 — Check `unzip`

Run:

```bash
unzip -v
```

Confirm that the utility is available.

---

## Task 3 — Create the Lab Workspace

Run:

```bash
mkdir -p ~/zip-lab
```

Then:

```bash
cd ~/zip-lab
```

---

## Task 4 — Create Sample Files

Run:

```bash
echo "This is file 1" > file1.txt
echo "This is file 2" > file2.txt
```

Verify:

```bash
ls -l
```

---

## Task 5 — Create the ZIP Archive

Run:

```bash
zip myarchive.zip file1.txt file2.txt
```

Verify that the archive exists:

```bash
ls -lh myarchive.zip
```

---

## Task 6 — Inspect the Archive

Run:

```bash
unzip -l myarchive.zip
```

Confirm that both files are listed.

---

## Task 7 — Extract the Archive

For a clean extraction test, create a separate directory:

```bash
mkdir extracted
```

Copy the archive into it:

```bash
cp myarchive.zip extracted/
```

Move into the extraction directory:

```bash
cd extracted
```

Extract the archive:

```bash
unzip myarchive.zip
```

---

## Task 8 — Verify Extraction

Run:

```bash
ls -l
```

Then inspect the files:

```bash
cat file1.txt
```

and:

```bash
cat file2.txt
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `zip -v` | Display ZIP utility information |
| `unzip -v` | Display UNZIP utility information |
| `zip archive.zip file1 file2` | Create a ZIP archive |
| `unzip -l archive.zip` | List archive contents |
| `unzip archive.zip` | Extract a ZIP archive |
| `ls -l` | List files with detailed information |
| `cat file` | Display file contents |

---

# 🧠 Key Concepts

## ZIP Archive

A ZIP archive is a container that can hold multiple files and compressed data.

Example:

```text
myarchive.zip
```

---

## `zip`

The `zip` command creates ZIP archives.

Example:

```bash
zip myarchive.zip file1.txt file2.txt
```

---

## `unzip`

The `unzip` command extracts ZIP archives.

Example:

```bash
unzip myarchive.zip
```

---

## `unzip -l`

The `-l` option lists the contents of an archive without extracting the files.

Example:

```bash
unzip -l myarchive.zip
```

This is useful for checking what an archive contains before extraction.

---

# 🛡️ Security & Administration Perspective

ZIP archives are commonly used for:

- File transfers
- Sharing multiple files
- Backup-related workflows
- Software distribution
- Organizing collections of files
- Reducing the size of transferred data

Before extracting an archive obtained from an unknown or untrusted source, inspect its contents first:

```bash
unzip -l archive.zip
```

This helps you understand what files are contained in the archive before extraction.

Only extract files into locations where you understand the resulting changes.

---

# ⚠️ Best Practices

### 1. Inspect archives before extraction

Use:

```bash
unzip -l archive.zip
```

before extracting an unfamiliar archive.

### 2. Use dedicated directories for practice

For example:

```text
~/zip-lab
```

keeps experimental files separate from important data.

### 3. Use meaningful archive names

For example:

```text
project_backup.zip
```

is easier to understand than:

```text
archive1.zip
```

### 4. Verify important files after extraction

Check that the expected files exist:

```bash
ls -l
```

You can also inspect their contents:

```bash
cat filename
```

### 5. Keep backups of important data

Creating an archive should not be considered the same as maintaining a complete backup strategy.

---

# 📝 Questions

1. What is the purpose of the `zip` command?
2. What is the purpose of the `unzip` command?
3. How can you check whether `zip` is installed?
4. How can you check whether `unzip` is installed?
5. How do you create a ZIP archive containing multiple files?
6. What does the `-l` option do with `unzip`?
7. How can you inspect an archive without extracting it?
8. How do you extract a ZIP archive?
9. Why is it useful to inspect an unfamiliar archive before extraction?
10. What are some common uses of ZIP archives?
11. Why is a dedicated practice directory useful?
12. What is the difference between creating an archive and extracting an archive?

---

# 🧩 Challenge

Create three additional files:

```bash
cd ~/zip-lab
```

Then:

```bash
echo "Linux administration" > linux.txt
echo "Network administration" > networking.txt
echo "Security administration" > security.txt
```

Create an archive containing all three:

```bash
zip administration.zip linux.txt networking.txt security.txt
```

Inspect the archive:

```bash
unzip -l administration.zip
```

Create a separate directory:

```bash
mkdir challenge-extracted
```

Copy the archive:

```bash
cp administration.zip challenge-extracted/
```

Enter the directory:

```bash
cd challenge-extracted
```

Extract the archive:

```bash
unzip administration.zip
```

Verify:

```bash
ls -l
```

Then inspect each file:

```bash
cat linux.txt
cat networking.txt
cat security.txt
```

---

# 📁 Practical Workflow

The basic workflow from this lab is:

```text
Create files
     ↓
Create ZIP archive
     ↓
Inspect archive
     ↓
Extract archive
     ↓
Verify files
```

Example:

```bash
zip myarchive.zip file1.txt file2.txt
```

Then:

```bash
unzip -l myarchive.zip
```

Then:

```bash
unzip myarchive.zip
```

Finally:

```bash
ls
```

---

# 🧹 Cleanup

When you have completed the lab and no longer need the practice files, remove the dedicated practice directory:

```bash
rm -rf ~/zip-lab
```

> **Warning:** Only run this command if `~/zip-lab` contains the practice files created for this lab and nothing you want to keep.

---

# 📌 Summary

In this lab, you learned how to work with ZIP archives using `zip` and `unzip`.

You practiced:

- Checking whether `zip` and `unzip` are installed
- Installing the utilities when necessary
- Creating sample files
- Creating a ZIP archive containing multiple files
- Listing archive contents
- Extracting a ZIP archive
- Verifying extracted files
- Applying ZIP archives to practical file-management tasks

The key commands are:

```bash
zip myarchive.zip file1.txt file2.txt
```

```bash
unzip -l myarchive.zip
```

```bash
unzip myarchive.zip
```

These commands provide a useful foundation for file compression, transfers, and archive management in Linux.

---

# ✅ Lab Completion Checklist

- [ ] I can check whether `zip` is installed
- [ ] I can check whether `unzip` is installed
- [ ] I understand what a ZIP archive is
- [ ] I can create a ZIP archive
- [ ] I can add multiple files to a ZIP archive
- [ ] I can inspect ZIP archive contents
- [ ] I understand the `unzip -l` command
- [ ] I can extract a ZIP archive
- [ ] I can verify extracted files
- [ ] I understand common uses of ZIP archives
- [ ] I understand the importance of inspecting unfamiliar archives
- [ ] I completed the practical lab
- [ ] I completed the challenge
- [ ] I cleaned up my practice files

---

## 🚀 Next Lab

**Lab 21 — Package Management**
