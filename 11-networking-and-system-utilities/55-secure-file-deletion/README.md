# Lab 55 — Secure File Deletion Using shred

## 📌 Overview

Linux provides the `shred` utility for overwriting the contents of regular files before deletion.

This lab introduces the command and explains its appropriate use and limitations.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand the purpose of `shred`
- Create a test file
- Overwrite a file using `shred`
- Remove a file after overwriting
- Understand limitations of secure deletion

---

## 📚 Prerequisites

You should have:

- Basic Linux command-line knowledge
- Understanding of files and directories
- A Linux terminal

---

## 🧠 Understanding shred

The `shred` command overwrites the contents of a file.

Basic syntax:

```bash
shred filename
```

A common combination is:

```bash
shred -u filename
```

The `-u` option removes the file after overwriting.

---

## 🧪 Practical Lab

### Task 1 — Create a test file

```bash
echo "This is temporary test data." > secure-test.txt
```

View the file:

```bash
cat secure-test.txt
```

### Task 2 — Overwrite the file

```bash
shred secure-test.txt
```

Check the file:

```bash
ls -l secure-test.txt
```

### Task 3 — Overwrite and remove

Create another test file:

```bash
echo "Temporary information." > secure-test-2.txt
```

Run:

```bash
shred -u secure-test-2.txt
```

Verify:

```bash
ls -l secure-test-2.txt
```

The file should no longer exist.

---

## 🔎 Useful Options

### Specify overwrite passes

```bash
shred -n 3 secure-test.txt
```

This requests three overwrite passes.

### Overwrite and remove

```bash
shred -u secure-test.txt
```

---

## 🧠 Important Limitations

`shred` should not be treated as a universal secure-erasure solution.

Its effectiveness depends on how data is stored.

Modern storage technologies and filesystems may use:

- SSD wear leveling
- Copy-on-write behavior
- Snapshots
- Journaling
- Backups

Therefore, overwriting one file does not necessarily guarantee that every previous copy of its data has disappeared from every storage layer.

---

## 🛡️ Security Perspective

Secure data disposal is an important part of information security.

Organizations should have appropriate procedures for:

- Temporary sensitive files
- Storage disposal
- Backup management
- Retired devices
- Data retention

The correct deletion method depends on the storage technology and organizational requirements.

---

## ⚠️ Best Practices

- Perform this lab only on test files.
- Never run `shred` against an important file without verifying the target.
- Understand your storage technology.
- Follow organizational data-retention policies.
- Use approved secure-erasure procedures for sensitive systems.

---

## 📝 Questions

1. What does `shred` do?
2. What does `shred -u` do?
3. Why should `shred` only be tested on disposable files?
4. Why may `shred` not guarantee complete removal on every storage technology?
5. Why are secure data-disposal procedures important?

---

## 🧹 Cleanup

If the first test file still exists:

```bash
shred -u secure-test.txt
```

---

## 📋 Lab Completion Checklist

- [ ] Create a test file
- [ ] Use `shred`
- [ ] Use `shred -u`
- [ ] Understand overwrite behavior
- [ ] Understand storage limitations
- [ ] Understand secure disposal concepts

---

## 📌 Summary

In this lab, you learned about the `shred` utility and its role in file disposal.

You also learned that secure deletion depends on the underlying storage technology and should be handled according to appropriate security procedures.

---

## 🚀 Next Lab

**Section 12 — Logging & System Maintenance**
