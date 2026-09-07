# Lab 15 — Job Control Basics

> Learn how to control running jobs by suspending, resuming, and moving processes between the foreground and background.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand job control in Linux
- Start a long-running process
- Suspend a foreground process using `Ctrl+Z`
- Resume a suspended process in the background using `bg`
- View active jobs using `jobs`
- Bring a background job back to the foreground using `fg`
- Understand the difference between foreground and background jobs
- Improve multitasking skills in the Linux terminal

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Access to a Linux system
- A terminal
- Basic knowledge of Linux commands
- Basic understanding of processes
- Completion of **Lab 14 — Basic Process Management**

> **Note:** This lab can be completed without root privileges.

---

# 1. Understanding Job Control

**Job control** is a feature provided by Unix/Linux shells that allows users to manage processes running from the terminal.

It allows you to:

- Stop a running foreground job
- Resume a stopped job
- Run jobs in the background
- Bring background jobs back to the foreground
- Monitor jobs associated with the current shell

This is especially useful when working with commands that take a long time to complete.

---

# 2. Foreground vs Background Jobs

## Foreground

A foreground process occupies the terminal while it is running.

For example:

```bash
sleep 100
```

The terminal waits for the `sleep` command to finish.

You normally cannot enter another command in that terminal until the foreground process finishes or is suspended.

---

## Background

A background process runs without blocking the terminal.

For example:

```bash
sleep 100 &
```

The `&` tells the shell to start the command as a background job.

You can continue entering commands while the process runs.

---

# 3. The `sleep` Command

The `sleep` command pauses execution for a specified amount of time.

Basic syntax:

```bash
sleep NUMBER
```

For example:

```bash
sleep 100
```

This pauses execution for 100 seconds.

You can also start it directly in the background:

```bash
sleep 100 &
```

The shell will return control of the terminal to you.

---

# 4. Suspending a Foreground Process with `Ctrl+Z`

When a command is running in the foreground, you can suspend it using:

```text
Ctrl+Z
```

For example:

```bash
sleep 100
```

While the command is running, press:

```text
Ctrl+Z
```

The shell will suspend the process and report a job number.

You may see output similar to:

```text
[1]+  Stopped                 sleep 100
```

The exact job number can be different on your system.

### What happened?

`Ctrl+Z` sends a job-control signal that stops the currently running foreground job.

The job is not necessarily terminated.

It is placed into a **stopped state** and can later be resumed.

---

# 5. Viewing Jobs with `jobs`

The `jobs` command displays jobs managed by the current shell.

Run:

```bash
jobs
```

You may see:

```text
[1]+  Stopped                 sleep 100
```

After resuming the job in the background, you may see:

```text
[1]+  Running                 sleep 100 &
```

The number inside the brackets is the **job ID**.

For example:

```text
[1]
```

means the job ID is `1`.

---

# 6. Resuming a Job in the Background

A stopped job can be resumed in the background with:

```bash
bg
```

For example:

```bash
sleep 100
```

Press:

```text
Ctrl+Z
```

Then run:

```bash
bg
```

The shell resumes the suspended job in the background.

Verify its status:

```bash
jobs
```

You should see something similar to:

```text
[1]+  Running                 sleep 100 &
```

The terminal is now available for other commands.

---

# 7. Bringing a Job to the Foreground

The `fg` command brings a background or stopped job back into the foreground.

First check the job number:

```bash
jobs
```

Example:

```text
[1]+  Running                 sleep 100 &
```

The job ID is `1`.

Bring it to the foreground:

```bash
fg %1
```

The `%1` refers to job ID 1.

If your job has another ID, replace `1` with that number.

For example:

```bash
fg %2
```

would bring job 2 to the foreground.

---

# 8. Understanding `bg` and `fg`

The two commands perform opposite job-control operations.

### `bg`

Resumes a stopped job in the background:

```bash
bg
```

### `fg`

Brings a job into the foreground:

```bash
fg %1
```

The workflow can therefore look like:

```text
Foreground
    │
    │ Ctrl+Z
    ▼
Stopped
    │
    │ bg
    ▼
Background
    │
    │ fg %1
    ▼
Foreground
```

---

# 🧪 Practical Lab

Perform the following exercise in your terminal.

## Task 1 — Start a Long-Running Process

Run:

```bash
sleep 100
```

The terminal will remain occupied while the command is running.

The `sleep` command is intentionally being used here as a safe test process.

---

## Task 2 — Suspend the Process

While `sleep 100` is running, press:

```text
Ctrl+Z
```

You should receive output similar to:

```text
[1]+  Stopped                 sleep 100
```

The job number may be different.

---

## Task 3 — Check the Job

Run:

```bash
jobs
```

Confirm that the `sleep` job appears as stopped.

Example:

```text
[1]+  Stopped                 sleep 100
```

---

## Task 4 — Resume the Job in the Background

Run:

```bash
bg
```

Then check:

```bash
jobs
```

You should see something similar to:

```text
[1]+  Running                 sleep 100 &
```

The terminal is now available for other commands.

---

## Task 5 — Bring the Job Back to the Foreground

Check the job number:

```bash
jobs
```

If the job number is `1`, run:

```bash
fg %1
```

The job is now running in the foreground.

Because `sleep` does not require interaction, the terminal will remain occupied until the remaining sleep time expires.

---

## Task 6 — Practice Starting a Background Job Directly

Start another test job:

```bash
sleep 60 &
```

The shell should immediately return control to you.

Check the jobs:

```bash
jobs
```

You may see:

```text
[2]+  Running                 sleep 60 &
```

The exact job number may differ.

---

# 🔎 Command Reference

| Command / Key | Purpose |
|---|---|
| `sleep 100` | Run a process that waits for 100 seconds |
| `sleep 100 &` | Start `sleep` as a background job |
| `Ctrl+Z` | Suspend the current foreground job |
| `jobs` | List jobs managed by the current shell |
| `bg` | Resume a stopped job in the background |
| `fg %1` | Bring job 1 to the foreground |
| `%1` | Refers to job ID 1 |

---

# 🧠 Key Concepts

## Job Control

Job control allows the shell to manage processes started from the terminal.

It provides mechanisms for:

- Suspending jobs
- Resuming jobs
- Running jobs in the background
- Bringing jobs into the foreground

---

## Job ID

A job ID is assigned by the shell.

Example:

```text
[1]+  Running    sleep 100 &
```

Here:

```text
1
```

is the job ID.

It can be referenced using:

```bash
%1
```

---

## Foreground Job

A foreground job occupies the terminal.

Example:

```bash
sleep 100
```

---

## Background Job

A background job allows the terminal to remain available.

Example:

```bash
sleep 100 &
```

---

## `Ctrl+Z`

`Ctrl+Z` suspends the current foreground job.

It does not normally terminate the job.

---

## `bg`

The `bg` command resumes a stopped job in the background.

```bash
bg
```

---

## `fg`

The `fg` command brings a job into the foreground.

```bash
fg %1
```

---

# 🛡️ Security & Administration Perspective

Job control is an important Linux administration skill.

System administrators frequently work with:

- Long-running commands
- Maintenance scripts
- Monitoring tools
- Administrative tasks
- Log-processing commands
- Troubleshooting operations

Understanding foreground and background jobs helps administrators manage terminal sessions efficiently.

It also helps when troubleshooting processes because you can suspend or resume your own jobs without immediately terminating them.

---

# ⚠️ Best Practices

### 1. Practice with safe commands

Use simple commands such as:

```bash
sleep 100
```

when learning job control.

### 2. Understand the job number

Always check:

```bash
jobs
```

before using:

```bash
fg %1
```

or another job-specific command.

### 3. Remember that job IDs belong to the shell

A job ID such as:

```text
%1
```

refers to a job managed by the current shell session.

It is different from a system-wide process ID (PID).

### 4. Do not confuse job IDs with PIDs

Job ID:

```text
%1
```

PID:

```text
1234
```

They are different identifiers used for different purposes.

---

# 📝 Questions

1. What is job control in Linux?
2. What is the difference between a foreground and background job?
3. What does `Ctrl+Z` do?
4. What does the `jobs` command display?
5. What does the `bg` command do?
6. What does the `fg` command do?
7. What does `%1` represent in `fg %1`?
8. Why is `sleep` useful for practicing job control?
9. What is the difference between a job ID and a PID?
10. Why can background jobs be useful when working from a terminal?

---

# 🧩 Challenge

Complete the following sequence without closing your terminal:

### Step 1

Start:

```bash
sleep 120
```

### Step 2

Suspend it:

```text
Ctrl+Z
```

### Step 3

Check the job:

```bash
jobs
```

### Step 4

Resume it in the background:

```bash
bg
```

### Step 5

Verify:

```bash
jobs
```

### Step 6

Bring it back to the foreground using its actual job ID:

```bash
fg %JOB_ID
```

Replace `JOB_ID` with the number shown by `jobs`.

### Step 7

Wait for the command to finish.

---

# 🧹 Cleanup

The `sleep` commands used in this lab automatically finish after their specified time.

If you want to stop a `sleep` job that you started yourself, you can bring it to the foreground and allow it to finish, or manage your own test job appropriately.

Check for remaining jobs with:

```bash
jobs
```

---

# 📌 Summary

In this lab, you learned the fundamentals of Linux job control.

You practiced:

- Starting a long-running process
- Suspending a foreground process with `Ctrl+Z`
- Listing jobs with `jobs`
- Resuming jobs with `bg`
- Bringing jobs back to the foreground with `fg`
- Understanding job IDs
- Distinguishing job IDs from process IDs
- Working with foreground and background processes

These skills are important for efficient Linux command-line multitasking and system administration.

---

# ✅ Lab Completion Checklist

- [ ] I understand what job control is
- [ ] I understand foreground processes
- [ ] I understand background processes
- [ ] I can start a long-running process
- [ ] I can suspend a process with `Ctrl+Z`
- [ ] I can list jobs with `jobs`
- [ ] I can resume a stopped job with `bg`
- [ ] I can bring a job to the foreground with `fg`
- [ ] I understand Linux job IDs
- [ ] I understand the difference between job IDs and PIDs
- [ ] I can safely practice job control using test processes

---

## 🚀 Next Lab

**Lab 16 — Using Aliases**
