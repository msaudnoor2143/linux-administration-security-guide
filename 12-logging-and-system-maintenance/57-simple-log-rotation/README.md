# Lab 57 — Simple Log Rotation

## 📌 Overview

Log files can grow continuously as applications and services generate new events.

Log rotation helps control log size and prevents storage from being consumed unnecessarily.

This lab introduces the concept of log rotation and the `logrotate` utility.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand log rotation
- Understand why logs need maintenance
- Inspect `logrotate` configuration
- Understand basic rotation policies
- Perform safe testing with a dedicated test log

---

## 📚 Prerequisites

You should have:

- Basic Linux command-line knowledge
- Familiarity with files
- Basic understanding of system logs
- A Linux system with `logrotate`

---

## 🧠 Why Log Rotation Matters

Logs can grow over time.

Without appropriate maintenance, large log files can consume significant disk space.

Log rotation can:

- Rename old logs
- Create new log files
- Compress older logs
- Keep a defined number of historical files
- Help manage storage usage

---

## 🔎 Check logrotate

Check whether it is installed:

```bash
logrotate --version
```

View the main configuration:

```bash
cat /etc/logrotate.conf
```

List configuration files:

```bash
ls -lh /etc/logrotate.d/
```

---

## 🧪 Practical Lab

### Task 1 — Inspect configuration

```bash
cat /etc/logrotate.conf
```

### Task 2 — Inspect additional configurations

```bash
ls -lh /etc/logrotate.d/
```

### Task 3 — Create a test log

Create a temporary working directory:

```bash
mkdir -p ~/logrotate-lab
```

Create a test log:

```bash
echo "Test log entry" > ~/logrotate-lab/application.log
```

Add another entry:

```bash
echo "Another test entry" >> ~/logrotate-lab/application.log
```

View it:

```bash
cat ~/logrotate-lab/application.log
```

---

## ⚙️ Understanding a Rotation Policy

A basic policy may specify:

- Rotation frequency
- Number of historical files
- Compression
- Whether an empty log should be rotated
- File ownership and permissions

A typical configuration structure can look like:

```text
/path/to/log {
    daily
    rotate 7
    compress
    missingok
    notifempty
}
```

This is an example structure for understanding the configuration format.

---

## 🧪 Test Configuration Safely

When working with a real logrotate configuration, validate configuration behavior before applying changes.

A common debug option is:

```bash
sudo logrotate -d /etc/logrotate.conf
```

The `-d` option performs a debug-style inspection without carrying out normal rotation changes.

---

## 🛡️ Security Perspective

Log rotation supports security monitoring by ensuring that useful historical logs remain available while storage is controlled.

However, security logs should be retained according to organizational requirements.

Do not rotate, delete, or overwrite logs simply to hide activity.

---

## ⚠️ Best Practices

- Keep appropriate retention periods.
- Protect log permissions.
- Compress older logs where appropriate.
- Test configuration before deployment.
- Never use log rotation as a way to conceal activity.
- Ensure security logs are retained according to policy.

---

## 📝 Questions

1. Why is log rotation necessary?
2. What is `logrotate`?
3. Where is the main logrotate configuration?
4. What is `/etc/logrotate.d/` used for?
5. Why is log retention important for security?
6. What does a debug operation help with?

---

## 🧹 Cleanup

Remove the test directory:

```bash
rm -rf ~/logrotate-lab
```

---

## 📋 Lab Completion Checklist

- [ ] Check `logrotate`
- [ ] Inspect `/etc/logrotate.conf`
- [ ] Inspect `/etc/logrotate.d/`
- [ ] Create a test log
- [ ] Understand rotation policies
- [ ] Perform a safe configuration inspection
- [ ] Understand security log retention

---

## 📌 Summary

In this lab, you learned the purpose of log rotation and how Linux commonly manages growing log files.

Proper log rotation is important for storage management, troubleshooting, monitoring, and security operations.

---

## 🚀 Next Lab

**Lab 58 — Setting Up Aliases in .bashrc**
