# Lab 25 — Creating and Managing Users

Learn how to create, manage, and remove user accounts in a Linux environment using essential user-management commands such as `useradd`, `passwd`, and `userdel`.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Create a new Linux user.
- Understand the purpose of the `useradd` command.
- Set a password for a user using `passwd`.
- Remove a user account using `userdel`.
- Understand the difference between removing a user and removing a user's home directory.
- Understand the importance of proper user account management.

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Basic knowledge of Linux terminal commands.
- Access to a Linux system.
- Administrator or `sudo` privileges.

---

# 1. Understanding Linux Users

Linux is a multi-user operating system.

A user account provides an identity that can be used to:

- Log in to the system.
- Own files and directories.
- Run processes.
- Access permitted resources.
- Receive permissions based on ownership and group membership.

User account information is maintained by Linux through system account databases, including `/etc/passwd`.

---

# 2. Creating a New User

The `useradd` command is used to create a new user account.

### Basic syntax

```bash
sudo useradd newuser
```

This creates a user named:

```text
newuser
```

### Command breakdown

```text
sudo
```

Runs the command with administrative privileges.

```text
useradd
```

Creates a new user account.

```text
newuser
```

Specifies the username.

---

## Verify the User

After creating the account, check whether the user exists:

```bash
grep '^newuser:' /etc/passwd
```

You can also use:

```bash
id newuser
```

The `id` command displays information such as the user's UID and group information.

---

# 3. Setting a User Password

A newly created account should have appropriate authentication configured.

Use:

```bash
sudo passwd newuser
```

Linux will prompt you to enter and confirm a password.

### Important

When entering a password in the terminal, the characters normally will not be displayed. This is expected behavior.

Use a strong password appropriate for the environment.

---

# 4. Understanding `passwd`

The `passwd` command is used to change or manage user authentication passwords.

For example:

```bash
sudo passwd newuser
```

changes the password for `newuser`.

Administrators commonly use this command when:

- Creating accounts.
- Resetting forgotten passwords.
- Rotating credentials.
- Managing account authentication.

---

# 5. Deleting a User

The `userdel` command removes a user account.

Use:

```bash
sudo userdel newuser
```

This removes the user account.

However, the user's home directory and other associated files may remain.

---

# 6. Removing a User and Home Directory

To remove the user account together with its home directory, use:

```bash
sudo userdel -r newuser
```

The `-r` option requests removal of the user's home directory and related user-owned files associated with the account.

### Important

Be careful with:

```bash
sudo userdel -r username
```

because removing a user's home directory can permanently remove data stored there.

Always verify the username before executing the command.

---

# 🧪 Practical Lab

## Task 1 — Create a Test User

Create a temporary user called `labuser`:

```bash
sudo useradd labuser
```

---

## Task 2 — Verify the Account

Check the account:

```bash
id labuser
```

Then inspect the corresponding entry:

```bash
grep '^labuser:' /etc/passwd
```

Observe the information returned by both commands.

---

## Task 3 — Set a Password

Set a password for the test account:

```bash
sudo passwd labuser
```

Follow the prompts.

---

## Task 4 — Check the User's Account Information

Run:

```bash
id labuser
```

Also check:

```bash
getent passwd labuser
```

Observe the account information returned by the system.

---

## Task 5 — Remove the Test User

When you have finished experimenting, remove the test account:

```bash
sudo userdel labuser
```

---

## Task 6 — Verify Removal

Run:

```bash
id labuser
```

The command should indicate that the user no longer exists.

You can also check:

```bash
getent passwd labuser
```

No account entry should be returned.

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `sudo useradd username` | Create a user |
| `sudo passwd username` | Set or change a user's password |
| `id username` | Display user and group identity information |
| `getent passwd username` | Query the system user database |
| `grep '^username:' /etc/passwd` | Check the user's `/etc/passwd` entry |
| `sudo userdel username` | Delete a user account |
| `sudo userdel -r username` | Delete a user and associated home directory |

---

# 🧠 Key Concepts

## User Account

A Linux user account provides an identity through which a person or service can interact with the operating system.

---

## UID

Every Linux user is associated with a **User ID (UID)**.

You can view a user's UID with:

```bash
id username
```

---

## `/etc/passwd`

The `/etc/passwd` file contains account information used by Linux.

You can inspect a particular account with:

```bash
grep '^username:' /etc/passwd
```

Do not modify system account files manually unless you understand the consequences.

---

## `useradd`

Creates a new user account.

Example:

```bash
sudo useradd labuser
```

---

## `passwd`

Manages a user's password.

Example:

```bash
sudo passwd labuser
```

---

## `userdel`

Removes a user account.

Example:

```bash
sudo userdel labuser
```

The `-r` option can additionally remove the user's home directory and associated user-owned data.

---

# 🛡️ Security Perspective

User management is a fundamental part of Linux security.

Proper account management helps administrators:

- Control access to systems.
- Give users separate identities.
- Track ownership of files.
- Apply appropriate permissions.
- Remove accounts that are no longer required.
- Reduce unnecessary access to system resources.

A good security practice is to avoid sharing user accounts between multiple people. Individual accounts provide better accountability and access control.

---

# ⚠️ Best Practices

- Use unique accounts for individual users.
- Give users only the access they need.
- Use strong passwords where password authentication is required.
- Avoid sharing administrator credentials.
- Verify usernames before deleting accounts.
- Be especially careful with `userdel -r`.
- Remove unused accounts when they are no longer required.
- Avoid directly editing `/etc/passwd` unless you know exactly what you are doing.

---

# 📝 Questions

1. What is the purpose of the `useradd` command?
2. Why is `sudo` commonly required when creating users?
3. What command is used to set a user's password?
4. What information can the `id` command display?
5. What is `/etc/passwd` used for?
6. What is the difference between `userdel username` and `userdel -r username`?
7. Why should administrators be careful when using `userdel -r`?
8. Why is individual user-account management important for security?

---

# 🚀 Challenge

Create a temporary user named:

```text
securitylab
```

Then:

1. Create the user.
2. Verify the account using `id`.
3. Check the account using `getent`.
4. Assign a password.
5. Verify the account information again.
6. Remove the test account.
7. Confirm that the account has been removed.

Useful commands:

```bash
sudo useradd securitylab
id securitylab
getent passwd securitylab
sudo passwd securitylab
sudo userdel securitylab
id securitylab
```

Do not use an existing system username for this challenge.

---

# 📋 Summary

In this lab, you learned the fundamentals of Linux user management.

You practiced:

- Creating users with `useradd`.
- Setting passwords with `passwd`.
- Inspecting user information with `id` and `getent`.
- Understanding `/etc/passwd`.
- Removing users with `userdel`.
- Understanding the additional effect of `userdel -r`.

The core commands from this lab are:

```bash
sudo useradd username
sudo passwd username
id username
getent passwd username
sudo userdel username
sudo userdel -r username
```

These commands provide the foundation for more advanced Linux account and access management.

---

# ✅ Lab Completion Checklist

- [ ] Created a Linux test user
- [ ] Verified the user with `id`
- [ ] Checked the account with `getent`
- [ ] Set a password using `passwd`
- [ ] Inspected the user's account information
- [ ] Removed the test user
- [ ] Verified that the user was removed
- [ ] Completed the challenge
- [ ] Answered the review questions

---

# 🚀 Next Lab

**Lab 26 — Group Management**

In the next lab, you will learn how Linux groups are used to organize users and manage access to shared resources.
