# Lab 49 — Using and Creating Man Pages

> Learn how to use Linux manual pages for command reference and create a simple custom manual page for a script.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Use the `man` command
- Navigate manual pages
- Understand common man-page sections
- Create a simple script
- Understand basic man-page formatting
- Compress a manual page
- Install a custom manual page
- View the custom page with `man`

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Basic Linux command-line knowledge
- Familiarity with files and directories
- `man`
- `gzip`
- A text editor or command-line method for creating files

---

# 1. Understanding Manual Pages

Linux provides extensive documentation through manual pages, commonly called **man pages**.

The primary command is:

```bash
man
```

For example:

```bash
man ls
```

---

# 2. Navigating a Man Page

Inside a manual page:

- Use arrow keys to scroll.
- Use Page Up/Page Down to navigate.
- Press `/` to search.
- Press `q` to exit.

---

# 3. Common Man Page Sections

A man page commonly contains sections such as:

```text
NAME
SYNOPSIS
DESCRIPTION
OPTIONS
```

These sections help users understand what a command does and how to use it.

---

# 4. Creating a Simple Script

Create a test script:

```bash
cat > test_script.sh <<'EOF'
#!/bin/bash
echo "This is a test script."
EOF
```

Make it executable:

```bash
chmod +x test_script.sh
```

Run it:

```bash
./test_script.sh
```

---

# 5. Creating a Custom Man Page

A basic manual page uses formatting directives.

Example:

```text
.TH TEST_SCRIPT 1 "Version 1.0" "Custom Manual"
.SH NAME
test_script \- A simple test script demonstration.
.SH SYNOPSIS
test_script
.SH DESCRIPTION
This script outputs a simple message.
```

Important directives include:

```text
.TH
.SH
```

---

# 6. Compressing a Man Page

Man pages are commonly stored in compressed form.

For example:

```bash
gzip test_script.1
```

This creates:

```text
test_script.1.gz
```

---

# 7. Installing the Man Page

A local section-1 manual page can be placed under:

```text
/usr/local/share/man/man1/
```

For example:

```bash
sudo mkdir -p /usr/local/share/man/man1
sudo mv test_script.1.gz /usr/local/share/man/man1/
```

---

# 8. Viewing the Custom Man Page

Run:

```bash
man test_script
```

If the system does not immediately locate the page, the manual-page database may need updating depending on the distribution.

---

# 🧪 Practical Lab

## Task 1 — Open an Existing Man Page

Run:

```bash
man ls
```

Find:

- NAME
- SYNOPSIS
- DESCRIPTION
- OPTIONS

Exit:

```text
q
```

---

## Task 2 — Create a Test Script

Run:

```bash
cat > test_script.sh <<'EOF'
#!/bin/bash
echo "This is a test script."
EOF
```

Make it executable:

```bash
chmod +x test_script.sh
```

Run:

```bash
./test_script.sh
```

---

## Task 3 — Create the Man Page

Create:

```bash
cat > test_script.1 <<'EOF'
.TH TEST_SCRIPT 1 "Version 1.0" "Custom Manual"
.SH NAME
test_script \- A simple test script demonstration.
.SH SYNOPSIS
test_script
.SH DESCRIPTION
This script outputs a simple message.
.SH AUTHOR
Lab User
EOF
```

---

## Task 4 — Compress the Man Page

Run:

```bash
gzip test_script.1
```

Verify:

```bash
ls -l test_script.1.gz
```

---

## Task 5 — Install the Man Page

Create the local man directory:

```bash
sudo mkdir -p /usr/local/share/man/man1
```

Move the compressed page:

```bash
sudo mv test_script.1.gz /usr/local/share/man/man1/
```

---

## Task 6 — View the Custom Man Page

Run:

```bash
man test_script
```

Press:

```text
q
```

to exit.

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `man COMMAND` | Open a manual page |
| `gzip file` | Compress a file |
| `chmod +x file` | Make a script executable |
| `mkdir -p` | Create directories |
| `mv` | Move files |
| `man test_script` | View the custom man page |

---

# 🧠 Key Concepts

## Man Page

Documentation for Linux commands, utilities, interfaces, and other system components.

## `.1`

A common manual-page section designation for user commands.

## `.gz`

Compressed format commonly used for installed man pages.

## `.TH`

Defines the manual-page header.

## `.SH`

Defines a section heading.

---

# 🛡️ Security Perspective

Manual pages are an important administrative resource.

Security professionals frequently need to understand:

- Command options
- Configuration syntax
- Permission behavior
- Networking utilities
- Security tools

Using authoritative local documentation helps reduce mistakes caused by relying on incomplete command examples.

---

# ⚠️ Best Practices

- Read `man` documentation before unfamiliar commands.
- Verify command options before using them.
- Keep custom documentation accurate.
- Avoid installing custom files into system locations without understanding their purpose.

---

# 📝 Questions

1. What does `man` do?
2. How do you exit a man page?
3. What does `.1` represent?
4. Why are man pages often compressed?
5. What does `.TH` do?
6. What does `.SH` do?
7. Where can local section-1 man pages be installed?
8. Why are man pages useful for security professionals?

---

# 🚀 Challenge

Create a second custom man page for a simple script you write yourself.

Include:

```text
NAME
SYNOPSIS
DESCRIPTION
AUTHOR
```

Install it under the appropriate local man directory and view it using:

```bash
man your_command
```

---

# ✅ Lab Completion Checklist

- [ ] I can use `man`
- [ ] I can navigate a manual page
- [ ] I understand common man-page sections
- [ ] I can create a simple script
- [ ] I understand basic man-page formatting
- [ ] I can compress a man page
- [ ] I understand how local man pages are installed
- [ ] I can view a custom man page

---

## Summary

In this lab, you learned how to use Linux manual pages and created a custom manual page for a simple script. You also learned how manual pages are structured, compressed, installed, and accessed through the `man` command.

---

## 🚀 Next Lab

**Lab 50 — Introduction to Shell Variables**
