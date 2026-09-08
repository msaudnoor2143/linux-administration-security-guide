# Lab 46 — Bash Profile vs. Bashrc

> Learn the difference between Bash login-shell and interactive-shell configuration files and customize your shell using aliases and environment variables.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand `.bash_profile`
- Understand `.bashrc`
- Understand login and non-login shells
- Inspect hidden shell configuration files
- Create backups
- Add aliases
- Add environment variables
- Reload `.bashrc`
- Verify shell customization

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Basic Linux command-line knowledge
- Bash installed
- A Linux home directory
- Familiarity with aliases and environment variables

> Note: Modern Ubuntu systems commonly use `~/.profile` in addition to `~/.bashrc`, and `.bash_profile` may not exist by default.

---

# 1. Understanding `.bashrc`

The file:

```text
~/.bashrc
```

is commonly used for interactive non-login Bash shell configuration.

It can contain:

- Aliases
- Functions
- Environment customization
- Shell options
- Prompt configuration

---

# 2. Understanding `.bash_profile`

The file:

```text
~/.bash_profile
```

is traditionally associated with login Bash shells.

Not every Linux system creates this file by default.

Some systems instead use:

```text
~/.profile
```

for login-session configuration.

---

# 3. Inspecting Your Home Directory

Move home:

```bash
cd ~
```

List hidden files:

```bash
ls -la
```

Look for:

```text
.bashrc
.bash_profile
.profile
```

---

# 4. Backing Up Configuration Files

Before changing shell configuration, create backups.

For `.bashrc`:

```bash
cp ~/.bashrc ~/.bashrc.backup
```

If `.bash_profile` exists:

```bash
cp ~/.bash_profile ~/.bash_profile.backup
```

---

# 5. Creating an Alias

An alias provides a shortcut for a command.

For example:

```bash
alias ll='ls -la'
```

Now:

```bash
ll
```

runs:

```bash
ls -la
```

---

# 6. Adding an Alias to `.bashrc`

Add the alias to your `.bashrc` so it can be loaded automatically.

The conceptual entry is:

```bash
alias ll='ls -la'
```

---

# 7. Environment Variables

An environment variable can be exported with:

```bash
export MY_VAR="Hello World!"
```

Check it:

```bash
echo "$MY_VAR"
```

---

# 8. Reloading `.bashrc`

After modifying `.bashrc`, reload it:

```bash
source ~/.bashrc
```

The current shell can then use the updated configuration.

---

# 🧪 Practical Lab

## Task 1 — Inspect Shell Configuration

Run:

```bash
cd ~
```

Then:

```bash
ls -la
```

Identify:

```text
.bashrc
.profile
.bash_profile
```

if present.

---

## Task 2 — Back Up `.bashrc`

Run:

```bash
cp ~/.bashrc ~/.bashrc.backup
```

Verify:

```bash
ls -l ~/.bashrc*
```

---

## Task 3 — Create an Alias

For the current shell:

```bash
alias ll='ls -la'
```

Test:

```bash
ll
```

---

## Task 4 — Create an Environment Variable

Run:

```bash
export MY_VAR="Hello World!"
```

Verify:

```bash
echo "$MY_VAR"
```

---

## Task 5 — Reload `.bashrc`

After adding your configuration to `.bashrc`, reload it:

```bash
source ~/.bashrc
```

Test:

```bash
ll
```

and:

```bash
echo "$MY_VAR"
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `cd ~` | Go to home directory |
| `ls -la` | Show hidden files |
| `cp` | Copy files |
| `alias` | Create command shortcuts |
| `export` | Export an environment variable |
| `echo` | Display variable contents |
| `source ~/.bashrc` | Reload Bash configuration |

---

# 🧠 Key Concepts

## `.bashrc`

Commonly used for interactive non-login Bash shell configuration.

## `.bash_profile`

Traditionally associated with login Bash shells.

## `.profile`

Commonly used for login-session configuration on many Linux systems.

## Alias

A shortcut for a command.

## Environment Variable

A named value available to processes in the shell environment.

---

# 🛡️ Security Perspective

Shell configuration files can influence how commands and programs execute.

Be careful when:

- Adding commands
- Copying configuration from unknown sources
- Modifying `PATH`
- Adding scripts to startup files

A malicious or incorrect shell configuration can affect command execution.

---

# ⚠️ Best Practices

- Back up configuration files.
- Review commands before adding them.
- Avoid copying unknown shell configurations.
- Keep aliases understandable.
- Be careful with `PATH` modifications.

---

# 📝 Questions

1. What is `.bashrc`?
2. What is `.bash_profile`?
3. What is `.profile`?
4. What is an alias?
5. What does `source ~/.bashrc` do?
6. What does `export` do?
7. Why should shell configuration files be backed up?
8. Why can shell configuration affect security?

---

# 🚀 Challenge

Create three useful aliases for your own Linux workflow.

For example:

```text
ll
la
```

Then create one environment variable and explain its purpose.

---

# ✅ Lab Completion Checklist

- [ ] I understand `.bashrc`
- [ ] I understand `.bash_profile`
- [ ] I understand `.profile`
- [ ] I can inspect hidden configuration files
- [ ] I can create an alias
- [ ] I can create an environment variable
- [ ] I can reload `.bashrc`
- [ ] I understand the security implications of shell configuration

---

## Summary

In this lab, you learned how Bash configuration files influence the shell environment. You explored `.bashrc`, `.bash_profile`, and `.profile`, created aliases, configured an environment variable, and learned how to reload shell configuration.

---

## 🚀 Next Lab

**Lab 47 — Using the `history` Command**
