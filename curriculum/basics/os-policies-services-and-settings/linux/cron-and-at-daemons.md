---
title: Cron and At Daemons
description: 
published: true
tags: curriculum, basic, linux
editor: markdown
---
# Introduction 

# cron Daemon

The cron daemon (`crond`) schedules tasks to run at specified times and intervals. It utilizes various configuration files for this purpose.

## Configuration Files for cron

### `/etc/crontab`
- Description: Holds entries that direct commands to execute at specific times.
- Features:
  - Used to schedule custom tasks system-wide.
  - Editable only by the root user.
  - Tasks in this file are run as the root user.

### `/etc/cron.directory`
- Description: cron executes scripts in the following directories at specified intervals for the whole system:
  - `/etc/cron.hourly`
  - `/etc/cron.daily`
  - `/etc/cron.weekly`
  - `/etc/cron.monthly`

### `/var/spool/cron/username`
- Description: Allows individual users to create personal crontab files at `/var/spool/cron/username`, if permitted.

### `/etc/cron.allow`
- Description: Identifies users who are allowed to create their own cron jobs.
- Rules:
  - If this file exists, only listed users can create crontab files in `/var/spool/cron/username`.
  - `/etc/cron.deny` is ignored if this file exists.

### `/etc/cron.deny`
- Description: Identifies users who are not allowed to create cron jobs.
- Rules:
  - If this file exists, listed users are not allowed to edit `/var/spool/cron/username`.
  - This file is processed only if `/etc/cron.allow` does not exist.

## Cron Job Syntax

Each entry in `/etc/crontab` or `/var/spool/cron/username` follows a specific format, illustrated below:

| Example | Minute | Hour | Day of Month | Month | Day of Week | Command |
|---------|--------|------|--------------|-------|-------------|---------|
| `00 5 * * 6 /bin/tar -cf /home /mnt/usb/homebak.tar` | 00 | 5 | * | * | 6 | `/bin/tar -cf /home /mnt/usb/homebak.tar` |
| `15 23 25 * * /bin/updatedb` | 15 | 23 | 25 | * | * | `/bin/updatedb` |
| `00 24 1 1,6 * /bin/who > /root/who.txt` | 00 | 24 | 1 | 1 and 6 | * | `/bin/who > /root/who.txt` |

## Managing cron Tasks

Use the `crontab` command for managing cron tasks:

- **Editing Crontab**: `crontab -e` edits the current user's crontab file.
- **Listing Cron Jobs**: `crontab -l` lists cron jobs for the current user.
- **Removing Crontab**: `crontab -r` removes the current user's crontab file.
- **Specifying User**: Add `-u username` to specify a different user for the `-e`, `-l`, and `-r` options.

## Additional Details

- Some distributions use separate files in `/etc/cron.d` in addition to lines in `/etc/crontab`.
- The cron daemon is managed using its init script in `/etc/rc.d/init.d/` or `/etc/init.d/` on init-based distributions, and with the `crond.service` file and the `systemctl` command on systemd-based distributions.

# At Daemon

The `at` daemon is used for scheduling tasks to run once at a specified future time. Unlike `cron`, which is designed for recurring tasks, `at` executes commands at a specified time and date.

## How the at Daemon Works

- **Scheduling Tasks**: Users schedule jobs using the `at` command, specifying the time for the job to run.
- **Execution**: The `atd` service (at daemon) then runs these commands at the specified time.

## Basic at Commands

### Scheduling a Job with at

- Command Format: `at [time] [date]`
- Example: Schedule a job for 5 PM on July 10th:
  ```bash
  at 5pm Jul 10
  ```
  After entering this command, you'll be prompted to enter the command(s) to execute.

### Listing Scheduled Jobs

- To view your currently scheduled `at` jobs:
  ```bash
  atq
  ```

### Removing a Job

- To remove a job from the `at` queue, first find its job number with `atq`, then use `atrm`:
  ```bash
  atrm [job number]
  ```

## Configuration Files for at

### `/etc/at.deny`
- Description: Lists users who are denied access to the `at` command.
- If `/etc/at.allow` exists, this file is ignored.

### `/etc/at.allow`
- Description: Lists users who are allowed to use the `at` command.
- If this file exists, only listed users can use `at`; all others are denied.

## Managing the at Daemon

- **Starting atd Service**: The `atd` service is usually started by default. If not, you can start it manually:
  ```bash
  sudo systemctl start atd
  ```

- **Enabling atd on Boot**: To ensure `atd` starts at boot:
  ```bash
  sudo systemctl enable atd
  ```

- **Checking atd Status**: To check the status of the `atd` service:
  ```bash
  sudo systemctl status atd
  ```

## Additional Details

- **Time Formats**: The `at` command is flexible with time formats, understanding phrases like `now + 1 hour`, `5pm tomorrow`, etc.
- **Environment**: The `at` job runs with the user's environment at the time of scheduling.
- **Output**: By default, the output of `at` jobs is mailed to the user. Ensure local mail is configured if this functionality is needed.

*This guide provides a basic overview of the `at` daemon and its usage in Linux.*
