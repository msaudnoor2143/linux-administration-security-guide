# Lab 44 — Basic LVM Concepts

> Learn the fundamentals of Logical Volume Manager (LVM), including physical volumes, volume groups, and logical volumes.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand LVM
- Identify logical volumes
- Understand physical volumes
- Create a physical volume
- Create a volume group
- Create a logical volume
- Format a logical volume
- Mount a logical volume
- Remove LVM components safely

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Basic Linux command-line knowledge
- `sudo` privileges
- A dedicated test disk or virtual disk
- Basic understanding of filesystems and partitions

> ⚠️ **Important:** LVM operations can destroy data. Use a dedicated test disk or virtual machine.

---

# 1. Understanding LVM

LVM stands for:

**Logical Volume Manager**

LVM provides a flexible method of managing storage.

Traditional partitions are tied directly to physical disk boundaries.

LVM introduces an abstraction layer:

```text
Physical Volume
       ↓
Volume Group
       ↓
Logical Volume
       ↓
Filesystem
```

This makes storage management more flexible.

---

# 2. Physical Volumes

A **Physical Volume (PV)** is storage prepared for LVM.

Example:

```bash
sudo pvcreate /dev/sdb
```

This prepares `/dev/sdb` for LVM.

---

# 3. Volume Groups

A **Volume Group (VG)** combines one or more physical volumes.

Example:

```bash
sudo vgcreate myvg /dev/sdb
```

The volume group can then provide storage for logical volumes.

---

# 4. Logical Volumes

A **Logical Volume (LV)** is created inside a volume group.

Example:

```bash
sudo lvcreate -L 1G -n mylv myvg
```

This creates:

```text
mylv
```

with a size of:

```text
1G
```

inside:

```text
myvg
```

---

# 5. Viewing Existing Logical Volumes

Use:

```bash
sudo lvdisplay
```

This displays detailed information about logical volumes.

You can also inspect physical volumes:

```bash
sudo pvdisplay
```

and volume groups:

```bash
sudo vgdisplay
```

---

# 6. Formatting a Logical Volume

Once a logical volume has been created, it can be formatted.

For example:

```bash
sudo mkfs.ext4 /dev/myvg/mylv
```

This creates an ext4 filesystem.

---

# 7. Mounting the Logical Volume

Create a mount point:

```bash
sudo mkdir -p /mnt/mylv
```

Mount the logical volume:

```bash
sudo mount /dev/myvg/mylv /mnt/mylv
```

Verify:

```bash
df -h
```

---

# 8. Removing the LVM Configuration

After testing, the original lab removes the configuration in reverse order.

First unmount:

```bash
sudo umount /mnt/mylv
```

Remove the logical volume:

```bash
sudo lvremove /dev/myvg/mylv
```

Remove the volume group:

```bash
sudo vgremove myvg
```

Remove the physical-volume label:

```bash
sudo pvremove /dev/sdb
```

> Only perform these operations on the dedicated test storage created for this lab.

---

# 🧪 Practical Lab

## Task 1 — Inspect Existing LVM

Run:

```bash
sudo lvdisplay
```

Then:

```bash
sudo vgdisplay
```

And:

```bash
sudo pvdisplay
```

Observe the existing configuration.

---

## Task 2 — Identify a Test Disk

Run:

```bash
sudo fdisk -l
```

Identify your dedicated test disk.

For this example:

```text
/dev/sdb
```

---

## Task 3 — Create a Physical Volume

Run:

```bash
sudo pvcreate /dev/sdb
```

Verify:

```bash
sudo pvdisplay
```

---

## Task 4 — Create a Volume Group

Run:

```bash
sudo vgcreate myvg /dev/sdb
```

Verify:

```bash
sudo vgdisplay myvg
```

---

## Task 5 — Create a Logical Volume

Create a 1 GiB logical volume:

```bash
sudo lvcreate -L 1G -n mylv myvg
```

Verify:

```bash
sudo lvdisplay
```

---

## Task 6 — Format the Logical Volume

Run:

```bash
sudo mkfs.ext4 /dev/myvg/mylv
```

---

## Task 7 — Mount the Logical Volume

Create the mount point:

```bash
sudo mkdir -p /mnt/mylv
```

Mount:

```bash
sudo mount /dev/myvg/mylv /mnt/mylv
```

Verify:

```bash
df -h
```

---

## Task 8 — Remove the Test Configuration

Unmount:

```bash
sudo umount /mnt/mylv
```

Remove the logical volume:

```bash
sudo lvremove /dev/myvg/mylv
```

Remove the volume group:

```bash
sudo vgremove myvg
```

Remove the physical volume configuration:

```bash
sudo pvremove /dev/sdb
```

Verify:

```bash
sudo pvdisplay
sudo vgdisplay
sudo lvdisplay
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `pvcreate` | Create a physical volume |
| `pvdisplay` | Display physical-volume information |
| `vgcreate` | Create a volume group |
| `vgdisplay` | Display volume-group information |
| `lvcreate` | Create a logical volume |
| `lvdisplay` | Display logical-volume information |
| `mkfs.ext4` | Create an ext4 filesystem |
| `mount` | Mount the filesystem |
| `umount` | Unmount the filesystem |
| `lvremove` | Remove a logical volume |
| `vgremove` | Remove a volume group |
| `pvremove` | Remove LVM metadata from a physical volume |

---

# 🧠 Key Concepts

```text
Physical Disk
     ↓
Physical Volume
     ↓
Volume Group
     ↓
Logical Volume
     ↓
Filesystem
     ↓
Mount Point
```

This layered approach is one of the main advantages of LVM.

---

# 🛡️ Security Perspective

Storage configuration is important for system reliability and security.

Administrators must understand:

- Which disks are being used
- Which logical volumes contain data
- Which filesystems are mounted
- Which storage operations may destroy information

Incorrect LVM commands can permanently remove data.

---

# ⚠️ Best Practices

- Use test disks.
- Verify device names before `pvcreate`.
- Never run `lvremove` against an unknown volume.
- Maintain backups.
- Unmount filesystems before removing their logical volumes.
- Understand the complete LVM hierarchy before making changes.

---

# 📝 Questions

1. What does LVM stand for?
2. What is a physical volume?
3. What is a volume group?
4. What is a logical volume?
5. Why is LVM more flexible than traditional partitioning?
6. What does `pvcreate` do?
7. What does `vgcreate` do?
8. What does `lvcreate` do?
9. Why must a logical volume be unmounted before removal?
10. What is the relationship between PV, VG, and LV?

---

# 🚀 Challenge

Create a diagram showing:

```text
/dev/sdb
   ↓
PV
   ↓
myvg
   ↓
mylv
   ↓
ext4
   ↓
/mnt/mylv
```

Then explain each layer.

---

# ✅ Lab Completion Checklist

- [ ] I understand LVM
- [ ] I understand physical volumes
- [ ] I understand volume groups
- [ ] I understand logical volumes
- [ ] I can inspect LVM components
- [ ] I can create a test PV
- [ ] I can create a test VG
- [ ] I can create an LV
- [ ] I can format and mount an LV
- [ ] I understand how to safely remove test LVM configuration

---

## Summary

In this lab, you learned the fundamental LVM architecture and practiced creating physical volumes, volume groups, and logical volumes. You also formatted, mounted, and safely removed a test logical volume.

LVM is an important Linux storage-management technology used in many professional environments.

---

## 🚀 Next Lab

**Lab 45 — Introduction to `/etc/fstab`**
