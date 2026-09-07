# Lab 11 — Environment Variables

> Learn how Linux environment variables store configuration information and influence shell sessions and programs.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand what environment variables are
- View existing environment variables
- Display individual variables
- Use the `printenv` command
- Use the `env` command
- Understand the `PATH` variable
- Create temporary environment variables
- Understand the difference between shell variables and environment variables
- Understand how environment variables affect Linux programs

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Access to a Linux system
- A terminal
- Basic knowledge of the Linux command line
- Basic understanding of shells
- Completion of **Lab 10 — Understanding Shells**

> **Note:** The exercises in this lab can be completed without root privileges.

---

# 1. Understanding Environment Variables

Environment variables are named values that provide information to the shell and programs running on the system.

They can contain information such as:

- User information
- Home directory location
- Shell information
- Command search paths
- Current working environment
- Program configuration

Examples include:

```text
HOME
USER
SHELL
PATH
PWD
```

You can display the value of an environment variable by placing `$` before its name.

For example:

```bash
echo $HOME
```

---

# 2. Displaying Environment Variables

One of the simplest ways to view an environment variable is with `echo`.

### Display the current user's home directory

```bash
echo $HOME
```

A typical result may look like:

```text
/home/username
```

### Display the current user

```bash
echo $USER
```

### Display the current shell

```bash
echo $SHELL
```

### Display the current working directory

```bash
echo $PWD
```

The exact values depend on your Linux system and current session.

---

# 3. Using `printenv`

The `printenv` command displays environment variables.

### Display all environment variables

```bash
printenv
```

This may produce a large amount of output.

You can also display one specific variable:

```bash
printenv HOME
```

For example:

```bash
printenv USER
```

or:

```bash
printenv SHELL
```

### Understanding the syntax

```bash
printenv VARIABLE_NAME
```

Example:

```bash
printenv PATH
```

---

# 4. Using `env`

The `env` command can also display the environment available to the current shell.

Run:

```bash
env
```

You will see many variables in the following general format:

```text
VARIABLE=value
```

For example:

```text
HOME=/home/username
USER=username
SHELL=/bin/bash
```

The actual values depend on your system.

---

# 5. Understanding the `PATH` Variable

The `PATH` environment variable is one of the most important variables in Linux.

Display it with:

```bash
echo $PATH
```

It normally contains multiple directories separated by colons:

```text
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

When you enter a command such as:

```bash
ls
```

the shell searches directories in `PATH` to find the executable.

You can inspect the individual directories using:

```bash
echo $PATH | tr ':' '\n'
```

This displays each directory on a separate line.

---

# 6. Checking Where a Command Comes From

The `command -v` command can show which executable the shell will use.

For example:

```bash
command -v ls
```

You may see something similar to:

```text
/usr/bin/ls
```

You can also check:

```bash
command -v bash
```

This helps demonstrate how the shell locates commands through the `PATH` environment variable.

---

# 7. Creating a Temporary Environment Variable

You can create an environment variable for the current shell session using:

```bash
export LAB_NAME="Linux Administration"
```

Display it:

```bash
echo $LAB_NAME
```

You can also use:

```bash
printenv LAB_NAME
```

The variable is available to programs launched from that shell.

---

# 8. Understanding `export`

The `export` command marks a shell variable for inclusion in the environment of subsequently executed commands.

Example:

```bash
export LAB_NAME="Linux Administration"
```

Check it:

```bash
echo $LAB_NAME
```

And:

```bash
printenv LAB_NAME
```

Environment variables can also be passed to programs launched from the shell.

For example:

```bash
env | grep '^LAB_NAME='
```

You should see:

```text
LAB_NAME=Linux Administration
```

---

# 9. Shell Variables vs Environment Variables

A normal shell variable can be created without `export`.

For example:

```bash
TEST_VARIABLE="hello"
```

Display it:

```bash
echo $TEST_VARIABLE
```

However, it is not automatically part of the environment inherited by child processes.

Export it:

```bash
export TEST_VARIABLE
```

Now it becomes an environment variable for child processes launched afterward.

You can verify:

```bash
printenv TEST_VARIABLE
```

---

# 🧪 Practical Lab

Perform the following exercises in your normal Linux terminal.

First verify your current location:

```bash
pwd
```

Then verify your current shell:

```bash
echo $SHELL
```

---

## Task 1 — Display Common Environment Variables

Display the following variables:

```bash
echo $HOME
echo $USER
echo $SHELL
echo $PWD
```

Observe the values returned by your system.

---

## Task 2 — Use `printenv`

Display your home directory using:

```bash
printenv HOME
```

Then display:

```bash
printenv USER
```

And:

```bash
printenv SHELL
```

Compare the results with the values obtained using `echo`.

---

## Task 3 — Display the Environment

Run:

```bash
env
```

Observe the environment variables available to your shell.

Because the output may be large, you can search for specific variables:

```bash
env | grep '^HOME='
```

Try:

```bash
env | grep '^USER='
```

And:

```bash
env | grep '^SHELL='
```

---

## Task 4 — Inspect `PATH`

Display your current `PATH`:

```bash
echo $PATH
```

Then display each directory separately:

```bash
echo $PATH | tr ':' '\n'
```

Observe how the shell has multiple directories available when searching for commands.

---

## Task 5 — Locate Commands

Use:

```bash
command -v ls
```

Then:

```bash
command -v bash
```

And:

```bash
command -v python3
```

If `python3` is installed and available through your `PATH`, its executable path should be displayed.

---

## Task 6 — Create an Environment Variable

Create a temporary environment variable:

```bash
export LAB_NAME="Linux Administration"
```

Display it:

```bash
echo $LAB_NAME
```

Verify that it is part of the environment:

```bash
printenv LAB_NAME
```

---

## Task 7 — Create a Shell Variable

Create a normal shell variable:

```bash
LOCAL_VARIABLE="Shell Variable"
```

Display it:

```bash
echo $LOCAL_VARIABLE
```

Now try:

```bash
printenv LOCAL_VARIABLE
```

Notice the difference.

Because the variable has not been exported, it is not currently an environment variable.

Export it:

```bash
export LOCAL_VARIABLE
```

Then run:

```bash
printenv LOCAL_VARIABLE
```

It should now be displayed.

---

## Task 8 — Check the Current Environment

Search for the variables created during this lab:

```bash
env | grep -E 'LAB_NAME|LOCAL_VARIABLE'
```

You should see entries similar to:

```text
LAB_NAME=Linux Administration
LOCAL_VARIABLE=Shell Variable
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `echo $VARIABLE` | Display the value of a variable |
| `printenv` | Display environment variables |
| `printenv VARIABLE` | Display one environment variable |
| `env` | Display the current environment |
| `export VARIABLE=value` | Create/export an environment variable |
| `export VARIABLE` | Export an existing shell variable |
| `command -v command` | Show the executable selected for a command |
| `echo $PATH` | Display the command search path |
| `tr ':' '\n'` | Convert `PATH` entries into separate lines |
| `grep` | Search command output for matching text |

---

# 🧠 Key Concepts

## Environment Variables

Environment variables provide information and configuration to the shell and processes running from it.

Example:

```bash
echo $HOME
```

---

## `$HOME`

Stores the current user's home directory.

Example:

```bash
echo $HOME
```

---

## `$USER`

Usually identifies the current user.

Example:

```bash
echo $USER
```

---

## `$SHELL`

Shows the user's configured shell.

Example:

```bash
echo $SHELL
```

---

## `$PWD`

Represents the current working directory of the shell.

Example:

```bash
echo $PWD
```

---

## `$PATH`

Defines directories searched by the shell when locating executable commands.

Example:

```bash
echo $PATH
```

---

## `export`

Makes a shell variable available in the environment inherited by child processes.

Example:

```bash
export APP_MODE="testing"
```

---

## Shell Variable

A shell variable exists within the shell where it was created.

Example:

```bash
MY_VARIABLE="example"
```

It can be exported later:

```bash
export MY_VARIABLE
```

---

# 🛡️ Security Perspective

Environment variables are important in system administration and security.

They can influence:

- Application behavior
- Command execution
- Shell configuration
- Script behavior
- Development environments
- System administration tasks

The `PATH` variable is especially important because it determines where the shell searches for commands.

Administrators and security professionals should understand the environment in which scripts and programs execute.

### Avoid storing sensitive information carelessly

Environment variables can sometimes contain configuration information or secrets.

For example:

```text
API keys
Tokens
Passwords
Connection information
```

Sensitive values should not be casually exposed in terminal output, scripts, logs, or public repositories.

For this reason, this lab uses only harmless demonstration values.

---

# ⚠️ Best Practices

### 1. Inspect variables before changing them

Use:

```bash
echo $PATH
```

or:

```bash
printenv PATH
```

### 2. Be careful when modifying `PATH`

Incorrect `PATH` changes can make commands difficult to locate.

### 3. Avoid exposing secrets

Do not place real passwords, API keys, access tokens, or private credentials into public GitHub repositories.

### 4. Use harmless values while learning

For example:

```bash
export LAB_NAME="Linux Administration"
```

### 5. Understand the scope of variables

A variable created in one shell session does not necessarily persist after that session ends.

---

# 📝 Questions

1. What is an environment variable?
2. What does the `echo` command do when used with `$VARIABLE`?
3. What is the purpose of `printenv`?
4. What does the `env` command display?
5. What is the purpose of the `PATH` variable?
6. Why are directories in `PATH` separated by colons?
7. What does `export` do?
8. What is the difference between a shell variable and an environment variable?
9. How can you check which executable will be used for a command?
10. Why should sensitive information be handled carefully when using environment variables?

---

# 🧪 Challenge

Create a temporary environment variable named:

```text
SECURITY_LAB
```

with the value:

```text
Linux Security Practice
```

Use:

```bash
export SECURITY_LAB="Linux Security Practice"
```

Then verify it using:

```bash
echo $SECURITY_LAB
```

and:

```bash
printenv SECURITY_LAB
```

Finally, search for it using:

```bash
env | grep '^SECURITY_LAB='
```

---

# 🧹 Cleanup

The variables created during this lab are temporary unless you explicitly add them to shell configuration files.

You can remove them from the current shell with:

```bash
unset LAB_NAME
unset LOCAL_VARIABLE
unset SECURITY_LAB
```

Verify:

```bash
printenv LAB_NAME
printenv LOCAL_VARIABLE
printenv SECURITY_LAB
```

These commands should no longer display the variables.

> **Note:** If a variable was configured permanently in a shell startup file, `unset` only removes it from the current session.

---

# 📌 Summary

In this lab, you learned how Linux environment variables work and how they provide information and configuration to shells and processes.

You practiced:

- Displaying variables with `echo`
- Viewing variables with `printenv`
- Viewing the environment with `env`
- Understanding `$HOME`, `$USER`, `$SHELL`, and `$PWD`
- Inspecting `$PATH`
- Locating commands with `command -v`
- Creating environment variables with `export`
- Understanding shell variables versus environment variables
- Removing temporary variables with `unset`

Environment variables are an important foundation for shell scripting, system administration, automation, and security work.

---

# ✅ Lab Completion Checklist

- [ ] I understand what environment variables are
- [ ] I can display variables with `echo`
- [ ] I can use `printenv`
- [ ] I can use `env`
- [ ] I understand `$HOME`
- [ ] I understand `$USER`
- [ ] I understand `$SHELL`
- [ ] I understand `$PWD`
- [ ] I understand `$PATH`
- [ ] I can inspect the directories in `PATH`
- [ ] I can locate commands with `command -v`
- [ ] I can create an environment variable with `export`
- [ ] I understand shell variables versus environment variables
- [ ] I understand why sensitive information should be handled carefully
- [ ] I can remove temporary variables with `unset`

---

## 🚀 Next Lab

**Lab 12 — Basic Shell Scripting**
