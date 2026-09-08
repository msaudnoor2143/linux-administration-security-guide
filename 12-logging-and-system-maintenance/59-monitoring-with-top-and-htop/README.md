# Lab 59 — Monitoring with top and htop

## 📌 Overview

System monitoring is an essential part of Linux administration.

The `top` and `htop` utilities provide interactive views of running processes and system resource usage.

This lab introduces both tools and their use for basic system monitoring.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Monitor running processes
- Observe CPU usage
- Observe memory usage
- Understand process information
- Use `top`
- Use `htop`
- Identify resource-intensive processes

---

## 📚 Prerequisites

You should have:

- Basic Linux command-line knowledge
- Basic understanding of processes
- Access to a Linux terminal

---

## 🧠 System Monitoring

Linux systems run many processes simultaneously.

Administrators may need to monitor:

- CPU usage
- Memory usage
- Running processes
- Process IDs
- System load

Two common interactive tools are:

```text
top
htop
```

---

## 📊 Using top

Run:

```bash
top
```

The interface updates continuously.

It provides information about:

- Processes
- Process IDs
- CPU usage
- Memory usage
- Process states
- System load

Exit `top` by pressing:

```text
q
```

---

## 🔎 Understanding Process Information

Important fields commonly shown by `top` include:

- PID — Process ID
- USER — Process owner
- PR — Priority
- NI — Nice value
- VIRT — Virtual memory
- RES — Resident memory
- %CPU — CPU usage
- %MEM — Memory usage
- COMMAND — Process name

---

## 🖥️ Using htop

Check whether `htop` is installed:

```bash
htop --version
```

If it is not installed on an Ubuntu/Debian system:

```bash
sudo apt update
sudo apt install htop
```

Run:

```bash
htop
```

Exit with:

```text
F10
```

or:

```text
q
```

depending on the environment.

---

## 🧪 Practical Lab

### Task 1 — Run top

```bash
top
```

Observe:

- CPU usage
- Memory usage
- Load average
- Running processes

Exit using:

```text
q
```

### Task 2 — Run htop

```bash
htop
```

Explore the process list.

Exit when finished.

### Task 3 — Identify resource usage

Look for processes with relatively high:

```text
%CPU
%MEM
```

Do not terminate a process simply because it consumes resources. First understand what the process does.

---

## 🔎 Useful Commands

Display running processes:

```bash
ps aux
```

Display system uptime:

```bash
uptime
```

Display memory usage:

```bash
free -h
```

Display filesystem usage:

```bash
df -h
```

---

## 🧠 Key Concepts

### Process ID

Every running process has a PID.

### CPU Usage

Shows how much processor capacity a process is consuming.

### Memory Usage

Shows how much memory a process is using.

### Load Average

Provides an indication of system workload over time.

---

## 🛡️ Security Perspective

Process monitoring can help administrators investigate unusual system behavior.

Examples include:

- Unexpected processes
- Unusual resource consumption
- Unknown services
- Processes running under unexpected users

Process monitoring is only one part of system investigation and should be combined with logs and other administrative information.

---

## ⚠️ Best Practices

- Do not terminate processes without understanding their purpose.
- Avoid changing process priorities without a reason.
- Compare unusual activity against expected system behavior.
- Investigate persistent high resource usage.
- Use administrative privileges only when necessary.

---

## 📝 Questions

1. What is `top` used for?
2. What is `htop`?
3. What does PID mean?
4. What does `%CPU` represent?
5. What does `%MEM` represent?
6. Why can process monitoring be useful for security?
7. Why should you avoid terminating an unfamiliar process immediately?

---

## 📋 Lab Completion Checklist

- [ ] Run `top`
- [ ] Understand basic process information
- [ ] Observe CPU usage
- [ ] Observe memory usage
- [ ] Run `htop`
- [ ] Understand PIDs
- [ ] Understand monitoring from a security perspective

---

## 📌 Summary

In this lab, you learned how to monitor Linux processes and system resources using `top` and `htop`.

These tools are important for troubleshooting, performance monitoring, administration, and security investigations.

---

## 🚀 Next Lab

**Lab 60 — Introduction to SELinux**
