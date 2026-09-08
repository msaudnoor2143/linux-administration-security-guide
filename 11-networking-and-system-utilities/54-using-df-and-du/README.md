# Lab 54 — Using df and du

## 📌 Overview

Linux provides several utilities for monitoring storage usage.

Two important commands are:

- `df` — reports filesystem disk-space usage
- `du` — estimates the space used by files and directories

This lab introduces both commands and demonstrates their practical use.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Check filesystem disk usage
- Understand available and used space
- Check directory sizes
- Identify large directories
- Use human-readable output
- Troubleshoot storage-related issues

---

## 📚 Prerequisites

You should have:

- Basic Linux command-line knowledge
- Familiarity with files and directories

---

## 💾 Using df

Run:

```bash
df
```

For easier reading:

```bash
df -h
```

The `-h` option produces human-readable units such as MB and GB.

---

## 📊 Checking a Specific Filesystem

For example:

```bash
df -h /
```

This checks the filesystem containing `/`.

---

## 📁 Using du

Check the size of the current directory:

```bash
du -sh .
```

The options mean:

- `-s` — summary
- `-h` — human-readable

Check a specific directory:

```bash
du -sh /var
```

---

## 📂 View Directory Sizes

Run:

```bash
du -h --max-depth=1 .
```

This provides a summary for directories directly under the current directory.

---

## 🧪 Practical Lab

### Task 1 — Check filesystem usage

```bash
df -h
```

### Task 2 — Check the root filesystem

```bash
df -h /
```

### Task 3 — Check the current directory

```bash
du -sh .
```

### Task 4 — Check `/var`

```bash
du -sh /var
```

### Task 5 — Inspect directories

From your home directory:

```bash
cd ~
du -h --max-depth=1 .
```

### Task 6 — Identify large directories

Review the output and identify which directories consume the most space.

---

## 🔎 Command Reference

| Command | Purpose |
|---|---|
| `df` | Display filesystem usage |
| `df -h` | Human-readable filesystem usage |
| `df -h /` | Check root filesystem |
| `du -sh .` | Size of current directory |
| `du -sh /var` | Size of `/var` |
| `du -h --max-depth=1 .` | Show immediate directory sizes |

---

## 🧠 Key Concepts

### df

`df` focuses on filesystem-level storage usage.

It helps answer:

> How much space is available on this filesystem?

### du

`du` focuses on files and directories.

It helps answer:

> Which files or directories are consuming storage?

Using both commands provides a better picture of storage usage.

---

## 🛡️ Security Perspective

Disk usage monitoring can contribute to security monitoring.

Unexpected storage growth may result from:

- Excessive logs
- Temporary files
- Application data
- Backup files
- Unexpectedly generated files

Administrators should investigate unusual growth rather than simply deleting files.

---

## ⚠️ Best Practices

- Check before deleting large files.
- Avoid deleting system files without understanding their purpose.
- Monitor important filesystems regularly.
- Use human-readable output when troubleshooting.
- Check logs before removing them.

---

## 📝 Questions

1. What is the difference between `df` and `du`?
2. What does `df -h` do?
3. What does `du -sh` do?
4. Why is `/var` often important when investigating disk usage?
5. Why should large files not automatically be deleted?

---

## 📋 Lab Completion Checklist

- [ ] Run `df`
- [ ] Use human-readable output
- [ ] Check root filesystem usage
- [ ] Run `du`
- [ ] Check directory sizes
- [ ] Identify large directories
- [ ] Understand storage troubleshooting

---

## 📌 Summary

In this lab, you learned how to use `df` and `du` to investigate Linux storage usage.

These commands are essential for system administration, troubleshooting, capacity planning, and monitoring.

---

## 🚀 Next Lab

**Lab 55 — Secure File Deletion Using shred**
