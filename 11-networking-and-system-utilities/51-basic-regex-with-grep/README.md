# Lab 51 — Basic Regex with grep

## 📌 Overview

Regular expressions (regex) provide a powerful way to search and match text based on patterns.

In this lab, you will use `grep` with basic regular expressions to search files and identify specific text patterns.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand the purpose of regular expressions
- Use `grep` for pattern matching
- Search for exact text patterns
- Use basic regex metacharacters
- Combine `grep` with regular expressions
- Apply regex techniques to practical text-search tasks

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Basic Linux command-line knowledge
- Familiarity with files and directories
- Basic understanding of `grep`
- Access to a Linux terminal

---

## 🧠 Introduction to Regular Expressions

A regular expression is a pattern used to match text.

For example:

```bash
grep "error" logfile.txt
```

This searches for lines containing the word `error`.

Regular expressions make searches more flexible by allowing patterns instead of only literal text.

---

## 🔎 Basic grep Usage

Create a sample file:

```bash
cat > sample.txt <<'EOF'
Linux administration
Linux security
Network administration
System monitoring
Security operations
Database administration
EOF
```

Search for a specific word:

```bash
grep "Linux" sample.txt
```

Search for `security`:

```bash
grep "security" sample.txt
```

---

## 🔤 Basic Regex Metacharacters

### `^` — Beginning of a line

```bash
grep "^Linux" sample.txt
```

This matches lines beginning with `Linux`.

### `$` — End of a line

```bash
grep "administration$" sample.txt
```

This matches lines ending with `administration`.

### `.` — Any single character

```bash
grep "Net.ork" sample.txt
```

The dot represents one character.

### `*` — Zero or more occurrences

```bash
grep "Secu*" sample.txt
```

The pattern allows the character immediately before `*` to occur zero or more times.

---

## 🔢 Searching for Numbers

Create another sample file:

```bash
cat > numbers.txt <<'EOF'
User01
User02
Admin01
Server10
Server20
Backup30
EOF
```

Search for lines containing `01`:

```bash
grep "01" numbers.txt
```

Search for lines beginning with `User`:

```bash
grep "^User" numbers.txt
```

---

## 🔠 Case-Insensitive Searches

Use `-i` to ignore letter case:

```bash
grep -i "linux" sample.txt
```

---

## 📊 Display Matching Line Numbers

Use `-n`:

```bash
grep -n "Linux" sample.txt
```

---

## 🔢 Count Matches

Use `-c`:

```bash
grep -c "Linux" sample.txt
```

---

## 🧪 Practical Lab

### Task 1 — Create a log file

```bash
cat > application.log <<'EOF'
INFO: Application started
INFO: User authentication successful
WARNING: High memory usage
ERROR: Database connection failed
INFO: Backup completed
ERROR: Authentication service unavailable
WARNING: Disk usage is high
EOF
```

### Task 2 — Find errors

```bash
grep "ERROR" application.log
```

### Task 3 — Find warnings

```bash
grep "WARNING" application.log
```

### Task 4 — Search case-insensitively

```bash
grep -i "error" application.log
```

### Task 5 — Show line numbers

```bash
grep -n "ERROR" application.log
```

### Task 6 — Count errors

```bash
grep -c "ERROR" application.log
```

### Task 7 — Match lines beginning with INFO

```bash
grep "^INFO" application.log
```

### Task 8 — Match lines beginning with ERROR

```bash
grep "^ERROR" application.log
```

---

## 🔎 Command Reference

| Command | Purpose |
|---|---|
| `grep "text" file` | Search for text |
| `grep -i` | Ignore case |
| `grep -n` | Show line numbers |
| `grep -c` | Count matching lines |
| `grep -v` | Show non-matching lines |
| `grep "^text"` | Match beginning of line |
| `grep "text$"` | Match end of line |

---

## 🧠 Key Concepts

- Regex defines text-matching patterns.
- `grep` is commonly used for searching files.
- `^` represents the beginning of a line.
- `$` represents the end of a line.
- `.` represents a single character.
- `*` represents zero or more occurrences.
- Regex is particularly useful when analyzing logs and configuration files.

---

## 🛡️ Security Perspective

Regex and `grep` are useful in security operations.

Security analysts can use them to search logs for:

- Authentication failures
- Suspicious usernames
- IP addresses
- Error messages
- Configuration problems
- Security-related events

For example:

```bash
grep -i "failed" application.log
```

can help locate failed operations or authentication events.

---

## ⚠️ Best Practices

- Quote patterns when appropriate.
- Test regex against sample data before using it on important files.
- Be careful when searching very large files.
- Avoid modifying files when performing investigations.
- Use read-only search commands during incident analysis.

---

## 📝 Questions

1. What is a regular expression?
2. What does `^` represent?
3. What does `$` represent?
4. What does `grep -i` do?
5. How can you display matching line numbers?
6. How can `grep` help with security log analysis?

---

## 🧹 Cleanup

```bash
rm -f sample.txt numbers.txt application.log
```

---

## 📋 Lab Completion Checklist

- [ ] Understand basic regex
- [ ] Use `grep` for pattern matching
- [ ] Use `^` and `$`
- [ ] Search case-insensitively
- [ ] Display matching line numbers
- [ ] Count matches
- [ ] Apply regex to log analysis

---

## 📌 Summary

In this lab, you learned how to combine `grep` with basic regular expressions to search and analyze text.

These techniques form an important foundation for Linux administration, scripting, troubleshooting, and security analysis.

---

## 🚀 Next Lab

**Lab 52 — Network File Transfers (wget/curl)**
