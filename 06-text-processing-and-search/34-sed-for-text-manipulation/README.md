# Lab 34 — sed for Text Manipulation

> Learn how to use `sed`, the stream editor, to transform and manipulate text from files and command-line input.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand the purpose of `sed`.
- Perform basic text substitution.
- Replace multiple occurrences of text.
- Delete lines matching a pattern.
- Understand the `s` and `d` operations.
- Apply changes to command output.
- Modify files using in-place editing.

---

## 📚 Prerequisites

Before starting this lab, you should have:

- A Linux or Unix-like system.
- Terminal access.
- Basic command-line knowledge.
- Familiarity with text files.
- Basic understanding of patterns.

---

# 1. Understanding sed

`sed` is a **stream editor** used for filtering and transforming text.

It can process text from:

- Files
- Pipelines
- Standard input

Common operations include:

- Substitution
- Deletion
- Filtering
- Transformation

---

# 2. Create a Sample File

Create a practice file:

```bash
echo -e "Hello World\nHello Universe\nGoodbye World" > example.txt
```

View the file:

```bash
cat example.txt
```

---

# 3. Replacing Text

The basic substitution structure is:

```bash
sed 's/old/new/g' example.txt
```

For example:

```bash
sed 's/World/Earth/g' example.txt
```

This replaces occurrences of `World` with `Earth` in the command output.

---

# 4. Understanding the Substitution Syntax

Consider:

```bash
sed 's/World/Earth/g' example.txt
```

The components are:

| Component | Meaning |
|---|---|
| `s` | Substitute |
| `World` | Text to find |
| `Earth` | Replacement |
| `g` | Apply to all matches on each line |

---

# 5. Saving Changes to the File

By default, `sed` displays the transformed text without changing the original file.

To modify the file directly:

```bash
sed -i 's/World/Earth/g' example.txt
```

> ⚠️ Always be careful with `-i` because it changes the file itself.

---

# 6. Deleting Matching Lines

The deletion pattern is:

```bash
sed '/pattern/d' filename
```

For example:

```bash
sed '/Universe/d' example.txt
```

This displays the file without lines containing `Universe`.

---

# 7. Delete Lines In-Place

To permanently remove matching lines:

```bash
sed -i '/Universe/d' example.txt
```

Again, `-i` modifies the original file.

---

# 🧪 Practical Lab

## Task 1 — Create the Sample File

```bash
mkdir -p ~/sed-lab
cd ~/sed-lab
```

Create:

```bash
echo -e "Hello World\nHello Universe\nGoodbye World" > example.txt
```

View:

```bash
cat example.txt
```

---

## Task 2 — Replace Text

Run:

```bash
sed 's/World/Earth/g' example.txt
```

Notice that the displayed output changes while the original file remains unchanged.

Verify:

```bash
cat example.txt
```

---

## Task 3 — Save the Replacement

Run:

```bash
sed -i 's/World/Earth/g' example.txt
```

Verify:

```bash
cat example.txt
```

---

## Task 4 — Delete Matching Lines

Run:

```bash
sed '/Universe/d' example.txt
```

Observe the output.

---

## Task 5 — Delete the Lines Permanently

If you want to apply the deletion to the practice file:

```bash
sed -i '/Universe/d' example.txt
```

Verify:

```bash
cat example.txt
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `sed 's/old/new/g' file` | Replace text in displayed output |
| `sed -i 's/old/new/g' file` | Replace text directly in file |
| `sed '/pattern/d' file` | Display file without matching lines |
| `sed -i '/pattern/d' file` | Delete matching lines from file |

---

# 🧠 Key Concepts

### sed

A stream editor used for filtering and transforming text.

### Substitution

Uses the `s` operation:

```text
s/old/new/g
```

### Deletion

Uses the `d` operation:

```text
/pattern/d
```

### In-Place Editing

The `-i` option changes the original file.

---

# 🛡️ Security Perspective

`sed` is useful for automating configuration and log-processing tasks.

However, careless use can modify important files.

For example, changing configuration values incorrectly may affect system services.

Always test transformations before applying them to important files.

---

# ⚠️ Best Practices

- Test commands without `-i` first.
- Keep backups of important files.
- Work on copies when learning.
- Review output before saving changes.
- Avoid modifying system files without understanding the consequences.

---

# 📝 Questions

1. What is `sed`?
2. What does the `s` operation do?
3. What does the `g` flag mean?
4. What does `/pattern/d` do?
5. What does `-i` do?
6. Why should `-i` be used carefully?
7. How can sed help automate text processing?

---

# 🧪 Challenge

Create a file containing several repeated words.

Then:

1. Replace one word with another.
2. Display the modified output without changing the file.
3. Apply the replacement permanently.
4. Remove lines matching a pattern.
5. Verify the final file.

---

# 🧹 Cleanup

Remove the practice directory:

```bash
rm -rf ~/sed-lab
```

---

# ✅ Lab Completion Checklist

- [ ] I understand `sed`.
- [ ] I can perform substitutions.
- [ ] I understand the `s` operation.
- [ ] I understand the `g` flag.
- [ ] I can delete matching lines.
- [ ] I understand `-i`.
- [ ] I know why in-place editing should be used carefully.
- [ ] I completed the challenge.
- [ ] I cleaned up my practice files.

---

## 🚀 Next Lab

**Lab 35 — awk for Data Processing**
