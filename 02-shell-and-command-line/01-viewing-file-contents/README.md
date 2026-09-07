# Lab 08 — Viewing File Contents

> Learn how to inspect, browse, and search text files using `head`, `tail`, `more`, and `grep`.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- View the beginning of a file with `head`
- View the end of a file with `tail`
- Control how many lines are displayed
- Browse files interactively with `more`
- Search for specific text using `grep`
- Perform case-insensitive searches
- Search recursively through directories
- Understand how these commands are useful when working with large files and system logs

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Access to a Linux system
- A terminal
- Basic knowledge of navigating directories
- Basic knowledge of Linux files
- Completion of the previous Linux fundamentals labs

> **Note:** The exercises in this lab can be completed without root privileges.

---

# 1. Preparing the Lab Environment

For this lab, create a dedicated workspace so that the exercises do not interfere with important files.

Create the directory:

```bash
mkdir -p ~/linux-labs/lab-08-viewing-file-contents
```

Move into it:

```bash
cd ~/linux-labs/lab-08-viewing-file-contents
```

Verify your location:

```bash
pwd
```

---

## 1.1 Create a Practice File

Create a sample text file containing several lines:

```bash
printf '%s\n' \
'Linux is a powerful operating system.' \
'Linux provides many command-line utilities.' \
'System administrators use Linux every day.' \
'Security professionals often analyze Linux systems.' \
'The command line provides powerful tools.' \
'Logs can contain thousands of lines.' \
'The head command displays the beginning of a file.' \
'The tail command displays the end of a file.' \
'The more command allows interactive viewing.' \
'The grep command searches for matching text.' \
'Linux networking provides many useful tools.' \
'Linux permissions help protect system resources.' \
'System logs are important for troubleshooting.' \
'Security monitoring often involves searching logs.' \
'Learning Linux requires regular practice.' \
'Command-line skills are valuable for administrators.' \
'Files can be inspected without opening a graphical editor.' \
'Large files require efficient viewing techniques.' \
'Text processing is an important Linux skill.' \
'This is the final practice line.' > practice.txt
```

Verify that the file exists:

```bash
ls -l
```

You should see:

```text
practice.txt
```

---

# 2. Viewing the Beginning of a File with `head`

The `head` command displays the beginning of a text file.

By default, `head` displays the first **10 lines**.

### Basic syntax

```bash
head filename
```

### Example

```bash
head practice.txt
```

This displays the first 10 lines of `practice.txt`.

---

## 2.1 Displaying a Specific Number of Lines

The `-n` option allows you to specify how many lines should be displayed.

For example, display the first 5 lines:

```bash
head -n 5 practice.txt
```

Display the first 3 lines:

```bash
head -n 3 practice.txt
```

Display the first 15 lines:

```bash
head -n 15 practice.txt
```

---

## 2.2 Why `head` Is Useful

`head` is especially useful when working with large files.

Instead of displaying an entire file, you can quickly inspect its beginning.

For example:

```bash
head /var/log/syslog
```

or on systems using different log locations:

```bash
head /var/log/messages
```

> **Note:** The exact log files available depend on the Linux distribution and logging configuration.

---

# 3. Viewing the End of a File with `tail`

The `tail` command displays the end of a file.

By default, it displays the last **10 lines**.

### Basic syntax

```bash
tail filename
```

### Example

```bash
tail practice.txt
```

This displays the last 10 lines of the file.

---

## 3.1 Displaying a Specific Number of Lines

Use `-n` to specify the number of lines.

Display the last 5 lines:

```bash
tail -n 5 practice.txt
```

Display the last 15 lines:

```bash
tail -n 15 practice.txt
```

Display the last 3 lines:

```bash
tail -n 3 practice.txt
```

---

## 3.2 Why `tail` Is Useful

`tail` is particularly useful when checking the most recent entries in files such as logs.

For example:

```bash
tail /var/log/syslog
```

This can provide a quick view of recent log entries.

> **Security perspective:** Security administrators may use `tail` as a quick first step when inspecting recent system activity.

---

# 4. Paging Through a File with `more`

The `more` command allows you to view a file one screen at a time.

This is useful when a file contains more information than can comfortably fit on the terminal screen.

### Basic syntax

```bash
more filename
```

### Example

```bash
more practice.txt
```

The file will be displayed interactively.

---

## 4.1 Basic `more` Navigation

While viewing a file with `more`:

| Key | Action |
|---|---|
| `Space` | Move down by one page |
| `Enter` | Move down by one line |
| `q` | Quit the viewer |

For example:

```bash
more practice.txt
```

Then:

1. Press **Space** to move down a page.
2. Press **Enter** to move down one line.
3. Press **q** to exit.

---

## 4.2 Why Paging Is Useful

Imagine a log file contains thousands of lines.

Displaying everything at once can make the output difficult to inspect.

Using:

```bash
more filename
```

allows you to examine the content gradually.

---

# 5. Searching Text with `grep`

The `grep` command searches text and displays lines that match a specified pattern.

### Basic syntax

```bash
grep "search-term" filename
```

### Example

Search for the word `Linux`:

```bash
grep "Linux" practice.txt
```

Only lines containing the matching text will be displayed.

---

## 5.1 Searching for Another Term

Search for `command`:

```bash
grep "command" practice.txt
```

Search for `security`:

```bash
grep "security" practice.txt
```

Search for `logs`:

```bash
grep "logs" practice.txt
```

---

## 5.2 Case-Insensitive Searching

By default, `grep` is case-sensitive.

For example:

```bash
grep "linux" practice.txt
```

may not match:

```text
Linux is a powerful operating system.
```

because `Linux` and `linux` have different capitalization.

Use the `-i` option for a case-insensitive search:

```bash
grep -i "linux" practice.txt
```

This can match:

```text
Linux
linux
LINUX
```

---

## 5.3 Searching Recursively

The `-r` option allows `grep` to search through files inside a directory and its subdirectories.

### Basic syntax

```bash
grep -r "search-term" directory
```

### Example

Create another directory:

```bash
mkdir logs
```

Create a few practice files:

```bash
printf '%s\n' \
'Linux system log entry' \
'Normal system activity' \
'Security event detected' > logs/system.log
```

```bash
printf '%s\n' \
'User login recorded' \
'Linux authentication event' \
'Security monitoring active' > logs/security.log
```

Search the entire `logs` directory for `Linux`:

```bash
grep -r "Linux" logs/
```

Search case-insensitively:

```bash
grep -ri "linux" logs/
```

---

# 🧪 Practical Lab

Perform the following tasks inside:

```text
~/linux-labs/lab-08-viewing-file-contents
```

---

## Task 1 — Inspect the Beginning of a File

Display the first 10 lines:

```bash
head practice.txt
```

Then display only the first 5 lines:

```bash
head -n 5 practice.txt
```

### Verify

Confirm that the second command displays fewer lines than the first command.

---

## Task 2 — Inspect the End of a File

Display the last 10 lines:

```bash
tail practice.txt
```

Then display only the last 5 lines:

```bash
tail -n 5 practice.txt
```

### Verify

Confirm that the displayed content comes from the end of the file.

---

## Task 3 — Browse the File with `more`

Run:

```bash
more practice.txt
```

Practice the following:

```text
Space → next page
Enter → next line
q → quit
```

### Verify

You should be able to move through the file and exit the viewer.

---

## Task 4 — Search for Text

Search for `Linux`:

```bash
grep "Linux" practice.txt
```

Search for `command`:

```bash
grep "command" practice.txt
```

Search for `security`:

```bash
grep "security" practice.txt
```

---

## Task 5 — Perform a Case-Insensitive Search

Run:

```bash
grep -i "linux" practice.txt
```

Compare the result with:

```bash
grep "linux" practice.txt
```

### Question

Why can the first command find matches that the second command does not?

---

## Task 6 — Search a Directory Recursively

Search the `logs` directory for `Linux`:

```bash
grep -r "Linux" logs/
```

Now perform a case-insensitive recursive search:

```bash
grep -ri "linux" logs/
```

### Verify

The command should search through the files inside the `logs` directory.

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `head file` | Display the beginning of a file |
| `head -n 5 file` | Display the first 5 lines |
| `tail file` | Display the end of a file |
| `tail -n 5 file` | Display the last 5 lines |
| `more file` | Browse a file interactively |
| `grep "text" file` | Search for text |
| `grep -i "text" file` | Search without case sensitivity |
| `grep -r "text" directory` | Search recursively |
| `grep -ri "text" directory` | Recursive case-insensitive search |
| `pwd` | Display the current directory |
| `ls -l` | Display detailed file information |

---

# 🧠 Key Concepts

## `head`

Displays the beginning of a file.

```bash
head practice.txt
```

Specify the number of lines:

```bash
head -n 5 practice.txt
```

---

## `tail`

Displays the end of a file.

```bash
tail practice.txt
```

Specify the number of lines:

```bash
tail -n 5 practice.txt
```

---

## `more`

Provides interactive file viewing.

```bash
more practice.txt
```

Useful navigation:

```text
Space → next page
Enter → next line
q → quit
```

---

## `grep`

Searches for matching text.

```bash
grep "Linux" practice.txt
```

Case-insensitive search:

```bash
grep -i "linux" practice.txt
```

Recursive search:

```bash
grep -r "Linux" logs/
```

Recursive case-insensitive search:

```bash
grep -ri "linux" logs/
```

---

# 🛡️ Security Perspective

The commands covered in this lab are simple but extremely useful for Linux administration and security work.

Security professionals frequently need to inspect:

- System logs
- Authentication records
- Application logs
- Configuration files
- Network-related information
- Security events
- Error messages

For example, `grep` can help locate relevant entries inside a large collection of logs:

```bash
grep -i "error" logfile
```

Likewise, `tail` can quickly show the most recent entries:

```bash
tail logfile
```

And `head` can provide a quick overview of the beginning of a file:

```bash
head logfile
```

The important skill is knowing how to **inspect large amounts of text efficiently without needing to display an entire file**.

---

# ⚠️ Best Practices

### 1. Know which file you are inspecting

Before running commands, verify the file:

```bash
ls -l
```

### 2. Confirm your location

```bash
pwd
```

### 3. Use `head` and `tail` for quick inspection

Instead of displaying a very large file completely, inspect only the portion you need.

### 4. Use `grep` to narrow information

Searching for a relevant term is usually more efficient than manually reading thousands of lines.

### 5. Be careful when searching sensitive files

System logs and configuration files can contain sensitive information. Only inspect files you are authorized to access.

---

# 📝 Questions

1. What is the purpose of the `head` command?
2. How many lines does `head` display by default?
3. How can you display only the first 5 lines of a file?
4. What is the purpose of `tail`?
5. How can you display the last 15 lines of a file?
6. What is the purpose of the `more` command?
7. Which key exits `more`?
8. What does `grep` do?
9. What is the difference between `grep "linux"` and `grep -i "linux"`?
10. What does the `-r` option do with `grep`?
11. Why are `head`, `tail`, and `grep` useful when analyzing large log files?
12. Why should you be careful when inspecting sensitive system files?

---

# 🧪 Challenge

Without looking at the examples above, try to complete the following:

### Challenge 1

Display the first 7 lines of `practice.txt`.

### Challenge 2

Display the last 8 lines of `practice.txt`.

### Challenge 3

Use `more` to browse `practice.txt`.

### Challenge 4

Find every line containing `system`.

### Challenge 5

Find every occurrence of `LINUX`, `Linux`, or `linux`.

### Challenge 6

Search recursively through the `logs` directory for the word `security`, ignoring capitalization.

---

# 🧹 Lab Cleanup

When you have finished the exercises, you can remove the practice environment.

First verify where you are:

```bash
pwd
```

Then inspect the lab directory:

```bash
ls -la
```

If you are certain that the directory contains only your practice material, you can remove the lab workspace:

```bash
rm -r ~/linux-labs/lab-08-viewing-file-contents
```

> **Safety:** Never use recursive deletion on a directory unless you have verified the path and contents first.

---

# 📝 Lab Summary

In this lab, you learned four fundamental Linux file-viewing and searching utilities:

```text
head → beginning of a file
tail → end of a file
more → interactive file viewing
grep → searching text
```

You also learned how to:

- Control the number of displayed lines
- Search without considering capitalization
- Search through directories recursively
- Inspect large text files efficiently
- Apply these tools to practical Linux administration and security tasks

These commands form an important foundation for later work with **Linux logs, text processing, troubleshooting, monitoring, and security analysis**.

---

# ✅ Lab Completion Checklist

- [ ] I can use `head` to view the beginning of a file
- [ ] I can use `head -n` to control the number of lines
- [ ] I can use `tail` to view the end of a file
- [ ] I can use `tail -n` to control the number of lines
- [ ] I can use `more` to browse a file
- [ ] I know how to navigate and exit `more`
- [ ] I can search files with `grep`
- [ ] I understand case-sensitive searches
- [ ] I can perform case-insensitive searches with `grep -i`
- [ ] I can search directories recursively with `grep -r`
- [ ] I understand how these commands can help with log analysis
- [ ] I can safely inspect files from the Linux command line

---

## 🚀 Next Lab

**Lab 09 — Working with Links**
