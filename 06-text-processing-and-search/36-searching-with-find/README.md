# Lab 36 — Searching with find

> Learn how to search for files and directories using conditions such as filename and size, and execute commands on files discovered by `find`.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand the `find` command.
- Search for files by name.
- Search for files based on size.
- Work with the home directory.
- Understand search conditions.
- Use `-exec` with `find`.
- Process files discovered during a search.

---

## 📚 Prerequisites

Before starting this lab, you should have:

- A Linux or Unix-like operating system.
- Terminal access.
- Basic command-line knowledge.
- Familiarity with Linux directories.
- Basic understanding of file attributes.

---

# 1. Understanding find

The `find` command is used to search for files and directories according to specified conditions.

It is useful for:

- Locating files.
- Searching directory trees.
- Finding files based on size.
- Automating file processing.
- Performing administrative tasks.

---

# 2. Searching for Files by Name

The basic structure is:

```bash
find LOCATION -name "PATTERN"
```

For example:

```bash
find ~ -name "*.txt"
```

Here:

- `~` represents the current user's home directory.
- `-name` specifies that the filename should be matched.
- `"*.txt"` matches filenames ending in `.txt`.

---

# 3. Finding Files Larger Than 1 MB

The `-size` condition can be used to search by file size.

For example:

```bash
find ~ -size +1M
```

This searches the home directory for files larger than 1 megabyte.

---

# 4. Understanding Search Conditions

`find` can use different conditions to narrow down results.

Examples include:

- Filename
- File size
- File type
- Location

Using conditions makes searches more precise.

---

# 5. Using `-exec`

The `-exec` option allows another command to be executed for each file found.

For example:

```bash
find ~ -name "*.txt" -exec wc -l {} \;
```

This searches for `.txt` files and runs:

```bash
wc -l
```

against each matching file.

---

# 6. Understanding `{}`

In:

```bash
find ~ -name "*.txt" -exec wc -l {} \;
```

the:

```text
{}
```

placeholder is replaced by the path of each file found.

The:

```text
\;
```

marks the end of the `-exec` command.

---

# 🧪 Practical Lab

## Task 1 — Create a Practice Directory

Create:

```bash
mkdir -p ~/find-lab
cd ~/find-lab
```

Create several text files:

```bash
touch file1.txt file2.txt notes.txt report.log
```

Verify:

```bash
ls -l
```

---

## Task 2 — Search for `.txt` Files

Run:

```bash
find ~/find-lab -name "*.txt"
```

Observe the files returned.

---

## Task 3 — Search the Home Directory

You can search your complete home directory:

```bash
find ~ -name "*.txt"
```

This may return many results depending on your system.

---

## Task 4 — Search by Size

Run:

```bash
find ~/find-lab -size +1M
```

The practice files are normally smaller than 1 MB, so this may produce no output.

The important concept is the search condition.

---

## Task 5 — Create a Larger Test File

Create a test file larger than 1 MB:

```bash
dd if=/dev/zero of=~/find-lab/large-test.bin bs=1M count=2
```

Check its size:

```bash
ls -lh ~/find-lab/large-test.bin
```

Search for files larger than 1 MB:

```bash
find ~/find-lab -size +1M
```

---

## Task 6 — Use `-exec`

Add some text to the practice files:

```bash
echo "Linux administration" > ~/find-lab/file1.txt
echo "Text processing" > ~/find-lab/file2.txt
echo "System security" > ~/find-lab/notes.txt
```

Count lines in all `.txt` files:

```bash
find ~/find-lab -name "*.txt" -exec wc -l {} \;
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `find ~ -name "*.txt"` | Find `.txt` files in the home directory |
| `find LOCATION -name "PATTERN"` | Search by filename |
| `find ~ -size +1M` | Find files larger than 1 MB |
| `find LOCATION -exec COMMAND {} \;` | Execute a command on found files |
| `{}` | Placeholder for each found path |

---

# 🧠 Key Concepts

### find

A command for searching files and directories.

### Search Criteria

Conditions determine which files are returned.

### `-name`

Searches according to filename patterns.

### `-size`

Searches according to file size.

### `-exec`

Runs another command against files discovered by `find`.

### `{}`

Represents the current file returned by the search.

---

# 🛡️ Security Perspective

`find` is an important system-administration and security tool.

It can help locate:

- Unexpected files.
- Large files.
- Configuration files.
- Specific file types.
- Files requiring further investigation.

Combined with `-exec`, it can also automate processing of large numbers of files.

Because `-exec` can run commands against many files, it should be used carefully.

---

# ⚠️ Best Practices

- Test searches on a dedicated directory first.
- Review results before performing operations.
- Be especially careful when combining `find` with `-exec`.
- Avoid destructive commands while learning.
- Use precise search conditions.
- Do not modify files you are not authorized to manage.

---

# 📝 Questions

1. What is the purpose of `find`?
2. What does `-name` do?
3. What does `"*.txt"` mean?
4. What does `-size +1M` search for?
5. What is the purpose of `-exec`?
6. What does `{}` represent?
7. What does `\;` indicate?
8. Why should `-exec` be used carefully?
9. How can `find` help with system administration?
10. How can `find` assist in security investigations?

---

# 🧪 Challenge

Using your practice directory:

1. Find all `.txt` files.
2. Find files larger than 1 MB.
3. Use `-exec` to count lines in every `.txt` file.
4. Create another file type and search for it.
5. Experiment with different filename patterns.

Do not use destructive commands for the challenge.

---

# 🧹 Cleanup

Remove the practice directory:

```bash
rm -rf ~/find-lab
```

---

# 📝 Summary

In this lab, you learned how to use `find` to locate files according to specific criteria.

You practiced:

- Filename searches.
- Size-based searches.
- Working with the home directory.
- Using search patterns.
- Executing commands on discovered files with `-exec`.

These techniques are useful for Linux administration, file management, automation, and security investigations.

---

# ✅ Lab Completion Checklist

- [ ] I understand the `find` command.
- [ ] I can search by filename.
- [ ] I can use wildcard patterns with `-name`.
- [ ] I can search by file size.
- [ ] I understand `-exec`.
- [ ] I understand `{}`.
- [ ] I understand `\;`.
- [ ] I can use `find` safely.
- [ ] I completed the challenge.
- [ ] I cleaned up my practice files.

---

## 🎉 Section 06 Complete

You have now completed:

- **Lab 32 — Introduction to vi/vim**
- **Lab 33 — Basic Grep Usage**
- **Lab 34 — sed for Text Manipulation**
- **Lab 35 — awk for Data Processing**
- **Lab 36 — Searching with find**

The next section is:

**Section 07 — System Monitoring & Services**

Starting with **Lab 37 — Basic System Logs**.
