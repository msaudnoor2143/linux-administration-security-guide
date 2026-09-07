# Lab 07 — Using Wildcards

> **Level:** Beginner  
> **Category:** Linux Fundamentals  
> **Focus:** Shell Pattern Matching & File Management

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand Linux shell wildcards.
- Use wildcards for efficient file management.
- Understand pattern matching in filenames.
- Use `*` to match multiple characters.
- Use `?` to match exactly one character.
- Combine wildcards with commands such as `cp` and `rm`.
- Verify wildcard operations safely before making changes.

---

## 📋 Prerequisites

Before starting this lab, you should understand:

- Basic Linux terminal navigation.
- `pwd`
- `ls`
- `cd`
- `mkdir`
- `touch`
- `cp`
- `rm`

---

## 🧠 Key Concepts

### What Are Wildcards?

Wildcards are special characters interpreted by the Linux shell to match filenames and directory names according to a pattern.

The two wildcards covered in this lab are:

| Wildcard | Meaning | Example |
|---|---|---|
| `*` | Matches zero or more characters | `*.txt` |
| `?` | Matches exactly one character | `file?.txt` |

For example:

```text
file1.txt
file2.txt
report1.txt
report2.txt
notes.txt
```

The pattern:

```bash
*.txt
```

matches all of these files.

The pattern:

```bash
file?.txt
```

matches:

```text
file1.txt
file2.txt
```

but does not match:

```text
report1.txt
```

---

# 🧪 Lab Environment Setup

Create a dedicated directory so that wildcard commands do not accidentally affect unrelated files.

```bash
mkdir -p ~/linux-labs/lab-07-wildcards
cd ~/linux-labs/lab-07-wildcards

touch file1.txt file2.txt report1.txt report2.txt notes.txt

ls -l
```

Expected files:

```text
file1.txt
file2.txt
report1.txt
report2.txt
notes.txt
```

---

# 🔹 Task 1 — Understanding the `*` Wildcard

The asterisk `*` represents **zero or more characters**.

For example:

```bash
*.txt
```

means:

> Match any filename that ends with `.txt`.

Since all of our test files have the `.txt` extension, this pattern should match all of them.

## 1.1 Test the Pattern

Before performing an operation, you can use `printf` to see which files the shell expands the pattern to:

```bash
printf '%s\n' *.txt
```

Expected output:

```text
file1.txt
file2.txt
notes.txt
report1.txt
report2.txt
```

This is a useful habit when working with potentially destructive wildcard commands.

---

## 1.2 Create a Backup Directory

```bash
mkdir backup
```

Verify it:

```bash
ls -ld backup
```

---

## 1.3 Copy All Text Files

Use `cp` together with `*.txt`:

```bash
cp *.txt backup/
```

The shell expands `*.txt` into the matching filenames before `cp` receives the arguments.

Conceptually:

```text
cp file1.txt file2.txt notes.txt report1.txt report2.txt backup/
```

---

## 1.4 Verify the Copy

```bash
ls -l backup/
```

You should see:

```text
file1.txt
file2.txt
notes.txt
report1.txt
report2.txt
```

You can also compare the contents:

```bash
diff file1.txt backup/file1.txt
```

If there is no output, the files have identical contents.

---

# 🔹 Task 2 — Understanding the `?` Wildcard

The question mark `?` represents **exactly one character**.

Consider:

```bash
file?.txt
```

This pattern matches:

```text
file1.txt
file2.txt
```

because `?` represents one character.

It does not match:

```text
file10.txt
```

because `10` contains two characters.

---

## 2.1 Test the Pattern Safely

Before deleting anything, first display what the pattern matches:

```bash
printf '%s\n' file?.txt
```

Expected output:

```text
file1.txt
file2.txt
```

---

## 2.2 Remove the Matching Files

Now remove the files matched by the pattern:

```bash
rm file?.txt
```

---

## 2.3 Verify the Result

```bash
ls -l
```

The original directory should now contain:

```text
backup
notes.txt
report1.txt
report2.txt
```

The files:

```text
file1.txt
file2.txt
```

have been removed.

The copies inside `backup/` should still exist.

Verify:

```bash
ls -l backup/
```

---

# 🔹 Task 3 — More Wildcard Examples

Wildcards become particularly useful when working with large numbers of files.

Assume a directory contains:

```text
server.log
application.log
database.log
notes.txt
report.txt
image.png
```

### Match all `.log` files

```bash
ls *.log
```

### Match all `.txt` files

```bash
ls *.txt
```

### Match filenames beginning with `server`

```bash
ls server*
```

### Match filenames beginning with `report`

```bash
ls report*
```

### Match a single-character variation

```bash
ls file?.txt
```

---

# 🔹 Task 4 — Practice Challenge

Create another set of test files:

```bash
cd ~/linux-labs/lab-07-wildcards

touch server1.log server2.log server10.log client1.log client2.log notes.txt
```

List all log files:

```bash
printf '%s\n' *.log
```

List files beginning with `server`:

```bash
printf '%s\n' server*
```

List files matching `server?.log`:

```bash
printf '%s\n' server?.log
```

### Think About the Difference

The pattern:

```bash
server*.log
```

can match:

```text
server1.log
server2.log
server10.log
```

The pattern:

```bash
server?.log
```

matches:

```text
server1.log
server2.log
```

but not:

```text
server10.log
```

because `?` represents exactly one character.

---

# 🔐 Security Perspective

Wildcards are extremely useful in Linux administration, but they should be used carefully.

A command such as:

```bash
rm *.log
```

can remove many files at once.

Before using a destructive wildcard command, inspect the expansion first:

```bash
printf '%s\n' *.log
```

Then confirm that the listed files are actually the files you intend to modify.

### Good Practice

Prefer this workflow:

```text
1. Build the wildcard pattern
        ↓
2. Display what it matches
        ↓
3. Confirm the results
        ↓
4. Perform the operation
        ↓
5. Verify the result
```

This habit becomes especially important when working with production systems.

---

# ⚠️ Common Mistakes

### Mistake 1 — Confusing `*` and `?`

```bash
*.txt
```

matches zero or more characters.

```bash
?.txt
```

matches exactly one character before `.txt`.

---

### Mistake 2 — Assuming `?` Matches Multiple Characters

This:

```bash
server?.log
```

does not match:

```text
server10.log
```

because `10` contains two characters.

---

### Mistake 3 — Running `rm` Without Checking the Pattern

Avoid immediately running:

```bash
rm *.log
```

when you are unsure what it will match.

First use:

```bash
printf '%s\n' *.log
```

---

### Mistake 4 — Forgetting the Current Directory

Wildcards such as:

```bash
*.txt
```

normally operate on matching entries in the current working directory.

Check where you are with:

```bash
pwd
```

---

# 🔎 Useful Commands

| Command | Purpose |
|---|---|
| `pwd` | Display current directory |
| `ls` | List directory contents |
| `printf '%s\n' *.txt` | Display files matching a pattern |
| `touch` | Create files |
| `mkdir` | Create directories |
| `cp` | Copy files |
| `rm` | Remove files |
| `cd` | Change directory |

---

# 🧠 Knowledge Check

Answer these questions before moving to the next lab.

### 1. What does `*` represent?

<details>
<summary>Answer</summary>

Zero or more characters.

</details>

### 2. What does `?` represent?

<details>
<summary>Answer</summary>

Exactly one character.

</details>

### 3. What files could `*.txt` match?

<details>
<summary>Answer</summary>

Any files in the current directory whose names end with `.txt`.

</details>

### 4. Would `file?.txt` match `file10.txt`?

<details>
<summary>Answer</summary>

No. `?` represents exactly one character, while `10` contains two characters.

</details>

### 5. Why should you inspect a wildcard before using `rm`?

<details>
<summary>Answer</summary>

Because a wildcard can match multiple files, and an incorrect pattern could cause unintended files to be deleted.

</details>

---

# ✅ Completion Checklist

- [ ] I understand what wildcards are.
- [ ] I understand the `*` wildcard.
- [ ] I understand the `?` wildcard.
- [ ] I used `*.txt` with `cp`.
- [ ] I used `file?.txt` with `rm`.
- [ ] I verified wildcard expansion before a destructive operation.
- [ ] I understand why wildcards should be used carefully.
- [ ] I completed the practice challenge.
- [ ] I can explain the difference between `*` and `?`.

---

# 📌 Key Takeaways

The most important concepts from this lab are:

```text
*  → zero or more characters

?  → exactly one character

*.txt
→ matches files ending in .txt

file?.txt
→ matches file1.txt, file2.txt, etc.
→ does not match file10.txt
```

Wildcards make Linux file management much more efficient because they allow commands to operate on groups of files without specifying every filename individually.

At the same time, wildcard patterns should be reviewed carefully before destructive operations such as `rm`.

---

# 🚀 Next Lab

**Lab 08 — Viewing File Contents**
