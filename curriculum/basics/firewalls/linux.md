---
title: Firewalls for Linux
description: 
published: true
tags: curriculum, basic, firewalls, linux
editor: markdown
---

# Introduction
On Linux systems you can manage the firewall rules through the networking configurations, but the most common way is to use UFW, which stands for "Uncomplicated Firewall," it is a user-friendly interface for managing firewalls in Linux environments. Built atop the more complex iptables, UFW simplifies the process of configuring and managing a firewall on Linux systems. With straightforward commands, users can easily allow or deny network traffic based on port, service, or protocol, ensuring a balance between connectivity and security for Linux machines. Its intuitive approach has made UFW a popular choice among Linux users seeking effective yet uncomplicated firewall management.

> By default, when you enable UFW it is in a "deny any any" state, which means it will block any connections on any port from any IP address
{.is-info}

# Turn UFW On
UFW should come preinstalled on most Linux flavors, but if it is not available you can install it from all standard package managers.

1. Open the `Terminal`
2. Run the command `sudo ufw enable`

# Set UFW defaults
As Linux operates like a traditional firewall, unless otherwise stated in the ReadMe it is good practice to deny all incoming traffic and allow all outgoing traffic. By default, UFW is in deny any any, but these settings may have changed. 

## Deny all incoming traffic
1. Open the `Terminal`
2. Run the command `sudo ufw default deny incoming`

## Allow all outgoing traffic
1. Open the `Terminal`
2. Run the command `sudo ufw default allow outgoing`

## Rest UFW
This is not something you should typically do, but you have the options if there are more entries than you are willing to delete one by one.
1. Open the `Terminal`
2. Run the command `sudo ufw reset`

# List all UFW rules
Running this command will tell you if UFW is enabled and give a list of all rules.
1. Open the `Terminal`
2. Run the command `sudo ufw status`

# Add a UFW rule
To add a rule in the firewall it is best to be as specific as possible, limiting the potential attack surface as much as possible. For example if you need to allow ssh access from the IP 10.1.1.70 the most secure option is to specify the IP address in the rule and limit ssh traffic only from that IP rather than any IP. With UFW you can specify as much or as little as you want, but it is always recommended to add as much detail as possible.

Rule specifications can be as simple as a port or can include the IP. Most will follow the format `[port] from [IP address]` example: `80 from 10.1.1.70`. You can also specify the protocol by doing `[port]/[protocol]` example: `80/tcp`.
1. Open the `Terminal`
2. Run the command `sudo ufw allow [rule specification]`

# Remove a UFW rule
1. Open the `Terminal`
2. Run the command `sudo ufw delete [rule specification]`

# Enable UFW Logging
1. Open the `Terminal`
2. Run the command `sudo ufw logging on`

# Checklist
- [ ] Turn on UFW
- [ ] Set UFW defaults
- [ ] Review all rule entries
- [ ] Add all required entries
- [ ] Enable Logging

<br>