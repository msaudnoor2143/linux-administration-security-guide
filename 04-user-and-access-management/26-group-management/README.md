# Lab 26 — Group Management Basics

Linux groups provide a way to organize users and manage access to files, directories, and system resources.

In this lab, you will learn the fundamentals of Linux group management and how groups can be used to organize user access.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand Linux groups.
- Create groups with `groupadd`.
- View existing groups.
- Add users to groups.
- Remove users from groups.
- Delete groups.
- Check group membership.
- Understand the relationship between users, groups, and permissions.
- Apply basic group-management practices.

---

## 📚 Prerequisites

Before starting this lab, you should have:

- Access to a Linux system.
- A terminal.
- Basic knowledge of Linux users.
- Basic knowledge of Linux permissions.
- Administrative privileges using `sudo`.
- Completion of **Lab 25 — Creating and Managing Users**.

> **Note:** The exercises in this lab modify user and group information. Use a test Linux system or virtual machine whenever possible.

---

# 1. Understanding Linux Groups

A Linux group is a collection of users that can be managed together.

Groups are particularly useful when multiple users need access to the same files, directories, or resources.

For example, an organization could have a group named:

```text
developers
```

Several users could belong to that group.

Instead of managing access for every user individually, permissions can be assigned to the group.

---

# 2. Viewing Group Information

Linux stores group information in:

```text
/etc/group
```

You can view the file with:

```bash
cat /etc/group
```

For easier reading:

```bash
less /etc/group
```

A typical entry contains information similar to:

```text
developers:x:1001:user1,user2
```

The fields represent:

```text
group_name:password:GID:members
```

---

# 3. Checking Your Groups

The `groups` command displays the groups associated with a user.

Run:

```bash
groups
```

To check the groups of a specific user:

```bash
groups username
```

For example:

```bash
groups user1
```

---

# 4. Using `id` to View Group Information

The `id` command displays user and group information.

Run:

```bash
id
```

For a specific user:

```bash
id username
```

Example:

```bash
id user1
```

The output can include:

- User ID (UID)
- Primary group ID (GID)
- Supplementary groups

---

# 5. Creating a Group with `groupadd`

The `groupadd` command creates a new group.

### Syntax

```bash
sudo groupadd group_name
```

For example:

```bash
sudo groupadd developers
```

You can verify that the group exists with:

```bash
getent group developers
```

You can also search `/etc/group`:

```bash
grep '^developers:' /etc/group
```

---

# 6. Understanding Group IDs

Every Linux group has a numeric Group ID, known as a **GID**.

You can inspect the GID of a group using:

```bash
getent group developers
```

Example output:

```text
developers:x:1001:
```

Here:

```text
1001
```

is the GID.

The GID allows Linux to internally identify the group.

---

# 7. Adding a User to a Group

The `usermod` command can be used to modify user account information.

To add an existing user to a supplementary group:

```bash
sudo usermod -aG group_name username
```

For example:

```bash
sudo usermod -aG developers user1
```

### Understanding the options

```text
-a
```

means **append**.

```text
-G
```

specifies supplementary groups.

Together:

```bash
-aG
```

adds the user to the specified supplementary group without replacing their existing supplementary group memberships.

---

## ⚠️ Important

Be careful when using `usermod -G`.

For example:

```bash
sudo usermod -G developers user1
```

can replace the user's existing supplementary group memberships.

When adding a user to an additional group, use:

```bash
sudo usermod -aG developers user1
```

---

# 8. Verifying Group Membership

After adding a user to a group, check the membership with:

```bash
groups user1
```

You can also use:

```bash
id user1
```

And:

```bash
getent group developers
```

These commands provide different views of the same account and group relationships.

---

# 9. Removing a User from a Group

On systems using GNU/Linux tools, `gpasswd` can be used to remove a user from a supplementary group.

### Syntax

```bash
sudo gpasswd -d username group_name
```

Example:

```bash
sudo gpasswd -d user1 developers
```

Verify:

```bash
groups user1
```

---

# 10. Deleting a Group

The `groupdel` command removes a group.

### Syntax

```bash
sudo groupdel group_name
```

For example:

```bash
sudo groupdel developers
```

Verify:

```bash
getent group developers
```

If the group has been removed, the command should no longer return its group entry.

> **Note:** Deleting a group does not delete the users who belonged to that group.

---

# 🧪 Practical Lab

Perform the following exercise using a **test user and test group**.

Avoid using important system accounts or groups.

---

## Task 1 — Create a Test Group

Create a group called:

```text
linuxlab
```

Run:

```bash
sudo groupadd linuxlab
```

Verify:

```bash
getent group linuxlab
```

---

## Task 2 — Create a Test User

Create a temporary user:

```bash
sudo useradd labuser
```

Verify the account:

```bash
id labuser
```

---

## Task 3 — Add the User to the Group

Add `labuser` to `linuxlab`:

```bash
sudo usermod -aG linuxlab labuser
```

Verify:

```bash
groups labuser
```

You can also check:

```bash
id labuser
```

---

## Task 4 — Inspect the Group

Run:

```bash
getent group linuxlab
```

You should see `labuser` listed as a member of the group.

---

## Task 5 — Remove the User from the Group

Run:

```bash
sudo gpasswd -d labuser linuxlab
```

Verify:

```bash
groups labuser
```

And:

```bash
getent group linuxlab
```

---

## Task 6 — Clean Up the Test Environment

After completing the exercise, remove the test user:

```bash
sudo userdel labuser
```

Then remove the test group:

```bash
sudo groupdel linuxlab
```

Verify that the group no longer exists:

```bash
getent group linuxlab
```

---

# 🔎 Command Reference

| Command | Purpose |
|---|---|
| `groups` | Displays group membership |
| `id` | Displays UID, GID, and group information |
| `cat /etc/group` | Displays group database contents |
| `getent group` | Queries group information |
| `groupadd` | Creates a group |
| `usermod -aG` | Adds a user to a supplementary group |
| `gpasswd -d` | Removes a user from a group |
| `groupdel` | Deletes a group |

---

# 🧠 Key Concepts

### Group

A collection of users that can share access permissions.

---

### GID

The numeric identifier assigned to a Linux group.

---

### Primary Group

Each Linux user has a primary group associated with their account.

---

### Supplementary Groups

Additional groups that a user can belong to.

Supplementary groups are commonly used to provide additional access to resources.

---

### `/etc/group`

A local Linux database containing group information.

---

### `usermod -aG`

Used to add a user to an additional supplementary group.

Example:

```bash
sudo usermod -aG developers user1
```

The `-a` option is important because it appends the new group instead of replacing existing supplementary memberships.

---

# 🛡️ Security Perspective

Groups are an important part of Linux access control.

Instead of assigning permissions separately to every user, administrators can assign permissions to groups.

For example:

```text
developers
    ├── alice
    ├── bob
    └── charlie
```

A directory could then be assigned to the `developers` group.

This allows administrators to manage access more efficiently.

However, excessive group membership can also provide users with more access than they require.

This is why group membership should be reviewed regularly.

---

# ⚠️ Best Practices

### 1. Use descriptive group names

Choose names that clearly describe the group's purpose.

For example:

```text
developers
```

is clearer than:

```text
group1
```

---

### 2. Follow least privilege

Users should only belong to groups that they actually need.

---

### 3. Be careful with privileged groups

Some groups can provide access to sensitive system resources.

Review membership carefully before adding users.

---

### 4. Use `-aG` when adding supplementary groups

Prefer:

```bash
sudo usermod -aG group_name username
```

when adding an additional group.

---

### 5. Review group membership

Useful commands include:

```bash
groups username
```

and:

```bash
id username
```

---

### 6. Use test accounts during practice

When learning group management, avoid modifying important production accounts.

Use temporary users and groups instead.

---

# 📝 Questions

1. What is a Linux group?
2. What is the purpose of `/etc/group`?
3. What is a GID?
4. What command creates a new group?
5. How can you check a user's group membership?
6. What does `usermod -aG` do?
7. Why is the `-a` option important when adding supplementary groups?
8. How can a user be removed from a group?
9. What command deletes a group?
10. Does deleting a group delete the users who belonged to it?
11. Why are groups useful for access control?
12. Why should group membership be reviewed from a security perspective?

---

# 🧩 Challenge

Create a test group named:

```text
security-team
```

Create two test users:

```text
analyst1
analyst2
```

Add both users to the `security-team` group.

Verify their membership using:

```bash
groups analyst1
```

and:

```bash
groups analyst2
```

Then inspect the group directly:

```bash
getent group security-team
```

Finally, remove the test users and group after completing the challenge.

---

# 🧹 Cleanup

If you completed the challenge, remove the temporary accounts and group:

```bash
sudo userdel analyst1
sudo userdel analyst2
sudo groupdel security-team
```

Verify:

```bash
getent group security-team
```

---

# 📌 Summary

In this lab, you learned the fundamentals of Linux group management.

You learned how to:

- Understand Linux groups.
- Inspect group information.
- Create groups.
- Check group membership.
- Add users to groups.
- Remove users from groups.
- Delete groups.
- Understand GIDs.
- Use groups as part of Linux access control.
- Apply least-privilege principles to group membership.

Group management is an essential Linux administration skill and provides an important foundation for understanding access control and system security.

---

# ✅ Lab Completion Checklist

- [ ] I understand what Linux groups are.
- [ ] I understand the purpose of `/etc/group`.
- [ ] I can create a group with `groupadd`.
- [ ] I can identify a group's GID.
- [ ] I can check user group membership.
- [ ] I can add a user to a supplementary group.
- [ ] I understand the purpose of `usermod -aG`.
- [ ] I can remove a user from a group.
- [ ] I can delete a group.
- [ ] I understand how groups support access control.
- [ ] I understand the security importance of group membership.
- [ ] I completed the practical exercise.

---

## 🚀 Next Lab

**Lab 27 — Password Policies**
