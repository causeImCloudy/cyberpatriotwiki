---
title: User and Group Management for Linux
description: 
published: true
date: 2023-07-15T15:06:22.933Z
tags: curriculum, basic, user management, group management, linux
editor: markdown
dateCreated: 2023-07-15T14:37:04.286Z
---

# User Management

> All the following assumes you are root or have sudo privileges to execute the command.
{.is-success}


## The etc-passwd file
The /etc/passwd file on Linux systems contain the list of users and some of their basic settings. This file is set up like a spreadsheet with columns, only instead of nice lines, each column is delimited with a colon (:).

1. Open the `Terminal`
2. Run the command `cat /etc/passwd`
3. Run the command `awk -F: '{ print $1, $3, $4, $6 }' /etc/passwd`

The first command `cat /etc/passwd` displays the whole passwd file, which contains a lot of data. The second command `awk -F: '{ print $1, $3, $4, $6 }' /etc/passwd` will trim the content of the file and only print out the Username, User ID, Group ID, and Home Path. These are typically the most usefully entries within the passwd file.

- Username: A username in Linux is an identifier for a specific user account. Each user account in the system has a unique username associated with it.
- User ID (UID): Each user must be assigned a user ID (UID). UID 0 (zero) is reserved for root and UIDs 1-99 are reserved for other predefined accounts. Further UID 100-999 are reserved by system for administrative and system accounts/groups. User accounts typically start at 1000.
- Group ID (GID): The primary group ID (stored in /etc/group file)
- Home directory: The absolute path to the directory the user will be in when they log in. If this directory does not exist then users directory becomes `/`

> Incorrectly editing the passwd file can lock you out of the system or cause unexpected consequences.
{.is-warning}

<br>

## Remove unauthorized users

Each Cyber Patriot competition will have a list of authorized users located in a gray block within the Read Me. You should verify the list of authorized user/administrators to the actual list of user. If you find an unauthorized user you should remove the account.

Remove a user account:
1. Open the `Terminal`
2. Run the command `deluser [username] --remove-all-files`

> Be sure to answer all forensic questions before deleting a user with the `--remove-all-files` option
{.is-warning}

## Setting a Secure Password for users

Having a weak password on a user account makes it extremely vulnerable to attacks by outside individuals. With a weak password, an attacker can more easily guess the code to access a user’s files. Strong passwords make it much more likely that only the actual holder of the account can access it.

In CyberPatriot, the README will say something along the lines of "This company's security policies require that all user accounts be password protected". This will hint to you to complete the following on all standard users and root:

Change a user password:

1. Open the `Terminal`
2. Run the command `passwd [username]`
3. Enter a secure password
4. Confirm the secure password

> In Linux when typing a password you will not see feedback as you type in the terminal.
{.is-info}

<br>

## Disable the Guest Account
Guest accounts are meant to be used by everyone other than authorized users. This means anyone could access the system. By default, these accounts have very limited access to the system, however, they can be given more permission than required. It is best practice to disable this account if it is not required.

For CyberPatriot, unless the specifically state in the README to allow guests, you should disable this account. If you receive a penalty for doing so, don't be scared, it is very easy to re-enable this account. If the README says to allow guests, secure it as much as possible.

Disable the Guest Account:
1. Open the `Terminal`
2. Enter open the lightdm.conf in a text editor by running `nano /etc/lightdm/lightdm.conf`
3. Add or Edit the "allow-guest" line till it looks like the following: `allow-guest=false`
    - This line should be under [SeatDefaults]. If the line does not exist, add it directly below the [SeatDefaults] line.
4. Save the file by pressing <kbd>CTRL + X</kbd>.
5. Confirm overwrite (saving) of the file by typing <kbd>Y</kbd> then <kbd>Enter</kbd>.

<br>

## Password Expiration
Unlike Windows, each user can have its own password policies assigned to it. The default password policies is applied when the user is created or when their password changes.

1. Open the `Terminal`
2. Run the command `chage -m 7 -M 90 -W 14 -d 0 [USERNAME]`

This command will set a minimum age of 7, maximum age of 90, warn age of 14, and expire the password now forcing the user to change their password at next login.

<br>

## Checklist
- [ ] Verify only authorized users exist.
- [ ] Set a secure password for each user.
- [ ] Set the password policy for each user
- [ ] Secure the Guest account
- [ ] Create Users if specified in the Read Me

<br>

# Group Management
<br>

## The etc-group file
Similar to Windows, users can be placed into groups to manage permissions easier.

To check the groups, within a terminal window as root, enter cat /etc/group

Like the /etc/passwd file, this file is set up like a spreadsheet with columns, only instead of nice lines, each column is delimited with a colon `:`.


For each Cyber Patriot round you should check the following for all groups:

### Ensure the group has a unique ID

### Root group should be ID 0

<br>

## Sudoers
Any command that requires "Administrative" rights must be run as root. If you remember, you had to use `sudo` to switch users to the root user. That's because the root users requires a higher level of permission to log in to. The specific set of users that are allowed to use Sudo are called Sudoers.

Linux is set up by default to use two user groups as Sudoers, the sudo and adm groups. That's why in topic 7, we said check those groups.

There are two places to you should check for Sudoers, the /etc/sudoers file and the /etc/sudoers.d/ folder.

To check the /etc/sudoers file:
1. Open the `Terminal`
2. Run the command `visudo /etc/sudoers`
3. All lines beginning with a number sign `#` can be ignored these are comments.
4. All lines beginning with a percent sign `%` are group names.
    1. Only authorized groups should be present (sudo and adm are the default groups). 
    2. Delete unauthorized groups. 
5. All lines not starting with a symbol or `Defaults` are usernames. The only username should be root.
6. Remove the line `Defaults !authenticate`
7. Save the file by pressing <kbd>CTRL + X</kbd>.
8. Confirm overwrite (saving) of the file by typing <kbd>Y</kbd> then <kbd>Enter</kbd>.





