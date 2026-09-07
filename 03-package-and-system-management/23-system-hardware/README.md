# Lab 23 — System Hardware Information

This lab introduces basic Linux commands for retrieving and interpreting system hardware information.

You will inspect the system's **CPU, memory, and disk usage** using built-in Linux utilities.

---

## 🎯 Objective

By completing this lab, you will:

- Understand how to retrieve basic system hardware information.
- Learn how to inspect CPU architecture and processor information.
- Check RAM and swap usage.
- View filesystem disk usage.
- Interpret the output of `lscpu`, `free`, and `df`.
- Understand how these commands help with system monitoring and troubleshooting.

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Basic knowledge of the Linux command-line interface (CLI).
- Access to a Linux-based system such as Ubuntu or Fedora.
- Permission to execute system commands.

---

# 1. Display CPU Information

## 1.1 Understanding `lscpu`

The `lscpu` command displays detailed information about the CPU and processor architecture.

It gathers information from the Linux system's CPU information and presents it in a human-readable format.

The output can contain information such as:

- CPU architecture.
- Number of available CPUs.
- CPU vendor.
- CPU model.
- CPU family.
- Cache information.

---

## 1.2 Run `lscpu`

Execute:

```bash
lscpu
```

Review the information displayed by your system.

---

## 🔎 Important `lscpu` Information

### Architecture

Shows the processor architecture.

For example:

```text
x86_64
```

This indicates a 64-bit x86 architecture.

### CPU(s)

Shows the number of logical CPUs available to the operating system.

### Vendor ID

Identifies the processor manufacturer.

Examples include:

```text
GenuineIntel
```

or:

```text
AuthenticAMD
```

---

## 1.3 Example

A simplified example might look like:

```text
Architecture:        x86_64
CPU(s):              4
Vendor ID:           GenuineIntel
```

This represents a 64-bit system with four logical CPUs from Intel.

> Your actual output will depend on your hardware.

---

# 2. Check Memory Usage

## 2.1 Understanding `free`

The `free` command displays information about system memory.

It can show:

- RAM usage.
- Available memory.
- Free memory.
- Shared memory.
- Cache and buffers.
- Swap usage.

The `-h` option presents the values in a human-readable format.

---

## 2.2 Run `free -h`

Execute:

```bash
free -h
```

Review both the memory and swap information.

---

## 🔎 Important Memory Fields

### Total

The total amount of memory available.

### Used

Memory currently being used by the system and applications.

### Free

Memory that is currently unused.

### Available

An estimate of memory that can be made available for starting new applications without immediately relying on swap.

### Swap

Shows information about configured swap space.

---

## 2.3 Example

A simplified example might look like:

```text
              total        used        free      shared  buff/cache   available
Mem:           8.0Gi       2.3Gi       3.0Gi       1.1Gi       2.7Gi       4.2Gi
Swap:          2.0Gi          0B       2.0Gi
```

This example represents a system with approximately 8 GB of RAM and 2 GB of swap.

> The values on your system will be different.

---

# 3. View Disk Usage

## 3.1 Understanding `df`

The `df` command displays disk-space usage for mounted filesystems.

The `-h` option displays the values in a human-readable format.

This is useful when checking whether a filesystem is running out of available storage.

---

## 3.2 Run `df -h`

Execute:

```bash
df -h
```

Review the filesystems displayed by your system.

---

## 🔎 Important `df` Fields

### Filesystem

Identifies the filesystem or storage device.

### Size

Shows the total filesystem capacity.

### Used

Shows how much space is currently being used.

### Avail

Shows available space.

### Use%

Shows the percentage of filesystem space currently being used.

### Mounted on

Shows the directory where the filesystem is mounted.

---

## 3.3 Example

A simplified example might look like:

```text
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       100G   35G   61G  37% /
```

This indicates that the filesystem has approximately 100 GB of total capacity, with 35 GB used and 61 GB available.

---

# 🧪 Practical Lab

Complete the following tasks on your Linux system.

## Task 1 — Inspect the CPU

Run:

```bash
lscpu
```

Identify:

- CPU architecture.
- Number of CPUs.
- CPU vendor.
- CPU model.

---

## Task 2 — Inspect Memory

Run:

```bash
free -h
```

Identify:

- Total RAM.
- Used RAM.
- Free RAM.
- Available RAM.
- Total swap.
- Used swap.

---

## Task 3 — Inspect Disk Usage

Run:

```bash
df -h
```

Identify:

- Main filesystem.
- Total filesystem size.
- Used space.
- Available space.
- Usage percentage.
- Mount point.

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `lscpu` | Display CPU and processor information |
| `free` | Display memory and swap information |
| `free -h` | Display memory information in human-readable format |
| `df` | Display filesystem disk usage |
| `df -h` | Display disk usage in human-readable format |

---

# 🧠 Key Concepts

### CPU

The Central Processing Unit performs instructions and calculations required by the operating system and applications.

### CPU Architecture

Describes the architecture supported by the processor and operating system.

For example:

```text
x86_64
```

### RAM

Random Access Memory provides temporary working space for running programs and operating-system processes.

### Swap

Swap provides disk-based space that can be used when additional memory resources are needed.

### Filesystem

A filesystem organizes and manages data stored on a storage device.

### Mount Point

A mount point is a directory through which a filesystem becomes accessible.

---

# 🛡️ Security Perspective

Hardware information is useful when administering and securing Linux systems.

Knowing the available CPU, memory, and storage resources helps administrators:

- Detect unusual resource consumption.
- Troubleshoot system performance.
- Plan system capacity.
- Identify storage problems.
- Monitor systems running security tools.

For example, security monitoring applications may consume additional CPU, memory, and disk resources.

Regularly checking system resources can therefore support both **performance monitoring and security operations**.

---

# ⚠️ Best Practices

- Monitor disk space regularly.
- Investigate unexpectedly high resource usage.
- Keep sufficient free storage available.
- Understand the hardware resources available before deploying demanding services.
- Avoid assuming example hardware values match your own system.
- Use human-readable options such as `-h` when interpreting resource information.

---

# ❓ Questions

1. What does the `lscpu` command display?
2. What does `x86_64` represent?
3. What information does the `CPU(s)` field provide?
4. What is the purpose of the `free` command?
5. Why is `free -h` easier to read than `free`?
6. What is swap space?
7. What does the `df` command display?
8. What does the `Use%` field in `df -h` represent?
9. What is a filesystem mount point?
10. Why is monitoring disk usage important for Linux administrators?

---

# 🧩 Challenge

Without looking at the example outputs above:

1. Run `lscpu`.
2. Record your CPU architecture.
3. Record your number of available CPUs.
4. Run `free -h`.
5. Record your total and available memory.
6. Record your swap configuration.
7. Run `df -h`.
8. Identify the filesystem mounted at `/`.
9. Record its total, used, and available space.
10. Identify the filesystem with the highest usage percentage.

Then explain what your results tell you about the resources available on your Linux system.

---

# 📌 Summary

In this lab, you learned how to retrieve basic hardware and resource information from a Linux system.

You practiced:

- Using `lscpu` to inspect CPU information.
- Using `free -h` to inspect RAM and swap.
- Using `df -h` to inspect filesystem disk usage.
- Interpreting important fields from each command.
- Applying hardware information to system monitoring and troubleshooting.

These commands are foundational tools for Linux administration, system monitoring, and performance analysis.

---

# ✅ Lab Completion Checklist

- [ ] Ran `lscpu`.
- [ ] Identified CPU architecture.
- [ ] Identified the number of CPUs.
- [ ] Identified the CPU vendor.
- [ ] Ran `free -h`.
- [ ] Identified total and available RAM.
- [ ] Checked swap usage.
- [ ] Ran `df -h`.
- [ ] Identified the root filesystem.
- [ ] Checked disk usage percentage.
- [ ] Answered the review questions.
- [ ] Completed the challenge.

---

# 🚀 Next Lab

**Lab 24 — Disk Usage**

In the next lab, you will go deeper into Linux storage usage and learn how to examine disk-space consumption.
