---
title: Windows
description: 
published: true
tags: curriculum, basic, linux
editor: markdown
---

# Linux Security Modules (LSM)
Linux Security Modules (LSM) provide a framework within the Linux kernel for supporting various security models without favoring a specific security implementation. LSM allows kernel-level access controls to be implemented through hooks, enabling developers to add custom security policies without modifying core kernel code. Prominent implementations leveraging LSM include Security-Enhanced Linux (SELinux) and AppArmor. These modules help fortify Linux systems against unauthorized access, safeguarding both data and processes from potential threats.
 - [Linux Security Modules](/linux/lsm)
{.links-list}

<br> 

# Pluggable Authentication Modules (PAM)
Pluggable Authentication Modules, is a flexible mechanism for developing authentication-related applications in Unix-like operating systems. PAM provides a way to develop programs that are independent of authentication scheme, which can be module-specific, ensuring that applications can be agnostic to the underlying authentication logic. Configuration for PAM is housed in files within the /etc/pam.d/ directory or in the /etc/security/ directory, dictating the behavior of the authentication modules. These files determine how various services interact with PAM-enabled authentication methods, offering a granular approach to security and session control.
- [PAM Files](/linux/pam-files)
{.links-list}

<br> 

# Linux Services: systemd
Systemd is an init system and service manager for Linux operating systems that aims to streamline and unify service configuration and behavior across different distributions. Systemd not only initializes user-space components during system startup but also manages system processes throughout their lifecycle. With its centralized management approach, systemd uses "units" (representing services, mount points, devices, and more) described in declarative configuration files, making system state orchestration more straightforward and efficient
- [systemd](/linux/systemd)
{.links-list}

<br> 

# Cron and At Daemons
The cron and at daemons are scheduling tools in Unix-like operating systems that automate the execution of tasks at specified intervals. The cron daemon allows for regular, repeated task scheduling, using a configuration file called the "crontab" to specify tasks and their respective intervals. These tasks might be set to run hourly, daily, or any custom-defined frequency. In contrast, the at daemon facilitates the execution of a single task at a particular future time, such as "2 PM tomorrow." Together, these utilities offer users the flexibility to automate a broad range of system and application jobs, ensuring that vital tasks are executed consistently without manual intervention.
- [cron](/linux/cron)
- [at daemon](/linux/cron)
{.links-list}

<br> 

# Linux Syslog
Syslog is a standardized logging mechanism in Linux and other Unix-like operating systems, serving as a central repository for system and application messages. It provides a unified framework for recording and storing log data, facilitating easier monitoring, debugging, and troubleshooting. 
- [Linux syslog](/linux/syslog)
{.links-list}

<br> 

# File Permissions
Linux file permissions form the foundational layer of security for files and directories in Unix-like operating systems. Every file or directory has an associated owner and group, along with a set of permissions that dictate read (r), write (w), and execute (x) access for the owner, the group, and everyone else. These permissions ensure that only authorized users can read, modify, or execute specific files. 
- [File Permissions](/linux/file-permissions)
{.links-list}

<br> 

# Miscellaneous Linux Settings
Every configuration for Linux systems are housed in a file somewhere on the system. A lot of these files function similarly to the Windows registry. Below are a list of a few you should take look at but dont fall into any specific categories. 
- [Linux MISC](/linux/misc-settings)
{.links-list}

<br> 