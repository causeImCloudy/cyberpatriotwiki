---
title: Windows Features and Control Panel
description: 
published: true
tags: curriculum, basic, windows
editor: markdown
---
# Introduction

## Windows Action Center
The Windows Action Center is a central hub for the major security and system items within Windows. It will alert you to anything at fault reported. Things like your Anti-Virus is Out of Date, Not Installed, or Not Running; Windows Update not Running or Checking for Updates, and the Windows Firewall is turned off.

To manage the Action Center, use the following Run command: wscui.cpl. Make sure all of the items are enabled by going to the "Change Action Center settings" link on the left side of the screen. All options should be checked.

Resolve any items listed in Red, and investigate any options in Yellow.


## Windows Remote Access
Depending on your requirements for your system, you may or may not want Remote Desktop (or Terminal Services) enabled on a computer. You should only have it enabled if you or someone else requires access to the system without sitting down at the console. If you must have it enabled, you should secure it as much as you can.

To manage the Remote Access Settings, you will need to open the System Control Panel Applet by holding down the Windows key on your keyboard, and pressing the Pause key (usually located next to the Num, Caps, and Scroll Lock Lights on most keyboards, sometimes paired with Break) Once there, on the left side, select "Remote settings".

To DISABLE Remote Desktop: Uncheck the Remote Assistance checkbox, and select "Don't allow connections to this computer". Click OK to save these settings.

To SECURE Remote Desktop: Uncheck the Remote Assistance checkbox, and select "Allow connections from computers running any version of Remote Desktop with Network Level Authentication (more secure)". Go to "Select Users..." and verify only the users that require remote access are listed. Click OK to save these settings.

## Lock Screen Saver
If someone steps away from their computer without locking it, that leaves that computer open for anyone to walk up to and use. Without proper authentication, that rogue user could access data and make changes they are not authorized to access. We can reduce the amount of time by setting a screen saver timeout and forcing the user to re-login by displaying the logon screen when the computer is used again.

Select "Settings" from the Start Menu
Select the "Personalization" category
Choose "Lock screen" on the left
Click "Screen saver settings"
Choose 15 minutes in the Wait box
Check the "On resume, display logon screen" check box
Click OK

## Disable Non-Required Windows Features
A Windows Feature is an optional program (or set of programs) that can been installed on the system to change Windows. These can be different services to allow remote access, run a server, or accessories like games.

To remove features, you will need to open the Programs and Features Control Panel Applet by typing the following into a Run window:appwiz.cpl then click on the "Turn Windows Features On & Off" link on the left side of the window.

Internet Information Services (IIS)

Internet Information Services (IIS, formerly Internet Information Server) is an extensible web server created by Microsoft for use with Windows NT family. IIS supports HyperText Transfer Protocol (HTTP), HTTP over Secure Socket Layer (HTTPS), File Transfer Protocol (FTP), FTP over Secure Socket Layer (FTPS), Simple Mail Transfer Protocol (SMTP) and Network News Transfer Protocol (NNTP).

LPD Print Service

Located under Print and Document Services, LPD enables client computers to print to the Line Printer Daemon (LPD) service on this server using TCP/IP and the Line Printer Remote (LPR) protocol.

RIP Listener

RIP (Routing Information Protocol) Listener waits for route updates sent by routers (generally from Cisco) that use the Routing Information Protocol in a corporate LAN.

SMB 1.0/CIFS File Sharing Support

In computer networking, Server Message Block (SMB), one version of which was also known as Common Internet File System (CIFS) operates as an application-layer network protocol mainly used for providing shared access to files, printers, and serial ports and miscellaneous communications between nodes on a network. SMB v2 or v3 should be used, not v1.

Telnet Server

Enables a remote user to log on to this computer and run programs, and supports various TCP/IP Telnet clients, including UNIX-based and Windows-based computers. If this service is stopped, remote user access to programs might be unavailable. If this service is disabled, any services that explicitly depend on it will fail to start.


## Enable Data Execution Prevention(DEP) 
According to Microsoft, DEP is : “…a set of hardware and software technologies that perform additional checks on memory to help prevent malicious code from running on a system.”

Open an elevated command prompt
Enter the following command
bcdedit.exe /set {current} nx AlwaysOn
Restart your computer when convenient for the change to take effect

## SMB Shares
Shares are folders that can be remotely accessed and manipulated. One remote computers, you can access them directly, or mount the share as a drive, like an H drive. Files and Printers are shared using the Server Message Block or SMB infrastructure.

To manage these shares, you will need to open Computer Management by typing the following into a Run window: compmgmt.msc. Once there, on the left side, select "System Tools", then "Shared Folders", then "Shares".

Administrative shares (shares ending with a $-dollar sign) are hidden network shares created by Windows NT family of operating systems that allow system administrators to have remote access to every disk volume on a network-connected system.

This will list out every folder or drive that is being shared. The most common (and default) shares are the following:

ADMIN$: The folder Windows is installed in. Usually this is C:\Windows.
C$: The disk drives on the system. Usually only C:\ is listed, however, if there are more drives on the system, they would listed as well.
IPC$: This area, which is used for inter-process communication via named pipes and is not part of the file system. This share is required for the other shares to work, and can not be removed or disabled.
To disable any shares (except IPC$), right-click on the shares name and click Stop Sharing. If it is an admin share, you must confirm you want to remove them. If your computer does not need to share any folders or drives, disable all of them.

To disable the IPC$ share, you must disable the Server service as described in Section 1.3. Warning: Once you disable that service, you will not be able to manage any of the other shares. Make sure you Stop Sharing any shares you need to stop before disabling the Server service.

Registry Location SMB shares are stored in the registry as Multi-String Values at HKLM\System\CurrentControlSet\Services\LanmanServer\Shares\

### Securing SMB
There's a few items you should take care of when working with SMB.

Only share the directories that must be shared.
Disable SMBv1 by adding the following registry sub-key (DWORD): HKLM\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters\SMB = 0
Verify the directories are not serving anything that shouldn't be shared (passwords, rogue files, etc.)
Make sure only those user that should have access to the shares, have access, and other don't. Check this in each share's properties within Computer Management > Shared Folders.