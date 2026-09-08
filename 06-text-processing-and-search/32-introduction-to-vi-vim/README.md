# Lab 32 — Introduction to vi/vim

> Learn the fundamentals of the `vi`/`vim` text editor, including opening files, editing text, navigating through files, and performing search and replacement operations.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand the purpose of `vi` and `vim`.
- Open files using the editor.
- Create and edit text files.
- Understand Normal mode and Insert mode.
- Enter and exit Insert mode.
- Navigate through text.
- Save changes.
- Exit the editor.
- Search for text.
- Perform basic find-and-replace operations.

---

## 📚 Prerequisites

Before starting this lab, you should have:

- A Linux or Unix-like system.
- Terminal access.
- Basic command-line knowledge.
- Basic understanding of Linux files.
- Familiarity with commands such as `touch` and `ls`.

---

# 1. Understanding vi and Vim

`vi` is a classic text editor commonly available on Unix/Linux systems.

`vim`, meaning **Vi IMproved**, is an enhanced version of `vi`.

These editors are especially useful when working directly from a terminal and are commonly encountered when editing:

- Configuration files
- Scripts
- Source code
- System files
- Documentation

---

# 2. Creating a File

Before opening a file, create a practice file:

```bash
touch file.txt
```

Verify:

```bash
ls -l file.txt
```

---

# 3. Opening a File with vi

Open the file:

```bash
vi file.txt
```

If the file does not already exist, `vi` can create it when you save it.

---

# 4. Understanding vi Modes

One of the most important concepts in `vi`/`vim` is that the editor works with different modes.

### Normal Mode

Used for navigation and editor commands.

Press:

```text
Esc
```

to return to Normal mode.

### Insert Mode

Used for entering text.

Press:

```text
i
```

to enter Insert mode.

---

# 5. Entering Text

Open the file:

```bash
vi file.txt
```

Press:

```text
i
```

Then enter several lines of text.

For example:

```text
Linux administration
Text processing
System security
```

When finished entering text, press:

```text
Esc
```

to return to Normal mode.

---

# 6. Saving a File

From Normal mode, enter command mode with:

```text
:w
```

The `w` command writes the changes to the file.

---

# 7. Exiting vi

From Normal mode:

```text
:q
```

quits the editor.

A common save-and-exit sequence is:

```text
Esc
:w
:q
```

You can also use:

```text
:wq
```

to save and exit.

---

# 8. Basic Navigation

In Normal mode, the following keys can be used for navigation:

| Key | Movement |
|---|---|
| `h` | Left |
| `j` | Down |
| `k` | Up |
| `l` | Right |

Practice moving around your text using these keys.

---

# 9. Searching for Text

In Normal mode, press:

```text
/
```

Then type the text you want to find.

For example:

```text
/example
```

Press Enter to search.

---

# 10. Find and Replace

A basic substitution command is:

```text
:%s/old/new/g
```

The components mean:

- `%` — operate throughout the file
- `s` — substitution
- `old` — text to find
- `new` — replacement text
- `g` — replace all matching occurrences on each line

---

# 🧪 Practical Lab

## Task 1 — Create a Practice File

Run:

```bash
touch file.txt
```

---

## Task 2 — Open the File

```bash
vi file.txt
```

---

## Task 3 — Enter Insert Mode

Press:

```text
i
```

Enter several lines containing repeated words.

For example:

```text
Linux is powerful.
Linux is flexible.
Linux is widely used.
```

Press:

```text
Esc
```

---

## Task 4 — Save the File

Enter:

```text
:w
```

---

## Task 5 — Navigate

Practice:

```text
h
j
k
l
```

---

## Task 6 — Search

Search for:

```text
/Linux
```

---

## Task 7 — Replace Text

Return to Normal mode and use:

```text
:%s/Linux/Unix/g
```

Save:

```text
:w
```

Exit:

```text
:q
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `vi file.txt` | Open/create a file |
| `i` | Enter Insert mode |
| `Esc` | Return to Normal mode |
| `:w` | Save file |
| `:q` | Quit |
| `:wq` | Save and quit |
| `h` | Move left |
| `j` | Move down |
| `k` | Move up |
| `l` | Move right |
| `/pattern` | Search for text |
| `:%s/old/new/g` | Replace matching text |

---

# 🧠 Key Concepts

### vi/vim

Terminal-based text editors used extensively on Unix/Linux systems.

### Insert Mode

Used to enter text.

### Normal Mode

Used for navigation and editor commands.

### Command Mode

Used for commands such as saving, quitting, and substitution.

### Search and Replace

Vim provides powerful text manipulation through commands such as:

```text
:%s/old/new/g
```

---

# 🛡️ Security Perspective

Linux administrators frequently edit configuration files from the terminal.

Understanding `vi`/`vim` is useful when:

- Working on remote servers.
- Editing configuration files.
- Managing system services.
- Troubleshooting systems.
- Working in environments without graphical editors.

Always verify configuration changes before applying them to important systems.

---

# ⚠️ Best Practices

- Practice on test files first.
- Understand which mode you are in.
- Save important work before making large changes.
- Be careful when editing system configuration files.
- Verify changes after saving.
- Avoid modifying files you do not understand.

---

# 📝 Questions

1. What is `vi`?
2. What does Vim stand for?
3. What is Insert mode?
4. What is Normal mode?
5. How do you enter Insert mode?
6. How do you return to Normal mode?
7. What does `:w` do?
8. What does `:q` do?
9. What does `/pattern` do?
10. What does `:%s/old/new/g` accomplish?

---

# 🧪 Challenge

Create a file containing several repeated words.

Then:

1. Open it using `vi`.
2. Enter Insert mode.
3. Add text.
4. Save it.
5. Navigate using `h`, `j`, `k`, and `l`.
6. Search for a word.
7. Replace that word throughout the file.
8. Save and exit.

---

# 🧹 Cleanup

Remove the practice file:

```bash
rm -f file.txt
```

---

# ✅ Lab Completion Checklist

- [ ] I understand vi/vim.
- [ ] I can open a file.
- [ ] I understand Insert mode.
- [ ] I understand Normal mode.
- [ ] I can enter text.
- [ ] I can navigate using `h`, `j`, `k`, and `l`.
- [ ] I can save a file.
- [ ] I can exit vi.
- [ ] I can search for text.
- [ ] I can perform a basic replacement.

---

## 🚀 Next Lab

**Lab 33 — Basic Grep Usage**
