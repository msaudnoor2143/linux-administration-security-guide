# Lab 45 — Introduction to `/etc/fstab`

> Learn how Linux uses `/etc/fstab` to define filesystems that can be mounted automatically and how to safely inspect and test filesystem mount configurations.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand `/etc/fstab`
- Inspect existing filesystem entries
- Understand the fields in an fstab entry
- Identify storage devices
- Create mount points
- Back up `/etc/fstab`
- Understand how automatic mounting works
- Test fstab configuration

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Basic Linux filesystem knowledge
- Basic knowledge of mounting
- Access to a Linux system
- `sudo` privileges
- A test partition or removable device for practice

---

# 1. Understanding `/etc/fstab`

The file:

```text
/etc/fstab
```

contains filesystem mount configuration.

Linux can use this file to determine which filesystems should be mounted and where they should be mounted.

---

# 2. Viewing `/etc/fstab`

You can inspect the file with:

```bash
cat /etc/fstab
```

For easier reading:

```bash
less /etc/fstab
```

---

# 3. Understanding the Fields

A typical fstab entry contains six fields:

```text
device  mount_point  filesystem  options  dump  fsck
```

For example:

```text
/dev/sdb1 /media/usb ext4 defaults 0 2
```

The fields represent:

### 1. Device

The filesystem or device being mounted.

### 2. Mount Point

The directory where the filesystem becomes accessible.

### 3. Filesystem Type

Examples include:

```text
ext4
swap
ntfs
```

### 4. Mount Options

Examples include:

```text
defaults
ro
noexec
```

### 5. Dump

Historically used for filesystem backup-related behavior.

### 6. Filesystem Check Order

Controls filesystem checking order during boot for filesystems where applicable.

---

# 4. Identifying a Removable Device

Use:

```bash
lsblk
```

You can also use:

```bash
lsblk -f
```

Identify your test or removable partition.

For example:

```text
/dev/sdb1
```

---

# 5. Creating a Mount Point

Create:

```bash
sudo mkdir -p /media/usb
```

---

# 6. Backing Up `/etc/fstab`

Before making changes:

```bash
sudo cp /etc/fstab /etc/fstab.bak
```

Verify:

```bash
ls -l /etc/fstab*
```

---

# 7. Example fstab Entry

For a test ext4 filesystem:

```text
/dev/sdb1 /media/usb ext4 defaults 0 2
```

> The actual device, filesystem type, and mount point must match your test environment.

---

# 8. Testing the Configuration

After adding a valid entry, Linux can attempt to mount the filesystems defined in `/etc/fstab` with:

```bash
sudo mount -a
```

If the configuration is correct, the filesystem should mount without requiring a reboot.

Verify:

```bash
df -h
```

You can also use:

```bash
findmnt
```

---

# 🧪 Practical Lab

## Task 1 — Inspect `/etc/fstab`

Run:

```bash
cat /etc/fstab
```

Identify existing entries.

---

## Task 2 — Understand Existing Entries

For each active entry, identify:

```text
Device
Mount Point
Filesystem
Options
Dump
Check Order
```

---

## Task 3 — Identify a Test Device

Run:

```bash
lsblk -f
```

Identify a dedicated removable or test partition.

---

## Task 4 — Back Up `/etc/fstab`

Run:

```bash
sudo cp /etc/fstab /etc/fstab.bak
```

Verify:

```bash
ls -l /etc/fstab /etc/fstab.bak
```

---

## Task 5 — Prepare a Mount Point

Create:

```bash
sudo mkdir -p /media/usb
```

---

## Task 6 — Prepare a Test Entry

For a suitable ext4 test partition, the source lab uses:

```text
/dev/sdb1 /media/usb ext4 defaults 0 2
```

Do not blindly copy this device name.

Use the actual device identified by:

```bash
lsblk -f
```

---

## Task 7 — Test the Configuration

After adding the correct entry:

```bash
sudo mount -a
```

Then:

```bash
df -h
```

Verify that the expected mount point appears.

You can also run:

```bash
findmnt /media/usb
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `cat /etc/fstab` | Display fstab |
| `less /etc/fstab` | Read fstab interactively |
| `lsblk` | List block devices |
| `lsblk -f` | Display filesystem information |
| `cp /etc/fstab /etc/fstab.bak` | Back up fstab |
| `mkdir -p` | Create mount point |
| `mount -a` | Mount filesystems defined in fstab |
| `df -h` | Display filesystem usage |
| `findmnt` | Display mounted filesystems |

---

# 🧠 Key Concepts

## `/etc/fstab`

A configuration file describing filesystem mount behavior.

## Mount Point

The directory through which a filesystem is accessed.

## Mount Options

Options controlling how a filesystem is mounted.

## `mount -a`

Attempts to mount filesystems configured in `/etc/fstab`.

---

# 🛡️ Security Perspective

`/etc/fstab` can affect how storage is mounted during system startup.

Poorly configured mount options can introduce security risks.

For example, administrators may consider options such as:

```text
ro
noexec
nodev
nosuid
```

depending on the purpose of the filesystem and the system's security requirements.

The correct option depends on the specific workload and filesystem.

---

# ⚠️ Best Practices

- Back up `/etc/fstab` before modifying it.
- Verify device identifiers.
- Test changes with `mount -a`.
- Do not blindly copy example device names.
- Keep production configurations documented.
- Be careful because an invalid fstab configuration can affect boot behavior.

---

# 📝 Questions

1. What is `/etc/fstab`?
2. What is the purpose of a mount point?
3. What are the six common fstab fields?
4. What does `mount -a` do?
5. Why should `/etc/fstab` be backed up?
6. Why should device names not be blindly copied from examples?
7. What is the purpose of mount options?
8. Why can an incorrect fstab entry cause problems during boot?

---

# 🚀 Challenge

Inspect your current `/etc/fstab` and create a table in your notes:

| Device | Mount Point | Filesystem | Options |
|---|---|---|---|
| Your entry | Your entry | Your entry | Your entry |

Explain what each field means.

---

# ✅ Lab Completion Checklist

- [ ] I understand `/etc/fstab`
- [ ] I can inspect fstab
- [ ] I understand its fields
- [ ] I can identify filesystems
- [ ] I can create a mount point
- [ ] I know how to back up fstab
- [ ] I understand `mount -a`
- [ ] I understand why fstab changes must be tested carefully

---

## Summary

In this lab, you learned how `/etc/fstab` controls filesystem mount configuration. You inspected existing entries, learned the structure of an fstab line, backed up the configuration, and learned how to test filesystem mounting with `mount -a`.

---

## 🚀 Next Lab

**Lab 46 — Bash Profile vs. Bashrc**
