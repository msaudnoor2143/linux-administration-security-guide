# Lab 14 — Basic Process Management

> Learn how to view running processes, monitor system activity, and safely manage processes using Linux process-management commands.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand the basics of process management in Linux
- List currently running processes
- Interpret process information
- Understand Process IDs (PIDs)
- Monitor processes in real time
- Identify CPU and memory usage
- Terminate a process using its PID
- Understand the `SIGTERM` and `SIGKILL` signals
- Terminate processes by name using `pkill`
- Apply process-management techniques to system-resource problems

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Access to a Linux system
- A terminal or Linux command-line interface
- Basic knowledge of Linux commands
- Basic understanding of system resources
- Completion of **Lab 13 — Using Piping and Redirection**

> **Note:** The process-inspection exercises can be completed without root privileges. Avoid terminating system-critical processes.

---

# 1. Understanding Processes

A **process** is a running instance of a program.

Whenever you start an application or execute a command, Linux creates a process to perform that work.

Each process is assigned a unique **Process ID (PID)**.

Process management is an important Linux administration skill because administrators need to:

- Monitor running applications
- Identify resource-heavy processes
- Troubleshoot performance problems
- Stop unresponsive applications
- Manage system resources

---

# 2. Listing Running Processes with `ps`

The `ps` command provides a snapshot of processes currently running on the system.

A commonly used form is:

```bash
ps aux
```

The options provide a detailed view of processes:

- `a` — Display processes for all users
- `u` — Provide detailed user-oriented information
- `x` — Include processes without controlling terminals

Run:

```bash
ps aux
```

---

## 2.1 Understanding `ps aux` Output

The output contains several important fields.

Common fields include:

| Field | Meaning |
|---|---|
| `USER` | User who owns the process |
| `PID` | Process ID |
| `%CPU` | CPU usage |
| `%MEM` | Memory usage |
| `VSZ` | Virtual memory size |
| `RSS` | Resident memory size |
| `TTY` | Controlling terminal |
| `STAT` | Process state |
| `START` | Process start information |
| `TIME` | CPU time used |
| `COMMAND` | Command that started the process |

The most important field for this lab is:

```text
PID
```

The PID identifies a specific process.

---

# 🧪 Practical Lab

## Task 1 — List Running Processes

Run:

```bash
ps aux
```

Observe the output.

Identify:

1. The `USER` column
2. The `PID` column
3. The `%CPU` column
4. The `%MEM` column
5. The `COMMAND` column

Try filtering the output with:

```bash
ps aux | head
```

You can also search for a particular process:

```bash
ps aux | grep bash
```

This demonstrates how process management can be combined with the piping techniques learned in Lab 13.

---

# 3. Monitoring Processes with `top`

The `top` command provides a real-time view of running processes.

Run:

```bash
top
```

Unlike `ps`, which provides a snapshot, `top` continuously updates the process information.

---

## 3.1 What `top` Shows

While `top` is running, observe:

- Active processes
- CPU usage
- Memory usage
- Process IDs
- Running tasks
- System resource information

Look for processes using significant CPU or memory resources.

---

## 3.2 Useful `top` Controls

While inside `top`:

### Press `q`

```text
q
```

Quits `top` and returns to the shell.

### Press `h`

```text
h
```

Displays help and available interactive commands.

After exploring `top`, press:

```text
q
```

to exit.

---

# 4. Understanding Process IDs

Every running process has a unique Process ID called a **PID**.

For example, `ps aux` may show:

```text
USER       PID  %CPU %MEM COMMAND
user      1234   0.5  1.2 example-process
```

In this example:

```text
1234
```

is the PID.

The PID can be used with commands such as:

```bash
kill
```

to send a signal to the process.

---

# 5. Terminating a Process with `kill`

The `kill` command sends a signal to a process.

Basic syntax:

```bash
kill <PID>
```

For example:

```bash
kill 1234
```

The default signal sent by `kill` is generally:

```text
SIGTERM
```

SIGTERM requests that the process terminate gracefully.

This is normally preferable to immediately forcing a process to stop.

---

## Task 2 — Identify a Process ID

Use:

```bash
ps aux
```

or:

```bash
top
```

to identify a process that you understand and can safely manage.

Record its PID.

> **Important:** Do not randomly terminate system-critical processes. For practice, use a process that you started yourself or an application that is safe to close.

---

## Task 2.1 — Send SIGTERM

Use:

```bash
kill <PID>
```

Replace `<PID>` with the PID of your selected test process.

For example:

```bash
kill 1234
```

Then verify the process:

```bash
ps aux | grep 1234
```

You can also check the process list again:

```bash
ps aux
```

---

# 6. Understanding SIGKILL

Sometimes a process does not respond to a normal termination request.

Linux provides a stronger signal:

```text
SIGKILL
```

It can be sent using:

```bash
kill -9 <PID>
```

For example:

```bash
kill -9 1234
```

The number:

```text
-9
```

represents `SIGKILL`.

### Important Difference

```text
kill <PID>
```

normally sends:

```text
SIGTERM
```

while:

```text
kill -9 <PID>
```

sends:

```text
SIGKILL
```

SIGTERM gives the application an opportunity to shut down cleanly.

SIGKILL forces termination and does not provide the same opportunity for cleanup.

---

# ⚠️ Safety Warning

Do not use:

```bash
kill -9
```

against processes simply because you do not recognize them.

A process may belong to:

- The operating system
- A desktop environment
- A network service
- A security service
- Another user's session
- An important application

Always identify the process before terminating it.

---

# 7. Terminating Processes by Name with `pkill`

Instead of finding a PID first, Linux provides `pkill` to target processes by name.

Basic syntax:

```bash
pkill -x <process_name>
```

The `-x` option requires an exact process-name match.

For example:

```bash
pkill -x firefox
```

would target processes whose name exactly matches:

```text
firefox
```

---

# 🧪 Practical Lab

## Task 3 — Use `pkill`

For safe practice, use an application or process that you started yourself and that you can safely close.

First identify the process name:

```bash
ps aux
```

Then, if appropriate, use:

```bash
pkill -x <process_name>
```

For example:

```bash
pkill -x firefox
```

Verify that the process is no longer running:

```bash
ps aux | grep <process_name>
```

> **Important:** Do not use `pkill` on critical system processes or services.

---

# 8. Case Study — Managing System Resources

Consider a Linux system experiencing unusually high CPU usage.

A system administrator needs to identify which process is consuming excessive resources.

### Step 1 — Monitor the system

Run:

```bash
top
```

Observe the CPU and memory information.

---

### Step 2 — Identify a resource-heavy process

Look at the process list and identify the relevant PID.

For example:

```text
PID
```

might identify the process.

---

### Step 3 — Investigate the process

Use:

```bash
ps aux
```

to obtain additional information.

You can combine commands when useful:

```bash
ps aux | grep <process_name>
```

---

### Step 4 — Gracefully terminate the process

If the process is safe to terminate:

```bash
kill <PID>
```

---

### Step 5 — Recheck system resources

Run:

```bash
top
```

again and observe whether system resource usage has changed.

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `ps` | Display a snapshot of processes |
| `ps aux` | Display detailed information about running processes |
| `top` | Monitor processes and system resources in real time |
| `kill <PID>` | Send the default termination signal to a process |
| `kill -9 <PID>` | Send SIGKILL to a process |
| `pkill -x <name>` | Terminate processes by exact name |
| `ps aux \| grep <name>` | Search process output for a name |
| `head` | Display the beginning of command output |

---

# 🧠 Key Concepts

## Process

A process is a running instance of a program.

---

## PID

PID means:

```text
Process ID
```

It uniquely identifies a process.

---

## `ps`

The `ps` command provides a snapshot of running processes.

Example:

```bash
ps aux
```

---

## `top`

The `top` command provides a continuously updated view of processes and system resource usage.

Example:

```bash
top
```

---

## `kill`

The `kill` command sends signals to processes.

Example:

```bash
kill 1234
```

---

## SIGTERM

SIGTERM is the normal termination signal sent by:

```bash
kill <PID>
```

It requests that a process terminate gracefully.

---

## SIGKILL

SIGKILL can be sent using:

```bash
kill -9 <PID>
```

It forces the process to terminate.

---

## `pkill`

`pkill` allows processes to be targeted by name.

Example:

```bash
pkill -x process_name
```

---

# 🛡️ Security Perspective

Process management is important in cybersecurity and system administration.

Security professionals may need to:

- Monitor running processes
- Identify unusual processes
- Investigate resource usage
- Detect unexpected applications
- Respond to suspicious activity
- Stop unwanted processes
- Troubleshoot security tools and services

Process monitoring can therefore contribute to understanding the current state of a Linux system.

However, process termination should always be performed carefully because stopping the wrong process can affect system availability.

---

# ⚠️ Best Practices

### 1. Identify the process before terminating it

Use:

```bash
ps aux
```

or:

```bash
top
```

---

### 2. Prefer graceful termination

Use:

```bash
kill <PID>
```

before considering:

```bash
kill -9 <PID>
```

---

### 3. Be careful with `pkill`

Before running:

```bash
pkill -x <process_name>
```

make sure you know which process will be targeted.

---

### 4. Avoid critical system processes

Do not terminate processes simply because their names are unfamiliar.

---

### 5. Verify after making changes

After terminating a process, check:

```bash
ps aux
```

or:

```bash
top
```

to confirm the expected result.

---

# 📝 Questions

1. What is a process?
2. What does PID stand for?
3. What does the `ps` command do?
4. What information does `ps aux` display?
5. What is the difference between `ps` and `top`?
6. What does the `PID` column represent?
7. What does the `kill` command do?
8. What signal is normally sent by `kill <PID>`?
9. What does `kill -9 <PID>` do?
10. What does `-9` represent?
11. What is the purpose of `pkill`?
12. What does `pkill -x` do?
13. Why should SIGKILL not be the first choice for terminating a process?
14. Why is process management important for system administrators?
15. How can process monitoring help with system-resource problems?

---

# 🧩 Challenge

Imagine that a Linux system is experiencing high CPU usage.

Without terminating random processes:

### Step 1

Run:

```bash
top
```

Identify processes using significant CPU resources.

### Step 2

Use:

```bash
ps aux
```

to inspect the process list.

### Step 3

Use a pipe to search for a specific process:

```bash
ps aux | grep <process_name>
```

### Step 4

If you identify a process that you started yourself and can safely terminate, send:

```bash
kill <PID>
```

### Step 5

Run:

```bash
top
```

again and observe the system.

### Goal

Practice the complete workflow:

```text
Monitor
   ↓
Identify
   ↓
Investigate
   ↓
Terminate safely
   ↓
Verify
```

---

# 📌 Summary

In this lab, you learned the fundamentals of Linux process management.

You practiced:

- Listing processes with `ps aux`
- Monitoring processes with `top`
- Understanding PIDs
- Understanding CPU and memory usage
- Terminating processes with `kill`
- Understanding SIGTERM
- Understanding SIGKILL
- Using `pkill` to target processes by name
- Applying process-management techniques to resource-management scenarios

These skills are fundamental for Linux system administration, troubleshooting, and cybersecurity operations.

---

# ✅ Lab Completion Checklist

- [ ] I understand what a process is
- [ ] I understand what a PID is
- [ ] I can list processes using `ps aux`
- [ ] I can interpret basic process information
- [ ] I can monitor processes using `top`
- [ ] I understand CPU and memory usage
- [ ] I understand how `kill` works
- [ ] I understand SIGTERM
- [ ] I understand SIGKILL
- [ ] I understand when `kill -9` should be avoided
- [ ] I can use `pkill -x`
- [ ] I can safely identify a process before terminating it
- [ ] I understand the importance of process management for system administration

---

## 🚀 Next Lab

**Lab 15 — Job Control Basics**
