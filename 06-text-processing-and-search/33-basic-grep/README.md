# Lab 33 — Basic Grep Usage

> Learn how to search for text patterns within files and directories using the Linux `grep` command.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand the purpose of `grep`.
- Search for text in files.
- Search recursively through directories.
- Use context options.
- Understand basic pattern matching.
- Apply `grep` to practical text-search tasks.

---

## 📚 Prerequisites

Before starting this lab, you should have:

- A Linux-based system.
- Terminal access.
- Basic command-line knowledge.
- Basic understanding of files and directories.

---

# 1. Understanding grep

`grep` is a command-line utility used to search text using patterns.

It is especially useful for:

- Searching configuration files.
- Finding messages in logs.
- Filtering command output.
- Locating specific information.
- Investigating system data.

---

# 2. Search for a String in a File

The basic syntax is:

```bash
grep "search_term" filename.txt
```

For example:

```bash
grep "error" example.txt
```

This displays lines containing the specified pattern.

---

# 3. Create a Practice File

Create a sample file:

```bash
echo -e "network error at node 3\noperation successful at node 5\nnetwork connection established\nunexpected error at node 7" > sample.txt
```

View it:

```bash
cat sample.txt
```

---

# 4. Search the File

Search for `error`:

```bash
grep "error" sample.txt
```

The command returns lines containing the specified word.

---

# 5. Recursive Searching

The `-r` option allows `grep` to search through a directory and its subdirectories.

Syntax:

```bash
grep -r "search_term" /path/to/directory/
```

For example:

```bash
grep -r "error" ~/grep-lab
```

This searches files throughout the directory tree.

---

# 6. Display Context Around Matches

Sometimes the matching line alone is not enough.

### Lines after the match

Use:

```bash
grep -A 2 "error" sample.txt
```

This displays the matching line and two lines after it.

### Lines before the match

Use:

```bash
grep -B 2 "error" sample.txt
```

This displays two lines before the matching line.

### Both before and after

Use:

```bash
grep -A 2 -B 2 "error" sample.txt
```

---

# 🧪 Practical Lab

## Task 1 — Create a Practice File

```bash
mkdir -p ~/grep-lab
cd ~/grep-lab
```

Create:

```bash
echo -e "network error at node 3\noperation successful at node 5\nnetwork connection established\nunexpected error at node 7" > sample.txt
```

---

## Task 2 — Search for a String

Run:

```bash
grep "error" sample.txt
```

---

## Task 3 — Search for Another String

```bash
grep "network" sample.txt
```

---

## Task 4 — Search Recursively

Create another file:

```bash
echo "another network error" > second.txt
```

Search the directory:

```bash
grep -r "error" ~/grep-lab
```

---

## Task 5 — Display Context

Run:

```bash
grep -A 2 -B 2 "error" sample.txt
```

Observe the additional lines shown around each match.

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `grep "text" file` | Search for text in a file |
| `grep -r "text" directory` | Search recursively |
| `grep -A N` | Display N lines after a match |
| `grep -B N` | Display N lines before a match |
| `grep -A N -B N` | Display context before and after |

---

# 🧠 Key Concepts

### Pattern Matching

`grep` searches for patterns within text.

### Recursive Search

The `-r` option searches through directories and their contents.

### Context

`-A` and `-B` allow additional lines surrounding a match to be displayed.

---

# 🛡️ Security Perspective

`grep` is extremely useful in cybersecurity and system administration.

It can help administrators:

- Search logs for errors.
- Locate configuration entries.
- Investigate authentication records.
- Find suspicious strings.
- Analyze command output.

When searching sensitive system files, remember that the results may contain confidential information.

---

# ⚠️ Best Practices

- Search only files and systems you are authorized to inspect.
- Be careful when searching sensitive configuration files.
- Use recursive searches thoughtfully.
- Verify search patterns before drawing conclusions.
- Combine `grep` with other command-line tools when appropriate.

---

# 📝 Questions

1. What is `grep`?
2. What does `grep` search for?
3. What does `-r` do?
4. What does `-A` do?
5. What does `-B` do?
6. Why is recursive searching useful?
7. How can `grep` help with log analysis?

---

# 🧪 Challenge

Create several text files containing different messages.

Then:

1. Search for a specific word.
2. Search the entire directory recursively.
3. Display two lines after matches.
4. Display two lines before matches.
5. Display context on both sides.

---

# 🧹 Cleanup

Remove the practice directory:

```bash
rm -rf ~/grep-lab
```

---

# ✅ Lab Completion Checklist

- [ ] I understand `grep`.
- [ ] I can search a file.
- [ ] I can search recursively.
- [ ] I understand `-A`.
- [ ] I understand `-B`.
- [ ] I can display context around matches.
- [ ] I understand the security applications of grep.
- [ ] I completed the challenge.
- [ ] I cleaned up my test files.

---

## 🚀 Next Lab

**Lab 34 — sed for Text Manipulation**
