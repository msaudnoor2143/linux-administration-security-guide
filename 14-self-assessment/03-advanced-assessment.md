# 🔴 Advanced Linux Self-Assessment

This assessment evaluates advanced Linux administration, storage, filesystem, networking, maintenance and security concepts covered in **Labs 41–60**.

The focus is on understanding how Linux systems are structured and being able to reason about configuration, storage, maintenance and security.

---

# 🎯 Assessment Objective

You should demonstrate that you can:

- Understand disk partitioning
- Mount and unmount filesystems
- Configure swap
- Understand LVM
- Work with `/etc/fstab`
- Manage shell startup files
- Use shell history
- Chain commands
- Understand manual pages
- Work with shell variables
- Use regular expressions
- Transfer files using network utilities
- Inspect uptime
- Analyze filesystem usage
- Understand secure file deletion
- Inspect cron logs
- Understand log rotation
- Configure aliases
- Monitor system resources
- Understand SELinux

---

# 📚 Coverage

| Labs | Topic |
|---|---|
| 41 | Disk Partitioning |
| 42 | Mounting and Unmounting |
| 43 | Swap |
| 44 | LVM |
| 45 | `/etc/fstab` |
| 46 | Bash Profile vs Bashrc |
| 47 | History |
| 48 | Command Chaining |
| 49 | Manual Pages |
| 50 | Shell Variables |
| 51 | Regular Expressions |
| 52 | wget/curl |
| 53 | System Uptime |
| 54 | df/du |
| 55 | Secure File Deletion |
| 56 | Cron Logs |
| 57 | Log Rotation |
| 58 | Aliases in `.bashrc` |
| 59 | top/htop |
| 60 | SELinux |

---

# ⚠️ Important

Storage, swap, filesystem, firewall and SELinux exercises can affect system behavior.

Perform practical tasks inside a **VM or dedicated lab environment whenever possible**.

Do not experiment with important production filesystems.

---

# 💽 Part 1 — Disk Partitioning

## Task 1 — Inspect Storage

Identify:

- Available disks
- Partitions
- Filesystem types
- Mount points
- Available space

Explain the relationship between:

```text
Disk
 ↓
Partition
 ↓
Filesystem
 ↓
Mount Point
```

---

## Task 2 — Partitioning

Using a suitable disposable virtual disk:

1. Inspect the disk.
2. Create an appropriate partition.
3. Verify the partition.
4. Identify its filesystem state.

Do not modify the operating system's critical disk.

---

# 📂 Part 2 — Mounting

## Task 3 — Mount a Filesystem

Using a suitable test filesystem:

1. Create a mount point.
2. Mount the filesystem.
3. Verify the mount.
4. Inspect its contents.
5. Unmount it.
6. Verify that it is no longer mounted.

Explain why mount points are required.

---

# 🔄 Part 3 — Swap

## Task 4 — Swap Analysis

Determine:

- Whether swap is enabled.
- How much swap is available.
- How Linux reports swap usage.

Explain why swap exists.

In a disposable VM, demonstrate safe swap configuration if required.

---

# 🧱 Part 4 — LVM

## Task 5 — LVM Concepts

Explain:

```text
Physical Volume
       ↓
Volume Group
       ↓
Logical Volume
       ↓
Filesystem
       ↓
Mount Point
```

Inspect available LVM information if LVM is present.

---

## Task 6 — LVM Practical

Using a disposable virtual disk:

- Create or identify an appropriate physical volume.
- Create or identify a volume group.
- Create a logical volume.
- Create a suitable filesystem.
- Mount the logical volume.
- Verify the configuration.

Clean up the lab resources afterward where appropriate.

---

# 📋 Part 5 — `/etc/fstab`

## Task 7 — Filesystem Configuration

Inspect `/etc/fstab`.

Explain:

- Device/UUID
- Mount point
- Filesystem type
- Mount options
- Dump field
- Filesystem check field

Explain why incorrect `/etc/fstab` entries can cause boot problems.

---

# 🐚 Part 6 — Shell Environment

## Task 8 — Bash Startup Files

Explain the difference between:

```text
.bash_profile
.bashrc
```

Determine which files are present in your environment.

Explain when each is commonly used.

---

## Task 9 — History

Use the `history` command to:

- Inspect previous commands.
- Search command history.
- Reuse a previous command safely.

Explain why command history is useful for administration and troubleshooting.

---

# 🔗 Part 7 — Command Chaining

## Task 10 — Chaining

Demonstrate the behavior of:

```text
;
&&
||
```

Explain when each operator should be used.

Create a small workflow where the next command depends on the success or failure of a previous command.

---

# 📖 Part 8 — Manual Pages

## Task 11 — Documentation

Choose several Linux commands and locate their manual pages.

Demonstrate that you can:

- Find a command's purpose.
- Locate options.
- Find examples where available.
- Search within a manual page.

Explain why administrators should know how to use local documentation.

---

# 📦 Part 9 — Shell Variables

## Task 12 — Variables

Create shell variables and demonstrate:

- Assignment
- Expansion
- Quoting
- Exporting
- Reading variable values

Explain the difference between shell variables and environment variables.

---

# 🔎 Part 10 — Regular Expressions

## Task 13 — Regex

Create a text dataset.

Use `grep` with regular expressions to identify patterns such as:

- Specific prefixes
- Specific suffixes
- Repeated patterns
- Numeric patterns
- Structured text

Explain the pattern you created.

---

# 🌐 Part 11 — wget/curl

## Task 14 — Network File Retrieval

Using an authorized and appropriate public resource or local test server:

- Retrieve a file using `wget`.
- Retrieve information using `curl`.
- Inspect the result.
- Explain the difference between the tools.

Do not retrieve or interact with unauthorized resources.

---

# ⏱️ Part 12 — System Uptime

## Task 15 — Uptime

Determine:

- Current uptime
- Load information where available
- System start information where available

Explain what uptime and load information can tell an administrator.

---

# 💾 Part 13 — df and du

## Task 16 — Disk Analysis

Use `df` to analyze filesystem capacity.

Use `du` to analyze directory/file usage.

Explain why both commands are useful and why they answer different questions.

---

# 🧹 Part 14 — Secure File Deletion

## Task 17 — `shred`

On disposable test files:

1. Create a test file.
2. Examine it.
3. Demonstrate the purpose of `shred`.
4. Verify the intended result.

Explain why secure deletion behavior depends on the storage technology and filesystem.

---

# 📝 Part 15 — Cron Logs

## Task 18 — Log Inspection

Locate available cron-related logs.

Identify evidence of scheduled-task activity.

Explain how logs can help troubleshoot scheduled tasks.

---

# 🔄 Part 16 — Log Rotation

## Task 19 — Log Rotation

Inspect the log-rotation configuration available on your Linux system.

Explain:

- Why logs are rotated.
- Why old logs are retained.
- Why uncontrolled log growth is a problem.

---

# ⚡ Part 17 — Bashrc Aliases

## Task 20 — Persistent Alias

Create an appropriate alias in `.bashrc` inside your own user account.

Reload the shell configuration.

Verify the alias.

Explain the difference between a temporary alias and one configured through `.bashrc`.

---

# 📊 Part 18 — System Monitoring

## Task 21 — top/htop

Use `top` or `htop` to inspect:

- CPU activity
- Memory usage
- Running processes
- Load information

Identify a process and explain what information the monitoring tool provides.

---

# 🛡️ Part 19 — SELinux

## Task 22 — SELinux Status

Determine whether SELinux is available and identify its current mode where applicable.

Explain:

```text
Enforcing
Permissive
Disabled
```

Explain the difference between:

```text
DAC
MAC
```

---

## Task 23 — SELinux Contexts

Where SELinux is available, inspect security contexts for:

- Files
- Processes

Explain why contexts are important in SELinux.

---

# 🧠 Advanced Knowledge Questions

1. What is a partition?
2. What is a filesystem?
3. What is a mount point?
4. What is swap?
5. What are PV, VG and LV in LVM?
6. Why is `/etc/fstab` important?
7. What is the difference between `.bash_profile` and `.bashrc`?
8. Why is shell history useful?
9. What is the difference between `;`, `&&` and `||`?
10. Why are manual pages important?
11. What is the difference between a shell variable and an environment variable?
12. What is a regular expression?
13. What are `wget` and `curl` used for?
14. What does system uptime indicate?
15. What is the difference between `df` and `du`?
16. What is the purpose of `shred`?
17. Why is log rotation necessary?
18. What information can `top` provide?
19. What is SELinux?
20. What is the difference between DAC and MAC?
21. What are SELinux security contexts?
22. What do Enforcing and Permissive modes mean?

---

# 🧩 Advanced Challenge

Build and document a small Linux administration scenario involving:

1. A test storage device.
2. A filesystem.
3. A mount point.
4. Appropriate disk-usage analysis.
5. A shell environment configuration.
6. A scheduled task.
7. Log inspection.
8. System monitoring.
9. A security-control analysis involving SELinux where available.

Document:

- Configuration
- Commands used
- Verification
- Problems encountered
- Troubleshooting process
- Cleanup

---

# 📊 Suggested Scoring

| Area | Points |
|---|---:|
| Partitioning | 2 |
| Mounting | 2 |
| Swap | 2 |
| LVM | 4 |
| `/etc/fstab` | 3 |
| Bash environment | 2 |
| History & command chaining | 2 |
| Manual pages | 1 |
| Shell variables | 2 |
| Regex | 2 |
| wget/curl | 2 |
| Uptime/df/du | 3 |
| Secure deletion | 1 |
| Logs & log rotation | 3 |
| Monitoring | 2 |
| SELinux | 4 |
| **Total** | **35** |

---

# 🏅 Evaluation

### Excellent

You can reason about Linux storage, filesystem, environment, maintenance and security concepts and safely perform advanced lab tasks.

### Good

You understand the concepts and can perform most tasks with limited documentation.

### Developing

You understand the basic theory but require more practical experience.

### Review Required

Revisit Labs 41–60 before attempting the final assessment.

---

# ✅ Completion Checklist

- [ ] Storage inspected
- [ ] Partitioning concepts demonstrated
- [ ] Mounting demonstrated
- [ ] Swap inspected
- [ ] LVM concepts understood
- [ ] LVM practical completed
- [ ] `/etc/fstab` analyzed
- [ ] Bash startup files understood
- [ ] History demonstrated
- [ ] Command chaining demonstrated
- [ ] Manual pages used
- [ ] Shell variables demonstrated
- [ ] Regex demonstrated
- [ ] wget/curl demonstrated
- [ ] Uptime inspected
- [ ] df/du demonstrated
- [ ] Secure deletion concepts demonstrated
- [ ] Cron logs inspected
- [ ] Log rotation understood
- [ ] Persistent alias created
- [ ] top/htop used
- [ ] SELinux status/context concepts evaluated
- [ ] Knowledge questions answered
- [ ] Advanced challenge completed

---

# 🚀 Advancement Criteria

Once you can complete this assessment confidently, proceed to the **Final Comprehensive Assessment**, which combines skills from Labs 01–60.

**Next:** 🏆 Final Comprehensive Linux Administration & Security Assessment
