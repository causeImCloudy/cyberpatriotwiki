# Introduction

Firewalls are integral security components designed to filter and control the network traffic going in and out of a system. By setting up specific rules and policies, these firewalls can block or permit connections based on various criteria, such as source IP, destination IP, port number, and protocol type. While they primarily act as a barrier to protect systems from potential threats, OS firewalls can also be used to limit application network access and isolate network services. Available in most modern operating systems, these firewalls are essential tools for maintaining a system's network security and integrity.

Opposed to traditional firewalls that are standalone devices filtering thousands of requests per second, the firewalls we will be talking about are host based and essentially operate as an application on the OS. 

# Windows

The Windows Firewall is a security utility integrated into the Windows operating system, designed to monitor and filter incoming and outgoing network traffic. It uses predefined rules to allow or block connections based on IP addresses, port numbers, and specific protocols. Over the years, with each subsequent Windows release, the firewall has evolved, gaining enhanced features and better user interfaces. 
- [Windows](./firewalls/windows)
{.links-list}


# Linux 
Linux firewalls, primarily managed through tools like iptables and its successor nftables, are fundamental to network security on Unix-like systems. They provide granular control over network connections. With a combination of rule chains and tables, Linux firewalls ensure both stateful and stateless packet filtering, establishing a robust and configurable barrier against malicious network activities. Linux firewalls, like many of the settings we have discussed, are specific to the Linux flavor. The most common firewall management package on Linux is the Uncomplicated Firewall (UFW).
- [Linux](./firewalls/linux)
{.links-list}