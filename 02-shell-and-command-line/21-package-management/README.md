# Lab 21 — Package Management

> Learn the fundamentals of managing software packages on Linux using the system package manager.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand Linux package management
- Identify the package manager used by a Linux distribution
- Search for available packages
- Install software packages
- Update package information
- Upgrade installed software
- Remove packages when they are no longer required
- Verify installed packages
- Understand why package management is important for system administration

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Access to a Linux system
- A terminal
- Basic knowledge of Linux commands
- Basic understanding of software installation
- Administrative privileges using `sudo`

> **Note:** Package-management commands differ between Linux distributions. Always use the package manager appropriate for your operating system.

---

# 1. Understanding Package Management

Linux software is commonly distributed through **packages**.

A package normally contains the files and metadata required to install a particular application or software component.

A package manager helps administrators:

- Find software
- Install software
- Update software
- Remove software
- Resolve dependencies
- Maintain installed packages

Instead of manually downloading and installing every component, a package manager can obtain software from configured repositories.

---

# 2. Common Linux Package Managers

Different Linux distributions use different package-management tools.

### Debian / Ubuntu

Commonly uses:

```bash
apt
```

Examples:

```bash
sudo apt update
```

```bash
sudo apt install package-name
```

---

### Red Hat / CentOS

Systems using older or compatible package-management workflows may use:

```bash
yum
```

Example:

```bash
sudo yum install package-name
```

Modern Red Hat-based systems commonly use:

```bash
dnf
```

Example:

```bash
sudo dnf install package-name
```

---

# 3. Updating Package Information

On Debian-based systems, update the local package information with:

```bash
sudo apt update
```

This refreshes information about packages available from the configured repositories.

> **Important:** `apt update` updates package information. It does not by itself upgrade all installed packages.

---

# 4. Searching for Packages

You can search the available package information with:

```bash
apt search package-name
```

For example:

```bash
apt search htop
```

This can help you determine whether a package is available from the configured repositories.

---

# 5. Installing a Package

On Debian-based systems, use:

```bash
sudo apt install package-name
```

For example, `htop` can be used as a practice package:

```bash
sudo apt install htop
```

After installation, check whether the program is available:

```bash
htop
```

> Press `q` to exit `htop`.

---

# 6. Checking an Installed Package

You can use:

```bash
apt list --installed
```

to view installed packages.

To search the installed-package list for a particular package:

```bash
apt list --installed | grep htop
```

---

# 7. Viewing Package Information

To display information about a package:

```bash
apt show htop
```

This can provide information such as:

- Package name
- Version
- Architecture
- Description
- Dependencies
- Package size

---

# 8. Upgrading Installed Packages

To upgrade installed packages on a Debian-based system:

```bash
sudo apt upgrade
```

The command checks for newer versions of installed packages and installs available updates.

A typical package-management workflow is:

```bash
sudo apt update
```

followed by:

```bash
sudo apt upgrade
```

---

# 9. Removing a Package

If a package is no longer required, it can be removed with:

```bash
sudo apt remove package-name
```

For example:

```bash
sudo apt remove htop
```

This removes the package while generally leaving configuration files behind.

---

# 10. Removing Packages and Configuration Files

On Debian-based systems, `purge` can also remove package configuration files:

```bash
sudo apt purge package-name
```

For example:

```bash
sudo apt purge htop
```

Use this carefully and understand what is being removed before confirming the operation.

---

# 11. Cleaning Unnecessary Packages

The package manager can identify packages that were installed as dependencies but are no longer needed.

You can review and remove such packages with:

```bash
sudo apt autoremove
```

> Always review the packages that the system proposes to remove before confirming.

---

# 🧪 Practical Lab

Perform the following exercises on an Ubuntu or Debian-based Linux system.

---

## Task 1 — Identify Your Distribution

Run:

```bash
cat /etc/os-release
```

Look for information such as:

```text
NAME
VERSION
ID
```

Determine which Linux distribution you are using.

---

## Task 2 — Update Package Information

Run:

```bash
sudo apt update
```

Observe the output.

Look for:

- Repository information
- Package lists
- Available updates
- Any warnings or errors

---

## Task 3 — Search for a Package

Search for `htop`:

```bash
apt search htop
```

Determine whether the package is available.

---

## Task 4 — View Package Information

Run:

```bash
apt show htop
```

Identify:

- Package name
- Version
- Architecture
- Description
- Dependencies

---

## Task 5 — Install the Package

Install `htop`:

```bash
sudo apt install htop
```

Confirm the installation when prompted.

---

## Task 6 — Verify Installation

Run:

```bash
htop
```

Observe the process-monitoring interface.

Exit using:

```text
q
```

Then verify the package using:

```bash
apt list --installed | grep htop
```

---

## Task 7 — Check for Available Upgrades

Run:

```bash
sudo apt upgrade
```

Review the packages that are proposed for upgrade.

> If your system has no available upgrades, that is also a valid result.

---

## Task 8 — Remove the Practice Package

Remove `htop`:

```bash
sudo apt remove htop
```

Verify that it has been removed:

```bash
apt list --installed | grep htop
```

No matching installed package should normally be displayed.

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `cat /etc/os-release` | Display Linux distribution information |
| `sudo apt update` | Refresh package information |
| `apt search package` | Search for packages |
| `apt show package` | Display package information |
| `sudo apt install package` | Install a package |
| `apt list --installed` | List installed packages |
| `sudo apt upgrade` | Upgrade installed packages |
| `sudo apt remove package` | Remove a package |
| `sudo apt purge package` | Remove package and configuration files |
| `sudo apt autoremove` | Remove packages no longer required |

---

# 🧠 Key Concepts

## Package

A package is a software distribution unit containing the files and metadata needed to install software.

---

## Package Manager

A package manager automates software installation, removal, updates, and dependency handling.

---

## Repository

A repository is a software source containing packages that a package manager can retrieve.

---

## `apt update`

```bash
sudo apt update
```

Refreshes the local information about packages available from configured repositories.

---

## `apt install`

```bash
sudo apt install package-name
```

Installs a package and its required dependencies.

---

## `apt remove`

```bash
sudo apt remove package-name
```

Removes an installed package.

---

## `apt purge`

```bash
sudo apt purge package-name
```

Removes the package and associated package configuration files.

---

## `apt upgrade`

```bash
sudo apt upgrade
```

Installs available updates for installed packages.

---

# 🛡️ Security Perspective

Package management is an important part of Linux security.

Security updates frequently address:

- Software vulnerabilities
- Bugs
- Stability problems
- Security weaknesses
- Dependency issues

Keeping packages updated helps reduce exposure to known vulnerabilities.

Administrators should obtain software from trusted repositories and understand what packages are being installed.

Before installing a package, useful checks include:

```bash
apt search package-name
```

and:

```bash
apt show package-name
```

This helps you understand what you are installing.

---

# ⚠️ Best Practices

### 1. Keep package information current

Periodically refresh package information:

```bash
sudo apt update
```

### 2. Review upgrades before confirming

When running:

```bash
sudo apt upgrade
```

read the proposed changes before accepting them.

### 3. Use trusted repositories

Avoid installing unknown software packages without understanding their source.

### 4. Understand dependencies

Installing one package may also install additional packages required for it to function.

### 5. Be careful with removal commands

Before running:

```bash
sudo apt remove
```

or:

```bash
sudo apt autoremove
```

review what the package manager plans to remove.

### 6. Keep production systems controlled

On important systems, package changes should follow the organization's maintenance and change-management procedures.

---

# 📝 Questions

1. What is a Linux package?
2. What is the purpose of a package manager?
3. What does `apt update` do?
4. Does `apt update` upgrade installed software?
5. How do you search for a package?
6. How can you view information about a package?
7. How do you install a package using `apt`?
8. How do you remove a package?
9. What is the difference between `apt remove` and `apt purge`?
10. What does `apt upgrade` do?
11. What is a software repository?
12. Why is package management important for Linux security?
13. Why should you review packages before using `apt autoremove`?
14. Why should software normally be obtained from trusted repositories?

---

# 🧩 Challenge

Use the package manager to investigate another package available on your system.

Start by searching:

```bash
apt search curl
```

Then inspect the package:

```bash
apt show curl
```

Determine:

- What the package does
- Its installed/available version
- Its architecture
- Its dependencies
- Its description

Check whether it is already installed:

```bash
apt list --installed | grep curl
```

Do **not** install or remove the package unless you understand the change you are making.

---

# 🔐 Administration Scenario

Imagine you are administering an Ubuntu server.

A security team reports that an installed application may have a newer version available.

A responsible workflow would be:

```text
Identify the system
       ↓
Refresh package information
       ↓
Check the package
       ↓
Review available updates
       ↓
Apply approved updates
       ↓
Verify the result
```

Useful commands include:

```bash
cat /etc/os-release
```

```bash
sudo apt update
```

```bash
apt show package-name
```

```bash
sudo apt upgrade
```

This workflow demonstrates why package management is a core system-administration skill.

---

# 🧹 Cleanup

If you installed `htop` specifically for this lab and no longer need it:

```bash
sudo apt remove htop
```

Then verify:

```bash
apt list --installed | grep htop
```

If you intentionally want to remove unused dependencies, review the proposed changes before running:

```bash
sudo apt autoremove
```

---

# 📌 Summary

In this lab, you learned the fundamentals of Linux package management.

You practiced:

- Identifying your Linux distribution
- Updating package information
- Searching for packages
- Inspecting package information
- Installing software
- Verifying installed packages
- Upgrading installed software
- Removing software
- Understanding repositories and dependencies
- Applying package-management practices from a security perspective

The core Debian/Ubuntu commands are:

```bash
sudo apt update
```

```bash
apt search package-name
```

```bash
apt show package-name
```

```bash
sudo apt install package-name
```

```bash
sudo apt upgrade
```

```bash
sudo apt remove package-name
```

Understanding these commands provides a foundation for maintaining Linux systems and keeping installed software under administrative control.

---

# ✅ Lab Completion Checklist

- [ ] I understand what a Linux package is
- [ ] I understand what a package manager does
- [ ] I can identify my Linux distribution
- [ ] I can update package information
- [ ] I can search for packages
- [ ] I can inspect package information
- [ ] I can install a package
- [ ] I can verify an installed package
- [ ] I understand how package upgrades work
- [ ] I can remove a package
- [ ] I understand the difference between `remove` and `purge`
- [ ] I understand the purpose of repositories
- [ ] I understand why package management matters for security
- [ ] I completed the practical lab
- [ ] I completed the challenge
- [ ] I cleaned up the practice package

---

## 🚀 Next Lab

**Lab 22 — Package Management**
