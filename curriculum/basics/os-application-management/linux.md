---
title: OS Application Management for Linux
description: 
published: true
date: 2023-08-17T03:15:16.465Z
tags: curriculum, basic, applications, linux
editor: markdown
dateCreated: 2023-08-09T18:36:09.469Z
---

# Introduction
On Linux systems there are tools called Package Managers that are designed to install, uninstall and manage programs for a system. While Package Manager are typically more supported and track applications better than Windows, you can still install programs and executables anywhere on the file system. 

Each Linux flavor has its own default package manager. For example Ubuntu has the Advanced Packaging Tool (apt), Fedora has the Red Hat Package Manager(RPM), and Arch has the pacman Package Manager (pacman). Each package manager is sightly different syntax but satisfies the same utility.

> For the sake of this documentation we will use apt as it's the most common. If you need to use another we may publish tips on those later, otherwise try googling "install using firefox"
{.is-success}

# Install a Program
Within Linux, you most likely will need to have elevated levels of permissions to install a program.
By default, Linux systems have a remote repository housing a list of applications to install. Think of this like the app store on iOS. These repositories are typically hosted by repositories list which expands the potential installable programs.

1. Open the `Terminal`
2. Run the command `sudo apt update`
3. Run the command `sudo apt install [program]`
4. If prompted type `y` to allow the program to install to disk

> Optionally you can include the option `-y` which will skip all confirmation prompts.
{.is-info}

<br>
<br>

# Uninstall a Program
To uninstall a program you run a similar command, but you also have the option to purge a program which removes all associated files.

1. Open the `Terminal`
2. Run the command `sudo apt uninstall [program]`
	- Or to purge use `sudo apt purge remove [program]`
3. If prompted type `y` to allow the program to uninstall from the disk

<br>
<br>

# Update a Program
Updating a program on Linux is two parts, first you must update your local repository from the remote repository then you upgrade the system. To upgrade a specific program, first update the repository and then install the program again following the above steps.

1. Open the `Terminal`
2. Run the command `sudo apt update`
3. Run the command `sudo apt upgrade`
4. If prompted type `y` to allow the program to update

> Optionally you can include the option `-y` which will skip all confirmation prompts.
{.is-info}

<br>
<br>


# Manage repositories
As mentioned above repositories are like the app store. To you can add and remove repositories. For Cyber Patriot you should ensure that all repositories are known and trusted sources.

## List installed packages
1. Open the `Terminal`
2. Run the command `sudo apt list --installed`

<br>

## Add a repository
1. Open the `Terminal`
2. Run the command `sudo add-apt-repository [repoistory]`

<br>

## Remove a repository

1. Open the `Terminal`
2. Run the command `sudo add-apt-repository -r [repoistory]`

<br>
<br>

# Checklist
- [ ] Install required programs
- [ ] Uninstall non essential programs
- [ ] Update all programs
- [ ] Add/Remove repositories

<br>