---
title: OS Application Management for Windows
description: 
published: true
date: 2023-08-17T03:16:09.805Z
tags: curriculum, basic, applications, windows
editor: markdown
dateCreated: 2023-08-09T16:39:13.833Z
---

# Introduction
Here is a quick introduction to specifics about Windows programs.

## Common Program Types
On Windows there are a few common types of executables/programs specific to Windows. These end in .exe, .msi, and .dll.  
- A file ending in `.exe` is a Portable Executable (PE) which is a stand-alone program.
- A file ending in `.msi` is a Microsoft Installer which installs a program through an installer program.
- A file ending in `.dll` is a Dynamic Linked Library (DLL) which contains a portion of executable code that multiple other programs can utilize. 

<br>

## Common Installation Locations
By default, there are a few location which are designated as program installation locations. While there are certain places meant for program files, this does not mean that a program **can not** live somewhere else on the file system.
- C:\Program Files - This is the standard install location for programs.
- C:\Program Files (x86) - This is the standard installation folder for x86 programs.
- C:\Users\<user>\AppData\Roaming - This is the standard location for program file specific to users.

<br> <br>

# Installing a Program
There are many ways to install a program on Windows, we will only cover a few in this section. In a corporate environment you will typically handle this through the centralized endpoint management software.

## Manually Install
You can always manually install any program. Each program may be slightly different depending on how to download it.

1. Download the program.
2. Open the file location.
3. Double-click the file.
4. If the file is a `.msi` you will have to click through the installer.

> Download sites are extremely different from each other. You may have to click around the website. Always ensure you are on the official site (i.e. mozilla.org). If you are having a hard time try googling "Firefox download". 
{.is-warning}

<br> 

## Ninite
The official Cyber Patriot recommendation to install software is an OpenSource tool called Ninite. Ninite bundles all the software you choose into a single installer. 

1. Read the README for required programs.
2. Navigate to https://ninite.com in a web browser.
3. Under the header `1. Pick the apps you want` select the apps you want to download or update.
4. Under the header `2. Download and run your custom installer/updater` click `Get Your Ninite`
5. Navigate to the downloaded file `Ninite <program> Installer.exe` 
6. Double-click the `Ninite <program> Installer.exe` file.
7. Allow Ninite to install all of your programs. 
8. Click `Show Details` 
9. Ensure all applications show `Ok` or `Installed` next to them.

> Ninite only has certain applications, if Cyber Patriot asks for other applications try installing them manually.
{.is-info}

<br> <br>

# Uninstalling a Program
Just like installing programs there are a handful of ways to uninstall a program. In a corporate environment you will typically handle this through the centralized endpoint management software.

> DO NOT REMOVE VMWare Tools, .NET Programs, C++ Redistributable, & any programs you installed or updated.
{.is-danger}

<br>

## Windows uninstaller program
You can manually uninstall a program by either deleting its executable or utilizes the Windows uninstaller.

1. Search 'Add or Remove Program' in the Windows search bar.
2. Click the option with a cog titled `Add or Remove Programs`.
3. Click the `...` on the right side of the program you want to remove.
4. Choose `Uninstall`.
5. If an uninstaller prompt comes up click through the uninstaller.

<br> 

## Using CCleaner
CCleaner (formerly Crap Cleaner), developed by Piriform, is a utility program used to clean potentially unwanted files (including temporary internet files, where malicious programs and code tend to reside) and invalid Windows Registry entries from a computer.  
CCleaner mirrors the utility of Ninite but to uninstall a program. The benefit of CCleaner is that it searches additional locations and removes temporary associated files.

1. Install CCleaner
2. Run CCleaner.
3. Select `Tools` on the left hand side.
4. Select the `Uninstaller` tool.
5. Select the program you want to uninstall.
6. Click the `Uninstall` option in the top right.

<br> <br>

# Update a Program
Managing a program can entail a lot of work, but the majority of what we are going to discuss in this section is about updating a program. 

<br>

## Update with Ninite
With Ninite to update an application all you have to do is select it before downloading the installer. 

<br>

## Update with CCleaner
1. Install CCleaner
2. Run CCleaner.
3. Select `Tools` on the left hand side.
4. Select the `Software Updater` tool.
5. Select the program you want to update.
6. Click the `Update` option in the top right.

<br>
<br> 

# Checklist
- [ ] Install required programs
- [ ] Uninstall non essential programs
- [ ] Update all programs

<br>