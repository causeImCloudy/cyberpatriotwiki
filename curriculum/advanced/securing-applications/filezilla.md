---
title: FileZilla
description: 
published: true
tags: curriculum, advanced
editor: markdown
---
# FileZilla Server Maintenance

## Updating FileZilla Server

First, ensure that FileZilla Server is updated to its latest stable version. FileZilla Server does not have an auto-update feature, so manual updates are necessary.

## Users

1. In the FileZilla Server Interface, go to **Edit** then **Users**.
2. If there is an "anonymous" user, and you don't need guest access, remove it.
3. Change authorized FTP user's passwords.
4. Verify the permissions of each user's Shared Folders.

## Settings

1. In the FileZilla Server Interface, go to **Edit** then **Settings**.

### General Settings
- Max Number Of Users: 10
- Number Of Threads: 2
- Connections Timeout: 120
- No Transfer Timeout: 120
- Login Timeout: 60

### Security Settings
- Protection Level: Require matching peer IP address of control connection

### Admin Interface Settings
- Change Admin Password

### FTP over TLS Settings
- Enable FTP over TLS support (FTPS)
- Disallow plain unencrypted FTP
- Generate New Certificate

### Autoban
- Enable Automatic Bans
- Ban IP address after 10 failed attempts within one hour
- Ban duration: 1 hour

## Windows File System

1. Within a Windows Explorer, navigate to the FTP root directory for each user.
2. Verify the following:
   - Check the permissions on the folder to ensure that only authorized users of that folder can write to the folder.
   - Verify that no files within the folder are malicious or confidential.

**Note:** Be sure to regularly review and update these settings as needed to maintain the security and functionality of your FileZilla Server.
