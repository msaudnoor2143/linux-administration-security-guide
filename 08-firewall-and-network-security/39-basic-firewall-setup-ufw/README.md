# Lab 39 — Basic Firewall Setup (UFW)

> Learn the fundamentals of host-based firewalls and configure basic inbound traffic rules using UFW on Ubuntu-based Linux systems.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand the purpose of a firewall
- Understand basic inbound and outbound traffic control
- Install UFW
- Enable UFW
- Allow required services
- Configure basic firewall rules
- Check firewall status
- Test rule changes
- Understand the security importance of minimizing exposed services

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Access to an Ubuntu or compatible Linux system
- A terminal
- Basic Linux command-line knowledge
- `sudo` privileges
- Basic understanding of networking and ports

> **Important:** If you are connected to the machine remotely through SSH, make sure SSH access is allowed before enabling the firewall. Otherwise, you may lose remote access.

---

# 1. Understanding Firewalls

A firewall controls network traffic according to configured rules.

A host-based firewall can control traffic entering or leaving an individual Linux machine.

Common firewall decisions include:

```text
ALLOW
DENY
REJECT
```

A firewall can help reduce the number of network services that are accessible from other systems.

---

# 2. Understanding UFW

UFW stands for:

**Uncomplicated Firewall**

It provides a simpler command-line interface for managing firewall rules on systems that use the underlying Linux firewall framework.

UFW is commonly used on Ubuntu systems.

---

# 3. Installing UFW

First update the package information:

```bash
sudo apt update
```

Install UFW:

```bash
sudo apt install ufw
```

If UFW is already installed, the package manager will indicate that it is already present.

---

# 4. Checking UFW Status

Before enabling the firewall, check its current status:

```bash
sudo ufw status
```

You can also request more detailed information:

```bash
sudo ufw status verbose
```

---

# 5. Enabling UFW

Enable the firewall:

```bash
sudo ufw enable
```

Check the status:

```bash
sudo ufw status verbose
```

The firewall should now report that it is active.

---

# 6. Understanding Default Policies

A common UFW configuration uses:

```text
deny incoming
allow outgoing
```

This means:

- Incoming connections are denied unless explicitly allowed.
- Outgoing connections are allowed by default.

You can explicitly configure these policies with:

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

Then verify:

```bash
sudo ufw status verbose
```

---

# 7. Allowing SSH

SSH is commonly used for remote administration.

To allow SSH:

```bash
sudo ufw allow ssh
```

You can verify the rule:

```bash
sudo ufw status
```

> **Critical:** If you are remotely connected through SSH, configure the SSH allow rule before enabling UFW.

---

# 8. Allowing HTTP

HTTP commonly uses TCP port `80`.

You can allow HTTP by service name:

```bash
sudo ufw allow http
```

Then check:

```bash
sudo ufw status
```

---

# 9. Understanding UFW Rules

After allowing SSH and HTTP, the rules may resemble:

```text
22/tcp    ALLOW
80/tcp    ALLOW
```

The exact formatting can vary.

The important idea is that traffic matching an allowed rule can pass through the firewall.

---

# 10. Checking Detailed Firewall Status

Use:

```bash
sudo ufw status verbose
```

This provides information about:

- Whether UFW is active
- Default incoming policy
- Default outgoing policy
- Configured rules

---

# 11. Testing Rule Changes

You can temporarily deny SSH:

```bash
sudo ufw deny ssh
```

Check the rules:

```bash
sudo ufw status
```

Then restore SSH access:

```bash
sudo ufw allow ssh
```

Verify:

```bash
sudo ufw status
```

> **Warning:** Do not perform this test on a remote machine unless you have another way to recover access. Blocking SSH can disconnect you.

---

# 🧪 Practical Lab

> Perform this exercise on a test Linux system whenever possible.

---

## Task 1 — Check UFW Installation

Run:

```bash
sudo ufw status
```

If UFW is not installed, install it:

```bash
sudo apt update
sudo apt install ufw
```

---

## Task 2 — Configure Default Policies

Run:

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

Verify:

```bash
sudo ufw status verbose
```

---

## Task 3 — Allow SSH

Add the SSH rule:

```bash
sudo ufw allow ssh
```

Verify:

```bash
sudo ufw status
```

---

## Task 4 — Allow HTTP

Add the HTTP rule:

```bash
sudo ufw allow http
```

Verify:

```bash
sudo ufw status
```

---

## Task 5 — Enable the Firewall

Enable UFW:

```bash
sudo ufw enable
```

Then verify:

```bash
sudo ufw status verbose
```

---

## Task 6 — Inspect the Final Configuration

Run:

```bash
sudo ufw status verbose
```

Record:

- Firewall status
- Default incoming policy
- Default outgoing policy
- SSH rule
- HTTP rule

---

## Task 7 — Practice a Rule Change

Temporarily deny SSH:

```bash
sudo ufw deny ssh
```

Check:

```bash
sudo ufw status
```

Restore SSH:

```bash
sudo ufw allow ssh
```

Verify again:

```bash
sudo ufw status
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `sudo ufw status` | Display firewall status and rules |
| `sudo ufw status verbose` | Display detailed firewall information |
| `sudo ufw enable` | Enable UFW |
| `sudo ufw disable` | Disable UFW |
| `sudo ufw allow ssh` | Allow SSH traffic |
| `sudo ufw allow http` | Allow HTTP traffic |
| `sudo ufw deny ssh` | Deny SSH traffic |
| `sudo ufw default deny incoming` | Deny incoming traffic by default |
| `sudo ufw default allow outgoing` | Allow outgoing traffic by default |

---

# 🧠 Key Concepts

## Firewall

A security mechanism that controls network traffic according to defined rules.

---

## UFW

A simplified firewall-management interface commonly used on Ubuntu.

---

## Incoming Traffic

Network connections attempting to reach the local system.

---

## Outgoing Traffic

Network connections initiated from the local system toward another system.

---

## Default Policy

The action applied when traffic does not match a more specific rule.

A common secure starting point is:

```text
Deny incoming
Allow outgoing
```

with explicit exceptions for required services.

---

## SSH

Secure Shell is commonly used for remote administration.

Its standard TCP port is:

```text
22
```

---

## HTTP

HTTP is commonly associated with:

```text
TCP port 80
```

---

# 🛡️ Security Perspective

A firewall is an important layer of host security.

A well-configured firewall can help:

- Reduce exposed services
- Restrict unwanted inbound connections
- Limit network attack surface
- Control access to administrative services
- Support system hardening

However, a firewall should not be treated as the only security control.

Other security measures include:

- Strong authentication
- Software updates
- Least privilege
- Secure configuration
- Logging and monitoring
- Service hardening

---

# ⚠️ Best Practices

### 1. Allow only required services

Avoid opening ports simply because they are available.

### 2. Protect remote administration

Before enabling a firewall on an SSH-managed machine, ensure SSH is allowed.

### 3. Review firewall rules regularly

Use:

```bash
sudo ufw status verbose
```

### 4. Test firewall changes carefully

Incorrect rules can block legitimate access.

### 5. Avoid unnecessary exposure

If a service is not required, consider whether it should be running or accessible.

---

# 📝 Questions

1. What is the purpose of a firewall?
2. What does UFW stand for?
3. What does `sudo ufw enable` do?
4. How do you check UFW status?
5. How do you allow SSH?
6. What port does SSH commonly use?
7. What port does HTTP commonly use?
8. What does `deny incoming` mean?
9. Why can enabling a firewall remotely be risky?
10. Why should only required services be allowed?

---

# 🚀 Challenge

Configure a test system with:

```text
Incoming: Denied by default
Outgoing: Allowed by default
SSH: Allowed
HTTP: Allowed
```

Then display the final configuration:

```bash
sudo ufw status verbose
```

Explain why each rule exists.

---

# ✅ Lab Completion Checklist

- [ ] I understand what a firewall does
- [ ] I understand UFW
- [ ] I can install UFW
- [ ] I can check UFW status
- [ ] I can enable UFW
- [ ] I can configure default policies
- [ ] I can allow SSH
- [ ] I can allow HTTP
- [ ] I can deny a service
- [ ] I understand why firewall configuration matters for security
- [ ] I understand the risk of locking myself out of SSH

---

## Summary

In this lab, you learned the fundamentals of host-based firewall management with UFW. You configured default traffic policies, allowed required services, inspected firewall rules, and practiced modifying access rules.

Firewall configuration is an important part of Linux system hardening because it helps reduce unnecessary network exposure.

---

## 🚀 Next Lab

**Lab 40 — Working with iptables**
