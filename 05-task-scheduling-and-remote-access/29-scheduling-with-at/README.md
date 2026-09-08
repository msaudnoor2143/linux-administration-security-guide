# Lab 29 — Scheduling Tasks with `at`

> Learn how to schedule commands for one-time execution using the Linux `at` utility.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand one-time task scheduling.
- Understand the difference between `cron` and `at`.
- Schedule commands with `at`.
- View pending `at` jobs.
- Remove scheduled jobs.
- Work with relative and specific execution times.
- Apply one-time scheduling safely.

---

## 📚 Prerequisites

Before starting this lab, you should have:

- A Linux system.
- Terminal access.
- Basic command-line knowledge.
- Familiarity with shell commands.
- Completion of Lab 28 — Scheduling Tasks with Crontab.

---

# 1. Understanding `at`

The `at` utility is designed for **one-time scheduled tasks**.

Unlike cron, which is commonly used for recurring tasks, `at` schedules a command to run once at a specified time.

Examples of appropriate uses include:

- Running a maintenance command later.
- Creating a delayed report.
- Scheduling a one-time administrative task.
- Running a script at a specified time.

---

# 2. Checking Whether `at` Is Available

Check whether the command exists:

```bash
which at
```

You can also check:

```bash
at -V
```

If `at` is not installed, installation depends on your Linux distribution.

On Debian/Ubuntu-based systems:

```bash
sudo apt install at
```

---

# 3. Scheduling a One-Time Task

The basic syntax is:

```bash
at TIME
```

For example:

```bash
at 14:30
```

The `at` command then provides an interactive prompt where commands can be entered.

For a safe test, you can schedule:

```bash
date >> ~/at-test.log
```

Finish the job input with:

```text
Ctrl+D
```

---

# 4. Listing Scheduled Jobs

Use:

```bash
atq
```

This displays pending `at` jobs.

---

# 5. Removing a Scheduled Job

Each job receives a job number.

For example:

```text
5
```

Remove it with:

```bash
atrm 5
```

Replace `5` with the actual job number.

---

# 6. Using Relative Times

`at` can also understand relative time expressions.

For example:

```bash
at now + 5 minutes
```

You can then enter a safe test command:

```bash
date >> ~/at-test.log
```

Finish with:

```text
Ctrl+D
```

Check the scheduled job:

```bash
atq
```

---

# 7. Cron vs `at`

| Feature | Cron | `at` |
|---|---|---|
| Recurring tasks | Yes | No |
| One-time task | Not its primary purpose | Yes |
| Configuration | Crontab | `at` queue |
| Typical use | Repeated automation | Delayed one-time execution |

---

# 🧪 Practical Lab

## Task 1 — Check `at`

Run:

```bash
which at
```

---

## Task 2 — Schedule a Test

Run:

```bash
at now + 2 minutes
```

At the prompt, enter:

```bash
date >> ~/at-test.log
```

Then press:

```text
Ctrl+D
```

---

## Task 3 — View the Queue

Run:

```bash
atq
```

---

## Task 4 — Wait for Execution

After the scheduled time, check:

```bash
cat ~/at-test.log
```

---

## Task 5 — Cancel a Job

Schedule another test:

```bash
at now + 10 minutes
```

Enter:

```bash
date >> ~/at-cancel-test.log
```

Press:

```text
Ctrl+D
```

List the queue:

```bash
atq
```

Identify the job number and remove it:

```bash
atrm JOB_NUMBER
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `at TIME` | Schedule a one-time task |
| `atq` | List pending jobs |
| `atrm JOB_ID` | Remove a scheduled job |
| `which at` | Locate the `at` command |
| `date` | Display current date/time |

---

# 🧠 Key Concepts

### `at`

Schedules commands for one-time execution.

### `atq`

Displays pending scheduled jobs.

### `atrm`

Removes a scheduled job.

### Job ID

Each scheduled task receives an identifier that can be used to manage it.

---

# 🛡️ Security Perspective

Scheduled tasks execute automatically, so administrators should know what jobs exist on a system.

Security considerations include:

- Review scheduled jobs.
- Avoid unnecessary privileged tasks.
- Protect scripts used by scheduled jobs.
- Remove obsolete scheduled jobs.
- Investigate unexpected jobs.

---

# ⚠️ Best Practices

- Use a safe test command while learning.
- Verify jobs with `atq`.
- Cancel unnecessary jobs.
- Avoid scheduling destructive commands.
- Do not give unnecessary privileges to scheduled tasks.
- Keep automation scripts protected.

---

# 📝 Questions

1. What is the purpose of `at`?
2. How is `at` different from cron?
3. What does `atq` do?
4. What does `atrm` do?
5. What is a job ID?
6. Why should scheduled tasks be monitored?
7. When would you choose `at` instead of cron?

---

# 🧪 Challenge

Determine how you would schedule a task:

1. Five minutes from now.
2. At a specific time today.
3. For the next day.
4. Then identify and cancel the scheduled task.

Use only safe test commands.

---

# 🧹 Cleanup

Check for pending jobs:

```bash
atq
```

Remove any remaining test jobs:

```bash
atrm JOB_ID
```

Remove test files:

```bash
rm -f ~/at-test.log ~/at-cancel-test.log
```

---

# ✅ Lab Completion Checklist

- [ ] I understand one-time scheduling.
- [ ] I can use `at`.
- [ ] I can schedule a test task.
- [ ] I can list jobs with `atq`.
- [ ] I can remove jobs with `atrm`.
- [ ] I understand `at` versus cron.
- [ ] I understand scheduling security concerns.
- [ ] I completed the challenge.
- [ ] I cleaned up my test jobs.

---

## 🚀 Next Lab

**Lab 30 — SSH Basics**
