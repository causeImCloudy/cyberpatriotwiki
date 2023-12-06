---
title: Windows Hosts File
description: 
published: true
tags: curriculum, basic, windows
editor: markdown
---
# Introduction

The very basic DNS resolution can occur with the Hosts file. Attackers will attempt to redirect common websites in your Hosts files to their web server where they can phish for your personal information.

Check the Hosts file by opening the following file in notepad: C:\Windows\System32\drivers\etc\hosts

Any line starting with the hashtag (#) is a comment and does not effect the host

The line with 127.0.0.1 and localhost together (and ::1 and localhost for IPv6) is normal.

All other lines are not there by default. Inspect and Remove them.

Since the current hosts file is read-only, if you make changes to the file, you will have to save the file to your desktop, then move the new file into the the folder containing the old hosts file to replace it.