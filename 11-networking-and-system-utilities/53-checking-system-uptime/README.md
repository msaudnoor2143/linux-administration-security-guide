# Lab 53 — Checking System Uptime

## 📌 Overview

System uptime indicates how long a Linux system has been running since its most recent boot.

Monitoring uptime can help administrators understand system availability, maintenance events, and recent reboots.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Check system uptime
- Understand uptime information
- Use the `uptime` command
- View system boot information
- Identify recent system restarts

---

## 📚 Prerequisites

You should have:

- Basic Linux command-line knowledge
- Access to a Linux terminal

---

## 🧠 Understanding Uptime

System uptime represents the amount of time that has passed since the system was started.

A change in uptime can indicate:

- Reboots
- Maintenance
- System crashes
- Power interruptions

---

## ⏱️ Using the uptime Command

Run:

```bash
uptime
```

The output typically includes:

- Current time
- How long the system has been running
- Number of logged-in users
- Load average

---

## 📊 Detailed Uptime Information

Use:

```bash
uptime -p
```

This provides a more readable uptime format.

---

## 🕐 System Boot Time

Use:

```bash
uptime -s
```

This displays the time when the system was booted.

You can also use:

```bash
who -b
```

to view the last system boot time.

---

## 🧪 Practical Lab

### Task 1 — Display uptime

```bash
uptime
```

### Task 2 — Display readable uptime

```bash
uptime -p
```

### Task 3 — Display boot time

```bash
uptime -s
```

### Task 4 — Check the last boot

```bash
who -b
```

### Task 5 — Compare the results

Record:

- Current uptime
- Boot time
- Number of logged-in users
- Load average

---

## 🔎 Command Reference

| Command | Purpose |
|---|---|
| `uptime` | Display uptime and load information |
| `uptime -p` | Display readable uptime |
| `uptime -s` | Display system start time |
| `who -b` | Display last boot time |

---

## 🧠 Key Concepts

- Uptime measures time since boot.
- Boot time identifies when the current system session started.
- Load average provides information about system workload.
- Unexpected reboot times can be useful during troubleshooting.

---

## 🛡️ Security Perspective

Uptime can be useful during security investigations.

Administrators may compare:

- System boot time
- Maintenance windows
- Incident timelines
- Unexpected restarts

Uptime alone does not establish why a system restarted, but it provides useful timeline information.

---

## 📝 Questions

1. What does system uptime represent?
2. Which command displays uptime?
3. What does `uptime -p` provide?
4. How can you identify the system boot time?
5. Why might uptime be useful during troubleshooting?

---

## 📋 Lab Completion Checklist

- [ ] Run `uptime`
- [ ] Use `uptime -p`
- [ ] Check boot time
- [ ] Use `who -b`
- [ ] Understand load average
- [ ] Understand the security relevance of uptime

---

## 📌 Summary

In this lab, you learned how to inspect Linux system uptime and boot information.

These simple commands provide useful information for administration, troubleshooting, monitoring, and security investigations.

---

## 🚀 Next Lab

**Lab 54 — Using df and du**
