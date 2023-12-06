---
title: File Permissions
description: 
published: true
tags: curriculum, basic, linux
editor: markdown
---
# Introduction 

File permissions in Linux are crucial for security and proper system management. Here's a guide on how to view and modify these permissions.

## Viewing File Permissions

1. **Open a Terminal Window**
   - Preferably as root. You can switch to root with `sudo -i`.

2. **List Files and Their Permissions**
   - Run `ls -ahl` to view the files and their permissions.

3. **Understanding the Output**
   - The first character indicates the type (`d` for directory, `-` for file).
   - The next 9 characters represent the permissions in three sets of three:
     - The first set for the user.
     - The second set for the group.
     - The third set for everyone else.
   - Permissions are indicated as `r` (read), `w` (write), and `x` (execute).

## Changing File Permissions with chmod

- **Basic Command**: `chmod [permissions] [file/directory]`
- **Example**: `chmod 777 CyberPatriot.txt`

### Understanding the Permission Numbers

- The numbers for permissions range from 0 to 7, derived from binary.
- Each digit represents a set of permissions (user, group, everyone).
- Binary to Permission Mapping:
  - `4` is read (`r`), `2` is write (`w`), `1` is execute (`x`).
  - Binary digits are added to get the total permission value.
  - For instance, `101` (binary) is `5` in decimal, representing `r-x` (read and execute).

### Examples

- `chmod 562 CyberPatriot.txt`
  - User (5): `101` in binary or `r-x` (read and execute).
  - Group (6): `110` in binary or `rw-` (read and write).
  - Everyone (2): `010` in binary or `-w-` (write only).

Remember, root always has permissions, and it's crucial to set permissions appropriately to ensure system security and functionality.
