# Lab 50 — Introduction to Shell Variables

> Learn how Bash stores values in shell variables, how exported variables reach child processes, and how special variables provide useful information for shell scripting.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand shell variables
- Create local variables
- Read variable values
- Export variables
- Access variables from subprocesses
- Understand `$?`
- Understand `$$`
- Understand `$#`
- Apply variables to shell scripting

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Basic Linux command-line knowledge
- Bash
- Familiarity with terminal commands
- Basic understanding of shell sessions

---

# 1. Understanding Shell Variables

A shell variable stores a value that can be referenced later.

For example:

```bash
MYVAR="HelloWorld"
```

The variable name is:

```text
MYVAR
```

and its value is:

```text
HelloWorld
```

---

# 2. Creating a Local Variable

Create:

```bash
MYVAR="HelloWorld"
```

Display it:

```bash
echo "$MYVAR"
```

Expected output:

```text
HelloWorld
```

A normal shell variable is available within the current shell environment.

---

# 3. Exporting a Variable

Use:

```bash
export MYVAR2="GlobalHello"
```

The variable is now exported to child processes.

---

# 4. Accessing an Exported Variable

Start a child Bash process:

```bash
bash -c 'echo "$MYVAR2"'
```

The child shell can access the exported variable.

---

# 5. Understanding `$?`

The variable:

```bash
$?
```

contains the exit status of the most recently executed command.

For example:

```bash
true
echo $?
```

The result should normally be:

```text
0
```

Now:

```bash
false
echo $?
```

will normally produce a non-zero value.

---

# 6. Understanding `$$`

The variable:

```bash
$$
```

represents the process ID (PID) of the current shell.

Run:

```bash
echo $$
```

The output will be a numeric process ID.

---

# 7. Understanding `$#`

The variable:

```bash
$#
```

represents the number of positional arguments supplied to a shell script or function.

For example, a shell command can demonstrate zero arguments:

```bash
bash -c 'echo $#'
```

The result is:

```text
0
```

---

# 🧪 Practical Lab

## Task 1 — Create a Local Variable

Run:

```bash
MYVAR="HelloWorld"
```

Display it:

```bash
echo "$MYVAR"
```

---

## Task 2 — Export a Variable

Run:

```bash
export MYVAR2="GlobalHello"
```

Check:

```bash
echo "$MYVAR2"
```

---

## Task 3 — Access It from a Child Shell

Run:

```bash
bash -c 'echo "$MYVAR2"'
```

Observe the output.

---

## Task 4 — Test `$?`

Run:

```bash
true
```

Then:

```bash
echo $?
```

Now:

```bash
false
```

Then:

```bash
echo $?
```

Compare the results.

---

## Task 5 — Test `$$`

Run:

```bash
echo $$
```

Record the PID.

---

## Task 6 — Test `$#`

Run:

```bash
bash -c 'echo $#'
```

Observe the number of arguments.

Then try:

```bash
bash -c 'echo $#' _ one two three
```

Observe the result.

---

# 🔎 Command Reference

| Variable/Command | Purpose |
|---|---|
| `MYVAR="value"` | Create a shell variable |
| `echo "$MYVAR"` | Display a variable |
| `export MYVAR` | Export a variable |
| `bash -c` | Execute commands in a child Bash process |
| `$?` | Previous command exit status |
| `$$` | Current shell PID |
| `$#` | Number of positional arguments |

---

# 🧠 Key Concepts

## Shell Variable

A named value stored in the shell environment.

## Exported Variable

A variable made available to child processes.

## Exit Status

A numeric result returned by a command.

## PID

Process ID identifying a running process.

## Positional Arguments

Arguments supplied to a shell script or function.

---

# 🛡️ Security Perspective

Environment variables can contain configuration values, paths, and other information used by applications.

However, sensitive information should not automatically be stored in environment variables simply because they are convenient.

Administrators should understand:

- Who can access environment information
- Which processes inherit exported variables
- Whether sensitive values may appear in debugging output

---

# ⚠️ Best Practices

- Use meaningful variable names.
- Quote variable expansions when appropriate.
- Understand which variables are exported.
- Avoid exposing sensitive information unnecessarily.
- Check exit statuses when writing automation.
- Use shell variables consistently in scripts.

---

# 📝 Questions

1. What is a shell variable?
2. How do you create a variable?
3. How do you access a variable?
4. What does `export` do?
5. What does `$?` represent?
6. What does `$$` represent?
7. What does `$#` represent?
8. Why are exported variables available to child processes?
9. Why should sensitive information be handled carefully in environment variables?

---

# 🚀 Challenge

Create a small shell script that displays:

```text
Current Shell PID
Number of Arguments
Last Command Exit Status
```

Use:

```text
$$
$#
$?
```

and explain what each value represents.

---

# ✅ Lab Completion Checklist

- [ ] I understand shell variables
- [ ] I can create local variables
- [ ] I can read variable values
- [ ] I understand `export`
- [ ] I can access exported variables from child processes
- [ ] I understand `$?`
- [ ] I understand `$$`
- [ ] I understand `$#`
- [ ] I understand how variables are used in shell scripting

---

## Summary

In this lab, you learned the fundamentals of Bash shell variables. You created local and exported variables, accessed variables from child processes, and explored special variables such as `$?`, `$$`, and `$#`.

These concepts provide an important foundation for Bash scripting and Linux automation.

---

## 🚀 Next Lab

**Lab 51 — Basic Regex with grep**
