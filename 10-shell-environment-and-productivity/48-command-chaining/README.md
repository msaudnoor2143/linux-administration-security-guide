# Lab 48 — Command Chaining

> Learn how Bash command-chaining operators control the execution of multiple commands based on command success or failure.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand command chaining
- Use `&&`
- Use `||`
- Use `;`
- Understand command exit status
- Build conditional command sequences
- Apply command chaining to administrative workflows

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Basic Linux command-line knowledge
- Familiarity with basic shell commands
- Access to a Unix-like terminal

---

# 1. Understanding Command Chaining

Command chaining allows multiple commands to be placed on one command line.

For example:

```bash
command1 && command2
```

The second command depends on the result of the first command.

Common operators include:

```text
&&
||
;
```

---

# 2. The `&&` Operator

The `&&` operator executes the next command only if the previous command succeeds.

Example:

```bash
mkdir new_directory && cd new_directory
```

If `mkdir` succeeds, `cd` runs.

---

## 2.1 Successful Command Followed by Failure

Try:

```bash
echo "Hello" && cd non_existent_directory
```

The first command succeeds.

The second command fails because the directory does not exist.

---

# 3. The `||` Operator

The `||` operator executes the next command if the previous command fails.

Example:

```bash
cd non_existent_directory || echo "Directory does not exist"
```

The `cd` command fails, so the `echo` command runs.

---

# 4. The `;` Operator

The semicolon runs commands sequentially regardless of whether the previous command succeeds.

Example:

```bash
echo "First"; echo "Second"; echo "Third"
```

All three commands execute.

---

## 4.1 Failure Does Not Stop the Sequence

Example:

```bash
echo "Start"; cd non_existent_directory; echo "Continue"
```

The `cd` command fails, but the final `echo` still executes.

---

# 5. Exit Status

Linux commands return an exit status.

Generally:

```text
0
```

means success.

A non-zero value generally indicates failure.

You can inspect the previous command's status using:

```bash
echo $?
```

This concept is important for understanding:

```text
&&
||
```

---

# 🧪 Practical Lab

## Task 1 — Test `&&`

Run:

```bash
mkdir command-chain-test && cd command-chain-test
```

Verify:

```bash
pwd
```

---

## Task 2 — Test Failure with `&&`

Return home:

```bash
cd ~
```

Run:

```bash
echo "Hello" && cd non_existent_directory
```

Observe the result.

---

## Task 3 — Test `||`

Run:

```bash
cd non_existent_directory || echo "Directory does not exist"
```

Observe the output.

---

## Task 4 — Test `;`

Run:

```bash
echo "First"; cd non_existent_directory; echo "Third command still runs"
```

Observe the behavior.

---

## Task 5 — Inspect Exit Status

Run:

```bash
true
```

Then:

```bash
echo $?
```

Now run:

```bash
false
```

Then:

```bash
echo $?
```

Compare the results.

---

# 🔎 Command Reference

| Operator/Command | Purpose |
|---|---|
| `cmd1 && cmd2` | Run `cmd2` only if `cmd1` succeeds |
| `cmd1 \|\| cmd2` | Run `cmd2` if `cmd1` fails |
| `cmd1 ; cmd2` | Run commands sequentially |
| `echo $?` | Display previous command's exit status |
| `true` | Return success |
| `false` | Return failure |

---

# 🧠 Key Concepts

### `&&`

Conditional execution based on success.

### `||`

Conditional execution based on failure.

### `;`

Sequential execution regardless of success or failure.

### Exit Status

A numeric result returned by a command.

---

# 🛡️ Security Perspective

Command chaining is useful in administration and automation, but careless chaining can cause unintended operations.

Before executing a complex chain:

- Understand each command.
- Understand failure behavior.
- Check paths.
- Avoid destructive commands during experimentation.

---

# ⚠️ Best Practices

- Test command chains with harmless commands first.
- Understand exit status.
- Avoid copying complex command chains without understanding them.
- Be especially careful when using `sudo`.
- Use scripts when command logic becomes complex.

---

# 📝 Questions

1. What is command chaining?
2. What does `&&` do?
3. What does `||` do?
4. What does `;` do?
5. What does `$?` represent?
6. What does exit status `0` generally mean?
7. Why can command chaining be useful in automation?
8. Why should complex command chains be tested carefully?

---

# 🚀 Challenge

Create a command chain that:

1. Creates a directory.
2. Enters it only if creation succeeds.
3. Prints a success message.

Example structure:

```bash
mkdir practice && cd practice && echo "Directory ready"
```

---

# ✅ Lab Completion Checklist

- [ ] I understand command chaining
- [ ] I can use `&&`
- [ ] I can use `||`
- [ ] I can use `;`
- [ ] I understand exit status
- [ ] I can inspect `$?`
- [ ] I understand conditional command execution

---

## Summary

In this lab, you learned how Bash uses `&&`, `||`, and `;` to control multiple commands. You also learned how exit status determines whether conditional commands execute.

These concepts are fundamental for shell scripting and Linux automation.

---

## 🚀 Next Lab

**Lab 49 — Using and Creating Man Pages**
