# Lab 38 — Systemd Services Overview

> Learn how `systemd` manages Linux services and how to inspect, start, stop, enable, and disable services using `systemctl`.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand the role of `systemd`
- Identify active system services
- List running services
- Inspect service status
- Start services
- Stop services
- Enable services at boot
- Disable services at boot
- Understand basic service management with `systemctl`

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Access to a Linux system
- Basic Linux command-line knowledge
- A terminal
- A Linux distribution using `systemd`
- `sudo` privileges for administrative service operations

> Common `systemd`-based distributions include Ubuntu, Debian, Fedora, and many other modern Linux distributions.

---

# 1. Understanding `systemd`

`systemd` is an initialization and service-management system used by many Linux distributions.

It is responsible for tasks such as:

- Starting services
- Managing background processes
- Handling system startup
- Tracking service states
- Managing dependencies between services

The main command used to interact with `systemd` is:

```bash
systemctl
```

---

# 2. Listing Running Services

To list active service units:

```bash
systemctl list-units --type=service
```

This displays services currently loaded and active according to the systemd unit manager.

You may see columns such as:

```text
UNIT
LOAD
ACTIVE
SUB
DESCRIPTION
```

---

## 2.1 Understanding Service States

Important status fields include:

### LOAD

Indicates whether the service unit configuration was loaded correctly.

### ACTIVE

Shows the general active state of the service.

### SUB

Provides a more detailed state.

For example, a service may show:

```text
active running
```

---

# 3. Checking the Status of a Service

Use:

```bash
systemctl status <service-name>
```

For example:

```bash
systemctl status apache2
```

if Apache is installed.

The output can provide information such as:

- Whether the service is running
- When it started
- Process information
- Recent service messages
- The service unit path

---

# 4. Starting a Service

To start a service:

```bash
sudo systemctl start <service-name>
```

Example:

```bash
sudo systemctl start apache2
```

After starting the service, verify its status:

```bash
systemctl status apache2
```

> Only use a service name that actually exists on your system.

---

# 5. Stopping a Service

To stop a running service:

```bash
sudo systemctl stop <service-name>
```

For example:

```bash
sudo systemctl stop apache2
```

Then verify:

```bash
systemctl status apache2
```

---

# 6. Enabling a Service at Boot

Starting a service does not necessarily mean it will automatically start after the next reboot.

To configure a service to start automatically during boot:

```bash
sudo systemctl enable <service-name>
```

For example:

```bash
sudo systemctl enable apache2
```

The service is then configured to start automatically when the appropriate systemd boot target is reached.

---

# 7. Disabling a Service at Boot

To prevent a service from automatically starting at boot:

```bash
sudo systemctl disable <service-name>
```

Example:

```bash
sudo systemctl disable apache2
```

This removes the boot-time enablement configuration.

> **Important:** Disabling a service from boot does not necessarily stop a service that is currently running.

If you also need to stop it immediately:

```bash
sudo systemctl stop apache2
```

---

# 8. Practical Service Workflow

A common administrative workflow is:

### Step 1 — Identify the service

```bash
systemctl list-units --type=service
```

### Step 2 — Check its status

```bash
systemctl status <service-name>
```

### Step 3 — Start it if required

```bash
sudo systemctl start <service-name>
```

### Step 4 — Verify

```bash
systemctl status <service-name>
```

### Step 5 — Configure boot behavior if required

```bash
sudo systemctl enable <service-name>
```

---

# 🧪 Practical Lab

> **Important:** Use a service that is actually installed on your system. Do not randomly stop critical system services.

---

## Task 1 — List Active Services

Run:

```bash
systemctl list-units --type=service
```

Review the output.

Identify one service that you recognize.

---

## Task 2 — Inspect a Service

Choose a non-critical service that exists on your system.

Check its status:

```bash
systemctl status <service-name>
```

Record:

- Active state
- Sub-state
- Service description
- Whether it is currently running

---

## Task 3 — Start a Service

If you have identified a suitable service that is stopped, start it:

```bash
sudo systemctl start <service-name>
```

Verify:

```bash
systemctl status <service-name>
```

---

## Task 4 — Stop a Service

For a suitable practice service:

```bash
sudo systemctl stop <service-name>
```

Verify:

```bash
systemctl status <service-name>
```

---

## Task 5 — Enable a Service

Configure the selected service to start during boot:

```bash
sudo systemctl enable <service-name>
```

---

## Task 6 — Disable a Service

If appropriate for your practice service:

```bash
sudo systemctl disable <service-name>
```

---

## Task 7 — Verify the Service Configuration

Check the service again:

```bash
systemctl status <service-name>
```

Observe the information displayed by systemd.

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `systemctl` | Main systemd management command |
| `systemctl list-units --type=service` | List service units |
| `systemctl status SERVICE` | Display service status |
| `sudo systemctl start SERVICE` | Start a service |
| `sudo systemctl stop SERVICE` | Stop a service |
| `sudo systemctl enable SERVICE` | Enable service at boot |
| `sudo systemctl disable SERVICE` | Disable service at boot |

---

# 🧠 Key Concepts

## `systemd`

The service and initialization system used by many modern Linux distributions.

---

## `systemctl`

The primary command-line interface for controlling systemd.

---

## Service Unit

A systemd configuration unit representing a service.

Examples may include:

```text
ssh.service
cron.service
apache2.service
```

The exact services installed depend on the system.

---

## Start vs Enable

These operations are different.

### Start

```bash
sudo systemctl start SERVICE
```

Starts the service now.

### Enable

```bash
sudo systemctl enable SERVICE
```

Configures the service to start automatically during boot.

---

## Stop vs Disable

These are also different.

### Stop

Stops the currently running service.

### Disable

Prevents the service from being automatically started during boot.

---

# 🛡️ Security Perspective

Service management is an important part of Linux security.

Every running network-facing service can potentially increase the system's attack surface.

Administrators should therefore understand:

- Which services are running
- Which services are required
- Which services are exposed
- Which services start automatically
- Which services should be disabled

For example, unnecessary services may create additional opportunities for unauthorized access or software vulnerabilities.

A security-conscious administrator should periodically review running services.

---

# ⚠️ Best Practices

### 1. Do not randomly stop system-critical services

Some services are required for normal system operation.

### 2. Identify a service before modifying it

Use:

```bash
systemctl status <service-name>
```

### 3. Prefer a practice service

If you are learning service management, use a non-critical service that you understand.

### 4. Understand the difference between start and enable

Starting affects the current system state.

Enabling affects future boot behavior.

### 5. Verify changes

After modifying a service:

```bash
systemctl status <service-name>
```

---

# 📝 Questions

1. What is `systemd`?
2. What is the purpose of `systemctl`?
3. How do you list active services?
4. How do you check a service's status?
5. What command starts a service?
6. What command stops a service?
7. What is the difference between `start` and `enable`?
8. What is the difference between `stop` and `disable`?
9. Why is service management important for security?
10. Why should administrators avoid disabling unknown services?

---

# 🚀 Challenge

Choose a non-critical service available on your system.

Document:

```text
Service Name:
Current Status:
Description:
Running:
Enabled at Boot:
```

Then explain:

- Why the service exists
- Whether it needs to run continuously
- Whether it should start automatically

---

# ✅ Lab Completion Checklist

- [ ] I understand the role of `systemd`
- [ ] I understand `systemctl`
- [ ] I can list active services
- [ ] I can inspect service status
- [ ] I understand how to start a service
- [ ] I understand how to stop a service
- [ ] I understand how to enable a service
- [ ] I understand how to disable a service
- [ ] I understand the difference between start and enable
- [ ] I understand why service management matters for security

---

## Summary

In this lab, you learned the fundamentals of `systemd` service management. You practiced listing services, checking service status, starting and stopping services, and configuring services to start or not start automatically during boot.

Understanding service management is an essential Linux administration and security skill because it allows administrators to control system functionality and reduce unnecessary attack surface.

---

## 🚀 Next Lab

**Lab 39 — Basic Firewall Setup (UFW)**
