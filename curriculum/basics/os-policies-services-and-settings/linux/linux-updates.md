---
title: "Linux Updates"
description: 
published: true
tags: curriculum, basic, linux
editor: markdown
---

# Introduction

1. **Update Package Lists**: Update the list of available packages and their versions, but it does not install or upgrade any packages.
   ```bash
   sudo apt-get update
   ```

2. **Upgrade Packages**: Upgrade all of the installed packages to their latest versions.
   ```bash
   sudo apt-get upgrade
   ```

3. **Dist-Upgrade**: Handles changing dependencies with new versions of packages and will install new packages or remove existing ones if necessary.
   ```bash
   sudo apt-get dist-upgrade
   ```

## Enabling Automatic Updates

1. **Install Unattended Upgrades Package** (if not already installed):
   ```bash
   sudo apt-get install unattended-upgrades
   ```

2. **Enable Automatic Updates**: Edit the configuration file to enable automatic updates.
   ```bash
   sudo dpkg-reconfigure -plow unattended-upgrades
   ```

3. **Configure Automatic Updates**: Customize the settings (e.g., update frequency, packages to update) by editing the configuration file.
   ```bash
   sudo nano /etc/apt/apt.conf.d/50unattended-upgrades
   ```

## Checking for Default Repositories

1. **Check Repository Configuration**: View the list of configured repositories.
   ```bash
   cat /etc/apt/sources.list
   ```

2. **Check for Additional Repositories**: Look for any additional repository configuration files.
   ```bash
   ls /etc/apt/sources.list.d/
   ```

3. **Ensure Default Repositories are Configured**: The `sources.list` file should contain the main repository, updates, and security updates. Adjust as necessary for your specific Linux distribution and version.
