# Lab 56 — Basic Cron Log Inspection

## 📌 Overview

Cron is commonly used to schedule recurring tasks on Linux systems.

System logs can provide information about scheduled jobs and help administrators troubleshoot automated tasks.

This lab introduces basic inspection of cron-related logs.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand cron logging
- Locate relevant system logs
- Search logs for cron-related entries
- Use `grep` to filter log information
- Investigate scheduled-task activity

---

## 📚 Prerequisites

You should have:

- Basic Linux command-line knowledge
- Basic understanding of cron
- Familiarity with `/var/log`
- Basic knowledge of `grep`

---

## 🧠 Cron and Logging

Cron executes scheduled tasks automatically.

Depending on the Linux distribution and logging configuration, cron-related events may appear in different locations.

Common examples include:

```text
/var/log/syslog
/var/log/cron
/var/log/messages
```

The exact location varies by distribution.

Systems using `systemd` may also provide relevant information through the journal.

---

## 📂 Inspect Log Files

Start by checking `/var/log`:

```bash
ls -lh /var/log
```

On systems using `/var/log/syslog`:

```bash
sudo grep -i cron /var/log/syslog
```

If a dedicated cron log exists:

```bash
sudo grep -i cron /var/log/cron
```

---

## 🔎 Search for Specific Entries

You can combine `grep` with `tail`:

```bash
sudo tail -n 50 /var/log/syslog | grep -i cron
```

---

## 🐧 systemd Journal

On systems using `systemd`, inspect the journal:

```bash
sudo journalctl
```

Search for cron-related entries:

```bash
sudo journalctl | grep -i cron
```

On some systems, the service may be named differently, such as `cron` or `crond`.

---

## 🧪 Practical Lab

### Task 1 — Inspect the log directory

```bash
ls -lh /var/log
```

### Task 2 — Identify possible cron logs

```bash
ls -lh /var/log | grep -i cron
```

### Task 3 — Search syslog if available

```bash
sudo grep -i cron /var/log/syslog
```

### Task 4 — Search the dedicated cron log if available

```bash
sudo grep -i cron /var/log/cron
```

### Task 5 — Inspect recent entries

```bash
sudo tail -n 50 /var/log/syslog | grep -i cron
```

---

## 🔎 Command Reference

| Command | Purpose |
|---|---|
| `ls -lh /var/log` | List log files |
| `grep -i cron` | Search for cron entries |
| `tail -n 50` | Display recent log lines |
| `journalctl` | View systemd journal |
| `journalctl \| grep -i cron` | Filter journal entries |

---

## 🛡️ Security Perspective

Cron logs can help administrators identify:

- Scheduled tasks
- Failed jobs
- Unexpected task execution
- Administrative activity
- Troubleshooting information

Unexpected scheduled tasks can deserve further investigation on systems where you have authorization to perform security analysis.

---

## ⚠️ Best Practices

- Respect system permissions.
- Do not modify logs during investigation.
- Preserve relevant evidence when troubleshooting.
- Remember that log locations differ between distributions.
- Use appropriate access controls when reviewing sensitive logs.

---

## 📝 Questions

1. What is cron?
2. Why are cron logs useful?
3. Where might cron-related events be stored?
4. What does `grep -i` do?
5. What is `journalctl`?
6. Why can unexpected scheduled tasks be important during security analysis?

---

## 📋 Lab Completion Checklist

- [ ] Inspect `/var/log`
- [ ] Search for cron logs
- [ ] Use `grep`
- [ ] Inspect recent log entries
- [ ] Understand systemd journal logging
- [ ] Understand cron log security relevance

---

## 📌 Summary

In this lab, you learned how to inspect logs associated with scheduled tasks.

Understanding cron logging is useful for troubleshooting automation and monitoring system activity.

---

## 🚀 Next Lab

**Lab 57 — Simple Log Rotation**
