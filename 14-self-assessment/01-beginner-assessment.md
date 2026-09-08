# 🟢 Beginner Linux Self-Assessment

This assessment evaluates the foundational Linux skills covered in **Labs 01–20**.

The objective is to determine whether you can independently perform basic Linux command-line, filesystem, shell, process, networking, archiving and compression tasks.

---

# 🎯 Assessment Objective

By completing this assessment, you should demonstrate that you can:

- Navigate Linux filesystems
- Manage files and directories
- Understand permissions and ownership
- Use wildcards
- Read file contents
- Work with links
- Understand shells
- Work with environment variables
- Create basic shell scripts
- Use pipes and redirection
- Manage processes and jobs
- Create aliases
- Use basic network tools
- Create archives
- Compress and extract files

---

# 📚 Coverage

This assessment covers:

| Labs | Topic |
|---|---|
| 01 | Navigating the Linux Filesystem |
| 02 | Working with Directories |
| 03 | Managing Files |
| 04 | Using Text Editors |
| 05 | File Permissions Basics |
| 06 | Working with Ownership |
| 07 | Using Wildcards |
| 08 | Viewing File Contents |
| 09 | Working with Links |
| 10 | Understanding Shells |
| 11 | Environment Variables |
| 12 | Basic Shell Scripting |
| 13 | Piping and Redirection |
| 14 | Process Management |
| 15 | Job Control |
| 16 | Aliases |
| 17 | Network Tools |
| 18 | `tar` |
| 19 | `gzip` and `bzip2` |
| 20 | ZIP/UNZIP |

---

# 📋 Assessment Rules

1. Use an authorized Linux environment.
2. Complete tasks without copying complete solutions from the original labs.
3. Use `man` pages and built-in help when necessary.
4. Verify your results.
5. Document important commands and outputs.
6. Clean up temporary files after the assessment.

---

# 🧪 Part 1 — Filesystem & File Management

## Task 1 — Filesystem Navigation

Starting from your home directory:

1. Display your current location.
2. List the contents of the directory.
3. Display hidden files.
4. Navigate to another directory.
5. Return to your home directory.
6. Display the directory structure using an appropriate command.

### Evaluation

You should demonstrate that you understand:

- `pwd`
- `ls`
- `cd`
- Absolute paths
- Relative paths

---

## Task 2 — Directory Management

Create an assessment workspace:

```text
linux-assessment/
├── documents/
├── scripts/
├── backups/
└── logs/
```

Verify that the structure exists.

---

## Task 3 — File Management

Inside the workspace:

- Create several files.
- Copy a file.
- Rename a file.
- Move a file.
- Remove a test file.
- Verify each operation.

---

# 🔐 Part 2 — Permissions & Ownership

## Task 4 — File Permissions

Create a test file and configure permissions so that:

- The owner can read and write.
- The group can read.
- Others have no access.

Verify the permissions.

### Evaluation

Demonstrate understanding of:

```text
r
w
x
```

and numeric permission notation.

---

## Task 5 — Ownership

Inspect the ownership of your assessment files.

Explain:

- File owner
- Group owner
- Permission relationship

If your environment permits it, demonstrate changing ownership or group ownership on a test file.

---

# 🔎 Part 3 — Wildcards & File Contents

## Task 6 — Wildcards

Create files with different extensions and names.

Use wildcard patterns to:

- Select multiple files.
- Select files with a specific extension.
- Select files beginning with a particular character.
- Select files matching a pattern.

---

## Task 7 — Viewing Contents

Create a text file containing several lines.

Use appropriate commands to:

- Display the complete file.
- Display the beginning.
- Display the end.
- Display the file one screen at a time.

Explain when each command is useful.

---

# 🔗 Part 4 — Links

## Task 8 — Links

Create:

- A hard link
- A symbolic link

Verify both links.

Explain the difference between them.

---

# 🐚 Part 5 — Shells & Environment

## Task 9 — Shell Identification

Determine:

- Your current shell.
- The location of the shell executable.
- Relevant shell/environment information.

Explain what a shell does.

---

## Task 10 — Environment Variables

Inspect existing environment variables.

Then:

1. Create a temporary environment variable.
2. Display it.
3. Use it in a command.
4. Explain the difference between a shell variable and an exported environment variable.

---

# 📜 Part 6 — Basic Shell Scripting

## Task 11 — Create a Script

Create a simple shell script that:

- Displays a greeting.
- Displays the current user.
- Displays the current directory.
- Displays the current date.
- Displays basic system information.

Make the script executable and run it.

---

# 🔀 Part 7 — Piping & Redirection

## Task 12 — Command Chaining

Demonstrate:

- Output redirection.
- Append redirection.
- Input redirection.
- A pipeline.

Create a small workflow where the output of one command becomes the input of another.

---

# ⚙️ Part 8 — Processes & Jobs

## Task 13 — Process Inspection

Demonstrate how to:

- List running processes.
- Identify a process.
- Inspect process information.
- Observe system activity.

Explain the difference between a process and a command.

---

## Task 14 — Job Control

Run a suitable command in the background.

Demonstrate:

- Background execution
- Viewing jobs
- Bringing a job to the foreground
- Returning a suitable process to the background

---

# ⚡ Part 9 — Aliases

## Task 15 — Create an Alias

Create a useful temporary alias.

Demonstrate that it works.

Explain why aliases can improve command-line productivity.

---

# 🌐 Part 10 — Basic Networking

## Task 16 — Network Tools

Use appropriate Linux networking commands to determine:

- Network configuration
- IP information
- Connectivity
- Basic route information
- DNS information where available

Explain what each command tells you.

---

# 📦 Part 11 — Archiving

## Task 17 — TAR Archive

Create an archive containing your assessment workspace.

Demonstrate:

- Creating an archive
- Listing archive contents
- Extracting the archive

---

# 🗜️ Part 12 — Compression

## Task 18 — gzip/bzip2

Compress suitable files using:

- `gzip`
- `bzip2`

Demonstrate how to decompress them.

Explain the difference between archiving and compression.

---

# 📁 Part 13 — ZIP

## Task 19 — ZIP Archive

Create a ZIP archive containing selected assessment files.

Demonstrate:

- Creating the archive
- Listing its contents
- Extracting it

---

# 🧠 Knowledge Questions

Answer the following without looking at the original labs.

1. What is the difference between an absolute and relative path?
2. What does `pwd` display?
3. What is the difference between a file and a directory?
4. What do `r`, `w`, and `x` represent?
5. What is the difference between ownership and permissions?
6. What is a symbolic link?
7. What is a hard link?
8. What is an environment variable?
9. What is the purpose of a shell?
10. What is a pipe?
11. What is the difference between `>` and `>>`?
12. What is a process?
13. What is job control?
14. What is an alias?
15. What is the difference between an archive and compressed data?

---

# 🧩 Beginner Challenge

Create a small Linux workspace containing:

```text
linux-assessment/
├── documents/
├── scripts/
├── backups/
└── logs/
```

Then:

1. Create files inside the directories.
2. Apply different permissions.
3. Create a symbolic link.
4. Create a shell script that reports basic information.
5. Redirect the script output to a log.
6. Compress the log.
7. Create an archive of the workspace.
8. Verify the archive.
9. Extract it into another directory.

The challenge should be completed as one connected workflow.

---

# 📊 Suggested Scoring

| Area | Points |
|---|---:|
| Filesystem & directories | 2 |
| File management | 2 |
| Permissions & ownership | 3 |
| Wildcards & file contents | 2 |
| Links | 2 |
| Shell & environment | 2 |
| Shell scripting | 2 |
| Piping & redirection | 2 |
| Processes & jobs | 2 |
| Aliases | 1 |
| Networking | 2 |
| Archives & compression | 2 |
| **Total** | **24** |

Convert the result to the Beginner Assessment weighting used in the main Section 14 README if required.

---

# 🏅 Beginner Evaluation

### Excellent

You can complete the practical tasks independently and explain why your commands work.

### Good

You can complete most tasks but require occasional reference to documentation.

### Developing

You understand the concepts but need assistance with several practical tasks.

### Review Required

You should revisit the corresponding Labs 01–20 before continuing.

---

# ✅ Completion Checklist

- [ ] Filesystem navigation completed
- [ ] Directory management completed
- [ ] File management completed
- [ ] Permissions demonstrated
- [ ] Ownership understood
- [ ] Wildcards demonstrated
- [ ] File contents inspected
- [ ] Hard and symbolic links demonstrated
- [ ] Shell identified
- [ ] Environment variables demonstrated
- [ ] Shell script created
- [ ] Pipes and redirection demonstrated
- [ ] Processes inspected
- [ ] Job control demonstrated
- [ ] Alias created
- [ ] Network tools used
- [ ] TAR archive created
- [ ] gzip/bzip2 demonstrated
- [ ] ZIP archive created
- [ ] Knowledge questions answered
- [ ] Beginner challenge completed

---

# 🚀 Advancement Criteria

Proceed to the Intermediate Assessment when you can complete the majority of these tasks **without step-by-step instructions** and can explain the purpose of the commands you use.

**Next:** 🟡 Intermediate Linux Self-Assessment
