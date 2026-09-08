# 🟡 Intermediate Linux Self-Assessment

This assessment evaluates practical Linux administration skills covered in **Labs 21–40**.

The assessment moves beyond basic command usage and evaluates your ability to manage software, users, scheduled tasks, remote access, text processing, logs, services and firewall configuration.

---

# 🎯 Assessment Objective

You should demonstrate that you can:

- Manage Linux packages
- Inspect hardware and disk usage
- Manage users and groups
- Understand password policies
- Schedule tasks
- Access remote systems
- Transfer files
- Edit and process text
- Search files
- Inspect logs
- Manage systemd services
- Configure basic firewalls

---

# 📚 Coverage

| Labs | Topic |
|---|---|
| 21 | APT Package Management |
| 22 | YUM/DNF Package Management |
| 23 | System Hardware Information |
| 24 | Disk Usage and File Size |
| 25 | Creating and Managing Users |
| 26 | Group Management |
| 27 | Password Policies |
| 28 | Crontab |
| 29 | `at` Scheduling |
| 30 | SSH |
| 31 | SCP/SFTP |
| 32 | vi/vim |
| 33 | grep |
| 34 | sed |
| 35 | awk |
| 36 | find |
| 37 | System Logs |
| 38 | systemd |
| 39 | UFW |
| 40 | iptables |

---

# 📋 Assessment Rules

- Use an authorized Linux environment.
- Perform administrative changes carefully.
- Use a VM where possible for firewall and service exercises.
- Do not modify systems you do not administer.
- Verify configuration after making changes.
- Record important observations.

---

# 📦 Part 1 — Package Management

## Task 1 — APT

On an appropriate Debian/Ubuntu system:

1. Inspect package information.
2. Search for a package.
3. Install an appropriate package.
4. Verify installation.
5. Inspect installed package information.
6. Remove the test package when finished.

Explain the purpose of the package manager.

---

## Task 2 — YUM/DNF

On an appropriate RPM-based system:

1. Identify the package manager available.
2. Search for a package.
3. Inspect package information.
4. Install a suitable package.
5. Verify it.
6. Remove the test package if appropriate.

Explain the relationship between YUM and DNF.

---

# 🖥️ Part 2 — Hardware & Disk Usage

## Task 3 — Hardware Inspection

Determine:

- CPU information
- Memory information
- Block-device information
- PCI/device information where available
- Kernel information

Explain what each category tells an administrator.

---

## Task 4 — Disk Usage

Identify:

- Filesystem usage
- Large directories
- Large files
- Available space

Explain the difference between filesystem capacity and directory size.

---

# 👤 Part 3 — Users & Groups

## Task 5 — User Management

Create a test user.

Demonstrate:

- User creation
- User information inspection
- Home directory identification
- Switching to or testing the account
- Removing the test account when finished

---

## Task 6 — Group Management

Create a test group.

Add the test user to the group.

Verify the membership.

Explain why groups are useful for access management.

---

# 🔐 Part 4 — Password Policies

## Task 7 — Password Management

Inspect the relevant password/account configuration on your Linux system.

Explain:

- Password aging
- Password expiration
- Account aging
- Basic password policy concepts

Demonstrate appropriate configuration in a safe test environment where supported.

---

# ⏰ Part 5 — Scheduling

## Task 8 — Crontab

Create a scheduled task that performs a harmless action such as writing a timestamp to a test log.

Verify the schedule.

Explain:

- Minute
- Hour
- Day of month
- Month
- Day of week

---

## Task 9 — `at`

Schedule a one-time harmless task.

Verify that the task has been scheduled.

Explain how `at` differs from `cron`.

---

# 🔑 Part 6 — Remote Access

## Task 10 — SSH

Using two authorized Linux systems or VMs:

1. Identify the SSH service.
2. Connect to the remote system.
3. Verify your identity and location.
4. Safely terminate the session.

Explain why SSH is preferred over insecure remote-access protocols.

---

## Task 11 — SCP/SFTP

Transfer a test file between authorized systems.

Demonstrate:

- Secure copy
- Secure file transfer
- Verification of the transferred file

---

# 📝 Part 7 — Text Editing

## Task 12 — vi/vim

Using `vi` or `vim`, create or modify a test configuration/text file.

Demonstrate understanding of:

- Normal mode
- Insert mode
- Saving
- Exiting
- Basic navigation

---

# 🔎 Part 8 — Text Processing

## Task 13 — grep

Create a text dataset.

Use `grep` to:

- Search for text
- Perform a case-insensitive search
- Display matching lines
- Count matches where appropriate

---

## Task 14 — sed

Use `sed` to perform controlled text transformations on a test file.

Demonstrate:

- Searching
- Replacing
- Selecting lines
- Writing transformed output

---

## Task 15 — awk

Create structured text containing multiple fields.

Use `awk` to:

- Select fields
- Filter records
- Produce formatted output
- Perform a simple calculation

---

## Task 16 — find

Use `find` to locate files based on:

- Name
- Type
- Size
- Modification criteria

Explain why `find` is useful to system administrators.

---

# 📜 Part 9 — Logs

## Task 17 — System Logs

Inspect available Linux logs.

Identify examples of:

- System activity
- Authentication-related information
- Service-related information
- Errors or warnings

Explain why logs are important for administration and security.

---

# ⚙️ Part 10 — systemd

## Task 18 — Service Management

Choose an appropriate service in your environment.

Demonstrate how to:

- Check service status
- Start a service
- Stop a service where safe
- Restart a service where appropriate
- Enable/disable startup behavior where appropriate

Do not disable critical system services.

---

# 🧱 Part 11 — UFW

## Task 19 — Basic Firewall

On a suitable test VM:

1. Inspect firewall status.
2. Configure appropriate basic rules.
3. Allow required traffic.
4. Verify the rules.
5. Test connectivity.
6. Return the system to a safe state.

Explain the purpose of a host firewall.

---

# 🔥 Part 12 — iptables

## Task 20 — Basic iptables

Inspect the current firewall rules.

Explain:

- Chains
- Rules
- Policies
- Packet filtering

On a disposable lab environment, demonstrate a basic rule and verify its effect.

Avoid locking yourself out of a remote system.

---

# 🧠 Knowledge Questions

1. What is a package manager?
2. What is the difference between APT and DNF?
3. What information can hardware inspection commands provide?
4. What is the difference between filesystem usage and directory size?
5. Why are groups useful?
6. What is password aging?
7. What is the difference between `cron` and `at`?
8. Why is SSH important?
9. What is the difference between SCP and SFTP?
10. What is the purpose of `grep`?
11. What problem does `sed` solve?
12. What makes `awk` useful for structured data?
13. How does `find` locate files?
14. Why are system logs important?
15. What is systemd?
16. What is a firewall?
17. What is the difference between UFW and iptables?

---

# 🧩 Intermediate Challenge

Create a small administrative environment containing:

- A test user
- A test group
- A test directory
- Appropriate permissions
- A scheduled task
- A system log entry or test log
- A simple text-processing workflow
- A basic firewall configuration

Then document:

1. What you configured.
2. Why you configured it.
3. How you verified it.
4. How you would troubleshoot it if it failed.

---

# 📊 Suggested Scoring

| Area | Points |
|---|---:|
| Package management | 3 |
| Hardware & disk management | 2 |
| Users & groups | 3 |
| Password policies | 2 |
| Scheduling | 2 |
| SSH/SCP/SFTP | 3 |
| vi/vim | 1 |
| grep/sed/awk/find | 4 |
| Logs | 2 |
| systemd | 2 |
| UFW/iptables | 4 |
| **Total** | **28** |

---

# 🏅 Evaluation

### Excellent

You can independently administer users, packages, services, scheduled tasks and basic firewall rules.

### Good

You understand the concepts and can complete most practical tasks with limited reference material.

### Developing

You understand the theory but need more practice applying administrative commands.

### Review Required

Revisit the corresponding Labs 21–40 before continuing.

---

# ✅ Completion Checklist

- [ ] APT assessment completed
- [ ] YUM/DNF assessment completed
- [ ] Hardware inspected
- [ ] Disk usage analyzed
- [ ] User created and managed
- [ ] Group created and managed
- [ ] Password policy concepts demonstrated
- [ ] Cron task created
- [ ] `at` task created
- [ ] SSH connection demonstrated
- [ ] SCP/SFTP transfer completed
- [ ] vi/vim task completed
- [ ] grep task completed
- [ ] sed task completed
- [ ] awk task completed
- [ ] find task completed
- [ ] Logs inspected
- [ ] systemd service managed
- [ ] UFW task completed
- [ ] iptables concepts demonstrated
- [ ] Knowledge questions answered
- [ ] Intermediate challenge completed

---

# 🚀 Advancement Criteria

Proceed to the Advanced Assessment when you can manage common Linux administration tasks confidently and can troubleshoot basic problems without step-by-step instructions.

**Next:** 🔴 Advanced Linux Self-Assessment
