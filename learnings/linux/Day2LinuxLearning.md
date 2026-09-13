# Day 2 — Linux File Permissions, Users & Ownership

## What I Learned

Today I learned:

* Linux file permissions
* `chmod`
* File ownership with `chown`
* Group ownership with `chgrp`
* Checking the current user with `whoami`
* Running commands with administrator privileges using `sudo`

---

## 1. Understanding `ls -l`

Command:

```bash
ls -l
```

Example:

```text
-rwxrwxrwx 1 amrit amrit 0 Sep 12 18:23 index.js
```

The permission section is:

```text
-rwxrwxrwx
```

It is divided into:

```text
- rwx rwx rwx
  │   │   │
  │   │   └── Others
  │   └────── Group
  └────────── Owner
```

### Permission meanings

| Permission | Meaning                  |
| ---------- | ------------------------ |
| `r`        | Read                     |
| `w`        | Write                    |
| `x`        | Execute                  |
| `-`        | Permission not available |

---

## 2. Owner, Group and Others

Example:

```text
-rwxrwxrwx
```

Means:

```text
Owner  → rwx
Group  → rwx
Others → rwx
```

---

## 3. Removing Group Write Permission

Command:

```bash
chmod g-w index.js
```

Before:

```text
-rwxrwxrwx
```

After:

```text
-rwxr-xrwx
```

`g-w` means:

```text
g = group
- = remove
w = write
```

So:

> Remove write permission from the group.

---

## 4. Adding Group Write Permission

Command:

```bash
chmod g+w index.js
```

Before:

```text
-rwxr-xrwx
```

After:

```text
-rwxrwxrwx
```

`g+w` means:

> Add write permission for the group.

---

## 5. Numeric Permissions

Linux permissions can also be represented using numbers.

```text
r = 4
w = 2
x = 1
```

Therefore:

```text
rwx = 4 + 2 + 1 = 7
rw- = 4 + 2 = 6
r-x = 4 + 1 = 5
r-- = 4
--- = 0
```

---

## 6. `chmod 766`

Command:

```bash
chmod 766 index.js
```

Result:

```text
-rwxrw-rw-
```

Breakdown:

```text
7 → rwx → Owner
6 → rw- → Group
6 → rw- → Others
```

---

## 7. `chmod 777`

Command:

```bash
chmod 777 index.js
```

Result:

```text
-rwxrwxrwx
```

Everyone has:

```text
read + write + execute
```

### Important

`777` gives maximum permissions to everyone and should generally be avoided unless there is a specific reason to use it.

---

# 8. Checking the Current User with `whoami`

The `whoami` command tells me **which user I am currently logged in as**.

Command:

```bash
whoami
```

Example output:

```text
amrit
```

This means the current Linux user is:

```text
amrit
```

### Why is `whoami` useful?

Before running commands involving permissions or ownership, I can check:

```bash
whoami
```

It is especially useful when working with:

* `sudo`
* `chown`
* File permissions
* Multiple Linux users
* SSH sessions

---

# 9. Running Commands as Administrator with `sudo`

`sudo` means:

> Run a command with elevated privileges.

For example:

```bash
sudo chown root index.js
```

Without `sudo`, a normal user may not have permission to change a file's owner.

When using `sudo`, Ubuntu may ask for my password:

```text
[sudo] password for amrit:
```

While typing the password, **nothing appears on the screen**. This is normal Linux behavior.

### Check sudo access

I can run:

```bash
sudo -v
```

If the password is correct, sudo authentication is successful.

---

# 10. `whoami` + `sudo` Practice

First check the current user:

```bash
whoami
```

Output:

```text
amrit
```

Then run:

```bash
sudo whoami
```

Output:

```text
root
```

This demonstrates an important concept:

```text
whoami
↓
amrit
```

But:

```text
sudo whoami
↓
root
```

The first command runs as my normal user.

The second command runs with elevated privileges as `root`.

---

# 11. Changing File Ownership with `chown`

The `chown` command is used to change the **owner** of a file.

First, I checked the current ownership:

```bash
ls -l index.js
```

Output:

```text
-rwxr--r-- 1 amrit amrit 0 Sep 12 18:23 index.js
```

This means:

```text
Owner → amrit
Group → amrit
```

### Change owner to root

Command:

```bash
sudo chown root index.js
```

Result:

```text
-rwxr--r-- 1 root amrit 0 Sep 12 18:23 index.js
```

The owner changed:

```text
amrit → root
```

The group remained:

```text
amrit
```

---

# 12. Changing Group Ownership with `chgrp`

The `chgrp` command is used to change the **group** of a file.

Command:

```bash
sudo chgrp root index.js
```

Result:

```text
-rwxr--r-- 1 root root 0 Sep 12 18:23 index.js
```

Now:

```text
Owner → root
Group → root
```

---

# 13. Changing Owner and Group Together

`chown` can change both owner and group at the same time.

Command:

```bash
sudo chown amrit:amrit index.js
```

Result:

```text
-rwxr--r-- 1 amrit amrit 0 Sep 12 18:23 index.js
```

Syntax:

```bash
sudo chown owner:group file
```

Example:

```bash
sudo chown amrit:amrit index.js
```

---

# 14. `chown` vs `chgrp`

| Command            | Purpose                |
| ------------------ | ---------------------- |
| `chown`            | Change owner           |
| `chgrp`            | Change group           |
| `chown user:group` | Change owner and group |

Examples:

```bash
sudo chown root index.js
```

Changes owner.

```bash
sudo chgrp root index.js
```

Changes group.

```bash
sudo chown amrit:amrit index.js
```

Changes both owner and group.

---

# 15. My Ownership Practice

I practiced ownership changes on:

```text
/mnt/d/developer-workspace/projects/backend/index.js
```

### Step 1 — Check current owner

```bash
ls -l index.js
```

Initial:

```text
-rwxr--r-- 1 amrit amrit 0 Sep 12 18:23 index.js
```

Current owner:

```text
amrit
```

Current group:

```text
amrit
```

### Step 2 — Change owner to root

```bash
sudo chown root index.js
```

Result:

```text
-rwxr--r-- 1 root amrit 0 Sep 12 18:23 index.js
```

### Step 3 — Change group to root

```bash
sudo chgrp root index.js
```

Result:

```text
-rwxr--r-- 1 root root 0 Sep 12 18:23 index.js
```

### Step 4 — Change owner and group back to amrit

```bash
sudo chown amrit:amrit index.js
```

Final result:

```text
-rwxr--r-- 1 amrit amrit 0 Sep 12 18:23 index.js
```

---

# 16. Common `chmod` Commands

### Add execute permission to owner

```bash
chmod u+x file
```

### Remove execute permission from owner

```bash
chmod u-x file
```

### Add write permission to group

```bash
chmod g+w file
```

### Remove write permission from group

```bash
chmod g-w file
```

### Add read permission to others

```bash
chmod o+r file
```

### Remove read permission from others

```bash
chmod o-r file
```

### Common numeric permissions

```bash
chmod 644 file
chmod 755 file
chmod 766 file
chmod 777 file
```

---

# 17. Common Permission Numbers

## 644

```bash
chmod 644 file
```

Result:

```text
-rw-r--r--
```

Commonly used for normal files.

## 755

```bash
chmod 755 file
```

Result:

```text
-rwxr-xr-x
```

Commonly used for executable files and scripts.

## 777

```bash
chmod 777 file
```

Result:

```text
-rwxrwxrwx
```

Everyone has full permissions.

Avoid using it unnecessarily.

---

# 18. Important Commands Learned

```bash
ls -l

whoami

sudo command

sudo -v

chmod g-w file
chmod g+w file
chmod u+x file
chmod u-x file
chmod o+r file
chmod o-r file

chmod 644 file
chmod 755 file
chmod 766 file
chmod 777 file

chown
chgrp
```

---

# Day 2 Checklist

* [x] Understand `ls -l`
* [x] Understand `r`, `w`, `x`
* [x] Understand owner, group and others
* [x] Learn `chmod`
* [x] Use symbolic permissions
* [x] Use numeric permissions
* [x] Practice `chmod 766`
* [x] Practice `chmod 777`
* [x] Enable WSL permission metadata
* [x] Verify permissions on D: drive
* [x] Learn how to check file ownership
* [x] Learn `chown`
* [x] Learn `chgrp`
* [x] Change owner to `root`
* [x] Change group to `root`
* [x] Change owner and group back to `amrit`
* [x] Learn `whoami`
* [x] Learn `sudo`
* [x] Practice `sudo whoami`

## Next

Next I will learn:

* Linux users
* Linux groups
* `id`
* `groups`
* `adduser`
* `usermod`
* More `chown` practice
* Why Linux permissions matter for security
* Executable shell scripts
