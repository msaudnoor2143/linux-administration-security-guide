# Lab 58 — Setting Up Aliases in .bashrc

## 📌 Overview

Shell aliases allow frequently used commands to be represented by shorter custom names.

This lab demonstrates how to create aliases and make them available automatically through the Bash configuration file.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand shell aliases
- Create temporary aliases
- Add aliases to `.bashrc`
- Reload `.bashrc`
- Test custom commands
- Remove aliases safely

---

## 📚 Prerequisites

You should have:

- Basic Linux command-line knowledge
- Familiarity with Bash
- Access to your home directory

---

## 🧠 What Is an Alias?

An alias assigns a short name to a command.

For example:

```bash
alias ll='ls -la'
```

After creating the alias:

```bash
ll
```

will execute:

```bash
ls -la
```

---

## ⚡ Temporary Alias

Create an alias:

```bash
alias ll='ls -la'
```

Check it:

```bash
alias ll
```

Use it:

```bash
ll
```

The alias normally exists only for the current shell session.

---

## 💾 Persistent Aliases

To make an alias available in future Bash sessions, it can be added to:

```text
~/.bashrc
```

Before modifying the file, create a backup:

```bash
cp ~/.bashrc ~/.bashrc.backup
```

Add an alias:

```bash
echo "alias ll='ls -la'" >> ~/.bashrc
```

Reload the configuration:

```bash
source ~/.bashrc
```

Test:

```bash
ll
```

---

## 🧪 Practical Lab

### Task 1 — Create a temporary alias

```bash
alias cls='clear'
```

Test:

```bash
cls
```

### Task 2 — Create a listing alias

```bash
alias ll='ls -la'
```

Test:

```bash
ll
```

### Task 3 — View aliases

```bash
alias
```

### Task 4 — Add a persistent alias

Create a backup first:

```bash
cp ~/.bashrc ~/.bashrc.backup
```

Add:

```bash
echo "alias lsl='ls -lah'" >> ~/.bashrc
```

Reload:

```bash
source ~/.bashrc
```

Test:

```bash
lsl
```

---

## ❌ Removing an Alias

Remove a temporary alias:

```bash
unalias lsl
```

If the alias was added to `.bashrc`, remove or edit the corresponding line there as well.

---

## 🛡️ Security Perspective

Aliases can improve productivity, but administrators should understand exactly what an alias executes.

Avoid creating aliases that hide important command behavior or make potentially destructive operations difficult to recognize.

---

## ⚠️ Best Practices

- Back up `.bashrc` before modifying it.
- Keep aliases simple and readable.
- Avoid aliases that hide destructive commands.
- Review aliases when troubleshooting unexpected command behavior.
- Use `type` to determine whether a command is an alias.

Example:

```bash
type ll
```

---

## 📝 Questions

1. What is a shell alias?
2. What is the difference between a temporary and persistent alias?
3. What file commonly stores Bash aliases?
4. What does `source ~/.bashrc` do?
5. How can you determine whether a command is an alias?
6. Why should aliases not hide destructive behavior?

---

## 🧹 Cleanup

If you want to restore the original `.bashrc` backup created during this lab:

```bash
cp ~/.bashrc.backup ~/.bashrc
source ~/.bashrc
```

Only do this if you created the backup specifically for this lab and do not need changes made afterward.

---

## 📋 Lab Completion Checklist

- [ ] Create a temporary alias
- [ ] Inspect aliases
- [ ] Back up `.bashrc`
- [ ] Add a persistent alias
- [ ] Reload `.bashrc`
- [ ] Test the alias
- [ ] Understand safe alias practices

---

## 📌 Summary

In this lab, you learned how to create Bash aliases and make them persistent using `.bashrc`.

Aliases can improve command-line productivity when they remain clear, predictable, and safe.

---

## 🚀 Next Lab

**Lab 59 — Monitoring with top and htop**
