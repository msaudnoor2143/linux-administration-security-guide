# Lab 42 — Mounting and Unmounting

> Learn how Linux attaches filesystems to the directory tree and how to safely mount and unmount storage devices.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand filesystem mounting
- Understand mount points
- Create a mount point
- Identify storage devices
- Mount a filesystem
- Verify a mounted filesystem
- Unmount a filesystem safely

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Basic Linux command-line knowledge
- Access to a Linux system
- `sudo` privileges
- A test partition or filesystem
- Basic understanding of disks and filesystems

---

# 1. Understanding Mounting

Linux uses a single filesystem hierarchy.

A filesystem becomes accessible when it is attached to a directory known as a **mount point**.

For example:

```text
/mnt/my_mount
```

A storage device can be mounted there:

```text
/dev/sdb1
      ↓
/mnt/my_mount
```

After mounting, files stored on the filesystem become accessible through the mount point.

---

# 2. Creating a Mount Point

Create a mount point:

```bash
sudo mkdir -p /mnt/my_mount
```

Verify:

```bash
ls -ld /mnt/my_mount
```

---

# 3. Identifying Storage Devices

Use:

```bash
lsblk
```

You may identify a partition such as:

```text
/dev/sdb1
```

You can also inspect filesystem information:

```bash
lsblk -f
```

This can show filesystem types and labels.

---

# 4. Mounting a Filesystem

The general syntax is:

```bash
sudo mount DEVICE MOUNT_POINT
```

Example:

```bash
sudo mount /dev/sdb1 /mnt/my_mount
```

After mounting, verify:

```bash
lsblk
```

You can also use:

```bash
df -h
```

---

# 5. Accessing the Mounted Filesystem

Move into the mount point:

```bash
cd /mnt/my_mount
```

Verify:

```bash
pwd
```

List its contents:

```bash
ls -la
```

The contents depend on the filesystem you mounted.

---

# 6. Unmounting a Filesystem

To safely detach the filesystem:

```bash
sudo umount /mnt/my_mount
```

Notice that the command is:

```text
umount
```

not:

```text
unmount
```

Verify:

```bash
lsblk
```

---

# 7. Why Unmounting Matters

Unmounting allows Linux to safely detach the filesystem.

A filesystem may fail to unmount if it is currently being used.

For example, if your shell is currently inside:

```text
/mnt/my_mount
```

move somewhere else:

```bash
cd ~
```

Then try:

```bash
sudo umount /mnt/my_mount
```

---

# 🧪 Practical Lab

## Task 1 — Create a Mount Point

Run:

```bash
sudo mkdir -p /mnt/my_mount
```

Verify:

```bash
ls -ld /mnt/my_mount
```

---

## Task 2 — Identify a Test Partition

Run:

```bash
lsblk
```

Then:

```bash
lsblk -f
```

Identify a dedicated test partition.

---

## Task 3 — Mount the Test Partition

For example:

```bash
sudo mount /dev/sdb1 /mnt/my_mount
```

Replace `/dev/sdb1` with your actual test partition.

Verify:

```bash
df -h
```

---

## Task 4 — Inspect the Mounted Filesystem

Run:

```bash
cd /mnt/my_mount
```

Then:

```bash
pwd
```

and:

```bash
ls -la
```

---

## Task 5 — Unmount the Filesystem

Return to your home directory:

```bash
cd ~
```

Unmount:

```bash
sudo umount /mnt/my_mount
```

Verify:

```bash
lsblk
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `mkdir -p` | Create a mount-point directory |
| `lsblk` | List block devices |
| `lsblk -f` | Display filesystem information |
| `mount` | Attach a filesystem |
| `umount` | Detach a filesystem |
| `df -h` | Display filesystem usage |
| `ls -la` | List directory contents |

---

# 🧠 Key Concepts

### Mount Point

A directory where a filesystem is attached.

### Mount

Attaches a filesystem to the Linux filesystem hierarchy.

### Unmount

Safely detaches a filesystem.

### Filesystem

A structure used to organize and store files on storage media.

---

# 🛡️ Security Perspective

Proper filesystem management helps protect data integrity.

Incorrectly disconnecting or manipulating storage can cause:

- Data corruption
- Filesystem errors
- Loss of data

Administrators should understand what device they are mounting and where it is being attached.

---

# ⚠️ Best Practices

- Confirm the device before mounting.
- Never mount an unknown device blindly.
- Avoid removing storage while it is mounted.
- Move out of a mount point before unmounting.
- Use test devices when learning.

---

# 📝 Questions

1. What is a mount point?
2. What does `mount` do?
3. What does `umount` do?
4. Why is `/mnt` commonly used for temporary mounts?
5. Why can a filesystem fail to unmount?
6. What does `lsblk -f` provide?
7. What is the difference between mounting and formatting?

---

# 🚀 Challenge

Use a test partition to:

```text
Identify → Mount → Inspect → Unmount → Verify
```

Record the device name and mount point used.

---

# ✅ Lab Completion Checklist

- [ ] I understand mount points
- [ ] I can create a mount point
- [ ] I can identify storage devices
- [ ] I can identify filesystems
- [ ] I can mount a filesystem
- [ ] I can verify a mount
- [ ] I can safely unmount a filesystem
- [ ] I understand why unmounting matters

---

## Summary

In this lab, you learned how Linux attaches filesystems to its directory hierarchy. You created a mount point, identified a storage device, mounted a filesystem, inspected it, and safely unmounted it.

---

## 🚀 Next Lab

**Lab 43 — Swap Space Configuration**
