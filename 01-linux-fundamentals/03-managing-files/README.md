# Lab 03 — Managing Files

> Learn how to create, inspect, modify, and safely remove files using essential Linux command-line tools.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Create empty files with `touch`
- Understand file timestamps
- Create files containing text
- Display file contents with `cat`
- Read files interactively with `less`
- Verify whether files exist
- Remove files with `rm`
- Understand the risks associated with file deletion
- Perform basic file-management operations safely

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Access to a Linux system
- A terminal
- Basic knowledge of `pwd`
- Basic knowledge of `ls`
- Completion of:
  - **Lab 01 — Navigating the Linux Filesystem**
  - **Lab 02 — Working with Directories**

> **Note:** These exercises should be performed inside a dedicated practice directory.

---

# 1. Create a Practice Directory

Before working with files, create a dedicated workspace.

Return to your home directory:

```bash
cd ~
```

Create a directory for this lab:

```bash
mkdir -p linux-file-management-lab
```

Enter it:

```bash
cd linux-file-management-lab
```

Verify your location:

```bash
pwd
```

You should see a path similar to:

```text
/home/your-user/linux-file-management-lab
```

> Your username and home-directory path will be different.

---

# 2. Creating an Empty File with `touch`

The `touch` command can create a new empty file.

### Basic syntax

```bash
touch filename
```

Create a file:

```bash
touch myfile.txt
```

Verify that it exists:

```bash
ls
```

You should see:

```text
myfile.txt
```

You can also inspect it with:

```bash
ls -l myfile.txt
```

---

## 2.1 Creating Multiple Files

`touch` can create multiple files in one command:

```bash
touch file1.txt file2.txt file3.txt
```

Verify:

```bash
ls
```

---

# 3. Understanding File Timestamps

`touch` is not only used to create files.

It can also update timestamps on an existing file.

For example:

```bash
touch myfile.txt
```

If `myfile.txt` already exists, `touch` updates its timestamps rather than creating another copy.

Inspect the timestamps with:

```bash
ls -l myfile.txt
```

For more detailed timestamp information:

```bash
stat myfile.txt
```

`stat` can display information such as:

- File size
- Permissions
- Owner
- Inode
- Access time
- Modification time
- Change time

---

# 4. Creating a File with Content

`touch` creates an empty file.

To create a file containing text, you can use `echo` with output redirection.

For example:

```bash
echo "Hello, this is a sample text file." > sample.txt
```

Verify:

```bash
ls
```

Then display the contents:

```bash
cat sample.txt
```

Expected output:

```text
Hello, this is a sample text file.
```

---

# 5. Understanding Output Redirection

The `>` operator redirects command output into a file.

For example:

```bash
echo "First line" > example.txt
```

This creates `example.txt` if it does not exist.

If the file already exists, `>` **overwrites its contents**.

For example:

```bash
echo "Second line" > example.txt
```

The original contents are replaced.

---

## 5.1 Appending to a File

The `>>` operator appends output instead of replacing the existing contents.

Example:

```bash
echo "First line" > example.txt
echo "Second line" >> example.txt
```

View the result:

```bash
cat example.txt
```

Output:

```text
First line
Second line
```

### Key Difference

```text
>    Replace file contents
>>   Append to existing contents
```

---

# 6. Viewing File Contents with `cat`

The `cat` command can display the contents of a file.

Example:

```bash
cat sample.txt
```

For a small file, `cat` is usually convenient.

---

## 6.1 Displaying Multiple Files

You can display multiple files:

```bash
cat file1.txt file2.txt
```

You can also combine their contents into another file:

```bash
cat file1.txt file2.txt > combined.txt
```

Verify:

```bash
cat combined.txt
```

---

# 7. Viewing Large Files with `less`

For larger files, displaying everything with `cat` may be inconvenient.

The `less` command provides an interactive way to read files.

Example:

```bash
less sample.txt
```

Inside `less`, you can navigate through the file.

Useful controls include:

| Key | Action |
|---|---|
| `Space` | Move down one page |
| `b` | Move back one page |
| `↑` | Move up |
| `↓` | Move down |
| `/word` | Search for a word |
| `n` | Next search result |
| `q` | Quit |

Press:

```text
q
```

to exit.

---

# 8. When to Use `cat` vs `less`

### Use `cat` when:

- The file is small
- You want to quickly display its contents
- You need to combine files

Example:

```bash
cat sample.txt
```

### Use `less` when:

- The file is large
- You need to scroll through content
- You need to search within a file
- You want controlled interactive viewing

Example:

```bash
less /var/log/syslog
```

> Some Linux distributions use different log files, so the example above may not exist on every system.

---

# 9. Checking Whether a File Exists

Use:

```bash
ls
```

to list files in the current directory.

For a specific file:

```bash
ls -l sample.txt
```

You can also use:

```bash
test -f sample.txt && echo "File exists"
```

If the file exists, the command prints:

```text
File exists
```

---

# 10. Removing a File with `rm`

The `rm` command removes files.

### Basic syntax

```bash
rm filename
```

For example:

```bash
rm myfile.txt
```

Verify:

```bash
ls
```

The file should no longer appear.

---

# ⚠️ Important: `rm` Is Destructive

Unlike moving a file to a graphical desktop trash/recycle bin, `rm` normally removes the file directly.

For example:

```bash
rm important.txt
```

can result in permanent data loss.

Always verify what you are deleting.

Before using `rm`, check:

```bash
pwd
```

and:

```bash
ls -la
```

---

# 11. Safer File Removal

The `-i` option asks for confirmation before deleting.

Example:

```bash
rm -i sample.txt
```

You may receive a prompt similar to:

```text
rm: remove regular file 'sample.txt'?
```

Enter:

```text
y
```

to confirm.

Enter:

```text
n
```

to cancel.

For beginners, `rm -i` is a useful way to reduce accidental deletion.

---

# 12. Wildcards and File Deletion

Linux supports wildcards.

For example:

```bash
*.txt
```

matches files ending in `.txt`.

You can use:

```bash
ls *.txt
```

to see matching files.

### ⚠️ Be extremely careful

A command such as:

```bash
rm *.txt
```

may delete **every matching `.txt` file in the current directory**.

Always inspect the files first:

```bash
ls *.txt
```

Then decide whether deletion is appropriate.

---

# 🧪 Practical Lab

Complete the following exercise inside:

```text
~/linux-file-management-lab
```

---

## Task 1 — Create Empty Files

Create three files:

```bash
touch notes.txt commands.txt security.txt
```

Verify:

```bash
ls -l
```

---

## Task 2 — Add Content

Write content to `notes.txt`:

```bash
echo "Linux filesystem practice" > notes.txt
```

Write content to `commands.txt`:

```bash
echo "pwd, ls, cd, touch, cat, less" > commands.txt
```

Write content to `security.txt`:

```bash
echo "Linux security requires careful file management." > security.txt
```

---

## Task 3 — View the Files

Display `notes.txt`:

```bash
cat notes.txt
```

Display `commands.txt`:

```bash
cat commands.txt
```

Display `security.txt`:

```bash
cat security.txt
```

---

## Task 4 — Append Information

Add another line to `security.txt`:

```bash
echo "Always verify paths before modifying or deleting files." >> security.txt
```

View the file:

```bash
cat security.txt
```

You should now see two lines.

---

## Task 5 — Inspect File Information

Run:

```bash
ls -l security.txt
```

Then:

```bash
stat security.txt
```

Identify:

- File size
- Permissions
- Owner
- Modification time

---

## Task 6 — Practice `less`

Open the file:

```bash
less security.txt
```

Press:

```text
q
```

to exit.

---

## Task 7 — Test Safe Deletion

Create a temporary file:

```bash
touch temporary.txt
```

Verify:

```bash
ls -l temporary.txt
```

Remove it safely:

```bash
rm -i temporary.txt
```

Confirm the deletion when prompted.

Then verify:

```bash
ls
```

---

## Task 8 — Inspect Before Deleting

Create three temporary files:

```bash
touch test1.txt test2.txt test3.txt
```

Before deleting anything, inspect them:

```bash
ls *.txt
```

Now remove only `test1.txt`:

```bash
rm -i test1.txt
```

Verify:

```bash
ls *.txt
```

You should still have:

```text
test2.txt
test3.txt
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `touch file` | Create an empty file or update timestamps |
| `ls` | List files |
| `ls -l` | Display detailed file information |
| `stat file` | Display detailed file metadata |
| `cat file` | Display file contents |
| `less file` | View a file interactively |
| `echo "text" > file` | Write/overwrite file contents |
| `echo "text" >> file` | Append to a file |
| `rm file` | Remove a file |
| `rm -i file` | Remove a file with confirmation |
| `test -f file` | Test whether a regular file exists |

---

# 🧠 Key Concepts

### `touch`

Creates an empty file or updates timestamps.

```bash
touch example.txt
```

### `cat`

Displays file contents.

```bash
cat example.txt
```

### `less`

Provides interactive file viewing.

```bash
less example.txt
```

### `>`

Redirects output and replaces existing file contents.

```bash
echo "Hello" > example.txt
```

### `>>`

Redirects output and appends to existing contents.

```bash
echo "Another line" >> example.txt
```

### `rm`

Removes files.

```bash
rm example.txt
```

### `rm -i`

Requests confirmation before deletion.

```bash
rm -i example.txt
```

---

# 🛡️ Security Perspective

File management is directly connected to Linux security.

Security professionals regularly work with:

- Configuration files
- Authentication information
- System logs
- Application files
- Scripts
- Evidence files
- Temporary files
- Security reports

For example:

```text
/etc
/var/log
/home
/tmp
```

Understanding how to safely inspect and manipulate files helps prevent accidental modification or deletion of important information.

During security investigations, commands such as:

```bash
cat
less
ls -l
stat
```

can help examine files and their metadata.

---

# ⚠️ Security & Safety Notes

### Verify your location

Before destructive operations:

```bash
pwd
```

### Inspect the target

```bash
ls -la
```

### Prefer confirmation

When learning:

```bash
rm -i file
```

is safer than immediately using:

```bash
rm file
```

### Be cautious with wildcards

Never blindly run:

```bash
rm *
```

or:

```bash
rm *.txt
```

until you understand exactly which files match the pattern.

### Avoid system directories

Do not experiment with deletion inside directories such as:

```text
/etc
/usr
/bin
/sbin
/boot
```

unless you specifically understand the administrative task and its consequences.

---

# 📝 Questions

1. What is the purpose of `touch`?
2. What happens when `touch` is used on an existing file?
3. What is the difference between `cat` and `less`?
4. What does the `>` operator do?
5. What does the `>>` operator do?
6. What is the purpose of `rm`?
7. Why can `rm` be dangerous?
8. What does `rm -i` provide?
9. Why should you inspect wildcard matches before using `rm`?
10. What information can `stat` provide about a file?
11. Why is file management important in cybersecurity?

---

# ✅ Lab Completion Checklist

- [ ] I can create empty files with `touch`
- [ ] I understand basic file timestamps
- [ ] I can create files containing text
- [ ] I can view files with `cat`
- [ ] I can navigate large files with `less`
- [ ] I understand `>` and `>>`
- [ ] I can inspect file metadata with `stat`
- [ ] I can safely remove files with `rm -i`
- [ ] I understand wildcard risks
- [ ] I can verify files before modifying or deleting them
- [ ] I understand the security importance of file management

---

## 🚀 Next Lab

**Lab 04 — Using Text Editors**
