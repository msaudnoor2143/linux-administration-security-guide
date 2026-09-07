# Lab 13 — Using Piping and Redirection

> Learn how to redirect command output to files, append information to existing files, and connect commands using pipes.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand input and output redirection in Linux
- Redirect command output to a file
- Use the `>` operator
- Append output to an existing file using `>>`
- Understand and use the pipe `|` operator
- Connect multiple commands together
- Build simple command-line workflows
- Understand how piping and redirection improve command-line efficiency

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Access to a Linux system
- A terminal or Linux command-line interface
- Basic familiarity with Linux commands
- Basic understanding of command output
- Completion of **Lab 12 — Basic Shell Scripting**

> **Note:** The exercises in this lab can be completed without root privileges.

---

# 1. Understanding Redirection

Linux commands normally receive input from standard input and send their output to standard output.

For example:

```bash
ls
```

normally displays the directory contents directly in the terminal.

Linux allows us to redirect that output somewhere else, such as a file.

This is called **output redirection**.

---

# 2. Redirecting Command Output with `>`

The `>` operator redirects the output of a command into a file.

### Basic syntax

```bash
command > filename
```

For example:

```bash
ls > output.txt
```

Instead of displaying the output of `ls` directly on the terminal, the output is written to:

```text
output.txt
```

---

## 2.1 Create a Practice Directory

It is good practice to perform exercises inside a dedicated directory.

Run:

```bash
mkdir -p ~/linux-piping-lab
cd ~/linux-piping-lab
```

Verify your location:

```bash
pwd
```

---

# 🧪 Practical Lab

## Task 1 — Redirect Command Output to a File

Run:

```bash
ls > output.txt
```

The command creates `output.txt` and stores the output of `ls` inside it.

View the file:

```bash
cat output.txt
```

You should see the directory contents that were produced by the `ls` command.

### Key Concept

The `>` operator **overwrites** the target file if it already exists.

For example:

```bash
ls > output.txt
```

If `output.txt` already contains information, its previous contents will be replaced by the new command output.

---

## Task 2 — Append Output to a File

The `>>` operator is used to append output to an existing file.

Unlike `>`, it does not replace the existing contents.

Run:

```bash
echo "Additional content" >> output.txt
```

Now display the file:

```bash
cat output.txt
```

You should see the original `ls` output followed by:

```text
Additional content
```

### Key Concept

The difference between the two operators is important:

```text
>   Overwrites the file
>>  Appends to the file
```

For example:

```bash
echo "First line" > example.txt
```

creates or replaces the file.

Then:

```bash
echo "Second line" >> example.txt
```

adds new content to the end.

Verify:

```bash
cat example.txt
```

---

# 3. Using Pipes

A pipe allows the output of one command to become the input of another command.

The pipe operator is:

```bash
|
```

### Basic syntax

```bash
command1 | command2
```

The output from `command1` is passed directly to `command2`.

This allows multiple small commands to be combined into a useful workflow.

---

## Task 3 — Pipe Output from One Command to Another

Run:

```bash
ps aux | grep bash
```

This command combines two commands.

### First command

```bash
ps aux
```

Displays information about running processes.

### Pipe

```bash
|
```

Passes the output of `ps aux` to the next command.

### Second command

```bash
grep bash
```

Searches the received output for lines containing:

```text
bash
```

Therefore:

```bash
ps aux | grep bash
```

can be used to locate processes related to Bash.

---

# 4. Combining Multiple Commands

Pipes can be chained together.

For example:

```bash
ps aux | grep bash | head
```

This workflow:

1. Lists running processes
2. Filters the results for `bash`
3. Displays the first part of the filtered output

Another example:

```bash
ls -la | grep ".txt"
```

This lists directory contents and filters the results for entries containing `.txt`.

---

# 🔎 Command Reference

| Command / Operator | Purpose |
|---|---|
| `ls` | List directory contents |
| `cat file` | Display file contents |
| `echo "text"` | Display text |
| `>` | Redirect output and overwrite a file |
| `>>` | Append output to a file |
| `\|` | Pipe output from one command into another |
| `ps aux` | Display running processes |
| `grep pattern` | Search input for matching text |
| `head` | Display the beginning of input/output |
| `pwd` | Display the current directory |

---

# 🧠 Key Concepts

## Output Redirection — `>`

The `>` operator sends command output into a file.

```bash
ls > output.txt
```

If the file already exists, its contents are replaced.

---

## Append Redirection — `>>`

The `>>` operator adds output to the end of a file.

```bash
echo "New information" >> output.txt
```

Existing contents remain unchanged.

---

## Pipes — `|`

The pipe operator connects commands together.

```bash
command1 | command2
```

The output of the first command becomes the input of the second command.

Example:

```bash
ps aux | grep bash
```

---

# 🛡️ Security Perspective

Piping and redirection are important skills for Linux administration and cybersecurity.

Security professionals frequently need to:

- Search system information
- Filter command output
- Analyze processes
- Examine logs
- Extract relevant information
- Automate command-line workflows
- Process large amounts of text

For example:

```bash
ps aux | grep bash
```

can help identify processes associated with Bash.

Similarly, command output can be redirected to files for later inspection:

```bash
ls -la > directory-report.txt
```

Understanding these operators is also important when writing Bash scripts and security automation.

---

# ⚠️ Best Practices

### 1. Understand `>` before using it

Remember:

```bash
>
```

overwrites the destination file.

Be careful when redirecting output to an existing file.

---

### 2. Use `>>` when you want to preserve existing content

For example:

```bash
echo "New entry" >> log.txt
```

This adds information without replacing the previous contents.

---

### 3. Verify important files

After redirecting output, check the result:

```bash
cat output.txt
```

---

### 4. Test commands in a dedicated directory

For practice, use:

```bash
~/linux-piping-lab
```

instead of experimenting inside important system directories.

---

### 5. Understand command chains before executing them

When multiple commands are connected with pipes, make sure you understand what each command is doing.

For example:

```bash
ps aux | grep bash
```

contains two commands connected by a pipe.

---

# 📝 Questions

1. What is output redirection?
2. What does the `>` operator do?
3. What happens if `>` is used on an existing file?
4. What is the purpose of `>>`?
5. What is the difference between `>` and `>>`?
6. What does the pipe `|` operator do?
7. What does `ps aux` display?
8. What is the purpose of `grep` in `ps aux | grep bash`?
9. Why are pipes useful in Linux?
10. Why should you be careful when using `>`?
11. How can command output be saved into a file?
12. How can multiple commands be connected together?

---

# 🧩 Challenge

Create a file containing a directory listing and then append additional information to it.

### Step 1

Run:

```bash
ls -la > system-report.txt
```

### Step 2

Append a message:

```bash
echo "System report generated from the Linux command line." >> system-report.txt
```

### Step 3

View the report:

```bash
cat system-report.txt
```

### Step 4

Try using a pipe:

```bash
ls -la | grep ".txt"
```

Observe how the output changes.

---

# 🧹 Cleanup

When you finish the lab, you can remove the practice directory:

```bash
cd ~
rm -r ~/linux-piping-lab
```

> Only remove the practice directory you created for this lab. Always verify paths before using recursive deletion.

---

# 📌 Summary

In this lab, you learned how Linux handles command output using **redirection and pipes**.

You practiced:

- Redirecting output with `>`
- Appending output with `>>`
- Viewing redirected output with `cat`
- Connecting commands with `|`
- Filtering process information with `grep`
- Combining multiple commands into command-line workflows

These concepts are fundamental for Linux administration, shell scripting, automation, and cybersecurity operations.

---

# ✅ Lab Completion Checklist

- [ ] I understand output redirection
- [ ] I can use `>` to redirect command output
- [ ] I understand that `>` can overwrite an existing file
- [ ] I can use `>>` to append output
- [ ] I understand the difference between `>` and `>>`
- [ ] I understand how the pipe `|` works
- [ ] I can connect two commands using a pipe
- [ ] I can use `grep` to filter command output
- [ ] I can combine multiple commands into a workflow
- [ ] I understand the security importance of command-line filtering and redirection

---

## 🚀 Next Lab

**Lab 14 — Basic Process Management**
