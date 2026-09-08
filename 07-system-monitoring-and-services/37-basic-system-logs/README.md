# Lab 37 — Basic System Logs

> Learn how to navigate Linux system logs, inspect recent system messages, search logs for important information, and monitor log files in real time.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand the purpose of Linux system logs
- Navigate the `/var/log` directory
- Identify common system log files
- Inspect recent log entries
- Search logs using `grep`
- View logs using `less`
- Monitor log files in real time using `tail -f`
- Understand the importance of logs for troubleshooting and security monitoring

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Access to a Linux system
- A terminal
- Basic knowledge of Linux filesystem navigation
- Basic knowledge of commands such as `cd`, `ls`, and `grep`
- `sudo` privileges for administrative log access

> **Note:** The exact log files available depend on the Linux distribution and logging configuration. Ubuntu commonly uses `/var/log/syslog`, while some distributions use `/var/log/messages`.

---

# 1. Understanding Linux System Logs

Linux systems continuously generate log information about:

- System activity
- Applications
- Services
- Authentication events
- Kernel messages
- Networking
- Hardware
- Errors and warnings
- Security-related events

These logs are extremely useful when troubleshooting problems or investigating unusual system behavior.

A common location for traditional Linux log files is:

```text
/var/log
```

---

# 2. Navigating to `/var/log`

Move into the system log directory:

```bash
cd /var/log
```

Verify your location:

```bash
pwd
```

Expected output:

```text
/var/log
```

Now list the available log files:

```bash
ls -lh
```

The `-l` option provides detailed information, while `-h` displays file sizes in a human-readable format.

---

## 2.1 Inspecting the Directory

You can also display the directory contents with:

```bash
ls -la
```

This includes hidden entries.

You may see files and directories such as:

```text
syslog
auth.log
kern.log
dpkg.log
journal/
```

The exact contents depend on your Linux distribution.

---

# 3. Identifying the Main System Log

Some Linux systems use:

```text
/var/log/syslog
```

while others may use:

```text
/var/log/messages
```

Check which files exist:

```bash
ls -l /var/log/syslog /var/log/messages
```

If one of them does not exist, that is not necessarily an error. It may simply mean your distribution uses a different logging configuration.

---

# 4. Viewing Log Files

Large log files should generally be viewed with `less` rather than opening them in an editor.

For systems using `syslog`:

```bash
less /var/log/syslog
```

For systems using `messages`:

```bash
less /var/log/messages
```

Inside `less`:

- Use the arrow keys to move
- Use `Page Up` and `Page Down`
- Press `/` to search
- Press `q` to exit

---

## 4.1 Viewing the Beginning of a Log

You can use:

```bash
head /var/log/syslog
```

This displays the beginning of the file.

---

## 4.2 Viewing the Most Recent Entries

Use:

```bash
tail /var/log/syslog
```

This displays the most recent lines.

You can request more lines:

```bash
tail -n 20 /var/log/syslog
```

---

# 5. Searching Logs with `grep`

Log files can contain thousands of entries, so searching is an important administrative skill.

For example, search for the word `error`:

```bash
grep "error" /var/log/syslog
```

Linux searches are normally case-sensitive.

To search without considering uppercase/lowercase differences:

```bash
grep -i "error" /var/log/syslog
```

---

## 5.1 Searching for Warnings

You can search for:

```bash
grep -i "warning" /var/log/syslog
```

---

## 5.2 Counting Matching Entries

Use:

```bash
grep -ic "error" /var/log/syslog
```

This gives the number of matching lines.

---

# 6. Monitoring Logs in Real Time

One of the most useful techniques for administrators and security analysts is watching a log file as new entries appear.

Use:

```bash
tail -f /var/log/syslog
```

The `-f` option means **follow**.

The command remains active and displays new log entries as they are written.

To stop the command:

```text
Ctrl + C
```

---

## 6.1 Monitoring More Lines

You can combine `-n` with `-f`:

```bash
tail -n 20 -f /var/log/syslog
```

This initially displays the last 20 lines and then continues following new entries.

---

# 🧪 Practical Lab

Perform these exercises on your Linux system.

---

## Task 1 — Navigate to the Log Directory

Run:

```bash
cd /var/log
```

Verify:

```bash
pwd
```

Then inspect the directory:

```bash
ls -lh
```

### Expected result

You should see a collection of log files and possibly log directories.

---

## Task 2 — Identify the Main System Log

Run:

```bash
ls -l /var/log/syslog /var/log/messages
```

Determine which file exists on your system.

If `syslog` exists, use:

```bash
less /var/log/syslog
```

If `messages` exists, use:

```bash
less /var/log/messages
```

Press:

```text
q
```

to exit.

---

## Task 3 — Search for Errors

If your system uses `syslog`:

```bash
grep -i "error" /var/log/syslog
```

If your system uses `messages`:

```bash
grep -i "error" /var/log/messages
```

Observe the matching entries.

---

## Task 4 — Monitor the Log in Real Time

For a system using `syslog`:

```bash
tail -f /var/log/syslog
```

Or:

```bash
tail -f /var/log/messages
```

Observe the output for a short period.

Stop monitoring with:

```text
Ctrl + C
```

---

## Task 5 — Combine `tail` and `grep`

You can filter a live log stream:

```bash
tail -f /var/log/syslog | grep -i "error"
```

This allows you to watch only new entries containing the selected keyword.

Stop with:

```text
Ctrl + C
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `cd /var/log` | Navigate to the log directory |
| `ls -lh` | List log files with human-readable sizes |
| `ls -la` | Display detailed directory contents |
| `pwd` | Show current directory |
| `less file` | Read a file interactively |
| `head file` | Display the beginning of a file |
| `tail file` | Display the end of a file |
| `tail -n 20 file` | Display the last 20 lines |
| `tail -f file` | Follow a log in real time |
| `grep "text" file` | Search for text |
| `grep -i "text" file` | Case-insensitive search |
| `grep -c "text" file` | Count matching lines |

---

# 🧠 Key Concepts

## `/var/log`

A common location for traditional Linux log files.

---

## `syslog`

A general-purpose system log commonly found on Debian/Ubuntu-based systems.

---

## `messages`

A general system log used by some Linux distributions.

---

## `grep`

A command-line search utility that allows administrators to find relevant information inside large text files.

---

## `tail -f`

Displays the end of a file and continues showing new data as it is added.

This makes it particularly useful for real-time monitoring.

---

# 🛡️ Security Perspective

Logs are an important source of security information.

Security professionals may inspect logs for:

- Authentication activity
- Failed login attempts
- Service failures
- Unexpected errors
- System changes
- Suspicious activity
- Network-related events

For example:

```bash
grep -i "failed" /var/log/auth.log
```

can help locate authentication failures on systems that maintain an `auth.log`.

> **Important:** The available log files and their contents vary between distributions.

A security analyst should understand where logs are stored and how to efficiently search them.

---

# ⚠️ Best Practices

### 1. Avoid modifying log files unnecessarily

Use read-oriented tools such as:

```bash
less
```

```bash
head
```

```bash
tail
```

and:

```bash
grep
```

when investigating logs.

### 2. Do not assume every Linux system uses the same log file

Check the actual files available on your system.

### 3. Protect sensitive log information

Logs may contain information about users, authentication activity, services, and system configuration.

### 4. Use filters when logs are large

Instead of reading thousands of lines manually:

```bash
grep -i "error" /var/log/syslog
```

can quickly narrow down relevant information.

---

# 📝 Questions

1. What is the purpose of Linux system logs?
2. What is the `/var/log` directory used for?
3. What is the difference between `head` and `tail`?
4. What does `tail -f` do?
5. How can `grep` help during troubleshooting?
6. Why might `/var/log/messages` not exist on your system?
7. Why are logs important for cybersecurity?
8. How can you monitor a log file continuously?
9. How do you stop `tail -f`?
10. Why should log files be handled carefully?

---

# 🚀 Challenge

Try monitoring a log file and filtering it for a keyword.

Example:

```bash
tail -f /var/log/syslog | grep -i "warning"
```

Then identify:

- Which log file your system uses
- Which type of events appear
- Which keywords are useful for troubleshooting

---

# ✅ Lab Completion Checklist

- [ ] I understand the purpose of Linux system logs
- [ ] I can navigate to `/var/log`
- [ ] I can list available log files
- [ ] I can identify the main system log on my distribution
- [ ] I can read logs using `less`
- [ ] I can search logs using `grep`
- [ ] I understand `tail`
- [ ] I can monitor a log using `tail -f`
- [ ] I understand the security importance of system logs

---

## Summary

In this lab, you explored Linux system logs and the `/var/log` directory. You learned how to inspect log files, search for specific events, and monitor logs in real time using `tail -f`.

These skills form an important foundation for Linux administration, troubleshooting, and security monitoring.

---

## 🚀 Next Lab

**Lab 38 — Systemd Services Overview**
