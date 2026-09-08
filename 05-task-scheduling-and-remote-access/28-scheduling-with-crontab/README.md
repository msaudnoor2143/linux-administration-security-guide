# Lab 28 — Scheduling Tasks with Crontab

> Learn how Linux uses `cron` and `crontab` to automatically execute recurring tasks at scheduled times.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand cron-based task scheduling.
- Understand the purpose of `crontab`.
- View existing cron jobs.
- Create scheduled tasks.
- Understand cron timing fields.
- Schedule recurring commands.
- Remove scheduled jobs.
- Troubleshoot basic cron jobs.
- Apply cron safely in administrative environments.

---

## 📚 Prerequisites

Before starting this lab, you should have:

- A Linux system.
- Terminal access.
- Basic Linux command-line knowledge.
- Familiarity with shell commands.
- Basic understanding of files and directories.
- Completion of previous Linux administration labs.

---

# 1. Understanding Cron

Linux provides scheduling mechanisms that allow commands and scripts to run automatically.

One of the most commonly used mechanisms is **cron**.

Cron can be used for recurring tasks such as:

- System maintenance
- Backups
- Log management
- Monitoring
- Report generation
- Automated scripts

A scheduled cron entry is called a **cron job**.

---

# 2. Understanding Crontab

The `crontab` command is used to manage scheduled jobs for a user.

View the current user's cron jobs:

```bash
crontab -l
```

If no jobs have been configured, you may see a message indicating that the user's crontab is empty.

---

# 3. Understanding the Cron Format

A standard cron entry contains five scheduling fields followed by the command:

```text
MINUTE HOUR DAY-OF-MONTH MONTH DAY-OF-WEEK COMMAND
```

For example:

```text
30 14 * * * command
```

The fields represent:

| Field | Meaning |
|---|---|
| Minute | 0–59 |
| Hour | 0–23 |
| Day of month | 1–31 |
| Month | 1–12 |
| Day of week | 0–7 |
| Command | Command to execute |

---

# 4. Cron Special Characters

Several characters are commonly used in cron schedules.

### `*`

Means every possible value.

Example:

```text
* * * * *
```

This represents every minute.

### `,`

Specifies multiple values.

Example:

```text
1,15,30
```

### `-`

Specifies a range.

Example:

```text
1-5
```

### `/`

Specifies an interval.

Example:

```text
*/10
```

This represents every ten units of the relevant field.

---

# 5. Creating a Cron Job

Open your user's crontab:

```bash
crontab -e
```

For this lab, create a simple scheduled task.

Example:

```text
*/5 * * * * date >> ~/cron-test.log
```

This schedules the `date` command to append the current date and time to:

```text
~/cron-test.log
```

every five minutes.

---

# 6. Verify the Cron Job

List your cron jobs:

```bash
crontab -l
```

You should see the entry you created.

After the scheduled time has passed, inspect the output:

```bash
cat ~/cron-test.log
```

---

# 7. Removing a Cron Job

Open the crontab:

```bash
crontab -e
```

Remove the test entry and save the file.

You can also remove all cron jobs belonging to the current user with:

```bash
crontab -r
```

> ⚠️ Be extremely careful with `crontab -r`. It removes the user's entire crontab.

---

# 🧪 Practical Lab

## Task 1 — Inspect Your Crontab

Run:

```bash
crontab -l
```

Record whether you already have scheduled jobs.

---

## Task 2 — Create a Test Directory

Create a safe practice directory:

```bash
mkdir -p ~/cron-lab
```

---

## Task 3 — Create a Cron Job

Open your crontab:

```bash
crontab -e
```

Add:

```text
*/5 * * * * date >> ~/cron-lab/timestamps.log
```

Save the crontab.

---

## Task 4 — Verify

Check the scheduled job:

```bash
crontab -l
```

After a few minutes:

```bash
cat ~/cron-lab/timestamps.log
```

---

## Task 5 — Schedule a Daily Task

A daily cron schedule can be represented by:

```text
0 2 * * * command
```

This represents a command scheduled for 02:00 every day.

Do not use a real destructive command for testing.

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `crontab -l` | List current user's cron jobs |
| `crontab -e` | Edit the current user's crontab |
| `crontab -r` | Remove the current user's crontab |
| `date` | Display date and time |
| `cat` | Display file contents |

---

# 🧠 Key Concepts

### Cron

A Linux service used to execute scheduled tasks.

### Cron Job

A command or script configured to run automatically.

### Crontab

The configuration containing a user's scheduled cron jobs.

### Scheduling Fields

Cron uses five timing fields:

```text
Minute Hour Day Month Weekday
```

---

# 🛡️ Security Perspective

Automated jobs are powerful because they can execute commands without manual intervention.

Security teams should therefore:

- Review scheduled tasks.
- Monitor unexpected cron jobs.
- Protect scripts executed by cron.
- Avoid unnecessary privileges.
- Use absolute paths where appropriate.
- Ensure scheduled scripts are not writable by unauthorized users.

Unexpected cron entries can also be an indicator that a system needs investigation.

---

# ⚠️ Best Practices

- Test cron jobs in a dedicated directory.
- Avoid destructive commands while learning.
- Always verify your crontab before modifying it.
- Be careful with `crontab -r`.
- Keep scheduled scripts protected.
- Use appropriate privileges.
- Log important automated operations.

---

# 📝 Questions

1. What is cron?
2. What is a cron job?
3. What does `crontab -l` do?
4. What does `crontab -e` do?
5. What are the five scheduling fields?
6. What does `*` mean in a cron expression?
7. What does `*/5` represent?
8. Why should cron scripts be protected?
9. Why can unexpected cron jobs be a security concern?

---

# 🧪 Challenge

Create a cron schedule that represents:

1. Every minute
2. Every hour
3. Every day at midnight
4. Every Sunday
5. Every 15 minutes

Write the five corresponding cron expressions without executing destructive commands.

---

# 🧹 Cleanup

Remove the test cron job:

```bash
crontab -e
```

Then remove the practice files:

```bash
rm -rf ~/cron-lab
```

---

# ✅ Lab Completion Checklist

- [ ] I understand cron.
- [ ] I understand crontab.
- [ ] I can list cron jobs.
- [ ] I can create a cron job.
- [ ] I understand the five scheduling fields.
- [ ] I can interpret common cron expressions.
- [ ] I can remove a cron job.
- [ ] I understand cron security risks.
- [ ] I completed the challenge.
- [ ] I cleaned up my test files.

---

## 🚀 Next Lab

**Lab 29 — Scheduling Tasks with `at`**
