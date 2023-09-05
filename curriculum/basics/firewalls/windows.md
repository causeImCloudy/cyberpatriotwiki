---
title: Firewalls for Windows
description: 
published: true
tags: curriculum, basic, firewalls, windows
editor: markdown
---

# Introduction
A Windows Firewall is an integrated security system in Microsoft Windows operating systems. It monitors and filters incoming and outgoing network traffic based on security policies and set rules. By acting as a barrier between a trusted internal network and potential external threats, the Windows Firewall helps prevent unauthorized access, malware, and other malicious activities from affecting a user's system or network.

This section will guide you through several security settings you should set for the Window Firewall.

# Restore Windows Firewall Defaults
The easiest solution to securing Windows Firewall is to restore it to Windows default.

1. Open `Control Panel`.
2. Click `System and Security`.
3. Click `Windows Defender Firewall`.
4. Choose `Restore Defaults` on the left side menu.
5. Click the `Restore Defaults` button.
6. Accept any prompt by clicking `Yes`.


# Turn the Windows Firewall On
1. Open `Control Panel`.
2. Click `System and Security`.
3. Click `Windows Defender Firewall`.
4. Choose `Turn Windows Defender Firewall on or off` on the left side menu.
5. Check the box `Turn on Windows Defender Firewall` under the `Private network settings` section.
6. Check the box `Turn on Windows Defender Firewall` under the `Public network settings` section.
7. Click `Okay`.

# Add an application through the Windows Firewall
1. Open `Control Panel`.
2. Click `System and Security`.
3. Click `Windows Defender Firewall`.
4. Choose `Allow an app or feature through Windows Defender Firewall` on the left side menu.
5. Click `Allow an other app...`.
6. Click `Browse` and locate the executable of the application you are trying to bypass.
7. Click `Network types...` and select public or private based on your needs.
8. Click `Add`.
9. Click `Okay`.


# Remove an application bypass from Windows Firewall
1. Open `Control Panel`.
2. Click `System and Security`.
3. Click `Windows Defender Firewall`.
4. Choose `Allow an app or feature through Windows Defender Firewall` on the left side menu.
5. Click the application you want to remove.
6. Uncheck both boxes to the right of the name of the application.
   - If the application is not a Windows default app you may also remove it by clicking `Remove`
7. Click `Okay`.

# Checklist
- [ ] Restore Windows Defender Firewall to default settings.
- [ ] Ensure Windows Defender Firewall is On and Running
- [ ] Add all necessary Windows Defender Firewall exception
- [ ] Remove or disable all unnecessary bypass entries in the Windows Defender Firewall