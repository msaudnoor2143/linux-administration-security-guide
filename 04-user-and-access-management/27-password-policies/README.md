# Lab 27: Password Policies

This lab introduces Linux password policies and the basic controls used to improve the security of user accounts. You will learn how to inspect password-related account information and apply password-management practices using standard Linux tools.

---

## 🎯 Objective

By completing this lab, you will:

- Understand the purpose of password policies in Linux.
- Learn how Linux stores password-related account information.
- Inspect password aging information.
- Configure password expiration settings.
- Understand minimum and maximum password-age controls.
- Apply basic password-security practices.
- Verify password-policy settings for a user account.

---

## 📚 Prerequisites

Before starting this lab, you should have:

- A Linux system or virtual machine.
- Basic Linux command-line knowledge.
- A user account with `sudo` privileges.
- Familiarity with the `passwd` command.
- Basic understanding of Linux users and permissions.

---

# 1. Understanding Password Policies

A password policy defines rules that help control how user passwords are managed.

Common password-policy controls include:

- Password expiration
- Minimum password lifetime
- Maximum password lifetime
- Warning period before expiration
- Account information associated with password aging

Password policies are particularly important on systems with multiple users because they help administrators maintain consistent account-security practices.

---

# 2. Understanding `/etc/passwd` and `/etc/shadow`

Linux stores basic user-account information in:

```bash
/etc/passwd
```

Password hashes and password-aging information are stored separately in:

```bash
/etc/shadow
```

The shadow file contains sensitive authentication information and should only be accessible to privileged users.

You can inspect the user database with:

```bash
cat /etc/passwd
```

To inspect the shadow database:

```bash
sudo cat /etc/shadow
```

> ⚠️ Do not modify `/etc/shadow` manually. Use the appropriate Linux account-management commands instead.

---

# 3. Checking Password Information

The `passwd` command can be used to manage passwords and inspect account-related password information.

For example:

```bash
sudo passwd -S username
```

Replace `username` with the account you want to inspect.

The command provides information about the account's password status.

You can also display password-aging information using:

```bash
sudo chage -l username
```

For example:

```bash
sudo chage -l student
```

This displays information such as:

- Last password change
- Password expiration
- Password inactivity period
- Account expiration
- Minimum password age
- Maximum password age
- Warning period

---

# 4. Understanding `chage`

The `chage` command is used to modify password-aging information for Linux users.

General syntax:

```bash
sudo chage [options] username
```

For example:

```bash
sudo chage -l student
```

The `-l` option displays the current password-aging information.

---

# 5. Setting the Minimum Password Age

The minimum password age determines how long a user must wait before changing their password again.

For example:

```bash
sudo chage -m 1 student
```

This sets the minimum password age to one day.

Check the result:

```bash
sudo chage -l student
```

---

# 6. Setting the Maximum Password Age

The maximum password age determines how long a password can remain valid before the user is required to change it.

For example:

```bash
sudo chage -M 90 student
```

This sets the maximum password age to 90 days.

Verify the configuration:

```bash
sudo chage -l student
```

---

# 7. Setting the Password Expiration Warning

Linux can warn a user a certain number of days before their password expires.

For example:

```bash
sudo chage -W 7 student
```

This configures a seven-day warning period.

Verify:

```bash
sudo chage -l student
```

---

# 8. Forcing a Password Change

An administrator can force a user to change their password during their next login.

Use:

```bash
sudo chage -d 0 student
```

After this setting is applied, the user's password is considered expired and they will be required to change it.

> ⚠️ Only apply this to test accounts in a lab environment unless you intentionally want to change a real account's login behavior.

---

# 🧪 Practical Lab

## Task 1 — Create a Test User

Create a temporary user for this exercise:

```bash
sudo useradd passwordlab
```

Set a password:

```bash
sudo passwd passwordlab
```

Use a password appropriate for a controlled lab environment.

---

## Task 2 — Inspect Password Aging

Display the password-aging information:

```bash
sudo chage -l passwordlab
```

Record the following:

- Last password change
- Password expires
- Minimum password age
- Maximum password age
- Warning period

---

## Task 3 — Configure Password Aging

Set the minimum password age to one day:

```bash
sudo chage -m 1 passwordlab
```

Set the maximum password age to 90 days:

```bash
sudo chage -M 90 passwordlab
```

Set the expiration warning period to seven days:

```bash
sudo chage -W 7 passwordlab
```

---

## Task 4 — Verify the Policy

Run:

```bash
sudo chage -l passwordlab
```

Confirm that the new password-aging values have been applied.

---

## Task 5 — Inspect Password Status

Run:

```bash
sudo passwd -S passwordlab
```

Observe the account's password status.

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `passwd` | Manage user passwords |
| `passwd -S username` | Display password status |
| `chage -l username` | Display password-aging information |
| `chage -m DAYS username` | Set minimum password age |
| `chage -M DAYS username` | Set maximum password age |
| `chage -W DAYS username` | Set password-expiration warning period |
| `chage -d 0 username` | Force password change at next login |
| `cat /etc/passwd` | View basic user-account information |
| `sudo cat /etc/shadow` | View protected password/account-aging information |

---

# 🧠 Key Concepts

### Password Aging

Password aging controls how long passwords remain valid and how frequently users may change them.

### Minimum Password Age

Controls the minimum number of days between password changes.

### Maximum Password Age

Controls how long a password remains valid.

### Warning Period

Determines how many days before expiration a user receives a warning.

### `/etc/shadow`

Contains protected password hashes and account-aging information.

### `chage`

Provides administrators with controls for configuring password-aging settings.

---

# 🛡️ Security Perspective

Password policies are one layer of Linux account security.

A properly configured system should combine password policies with:

- Appropriate user permissions
- Group-based access control
- Least-privilege administration
- Secure authentication practices
- Account monitoring
- Regular system updates
- SSH security controls

Password expiration alone does not make an account secure. It should be part of a broader authentication and access-control strategy.

---

# ⚠️ Best Practices

- Do not manually edit `/etc/shadow`.
- Do not share user passwords.
- Use separate accounts instead of sharing administrator accounts.
- Avoid unnecessarily long or aggressive password-expiration settings that can encourage poor password practices.
- Apply password policies consistently.
- Test policy changes on dedicated lab accounts first.
- Protect systems with multiple layers of security rather than relying only on password expiration.

---

# 🧪 Challenge

Create another test account:

```bash
sudo useradd securitytest
```

Set its password:

```bash
sudo passwd securitytest
```

Configure:

- Minimum password age: 2 days
- Maximum password age: 60 days
- Warning period: 10 days

Use `chage` to configure the settings:

```bash
sudo chage -m 2 securitytest
sudo chage -M 60 securitytest
sudo chage -W 10 securitytest
```

Verify everything:

```bash
sudo chage -l securitytest
```

### Challenge Questions

1. What is the purpose of `/etc/shadow`?
2. What does `chage -l` display?
3. What is the difference between minimum and maximum password age?
4. Why should `/etc/shadow` not be manually edited?
5. What does the `-W` option of `chage` control?
6. Why is password policy only one part of Linux security?

---

# 🧹 Cleanup

After completing the lab, remove the temporary accounts:

```bash
sudo userdel passwordlab
sudo userdel securitytest
```

If you also want to remove their home directories:

```bash
sudo userdel -r passwordlab
sudo userdel -r securitytest
```

Verify that the accounts no longer exist:

```bash
getent passwd passwordlab
getent passwd securitytest
```

No output indicates that the accounts are no longer present.

---

# 📝 Summary

In this lab, you learned how Linux manages password-related account information and how administrators can configure password-aging policies.

You practiced using:

- `passwd`
- `passwd -S`
- `chage`
- `/etc/passwd`
- `/etc/shadow`

You also configured minimum password age, maximum password age, and password-expiration warnings.

These concepts provide an important foundation for Linux account security and access management.

---

# ✅ Lab Completion Checklist

- [ ] Created a test Linux user.
- [ ] Set a password for the test account.
- [ ] Inspected password-aging information.
- [ ] Used `chage -l`.
- [ ] Configured minimum password age.
- [ ] Configured maximum password age.
- [ ] Configured an expiration warning period.
- [ ] Checked password status with `passwd -S`.
- [ ] Completed the challenge.
- [ ] Removed temporary accounts.

---

# 🚀 Next Lab

**Lab 28: Scheduling Tasks with Crontab**

In the next lab, you will learn how Linux schedules recurring tasks using `cron` and `crontab`.
