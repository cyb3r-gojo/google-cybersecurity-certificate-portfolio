# 04 – Linux File Permissions and Authorization
## Overview

This activity demonstrates how Linux file permissions are analyzed and modified to ensure that only authorized users can access sensitive research files. As a security professional, I inspected directory contents, interpreted permission strings, and updated file and directory permissions to align with organizational security requirements.

This task highlights my ability to use Linux commands (ls, chmod) to enforce proper authorization and protect sensitive data.

## Scenario Summary

A research team stores files inside a projects directory. My responsibility is to:

- Check current file and directory permissions

- Interpret Linux permission strings

- Identify unauthorized write permissions

- Remove insecure access using chmod

- Secure hidden files

- Restrict directory access to the correct user

All actions follow Linux authorization best practices.

## 1. Check File and Directory Details
Command used

```
ls -la
```
This command lists file details, including type, owner, group, and the 10-character permission string. It also displays hidden files (those beginning with a dot).

Current permissions (interpreted from provided document)

```
project_k.txt      -rw-rw-rw-
project_m.txt      -rw-r-----
project_r.txt      -rw-rw-r--
project_t.txt      -rw-rw-r--
.project_x.txt     -rw-w----
drafts/            drwx--x---
```
These permissions were used for analysis in the following steps.

## 2. Describe the Permission String
Example string:

```
-rw-rw-r--
```

Interpretation:

- -→ regular file

- rw- (user) → owner can read & write

- rw- (group) → group can read & write

- r-- (others) → others can only read

This 10-character permission structure helps determine who can view or modify a file.

## 3. Modify File Permissions (Remove Unauthorized Write Access)

Problem identified

The organization does NOT allow “others” to have write permissions.

project_k.txt currently has:

```
-rw-rw-rw-
```

This means everyone can write to the file — a major security risk.

Fix command

```
chmod o-w project_k.txt
```

Updated permissions

```
-rw-rw-r--
```
Now only authorized users can modify the file.

## 4. Secure a Hidden File (.project_x.txt)

Hidden file:

```
.project_x.txt
```

Current permissions:

```
-rw-w----
```

Security policy

- User → read

- Group → read

- No write permission for anyone

- Others → no access

Correct permissions

```
-r--r-----
```

Command used

```
chmod 440 .project_x.txt
```

File is now read-only for user and group.

## 5. Restrict Access to a Directory (drafts/)

Directory:

```
drafts/
```

Current permissions:
```
drwx--x---
```

Requirement

Only researcher2 (owner) should have full access.
```
drwx------
```

Command used
```
chmod 700 drafts
```
This removes group and other access entirely, securing the directory contents.

## 📌 Summary

In this task, I:

- Inspected Linux file permissions using ls -la

- Interpreted 10-character permission strings

- Identified insecure write permissions

- Removed unauthorized access using chmod

- Secured a hidden file by restricting write access

- Restricted directory access to the correct user

This demonstrates my ability to enforce authorization policies, work with hidden files, and secure Linux file systems effectively.
