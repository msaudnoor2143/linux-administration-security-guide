# Lab 31 — SCP and SFTP

> Learn how to securely transfer files between Linux systems using SSH-based file-transfer tools.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand secure file transfer.
- Use `scp` to copy files.
- Copy files to remote systems.
- Copy files from remote systems.
- Understand SFTP.
- Navigate a remote filesystem through SFTP.
- Upload and download files.
- Apply secure file-transfer practices.

---

## 📚 Prerequisites

Before starting this lab, you should have:

- A Linux system.
- Terminal access.
- Basic Linux filesystem knowledge.
- SSH access to an authorized remote Linux system.
- Completion of Lab 30 — SSH Basics.

---

# 1. Understanding Secure File Transfer

Administrators frequently need to move files between systems.

Examples include:

- Configuration files
- Scripts
- Logs
- Reports
- Backups
- Documentation

`scp` and `sftp` provide secure file-transfer mechanisms based on SSH.

---

# 2. Understanding SCP

**SCP** stands for Secure Copy Protocol.

It can be used to copy files between local and remote systems.

Basic syntax:

```bash
scp SOURCE DESTINATION
```

---

# 3. Copying a Local File to a Remote System

Suppose you have:

```text
report.txt
```

You can copy it to a remote user's home directory:

```bash
scp report.txt username@REMOTE_IP:~
```

Replace the username and IP address with your authorized lab system.

---

# 4. Copying a Remote File to the Local System

The general syntax is:

```bash
scp username@REMOTE_IP:/path/to/file .
```

The `.` represents the current local directory.

---

# 5. Copying a Directory

The recursive option `-r` can be used to copy directories:

```bash
scp -r directory username@REMOTE_IP:~
```

Use recursive copying carefully and only with directories you are authorized to transfer.

---

# 6. Understanding SFTP

**SFTP** stands for SSH File Transfer Protocol.

Unlike a single SCP copy operation, SFTP provides an interactive session for managing file transfers.

Start an SFTP session:

```bash
sftp username@REMOTE_IP
```

---

# 7. Useful SFTP Commands

Inside an SFTP session:

### Display the remote directory

```text
pwd
```

### List remote files

```text
ls
```

### Change remote directory

```text
cd directory
```

### Display local directory

```text
lpwd
```

### List local files

```text
lls
```

### Upload a file

```text
put filename
```

### Download a file

```text
get filename
```

### Exit SFTP

```text
exit
```

---

# 8. SCP vs SFTP

| Feature | SCP | SFTP |
|---|---|---|
| Secure transfer | Yes | Yes |
| SSH-based | Yes | Yes |
| Interactive session | No | Yes |
| Upload files | Yes | Yes |
| Download files | Yes | Yes |
| Directory operations | Basic | More extensive |

---

# 🧪 Practical Lab

## Task 1 — Create a Test File

On your local Linux machine:

```bash
mkdir -p ~/scp-sftp-lab
cd ~/scp-sftp-lab
```

Create a test file:

```bash
echo "Secure file transfer lab" > transfer-test.txt
```

Verify:

```bash
cat transfer-test.txt
```

---

## Task 2 — Copy the File with SCP

Use:

```bash
scp transfer-test.txt USERNAME@REMOTE_IP:~
```

Replace:

```text
USERNAME
REMOTE_IP
```

with your authorized lab credentials.

---

## Task 3 — Verify the Remote File

Connect through SSH:

```bash
ssh USERNAME@REMOTE_IP
```

Then:

```bash
ls -l ~/transfer-test.txt
```

Check the contents:

```bash
cat ~/transfer-test.txt
```

Exit:

```bash
exit
```

---

## Task 4 — Download the File

From the local machine:

```bash
scp USERNAME@REMOTE_IP:~/transfer-test.txt ~/scp-sftp-lab/
```

Verify:

```bash
ls -l ~/scp-sftp-lab/
```

---

# 9. Practical SFTP Exercise

Start an SFTP session:

```bash
sftp USERNAME@REMOTE_IP
```

Inside SFTP:

```text
pwd
```

Then:

```text
ls
```

Check the local directory:

```text
lpwd
```

List local files:

```text
lls
```

Upload the test file:

```text
put transfer-test.txt
```

Download it again using:

```text
get transfer-test.txt
```

Exit:

```text
exit
```

---

# 🔎 Command Reference

### SCP

| Command | Purpose |
|---|---|
| `scp file user@host:~` | Copy local file to remote home directory |
| `scp user@host:/path/file .` | Download remote file |
| `scp -r directory user@host:~` | Copy directory recursively |

### SFTP

| Command | Purpose |
|---|---|
| `sftp user@host` | Start SFTP session |
| `pwd` | Show remote working directory |
| `ls` | List remote files |
| `cd` | Change remote directory |
| `lpwd` | Show local working directory |
| `lls` | List local files |
| `put` | Upload file |
| `get` | Download file |
| `exit` | Close SFTP session |

---

# 🧠 Key Concepts

### SCP

A command-line mechanism for securely copying files through SSH.

### SFTP

An interactive file-transfer protocol that operates over SSH.

### Remote Host

The system receiving or providing files.

### Local Host

The system where you are currently working.

### SSH Authentication

The authentication mechanism used to establish the secure connection.

---

# 🛡️ Security Perspective

Secure file transfer is an important part of system administration.

Security considerations include:

- Transfer only authorized files.
- Protect SSH credentials.
- Protect private keys.
- Verify the destination system.
- Use appropriate file permissions.
- Avoid transferring sensitive information unnecessarily.
- Monitor unexpected file transfers.

---

# ⚠️ Best Practices

- Use SCP/SFTP instead of insecure unencrypted transfer methods when appropriate.
- Transfer only files you are authorized to access.
- Check destination paths carefully.
- Avoid overwriting important files accidentally.
- Protect SSH private keys.
- Use dedicated accounts where appropriate.
- Verify transferred files after important operations.

---

# 📝 Questions

1. What does SCP stand for?
2. What does SFTP stand for?
3. What protocol is used by SCP and SFTP?
4. How do you upload a file with SCP?
5. How do you download a file with SCP?
6. What does `scp -r` do?
7. What is the difference between SCP and SFTP?
8. What does `put` do in SFTP?
9. What does `get` do in SFTP?
10. Why should SSH credentials be protected?

---

# 🧪 Challenge

Using an authorized Linux lab server:

1. Create a local directory.
2. Create two test files.
3. Transfer both files to the remote machine.
4. Connect through SSH and verify them.
5. Start an SFTP session.
6. List the remote files.
7. Download one file.
8. Verify the downloaded copy locally.
9. Clean up the test files.

---

# 🧹 Cleanup

Remove the local practice directory:

```bash
rm -rf ~/scp-sftp-lab
```

On the remote lab machine, remove the test file:

```bash
rm -f ~/transfer-test.txt
```

Only remove files created specifically for this lab.

---

# 🔐 Security Reminder

Only use SCP, SFTP, and SSH against systems you own or have explicit authorization to access.

---

# ✅ Lab Completion Checklist

- [ ] I understand secure file transfer.
- [ ] I understand SCP.
- [ ] I understand SFTP.
- [ ] I can upload a file with SCP.
- [ ] I can download a file with SCP.
- [ ] I can start an SFTP session.
- [ ] I can use `put`.
- [ ] I can use `get`.
- [ ] I can navigate remote files with SFTP.
- [ ] I understand secure file-transfer practices.
- [ ] I completed the challenge.
- [ ] I cleaned up my test files.

---

## 🎉 Section 05 Complete

You have now covered:

- **Lab 28 — Scheduling Tasks with Crontab**
- **Lab 29 — Scheduling Tasks with `at`**
- **Lab 30 — SSH Basics**
- **Lab 31 — SCP and SFTP**

The next section is:

**Section 06 — Text Processing & Search**

Starting with **Lab 32 — Introduction to vi/vim**.
