# Lab 47 — Using the `history` Command

> Learn how Bash records previously executed commands and how command history can improve productivity during Linux administration.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- View shell history
- Understand history numbers
- Re-run previous commands
- Search command history
- Clear the current shell history
- Understand the security implications of shell history

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Basic Linux command-line knowledge
- Bash or a compatible shell
- Access to a terminal

---

# 1. Understanding Command History

Bash maintains a history of commands entered by the user.

This makes it easier to:

- Repeat commands
- Review previous operations
- Troubleshoot
- Avoid retyping long commands

---

# 2. Viewing History

Run:

```bash
history
```

You may see:

```text
  1  pwd
  2  ls
  3  cd /tmp
```

The number is the history entry number.

---

# 3. Re-running a Command

If a command appears as history entry `25`, it can be executed again using:

```bash
!25
```

Replace `25` with an actual history number from your system.

---

# 4. Searching History

You can search command history using:

```bash
history | grep "keyword"
```

For example:

```bash
history | grep "ssh"
```

This can help locate previously executed commands related to SSH.

---

# 5. Clearing History

The source lab demonstrates:

```bash
history -c
```

This clears the history list of the current shell session.

Afterward:

```bash
history
```

can be used to inspect the current history state.

> Shell history behavior can vary depending on shell configuration and history settings.

---

# 🧪 Practical Lab

## Task 1 — Generate Some History

Run:

```bash
pwd
```

```bash
ls
```

```bash
whoami
```

Then:

```bash
history
```

---

## Task 2 — Identify a History Number

Choose a harmless command from the history output.

For example:

```text
25  ls -la
```

Run:

```bash
!25
```

Use your actual history number.

---

## Task 3 — Search History

Run:

```bash
history | grep "ls"
```

Observe matching commands.

---

## Task 4 — Clear the Current History

Run:

```bash
history -c
```

Then:

```bash
history
```

Observe the result.

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `history` | Display command history |
| `!NUMBER` | Re-run a history entry |
| `history \| grep TEXT` | Search command history |
| `history -c` | Clear current shell history |

---

# 🧠 Key Concepts

## History

A record of previously entered shell commands.

## History Number

The numeric identifier assigned to a history entry.

## History Expansion

Bash can use syntax such as:

```bash
!25
```

to refer to a previous command.

---

# 🛡️ Security Perspective

Command history can contain sensitive information.

For example, commands may reveal:

- Administrative actions
- File paths
- Server addresses
- Configuration details
- Mistakenly exposed secrets

Avoid placing passwords or secrets directly into command-line arguments whenever possible.

---

# ⚠️ Best Practices

- Review commands before re-running them.
- Be careful when using `!NUMBER`.
- Avoid putting secrets directly into commands.
- Understand how your shell stores history.
- Do not assume clearing one history view removes every possible record of an action.

---

# 📝 Questions

1. What does `history` do?
2. What is a history number?
3. How do you re-run history entry 25?
4. How can you search history?
5. What does `history -c` do?
6. Why can shell history create security concerns?
7. Why should passwords not be placed directly in commands?

---

# 🚀 Challenge

Run several commands, then:

```bash
history | tail
```

Identify three commands you previously executed and explain why command history is useful for administration.

---

# ✅ Lab Completion Checklist

- [ ] I can display command history
- [ ] I understand history numbers
- [ ] I can re-run a previous command
- [ ] I can search history
- [ ] I understand `history -c`
- [ ] I understand the security implications of command history

---

## Summary

In this lab, you learned how Bash command history works. You practiced viewing previous commands, re-running commands by history number, searching history, and clearing the current shell's history.

---

## 🚀 Next Lab

**Lab 48 — Command Chaining**
