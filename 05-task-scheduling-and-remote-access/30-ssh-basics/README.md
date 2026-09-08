# Lab 30 — SSH Basics

> Learn how to securely connect to and administer a remote Linux system using SSH.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand SSH.
- Connect to remote Linux systems.
- Understand SSH server and client roles.
- Identify the SSH service.
- Use SSH authentication.
- Understand SSH host keys.
- Verify connectivity.
- Safely disconnect from a remote session.

---

## 📚 Prerequisites

Before starting this lab, you should have:

- A Linux system.
- Terminal access.
- Basic networking knowledge.
- A remote Linux system or second Linux virtual machine for practice.
- A valid account on the remote system.

---

# 1. Understanding SSH

**SSH**, or Secure Shell, is a protocol used to securely access remote systems.

SSH is commonly used by:

- System administrators
- DevOps engineers
- Network administrators
- Cybersecurity professionals
- Cloud engineers

SSH provides an encrypted communication channel between the client and server.

---

# 2. SSH Client and Server

An SSH connection normally involves two components.

### SSH Client

The machine initiating the connection.

### SSH Server

The machine accepting SSH connections.

The SSH server commonly listens on:

```text
TCP port 22
```

---

# 3. Checking the SSH Client

Check whether SSH is available:

```bash
ssh -V
```

---

# 4. Connecting to a Remote System

The basic syntax is:

```bash
ssh username@remote_host
```

For example:

```bash
ssh student@192.168.1.20
```

Replace the username and IP address with those belonging to your authorized lab system.

---

# 5. Understanding the Host-Key Prompt

During the first connection to a server, SSH may display a message asking whether you trust the host.

This happens because the SSH client has not previously stored that server's host key.

Verify the server identity before accepting it in a real environment.

---

# 6. Disconnecting from SSH

To leave a remote SSH session:

```bash
exit
```

You can also use:

```text
Ctrl+D
```

---

# 7. Checking the SSH Service

On systems using systemd:

```bash
sudo systemctl status ssh
```

Some distributions use:

```bash
sudo systemctl status sshd
```

The exact service name depends on the Linux distribution.

---

# 8. Starting and Stopping SSH

On systems where the service is named `ssh`:

```bash
sudo systemctl start ssh
```

Stop it with:

```bash
sudo systemctl stop ssh
```

Restart it with:

```bash
sudo systemctl restart ssh
```

Enable it at boot:

```bash
sudo systemctl enable ssh
```

> ⚠️ Do not disable SSH on a remote production system unless you have another authorized method of administration.

---

# 9. Checking Listening Ports

You can inspect listening sockets with:

```bash
ss -tln
```

To look specifically for SSH:

```bash
ss -tln | grep ':22'
```

---

# 🧪 Practical Lab

## Task 1 — Check SSH

Run:

```bash
ssh -V
```

---

## Task 2 — Identify Your Lab Machine

Find the local IP addresses:

```bash
ip addr
```

If using two virtual machines, identify the IP address of the remote machine.

---

## Task 3 — Check SSH Service

On the remote Linux machine:

```bash
sudo systemctl status ssh
```

If necessary, try:

```bash
sudo systemctl status sshd
```

---

## Task 4 — Test Connectivity

From the client machine:

```bash
ping REMOTE_IP
```

Replace:

```text
REMOTE_IP
```

with the authorized lab machine's IP address.

---

## Task 5 — Connect

Use:

```bash
ssh USERNAME@REMOTE_IP
```

After successfully connecting, verify the remote system:

```bash
hostname
```

Then:

```bash
whoami
```

---

## Task 6 — Disconnect

Run:

```bash
exit
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `ssh -V` | Display SSH client version |
| `ssh user@host` | Connect to a remote host |
| `exit` | End an SSH session |
| `systemctl status ssh` | Check SSH service |
| `systemctl start ssh` | Start SSH service |
| `systemctl stop ssh` | Stop SSH service |
| `systemctl restart ssh` | Restart SSH service |
| `ip addr` | Display network addresses |
| `ss -tln` | Display listening TCP sockets |
| `ping` | Test network reachability |

---

# 🧠 Key Concepts

### SSH

A secure protocol for remote administration.

### SSH Client

Initiates the connection.

### SSH Server

Accepts incoming SSH connections.

### Host Key

A cryptographic identity associated with an SSH server.

### Port 22

The conventional SSH TCP port.

---

# 🛡️ Security Perspective

SSH is a critical administration protocol, but it must be configured carefully.

Security measures include:

- Use strong authentication.
- Prefer SSH keys where appropriate.
- Protect private keys.
- Disable unnecessary accounts.
- Restrict SSH access where possible.
- Monitor authentication activity.
- Keep the SSH server updated.
- Avoid exposing administrative services unnecessarily.

---

# ⚠️ Best Practices

- Connect only to systems you are authorized to access.
- Verify host identities.
- Never share private SSH keys.
- Use separate accounts for different users.
- Avoid unnecessary root login.
- Keep SSH software updated.
- Use firewall controls to restrict unnecessary access.

---

# 📝 Questions

1. What does SSH stand for?
2. What is the purpose of SSH?
3. What is the difference between an SSH client and server?
4. What is the conventional SSH port?
5. What does `ssh user@host` do?
6. Why does SSH use host keys?
7. What does `ss -tln` show?
8. Why should SSH access be restricted?
9. Why should private keys be protected?

---

# 🧪 Challenge

Using two authorized Linux machines:

1. Identify the server IP.
2. Confirm network connectivity.
3. Check whether SSH is running.
4. Connect through SSH.
5. Run `hostname`.
6. Run `whoami`.
7. Disconnect safely.

Document the commands and results in your own lab notes.

---

# 🧹 Cleanup

Disconnect from the remote system:

```bash
exit
```

If you started an SSH service only for the lab and no longer need it, follow your lab environment's instructions before stopping it.

---

# ✅ Lab Completion Checklist

- [ ] I understand SSH.
- [ ] I understand client/server architecture.
- [ ] I can check the SSH version.
- [ ] I can identify a remote system.
- [ ] I can check the SSH service.
- [ ] I can establish an SSH session.
- [ ] I can verify the remote host.
- [ ] I can disconnect.
- [ ] I understand basic SSH security.

---

## 🚀 Next Lab

**Lab 31 — SCP and SFTP**
