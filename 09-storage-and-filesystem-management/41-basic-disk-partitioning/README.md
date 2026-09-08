# Lab 41 — Basic Disk Partitioning

> Learn the fundamentals of Linux disk partitioning, inspect available storage devices, and understand how partitions can be created and removed safely.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand disk partitioning
- Identify available disks and partitions
- Inspect block devices
- Use `lsblk`
- Use `fdisk`
- Use `cfdisk`
- Create a test partition
- Remove a test partition
- Understand the risks associated with disk partitioning

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Basic Linux command-line knowledge
- Access to a Linux system
- `sudo` privileges
- A test disk or virtual machine for practice
- Basic understanding of storage devices

> ⚠️ **Important:** Partitioning can destroy existing data. Use a virtual machine or dedicated test disk whenever possible.

---

# 1. Understanding Disk Partitioning

A physical storage device can be divided into logical sections called **partitions**.

For example:

```text
Disk
├── Partition 1
├── Partition 2
└── Partition 3
```

Partitions allow different filesystems, operating systems, or storage purposes to coexist on the same physical device.

Common Linux device names include:

```text
/dev/sda
/dev/sdb
/dev/nvme0n1
```

Partitions may appear as:

```text
/dev/sda1
/dev/sda2
/dev/nvme0n1p1
```

---

# 2. Listing Available Disks

The `lsblk` command provides a tree view of block devices.

Run:

```bash
lsblk
```

You may see something similar to:

```text
NAME        SIZE TYPE MOUNTPOINTS
sda          20G disk
├─sda1        1G part /boot
└─sda2       19G part /
```

The exact output depends on your system.

---

## 2.1 Understanding `lsblk`

Important columns include:

- Device name
- Size
- Device type
- Mount point

This makes `lsblk` a useful first command when investigating storage.

---

# 3. Using `fdisk`

For detailed partition information, use:

```bash
sudo fdisk -l
```

You can also inspect a specific disk:

```bash
sudo fdisk -l /dev/sda
```

> Replace `/dev/sda` with the actual test device on your system.

`fdisk` can display information such as:

- Partition numbers
- Partition sizes
- Partition types
- Disk size
- Partition table information

---

# 4. Using `cfdisk`

`cfdisk` provides a more interactive interface for partition management.

Open it against a **test disk only**:

```bash
sudo cfdisk /dev/sdb
```

The actual device name must be replaced with your test device.

Inside `cfdisk`, you may see options such as:

```text
New
Delete
Write
Quit
```

---

# 5. Creating a Test Partition

If you have a dedicated test disk with unused space, you can create a small partition.

For example:

```text
500M
```

Within `cfdisk`:

1. Select free space.
2. Choose **New**.
3. Specify the desired size.
4. Select the appropriate partition type.
5. Choose **Write**.
6. Confirm the operation.
7. Exit the tool.

> Never perform these steps on a disk containing important data unless you fully understand the consequences.

---

# 6. Removing a Test Partition

After testing, you can remove the test partition.

Open the test device:

```bash
sudo cfdisk /dev/sdb
```

Select the test partition.

Choose:

```text
Delete
```

Then:

```text
Write
```

Confirm the operation and exit.

---

# 🧪 Practical Lab

> **Recommended:** Perform this exercise using a Linux virtual machine with an additional virtual disk.

---

## Task 1 — List Block Devices

Run:

```bash
lsblk
```

Identify:

- Main disk
- Existing partitions
- Filesystem mount points
- Any additional test disk

---

## Task 2 — Inspect Partition Tables

Run:

```bash
sudo fdisk -l
```

If you have a dedicated test disk:

```bash
sudo fdisk -l /dev/sdb
```

Record the information displayed.

---

## Task 3 — Open the Partitioning Interface

On your dedicated test disk:

```bash
sudo cfdisk /dev/sdb
```

Inspect the available free space.

Do not make changes to your primary operating-system disk.

---

## Task 4 — Create a Test Partition

If free space exists:

1. Select free space.
2. Choose **New**.
3. Create a small test partition.
4. Review the proposed changes.
5. Write the changes.
6. Exit.

Then run:

```bash
lsblk
```

Verify that the new partition appears.

---

## Task 5 — Remove the Test Partition

Open the test disk again:

```bash
sudo cfdisk /dev/sdb
```

Select the test partition.

Choose:

```text
Delete
```

Then:

```text
Write
```

Confirm and exit.

Verify:

```bash
lsblk
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `lsblk` | List block devices |
| `sudo fdisk -l` | Display partition information |
| `sudo fdisk -l /dev/sda` | Inspect a specific disk |
| `sudo cfdisk /dev/sdb` | Open interactive partitioning tool |

---

# 🧠 Key Concepts

## Disk

A physical or virtual storage device.

---

## Partition

A logical division of a storage device.

---

## Block Device

A device that provides storage in blocks, such as disks and partitions.

---

## Partition Table

Data describing the partitions stored on a disk.

Common partitioning schemes include:

- MBR
- GPT

---

## `/dev/sda`

A common Linux naming convention for a disk device.

Your system may use another name such as:

```text
/dev/nvme0n1
```

---

# 🛡️ Security Perspective

Storage management is important in system administration and security.

Incorrect partition operations can result in:

- Data loss
- Unbootable systems
- Filesystem corruption
- Loss of important evidence

Security professionals should understand the storage layout of a system before performing administrative operations.

---

# ⚠️ Best Practices

- Always back up important data.
- Use virtual machines for practice.
- Confirm the device name before modifying partitions.
- Never assume `/dev/sda` is safe to modify.
- Double-check the selected disk before writing changes.
- Do not experiment on production systems.

---

# 📝 Questions

1. What is a disk partition?
2. What does `lsblk` display?
3. What is the purpose of `fdisk`?
4. What is `cfdisk`?
5. Why should partitioning be performed carefully?
6. What is the difference between a disk and a partition?
7. Why is a virtual machine recommended for this lab?
8. What can happen if the wrong disk is partitioned?

---

# 🚀 Challenge

Using a test virtual disk:

1. Identify the disk with `lsblk`.
2. Inspect it with `fdisk`.
3. Create a small test partition.
4. Verify it with `lsblk`.
5. Remove the partition.
6. Verify the final storage layout.

Document the process in your own notes.

---

# ✅ Lab Completion Checklist

- [ ] I understand disk partitioning
- [ ] I can identify block devices
- [ ] I can use `lsblk`
- [ ] I can use `fdisk`
- [ ] I understand `cfdisk`
- [ ] I can identify free disk space
- [ ] I understand how partitions are created
- [ ] I understand how partitions are removed
- [ ] I understand the risks of partition management

---

## Summary

In this lab, you learned how Linux represents disks and partitions and practiced inspecting storage devices with `lsblk` and `fdisk`. You also explored `cfdisk` for creating and removing partitions in a controlled test environment.

Partition management is a foundational Linux administration skill and should always be performed carefully.

---

## 🚀 Next Lab

**Lab 42 — Mounting and Unmounting**
