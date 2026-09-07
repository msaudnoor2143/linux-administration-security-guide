# Lab 19 — Compressing with `gzip` and `bzip2`

> Learn the basics of file compression and decompression using `gzip` and `bzip2` in Linux.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand file compression and decompression
- Compress files using `gzip`
- Decompress `.gz` files using `gunzip`
- Compress files using `bzip2`
- Decompress `.bz2` files using `bunzip2`
- Understand the differences between `gzip` and `bzip2`
- Understand common use cases for each compression tool

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Basic understanding of Linux files and directories
- Access to a Linux terminal
- Basic knowledge of commands such as `ls`
- `gzip` installed on the system
- `bzip2` installed on the system

You can check the tools with:

```bash
gzip --version
```

and:

```bash
bzip2 --version
```

> `gzip` and `bzip2` are commonly available on Linux systems.

---

# 1. Understanding File Compression

**Compression** reduces the amount of storage space required by a file.

Compressed files can also be useful when transferring or storing data.

Two common Linux compression utilities are:

```text
gzip
```

and:

```text
bzip2
```

Each produces its own compressed file format.

| Tool | Typical extension |
|---|---|
| `gzip` | `.gz` |
| `bzip2` | `.bz2` |

---

# 2. Using `gzip`

`gzip` is a popular Linux compression utility.

It is commonly used to compress individual files.

For example:

```bash
gzip example.txt
```

The original file is normally replaced by:

```text
example.txt.gz
```

---

# 3. Create a Practice File

For this lab, create a dedicated practice directory:

```bash
mkdir -p ~/compression-lab
```

Move into it:

```bash
cd ~/compression-lab
```

Create a sample file:

```bash
echo "This is a sample file for the gzip compression lab." > example.txt
```

Verify the file:

```bash
ls -lh example.txt
```

---

# 4. Compress a File Using `gzip`

Compress the sample file:

```bash
gzip example.txt
```

Now check the directory:

```bash
ls -lh
```

The original:

```text
example.txt
```

should have been replaced by:

```text
example.txt.gz
```

---

# 5. Understanding `.gz`

The `.gz` extension indicates that the file has been compressed using gzip.

For example:

```text
example.txt.gz
```

contains the compressed version of:

```text
example.txt
```

---

# 6. Decompressing with `gunzip`

The `gunzip` command is used to decompress gzip-compressed files.

First verify that the compressed file exists:

```bash
ls -lh example.txt.gz
```

Then decompress it:

```bash
gunzip example.txt.gz
```

Verify that the original file has returned:

```bash
ls -lh example.txt
```

You can also inspect its contents:

```bash
cat example.txt
```

---

# 7. Using `bzip2`

`bzip2` is another Linux compression utility.

It can provide a higher compression ratio than `gzip` in many situations, although compression can take longer.

A typical command is:

```bash
bzip2 sample.txt
```

The original file is normally replaced by:

```text
sample.txt.bz2
```

---

# 8. Create a Practice File for `bzip2`

Create another sample file:

```bash
echo "This is a sample file for the bzip2 compression lab." > sample.txt
```

Verify it:

```bash
ls -lh sample.txt
```

---

# 9. Compress a File Using `bzip2`

Compress the file:

```bash
bzip2 sample.txt
```

Check the result:

```bash
ls -lh
```

You should now have:

```text
sample.txt.bz2
```

---

# 10. Understanding `.bz2`

The `.bz2` extension indicates a file compressed using `bzip2`.

For example:

```text
sample.txt.bz2
```

is the compressed form of:

```text
sample.txt
```

---

# 11. Decompressing with `bunzip2`

The `bunzip2` command is used to decompress `.bz2` files.

First verify the compressed file:

```bash
ls -lh sample.txt.bz2
```

Then decompress it:

```bash
bunzip2 sample.txt.bz2
```

Verify the original file:

```bash
ls -lh sample.txt
```

Inspect its contents:

```bash
cat sample.txt
```

---

# 12. `gzip` vs `bzip2`

Both utilities compress files, but they have different characteristics.

| Feature | `gzip` | `bzip2` |
|---|---|---|
| Output | `.gz` | `.bz2` |
| Compression | Fast | Generally slower |
| Compression ratio | Good | Often higher |
| Decompression | `gunzip` | `bunzip2` |
| Common use | Fast compression | Higher compression |

The best choice depends on the requirements of the task.

---

# 🧪 Practical Lab

Complete the following tasks.

## Task 1 — Check the Compression Tools

Run:

```bash
gzip --version
```

Then:

```bash
bzip2 --version
```

Confirm that both tools are available.

---

## Task 2 — Create the Practice Directory

Run:

```bash
mkdir -p ~/compression-lab
```

Then:

```bash
cd ~/compression-lab
```

---

## Task 3 — Create the `gzip` Sample File

Run:

```bash
echo "This is a sample file for the gzip compression lab." > example.txt
```

Verify:

```bash
ls -lh example.txt
```

---

## Task 4 — Compress with `gzip`

Run:

```bash
gzip example.txt
```

Verify:

```bash
ls -lh example.txt.gz
```

---

## Task 5 — Decompress with `gunzip`

Run:

```bash
gunzip example.txt.gz
```

Verify:

```bash
ls -lh example.txt
```

Then:

```bash
cat example.txt
```

---

## Task 6 — Create the `bzip2` Sample File

Run:

```bash
echo "This is a sample file for the bzip2 compression lab." > sample.txt
```

Verify:

```bash
ls -lh sample.txt
```

---

## Task 7 — Compress with `bzip2`

Run:

```bash
bzip2 sample.txt
```

Verify:

```bash
ls -lh sample.txt.bz2
```

---

## Task 8 — Decompress with `bunzip2`

Run:

```bash
bunzip2 sample.txt.bz2
```

Verify:

```bash
ls -lh sample.txt
```

Then:

```bash
cat sample.txt
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `gzip file` | Compress a file using gzip |
| `gunzip file.gz` | Decompress a gzip file |
| `bzip2 file` | Compress a file using bzip2 |
| `bunzip2 file.bz2` | Decompress a bzip2 file |
| `gzip --version` | Display gzip version |
| `bzip2 --version` | Display bzip2 version |
| `ls -lh file` | Display file size and information |
| `cat file` | Display file contents |

---

# 🧠 Key Concepts

## Compression

Compression reduces the amount of storage space required by data.

---

## `gzip`

`gzip` is commonly used for fast file compression.

Example:

```bash
gzip example.txt
```

Output:

```text
example.txt.gz
```

---

## `gunzip`

`gunzip` restores a gzip-compressed file.

Example:

```bash
gunzip example.txt.gz
```

Output:

```text
example.txt
```

---

## `bzip2`

`bzip2` is another compression utility that can provide a higher compression ratio than `gzip` for some data.

Example:

```bash
bzip2 sample.txt
```

Output:

```text
sample.txt.bz2
```

---

## `bunzip2`

`bunzip2` restores a `.bz2` file.

Example:

```bash
bunzip2 sample.txt.bz2
```

Output:

```text
sample.txt
```

---

# 🛡️ Security & Administration Perspective

Compression is an important system-administration skill.

Administrators may compress files to:

- Reduce storage requirements
- Transfer files more efficiently
- Store archived data
- Manage large collections of files
- Reduce the size of data being transferred

Compression is also commonly used when managing logs and other administrative data.

When working with compressed files, always verify the source of files before opening or extracting unfamiliar content.

---

# ⚠️ Best Practices

### 1. Verify files before compressing

Use:

```bash
ls -lh filename
```

to confirm the file you intend to compress.

### 2. Keep important originals backed up

Compression normally replaces the original file with its compressed version.

For example:

```bash
gzip example.txt
```

normally results in:

```text
example.txt.gz
```

Make sure important data is backed up appropriately.

### 3. Understand the file extension

Remember:

```text
.gz
```

is associated with `gzip`, while:

```text
.bz2
```

is associated with `bzip2`.

### 4. Choose the appropriate tool

Use `gzip` when fast compression is important.

Use `bzip2` when a higher compression ratio may be more useful and slower compression is acceptable.

---

# 📝 Questions

1. What is file compression?
2. What is the purpose of `gzip`?
3. What file extension does `gzip` normally create?
4. What command decompresses a `.gz` file?
5. What is the purpose of `bzip2`?
6. What file extension does `bzip2` normally create?
7. What command decompresses a `.bz2` file?
8. What is one major difference between `gzip` and `bzip2`?
9. Why might an administrator use compression?
10. What happens to the original file when using a basic `gzip` command?
11. Why should important files be backed up before compression?
12. Which tool generally provides faster compression: `gzip` or `bzip2`?

---

# 🧩 Challenge

Create your own larger sample file:

```bash
cd ~/compression-lab
```

Then run:

```bash
for i in {1..1000}; do echo "Linux compression practice data" >> large-sample.txt; done
```

Check its size:

```bash
ls -lh large-sample.txt
```

Create a copy for gzip testing:

```bash
cp large-sample.txt gzip-test.txt
```

Create another copy for bzip2 testing:

```bash
cp large-sample.txt bzip2-test.txt
```

Compress the first copy:

```bash
gzip gzip-test.txt
```

Compress the second copy:

```bash
bzip2 bzip2-test.txt
```

Compare the resulting files:

```bash
ls -lh
```

Observe the compressed file sizes.

Then restore both files:

```bash
gunzip gzip-test.txt.gz
```

and:

```bash
bunzip2 bzip2-test.txt.bz2
```

Finally verify:

```bash
ls -lh
```

---

# 📊 Comparison Exercise

Use the challenge files to compare:

```text
large-sample.txt
gzip-test.txt.gz
bzip2-test.txt.bz2
```

Consider:

- Original file size
- gzip compressed size
- bzip2 compressed size
- Compression speed
- Resulting file extensions

Remember that compression results depend on the type and contents of the data.

---

# 🧹 Cleanup

When you have completed the lab and no longer need the practice files, remove the dedicated lab directory:

```bash
rm -rf ~/compression-lab
```

> **Warning:** Only use this command if `~/compression-lab` contains the practice files created for this lab and nothing you want to keep.

---

# 📌 Summary

In this lab, you learned how to compress and decompress individual files using `gzip` and `bzip2`.

You practiced:

- Compressing files with `gzip`
- Decompressing `.gz` files with `gunzip`
- Compressing files with `bzip2`
- Decompressing `.bz2` files with `bunzip2`
- Understanding `.gz` and `.bz2` file extensions
- Comparing the general characteristics of `gzip` and `bzip2`
- Applying compression to practical file-management tasks

The key commands are:

```bash
gzip filename
```

```bash
gunzip filename.gz
```

```bash
bzip2 filename
```

```bash
bunzip2 filename.bz2
```

Understanding these utilities provides an important foundation for Linux administration, storage management, and data handling.

---

# ✅ Lab Completion Checklist

- [ ] I understand file compression
- [ ] I can use `gzip`
- [ ] I can identify a `.gz` file
- [ ] I can use `gunzip`
- [ ] I can use `bzip2`
- [ ] I can identify a `.bz2` file
- [ ] I can use `bunzip2`
- [ ] I understand the basic differences between `gzip` and `bzip2`
- [ ] I understand why compression is useful
- [ ] I completed the practical lab
- [ ] I completed the challenge
- [ ] I cleaned up my practice files

---

## 🚀 Next Lab

**Lab 20 — Working with Archives and Compressed Files**
