---
title: Linux Syslog
description: 
published: true
tags: curriculum, basic, linux
editor: markdown
---
# Introduction 

## Enable Auditing
Auditing and Logging is extremely important when it comes to tracking down the reason for an incident that may occur.

Start by installing the auditing package (auditd) using a package manage.

Once it's installed, enable auditing by entering the following: auditctl -e 1

## Enable Logging

Syslog is a standard protocol used for collecting and forwarding log messages and event data from various system components and applications. It plays a crucial role in monitoring, troubleshooting, and auditing system activities on Ubuntu 20.04 and other Linux distributions.

In this guide, we will walk you through the process of configuring Syslog on Ubuntu 20.04.

### Installation Steps

#### Step 1: Check Syslog Installation

Before proceeding, ensure that the Syslog daemon (rsyslog) is already installed on your Ubuntu system. Most Ubuntu installations include it by default. To check if it's installed, run the following command:

```bash
dpkg -l | grep rsyslog
```

If it's not installed, you can install it using:

```bash
sudo apt-get install rsyslog
```

#### Step 2: Configuration Files

##### Main Configuration File

- The main configuration file for rsyslog is `/etc/rsyslog.conf`. You can customize the log settings in this file according to your requirements.

##### Configuration Directory

- Additional configuration can be added by creating files in the `/etc/rsyslog.d/` directory. These files should have a `.conf` extension and will be included in the main configuration.

#### Step 3: Basic Configuration

##### Logging Messages to Local Files

- By default, rsyslog logs messages to various local files in the `/var/log/` directory, such as `/var/log/syslog` and `/var/log/auth.log`. You can modify log destinations and settings in the configuration files mentioned earlier.

#### Step 4: Remote Logging (Optional)

##### Forwarding Logs to a Remote Syslog Server

- You can configure rsyslog to forward log messages to a remote syslog server. Edit the main configuration file `/etc/rsyslog.conf` and add the following line to forward logs to a remote server:

  ```bash
  *.* @remote_server_ip:port
  ```

  Replace `remote_server_ip` and `port` with the IP address and port number of your remote syslog server.

#### Step 5: Restart Syslog Service

- After making changes to the configuration files, restart the rsyslog service to apply the new settings:

  ```bash
  sudo systemctl restart rsyslog
  ```

### Conclusion

Configuring Syslog on Ubuntu 20.04 allows you to collect, store, and manage log data efficiently. Whether you're monitoring system events, troubleshooting issues, or enhancing security, Syslog is a valuable tool for maintaining the health and security of your Ubuntu system.

For advanced configuration options and more information, refer to the rsyslog documentation and Ubuntu's official documentation.
```