# Section 05 — Task Scheduling & Remote Access

This section introduces automated task scheduling and remote administration in Linux.

The labs cover cron, `at`, SSH, SCP, and SFTP.

---

## 🎯 Section Objectives

By completing this section, you will:

- Schedule recurring tasks using cron.
- Schedule one-time tasks using `at`.
- Understand SSH.
- Connect to remote Linux systems.
- Transfer files securely.
- Understand the difference between SCP and SFTP.

---

## 📚 Prerequisites

Before starting this section, you should have:

- Basic Linux command-line knowledge.
- Basic understanding of users and permissions.
- Access to a Linux system.
- Basic networking knowledge.

---

## 🧪 Labs in This Section

| Lab | Topic |
|---|---|
| Lab 28 | Scheduling Tasks with Crontab |
| Lab 29 | Scheduling Tasks with at |
| Lab 30 | SSH Basics |
| Lab 31 | Using SCP and SFTP |

---

## 🧠 What You Will Learn

### Cron

Cron allows recurring tasks to be scheduled automatically.

Common uses include:

- Backups.
- Maintenance tasks.
- Automated scripts.
- Periodic monitoring.

---

### at

The `at` command is designed for one-time scheduled tasks.

This makes it useful when a task should execute once at a specified time.

---

### SSH

Secure Shell provides encrypted remote access to Linux systems.

You will learn the fundamentals of:

- SSH connections.
- Remote administration.
- Authentication.
- Remote command execution.

---

### SCP and SFTP

You will learn how to transfer files between systems.

SCP provides secure file copying, while SFTP provides an interactive file-transfer environment.

---

## 🛡️ Security Perspective

Remote access must be properly secured.

Important considerations include:

- Strong authentication.
- Restricting unnecessary remote access.
- Protecting SSH credentials.
- Monitoring remote access.
- Using secure file-transfer methods.

---

## ⚠️ Best Practices

- Never share SSH credentials.
- Avoid unnecessary remote services.
- Verify the destination before transferring files.
- Review scheduled tasks regularly.
- Remove obsolete cron jobs.
- Protect private keys appropriately.

---

## 📝 Section Questions

1. What is cron?
2. What is the difference between cron and `at`?
3. What is SSH?
4. Why is SSH preferred over insecure remote-login methods?
5. What is SCP used for?
6. How does SFTP differ from SCP?
7. Why should scheduled tasks be reviewed?

---

## ✅ Section Completion Checklist

- [ ] Create cron jobs.
- [ ] Schedule one-time tasks.
- [ ] Understand SSH.
- [ ] Connect to remote systems.
- [ ] Transfer files securely.
- [ ] Understand SCP and SFTP.
- [ ] Apply remote-access security principles.

---

## 🚀 Next Section

Continue to:

**Section 06 — Text Processing & Search**
