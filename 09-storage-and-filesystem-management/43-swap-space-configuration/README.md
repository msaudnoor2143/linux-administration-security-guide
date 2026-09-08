# Lab 43 — Swap Space Configuration

> Learn what swap space is, inspect existing swap usage, create a swap file, activate it, and understand how swap can be configured to persist across reboots.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand swap space
- Check current swap usage
- Use `swapon`
- Use `free`
- Create a swap file
- Set secure swap-file permissions
- Initialize swap space
- Enable swap
- Understand persistent swap configuration

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Basic Linux command-line knowledge
- `sudo` privileges
- Sufficient free disk space
- A Linux system suitable for administrative practice

---

# 1. Understanding Swap Space

Swap is disk space that Linux can use as an extension of memory when required.

It is slower than physical RAM because it resides on storage.

Swap can exist as:

- A dedicated swap partition
- A swap file

This lab focuses on a swap file.

---

# 2. Checking Current Swap

Display active swap areas:

```bash
swapon --show
```

You can also inspect memory and swap usage:

```bash
free -h
```

The `-h` option displays values in a human-readable format.

---

# 3. Creating a Swap File

A swap file can be created at:

```text
/swapfile
```

For example, create a 1 GiB file:

```bash
sudo fallocate -l 1G /swapfile
```

Verify:

```bash
ls -lh /swapfile
```

---

# 4. Securing the Swap File

The swap file should not be accessible by ordinary users.

Set restrictive permissions:

```bash
sudo chmod 600 /swapfile
```

Verify:

```bash
ls -l /swapfile
```

---

# 5. Initializing the Swap File

Convert the file into swap space:

```bash
sudo mkswap /swapfile
```

This prepares the file to be used as swap.

---

# 6. Enabling Swap

Activate it:

```bash
sudo swapon /swapfile
```

Verify:

```bash
swapon --show
```

You can also run:

```bash
free -h
```

---

# 7. Persistent Swap Configuration

If the swap file should be activated automatically after reboot, an entry can be added to:

```text
/etc/fstab
```

A typical entry is:

```text
/swapfile none swap sw 0 0
```

After making changes, test the configuration carefully.

---

# 🧪 Practical Lab

## Task 1 — Check Current Swap

Run:

```bash
swapon --show
```

Then:

```bash
free -h
```

Record the current swap configuration.

---

## Task 2 — Create the Swap File

Create a test swap file:

```bash
sudo fallocate -l 1G /swapfile
```

Verify:

```bash
ls -lh /swapfile
```

---

## Task 3 — Secure the File

Run:

```bash
sudo chmod 600 /swapfile
```

Verify:

```bash
ls -l /swapfile
```

---

## Task 4 — Initialize Swap

Run:

```bash
sudo mkswap /swapfile
```

---

## Task 5 — Enable Swap

Run:

```bash
sudo swapon /swapfile
```

Verify:

```bash
swapon --show
```

Then:

```bash
free -h
```

---

## Task 6 — Understand Persistent Configuration

The source lab uses the following `/etc/fstab` entry:

```text
/swapfile none swap sw 0 0
```

Before editing `/etc/fstab`, always make a backup.

Example:

```bash
sudo cp /etc/fstab /etc/fstab.bak
```

> If you are only practicing the commands, you do not need to make the configuration permanent.

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `swapon --show` | Display active swap |
| `free -h` | Display memory and swap usage |
| `fallocate -l 1G /swapfile` | Create a 1 GiB file |
| `chmod 600 /swapfile` | Restrict file permissions |
| `mkswap /swapfile` | Initialize swap |
| `swapon /swapfile` | Enable swap |
| `cp /etc/fstab /etc/fstab.bak` | Back up fstab |

---

# 🧠 Key Concepts

## Swap

Storage space used by Linux as additional virtual memory.

## Swap File

A regular file configured for use as swap.

## `swapon`

Activates swap.

## `mkswap`

Initializes a device or file for swap use.

## `free`

Displays memory and swap statistics.

---

# 🛡️ Security Perspective

Swap can contain information that was previously present in memory.

Therefore:

- Protect swap appropriately.
- Restrict swap-file permissions.
- Understand the sensitivity of information handled by the system.
- Use appropriate security controls for systems handling sensitive data.

---

# ⚠️ Best Practices

- Check available disk space first.
- Use restrictive permissions on swap files.
- Back up `/etc/fstab` before modifying it.
- Test `/etc/fstab` changes carefully.
- Avoid creating unnecessary swap files on production systems.

---

# 📝 Questions

1. What is swap?
2. Why is swap slower than RAM?
3. What does `swapon --show` display?
4. What does `mkswap` do?
5. Why should `/swapfile` use restrictive permissions?
6. What does `fallocate` do?
7. Why is `/etc/fstab` relevant to persistent swap configuration?

---

# 🚀 Challenge

Create a temporary swap file and document:

```text
Initial Swap:
Swap File Size:
Permissions:
Swap Status Before:
Swap Status After:
```

Then explain the purpose of each command used.

---

# ✅ Lab Completion Checklist

- [ ] I understand swap space
- [ ] I can check swap usage
- [ ] I can create a swap file
- [ ] I can secure the swap file
- [ ] I can initialize swap
- [ ] I can enable swap
- [ ] I understand persistent swap configuration
- [ ] I understand why `/etc/fstab` must be handled carefully

---

## Summary

In this lab, you learned how to inspect existing swap space and configure a swap file. You used `fallocate`, `chmod`, `mkswap`, and `swapon` and learned how `/etc/fstab` can be used to configure persistent swap.

---

## 🚀 Next Lab

**Lab 44 — Basic LVM Concepts**
