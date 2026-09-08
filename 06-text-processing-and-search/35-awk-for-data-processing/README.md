# Lab 35 — awk for Data Processing

> Learn the fundamentals of `awk` for extracting columns and filtering rows from structured text data.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand the basic purpose of `awk`.
- Work with fields and records.
- Print selected columns.
- Filter rows using conditions.
- Print complete matching records.
- Apply `awk` to structured text data.

---

## 📚 Prerequisites

Before starting this lab, you should have:

- A Unix/Linux system.
- Terminal access.
- Basic command-line knowledge.
- Basic understanding of text files.
- Familiarity with whitespace-separated data.

---

# 1. Understanding awk

`awk` is a text-processing language commonly used for processing structured data.

It is particularly useful when data is organized into fields or columns.

For example:

```text
Name Age Gender
John 28 Male
Emma 22 Female
Mike 32 Male
Lucy 29 Female
```

Each line represents a record, while the individual values represent fields.

---

# 2. Create a Sample Data File

Create a practice directory:

```bash
mkdir -p ~/awk-lab
cd ~/awk-lab
```

Create the data file:

```bash
echo -e "Name Age Gender\nJohn 28 Male\nEmma 22 Female\nMike 32 Male\nLucy 29 Female" > data.txt
```

View it:

```bash
cat data.txt
```

---

# 3. Understanding awk Fields

In `awk`:

```text
$1
```

represents the first field.

```text
$2
```

represents the second field.

```text
$3
```

represents the third field.

```text
$0
```

represents the entire current record.

---

# 4. Printing Specific Columns

To print the first and third columns:

```bash
awk '{print $1, $3}' data.txt
```

This extracts:

- Name
- Gender

from the sample data.

---

# 5. Understanding the Command

Consider:

```bash
awk '{print $1, $3}' data.txt
```

The components mean:

- `awk` — execute the awk processor
- `{print ...}` — specify what to output
- `$1` — first field
- `$3` — third field
- `data.txt` — input file

---

# 6. Filtering Rows

`awk` can use conditions to decide which rows should be displayed.

For example:

```bash
awk '$2 > 25 {print $0}' data.txt
```

This checks whether the second field is greater than `25`.

Only matching records are printed.

---

# 7. Understanding `$0`

The variable:

```text
$0
```

represents the complete current line.

Therefore:

```bash
awk '$2 > 25 {print $0}' data.txt
```

prints the entire record when the age is greater than 25.

---

# 🧪 Practical Lab

## Task 1 — Create the Data File

```bash
mkdir -p ~/awk-lab
cd ~/awk-lab
```

Create:

```bash
echo -e "Name Age Gender\nJohn 28 Male\nEmma 22 Female\nMike 32 Male\nLucy 29 Female" > data.txt
```

Verify:

```bash
cat data.txt
```

---

## Task 2 — Print Name and Gender

Run:

```bash
awk '{print $1, $3}' data.txt
```

Observe how `awk` extracts selected columns.

---

## Task 3 — Filter by Age

Run:

```bash
awk '$2 > 25 {print $0}' data.txt
```

This displays records where the second field is greater than 25.

---

## Task 4 — Experiment with Columns

Print only names:

```bash
awk '{print $1}' data.txt
```

Print only ages:

```bash
awk '{print $2}' data.txt
```

Print only genders:

```bash
awk '{print $3}' data.txt
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `awk '{print $1}' file` | Print first field |
| `awk '{print $1, $3}' file` | Print selected fields |
| `awk '{print $0}' file` | Print complete record |
| `awk '$2 > 25 {print $0}' file` | Filter records by condition |

---

# 🧠 Key Concepts

### Record

A line of input processed by `awk`.

### Field

A value within a record.

### `$1`

First field.

### `$2`

Second field.

### `$3`

Third field.

### `$0`

Complete current record.

### Condition

A rule that determines whether a record should be processed.

---

# 🛡️ Security Perspective

`awk` is widely useful in system administration and security work.

It can help process:

- Log files
- Reports
- Network data
- User information
- System statistics
- Structured command output

For example, administrators can use field-based processing to extract relevant information from large log files.

---

# ⚠️ Best Practices

- Understand the structure of the input data.
- Test commands on sample files first.
- Verify field positions before interpreting results.
- Avoid making assumptions about data formatting.
- Protect sensitive data while processing it.

---

# 📝 Questions

1. What is `awk`?
2. What does `$1` represent?
3. What does `$2` represent?
4. What does `$3` represent?
5. What does `$0` represent?
6. How can `awk` print selected columns?
7. How can `awk` filter records?
8. Why is `awk` useful for log processing?

---

# 🧪 Challenge

Using `data.txt`:

1. Print only the names.
2. Print only the ages.
3. Print name and gender.
4. Display users older than 25.
5. Create your own condition and filter the records.

---

# 🧹 Cleanup

Remove the practice directory:

```bash
rm -rf ~/awk-lab
```

---

# ✅ Lab Completion Checklist

- [ ] I understand the purpose of awk.
- [ ] I understand fields and records.
- [ ] I can print specific columns.
- [ ] I understand `$1`, `$2`, `$3`, and `$0`.
- [ ] I can filter rows using conditions.
- [ ] I completed the challenge.
- [ ] I cleaned up my practice files.

---

## 🚀 Next Lab

**Lab 36 — Searching with find**
