# Lab 60 — Introduction to SELinux

## 📌 Overview

Security-Enhanced Linux (SELinux) is a security mechanism that provides an additional layer of access control on Linux systems.

Unlike traditional Linux permissions, SELinux can use security policies and labels to control what processes are allowed to access.

In this lab, you will explore the basic concepts of SELinux, check its current status, and learn how to work with its enforcement modes.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand the purpose of SELinux
- Check SELinux status
- Understand SELinux enforcement modes
- View SELinux security information
- Understand the concept of security contexts
- Perform basic SELinux administration
- Understand how SELinux contributes to system security

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Basic Linux command-line knowledge
- Familiarity with Linux permissions
- Basic understanding of users and processes
- Access to a Linux system that supports SELinux
- Administrative privileges for commands requiring `sudo`

> **Note:** SELinux is primarily associated with distributions such as RHEL, CentOS, Rocky Linux, AlmaLinux, and Fedora. Ubuntu systems generally use AppArmor instead.

---

## 🧠 What Is SELinux?

SELinux stands for:

**Security-Enhanced Linux**

It provides a form of **Mandatory Access Control (MAC)**.

Traditional Linux permissions are generally based on:

- User
- Group
- Other

SELinux adds another security layer by applying security policies to processes and resources.

This can limit what a compromised process is allowed to access, even if traditional Unix permissions might otherwise permit the access.

---

## 🔐 Mandatory Access Control

Linux traditionally uses Discretionary Access Control (DAC).

With DAC, file owners and administrators can determine permissions.

SELinux adds Mandatory Access Control through policies.

A simplified model is:

```text
Process
   |
   v
SELinux Policy
   |
   v
Allowed / Denied
   |
   v
Resource
```

This provides an additional security boundary around applications and services.

---

## 🔎 Check SELinux Status

Use:

```bash
sestatus
```

You can also use:

```bash
getenforce
```

Possible results include:

```text
Enforcing
Permissive
Disabled
```

---

## ⚙️ SELinux Modes

### Enforcing

In **Enforcing** mode, SELinux policies are actively applied.

Unauthorized actions can be blocked.

```text
Enforcing
```

is generally the preferred operational mode when the system is properly configured.

---

### Permissive

In **Permissive** mode, SELinux does not actively block policy violations.

Instead, it records information about violations.

This mode can be useful for troubleshooting and policy development.

Check the current mode:

```bash
getenforce
```

---

### Disabled

When SELinux is disabled, its security policy enforcement is not active.

Disabling security controls should not be treated as a normal troubleshooting solution.

---

## 🔄 Temporarily Changing Enforcement

On a system where SELinux is enabled, the enforcement state can be changed temporarily.

Check the current state:

```bash
getenforce
```

Switch to permissive:

```bash
sudo setenforce 0
```

Check again:

```bash
getenforce
```

Switch back to enforcing:

```bash
sudo setenforce 1
```

Verify:

```bash
getenforce
```

> **Important:** Only perform these changes on a lab system where you have authorization. Avoid changing SELinux enforcement on production systems without understanding the consequences.

---

## 🏷️ SELinux Security Contexts

SELinux uses security contexts to classify processes and resources.

View file contexts with:

```bash
ls -Z
```

For example:

```bash
ls -Z /var/www/
```

You may see additional security information associated with files.

---

## 👤 Process Contexts

Security contexts can also be viewed for running processes.

Use:

```bash
ps auxZ
```

This allows you to inspect the SELinux context associated with processes.

---

## 📂 Viewing Contexts

Create a test directory:

```bash
mkdir ~/selinux-lab
```

Create a test file:

```bash
echo "SELinux laboratory file" > ~/selinux-lab/test.txt
```

View its context:

```bash
ls -Z ~/selinux-lab/test.txt
```

The exact context values depend on the system's SELinux policy and configuration.

---

## 🧪 Practical Lab

### Task 1 — Check SELinux status

```bash
sestatus
```

Record:

- SELinux status
- Current mode
- Policy type, if displayed

---

### Task 2 — Check enforcement mode

```bash
getenforce
```

Record whether the system reports:

```text
Enforcing
```

```text
Permissive
```

or:

```text
Disabled
```

---

### Task 3 — View file security contexts

Create a test directory:

```bash
mkdir -p ~/selinux-lab
```

Create a test file:

```bash
echo "SELinux test data" > ~/selinux-lab/test.txt
```

View its context:

```bash
ls -Z ~/selinux-lab/test.txt
```

---

### Task 4 — View process contexts

Run:

```bash
ps auxZ
```

Review the SELinux context information associated with running processes.

---

### Task 5 — Check enforcement

Run:

```bash
getenforce
```

If your lab environment permits changing enforcement temporarily, test:

```bash
sudo setenforce 0
```

Check:

```bash
getenforce
```

Then restore enforcement:

```bash
sudo setenforce 1
```

Verify:

```bash
getenforce
```

---

## 🔎 Command Reference

| Command | Purpose |
|---|---|
| `sestatus` | Display detailed SELinux status |
| `getenforce` | Display current enforcement mode |
| `setenforce 0` | Temporarily switch to permissive mode |
| `setenforce 1` | Temporarily switch to enforcing mode |
| `ls -Z` | Display SELinux file contexts |
| `ps auxZ` | Display process contexts |

---

## 🧠 Key Concepts

### SELinux

A Linux security mechanism providing Mandatory Access Control.

### DAC

Traditional Linux Discretionary Access Control based primarily on ownership and permissions.

### MAC

Mandatory Access Control in which policy determines what access is allowed.

### Enforcing

SELinux actively enforces its policies.

### Permissive

SELinux records policy violations but does not normally block them.

### Disabled

SELinux is not active.

### Security Context

Additional security information used by SELinux to apply policies to processes and resources.

---

## 🛡️ Security Perspective

SELinux provides defense in depth.

For example, if a network-facing service is compromised, SELinux policies can restrict what that service is allowed to access.

This can reduce the potential impact of a compromised application.

SELinux is therefore particularly valuable for:

- Servers
- Web applications
- Network services
- Enterprise Linux environments
- Security-sensitive systems

---

## ⚠️ Best Practices

- Prefer enforcing mode on properly configured systems.
- Do not disable SELinux simply because an application encounters a problem.
- Investigate policy denials before changing security controls.
- Test SELinux policy changes in a controlled environment.
- Understand security contexts before modifying them.
- Do not make security-policy changes on production systems without proper authorization and testing.

---

## 📝 Questions

1. What does SELinux stand for?
2. What is the difference between DAC and MAC?
3. What are the three main SELinux modes?
4. What is the purpose of `sestatus`?
5. What does `getenforce` display?
6. What does `setenforce 0` do?
7. What does `setenforce 1` do?
8. What does `ls -Z` display?
9. Why can SELinux reduce the impact of a compromised service?
10. Why should SELinux not simply be disabled when troubleshooting an application?

---

## 🧪 Challenge

Create a small test directory and inspect its SELinux context.

```bash
mkdir -p ~/selinux-challenge
echo "Security context test" > ~/selinux-challenge/test.txt
ls -Zd ~/selinux-challenge
ls -Z ~/selinux-challenge/test.txt
```

Then inspect the context of a running process:

```bash
ps auxZ | head
```

Answer:

1. What security context is associated with the directory?
2. What security context is associated with the file?
3. What information is displayed for the running processes?

---

## 🧹 Cleanup

Remove the test files and directory:

```bash
rm -rf ~/selinux-lab ~/selinux-challenge
```

If you changed SELinux enforcement during the lab, make sure it has been restored to the appropriate state before finishing.

Check:

```bash
getenforce
```

---

## 📋 Lab Completion Checklist

- [ ] Understand the purpose of SELinux
- [ ] Understand DAC and MAC
- [ ] Check SELinux status
- [ ] Check the enforcement mode
- [ ] Understand Enforcing mode
- [ ] Understand Permissive mode
- [ ] Understand Disabled mode
- [ ] View file security contexts
- [ ] View process security contexts
- [ ] Understand SELinux's security role
- [ ] Complete the challenge

---

## 📌 Summary

In this final lab, you learned the fundamentals of Security-Enhanced Linux (SELinux).

You explored SELinux status, enforcement modes, security contexts, and basic administration commands.

SELinux provides an additional security layer beyond traditional Linux permissions and is an important technology to understand when working with enterprise Linux systems.

---

# 🎓 Linux Administration & Security Guide — Complete

With Lab 60 completed, all **60 Linux labs** in this project have now been organized into **13 sections** covering:

- Linux fundamentals
- Shell and command-line operations
- Package and system management
- User and access management
- Task scheduling and remote access
- Text processing and search
- System monitoring and services
- Firewall and network security
- Storage and filesystem management
- Shell environment and productivity
- Networking and system utilities
- Logging and system maintenance
- Linux security

This completes the practical Linux Administration & Security Guide.

---

## 🚀 Project Completion

**60 Labs • 13 Sections • Linux Administration & Security**

The repository now provides a structured progression from Linux fundamentals to system administration, networking, automation concepts, monitoring, and security.
