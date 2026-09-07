# Lab 22 — Package Management with YUM/DNF

Package management is a fundamental Linux administration skill. On RPM-based Linux distributions such as CentOS, Fedora, and Red Hat Enterprise Linux (RHEL), **YUM** and **DNF** are used to manage software packages and their dependencies.

This lab provides practical experience with updating package information, searching repositories, installing software, verifying installations, and removing packages.

---

## 🎯 Objective

By completing this lab, you will:

- Understand basic package management concepts.
- Learn how YUM and DNF work on RPM-based Linux systems.
- Update available package information.
- Apply available software updates.
- Search for packages in configured repositories.
- Install software packages.
- Verify installed software.
- Remove software packages.
- Understand the importance of keeping a Linux system updated.

---

## 📚 Prerequisites

Before starting this lab, you should have:

- A Linux system using an RPM-based distribution.
- CentOS, Fedora, or Red Hat Enterprise Linux (RHEL).
- Basic Linux command-line knowledge.
- A user account with `sudo` privileges.
- Access to configured software repositories.

> **Important:** This lab is intended for RPM-based distributions. Ubuntu and Debian normally use `apt` rather than YUM/DNF.

---

# 1. Understanding YUM and DNF

YUM and DNF are package-management tools used by RPM-based Linux distributions.

They can be used to:

- Find available software.
- Install packages.
- Remove packages.
- Update installed software.
- Resolve software dependencies.
- Obtain packages from configured repositories.

### YUM

YUM stands for **Yellowdog Updater, Modified**.

Example:

```bash
sudo yum install vim
```

### DNF

DNF is the modern package-management technology that replaced YUM in many newer RPM-based distributions.

Example:

```bash
sudo dnf install vim
```

The exact command available depends on the Linux distribution and version.

---

# 2. Task 1 — Update Package Information

## Objective

Learn how to update your system's package information so that the package manager has current information about available software and updates.

First, use YUM:

```bash
sudo yum update
```

Or, on systems using DNF:

```bash
sudo dnf update
```

Observe the output carefully.

The package manager may display:

- Packages with available updates.
- Dependencies.
- Packages that will be upgraded.
- Packages that may need to be installed.
- Download sizes.
- Disk-space requirements.

---

# 3. Applying Available Updates

After reviewing available updates, you can apply them using:

```bash
sudo yum upgrade
```

Or:

```bash
sudo dnf upgrade
```

The package manager will resolve the required dependencies and apply the available upgrades.

### Check the process carefully

Before confirming an upgrade, review:

- Which packages will change.
- Whether additional packages will be installed.
- Whether packages will be removed.
- How much data will be downloaded.
- How much disk space will be used.

---

# 4. Task 2 — Search for a Package

## Objective

Learn how to search the repositories for available packages.

For example, search for packages related to Vim:

```bash
yum search vim
```

Or:

```bash
dnf search vim
```

The results can contain package names and descriptions matching the search term.

### Try another search

For example:

```bash
dnf search nginx
```

If your system uses YUM:

```bash
yum search nginx
```

Review the returned package names and descriptions.

---

# 5. Task 3 — Install a Package

## Objective

Practice installing software using YUM or DNF.

The original exercise uses Vim as the example package.

### Using YUM

```bash
sudo yum install vim
```

### Using DNF

```bash
sudo dnf install vim
```

When prompted, review the proposed changes and confirm the installation.

The package manager may also install dependencies required by Vim.

---

# 6. Verify the Installation

After installation, verify that Vim is available:

```bash
vim --version
```

If the package was installed successfully, the command should display information about the installed Vim version.

You can also check whether the command is available:

```bash
command -v vim
```

This helps confirm that the executable can be found through your system's command path.

---

# 7. Remove a Package

## Objective

Learn how to remove an installed package.

### Using YUM

```bash
sudo yum remove vim
```

### Using DNF

```bash
sudo dnf remove vim
```

Review the packages that the package manager proposes to remove before confirming.

---

# 8. Verify the Removal

After removing Vim, check whether the command is still available:

```bash
command -v vim
```

You can also try:

```bash
vim --version
```

If Vim has been successfully removed, the command should no longer be available.

---

# 🧪 Practical Lab

Complete the following sequence on an RPM-based Linux system.

### Step 1 — Identify your package manager

```bash
command -v dnf
command -v yum
```

### Step 2 — Update package information

Use the appropriate command:

```bash
sudo dnf update
```

or:

```bash
sudo yum update
```

### Step 3 — Search for Vim

```bash
dnf search vim
```

or:

```bash
yum search vim
```

### Step 4 — Install Vim

```bash
sudo dnf install vim
```

or:

```bash
sudo yum install vim
```

### Step 5 — Verify the installation

```bash
vim --version
command -v vim
```

### Step 6 — Remove Vim

```bash
sudo dnf remove vim
```

or:

```bash
sudo yum remove vim
```

### Step 7 — Verify the removal

```bash
command -v vim
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `yum update` | Update package information and available packages |
| `dnf update` | Update package information and available packages |
| `yum upgrade` | Apply available package upgrades |
| `dnf upgrade` | Apply available package upgrades |
| `yum search <package>` | Search for packages |
| `dnf search <package>` | Search for packages |
| `yum install <package>` | Install a package |
| `dnf install <package>` | Install a package |
| `yum remove <package>` | Remove a package |
| `dnf remove <package>` | Remove a package |
| `vim --version` | Verify Vim installation |
| `command -v <command>` | Locate an available command |

---

# 🧠 Key Concepts

### Package

A package is a collection of software files distributed together so that the software can be installed and managed by the operating system.

### Repository

A repository is a software source containing packages that can be downloaded and installed by a package manager.

### Dependency

A dependency is another software package or component required for a program to work correctly.

### YUM

YUM is a package-management tool historically used extensively on RPM-based Linux distributions.

### DNF

DNF is the modern package-management tool used by many current RPM-based distributions.

### RPM

RPM is the underlying package format commonly associated with Red Hat-based Linux systems.

---

# 🛡️ Security Perspective

Package management is also an important part of Linux security.

Keeping packages updated can help ensure that security fixes are applied to vulnerable software.

For example:

```bash
sudo dnf update
```

or:

```bash
sudo yum update
```

Regular updates can help reduce the risk of running outdated software containing known security vulnerabilities.

However, updates should still be reviewed before deployment on important systems.

Administrators should consider:

- Package source.
- Package authenticity.
- Security updates.
- Dependencies.
- Compatibility.
- System stability.
- Impact on running services.

---

# ⚠️ Best Practices

- Use trusted software repositories.
- Avoid installing packages from unknown sources.
- Review proposed package changes before confirming.
- Keep important systems updated.
- Test major updates before applying them to production systems.
- Avoid removing packages without checking their dependencies.
- Use `sudo` only when administrative privileges are required.
- Maintain backups before significant system changes.

---

# ❓ Questions

1. What is the purpose of YUM?
2. What is DNF?
3. What type of Linux distributions commonly use YUM/DNF?
4. What is a software repository?
5. What is a package dependency?
6. What is the difference between installing and removing a package?
7. How can you search for a package using DNF?
8. How can you verify that Vim is installed?
9. Why are package updates important for security?
10. Why should administrators review package changes before confirming them?

---

# 🧩 Challenge

Perform the following without copying the practical sequence directly:

1. Search for another package available in your repositories.
2. Identify its package name.
3. Install it.
4. Verify that it was installed successfully.
5. Identify the installed command.
6. Remove the package.
7. Verify that it is no longer available.

Record the commands you used and explain what each command accomplished.

---

# 📝 Administration Scenario

Imagine you are administering an RPM-based Linux server.

A user requests that a software package be installed. Before installing it, you need to:

1. Search for the package.
2. Confirm that it is available from the configured repositories.
3. Install it.
4. Verify that it works.
5. Keep the system updated.
6. Remove the software when it is no longer required.

Use the YUM/DNF commands learned in this lab to complete the workflow.

---

# 🧹 Cleanup

If you installed Vim only for this lab and no longer need it, remove it with:

```bash
sudo dnf remove vim
```

or:

```bash
sudo yum remove vim
```

Then verify:

```bash
command -v vim
```

---

# 📌 Summary

In this lab, you learned the fundamentals of package management on RPM-based Linux systems.

You practiced:

- Updating package information.
- Applying available upgrades.
- Searching repositories.
- Installing packages.
- Verifying installations.
- Removing packages.
- Understanding dependencies and repositories.
- Considering package management from a security perspective.

YUM and DNF are essential tools for Linux administrators working with RPM-based distributions.

---

# ✅ Lab Completion Checklist

- [ ] Identified whether YUM or DNF is available.
- [ ] Updated package information.
- [ ] Reviewed available updates.
- [ ] Searched for a package.
- [ ] Installed Vim.
- [ ] Verified the installation.
- [ ] Removed Vim.
- [ ] Verified the removal.
- [ ] Answered the review questions.
- [ ] Completed the challenge.

---

# 🚀 Next Lab

**Lab 23 — System Hardware**

In the next lab, you will move from software/package management to understanding and inspecting Linux system hardware.
