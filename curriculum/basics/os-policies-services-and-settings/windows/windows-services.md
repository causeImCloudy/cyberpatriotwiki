---
title: Windows Services
description: 
published: true
tags: curriculum, basic, windows
editor: markdown
---
# Introduction

# Services to Disable

## HomeGroup Listener (HomeGroupListener)
- Description: Makes local computer changes associated with configuration and maintenance of the homegroup-joined computer. If this service is stopped or disabled, your computer will not work properly in a homegroup, and your homegroup might not work properly.
- Purpose: A homegroup is a group of PCs on a home network that can share files and printers. Using a homegroup makes sharing easier.

## HomeGroup Provider (HomeGroupProvider)
- Description: Performs networking tasks associated with configuration and maintenance of homegroups. If this service is stopped or disabled, your computer will be unable to detect other homegroups, and your homegroup might not work properly.

## LPD Service (LPDSVC)
- Description: Enables client computers to print to the Line Printer Daemon (LPD) service on this server using TCP/IP and the Line Printer Remote (LPR) protocol.

## Microsoft FTP Service (FTPSVC)
- Description: Enables this server to be a File Transfer Protocol (FTP) server. If this service is stopped, the server cannot function as an FTP server.

## Net.Tcp Port Sharing Service (NetTcpPortSharing)
- Description: Provides the ability to share TCP ports over the net.tcp protocol.

## Remote Access Connection Manager (RasMan)
- Description: Manages dial-up and virtual private network (VPN) connections from this computer to the Internet or other remote networks.

## Remote Desktop Services -OR- Terminal Services (TermService)
- Description: Allows users to connect interactively to a remote computer. Remote Desktop and Remote Desktop Session Host Server depend on this service.

## Remote Procedure Call (RPC) Locator (RpcLocator)
- Description: In Windows 2003 and earlier versions of Windows, manages the RPC name service database. In Windows Vista and later, this service does not provide any functionality.

## Remote Registry (RemoteRegistry)
- Description: Enables remote users to modify registry settings on this computer.

## RIP Listener (iprip)
- Description: Listens for route updates sent by routers that use the Routing Information Protocol version 1 (RIPv1).

## Routing and Remote Access (RemoteAccess)
- Description: Offers routing services to businesses in local area and wide area network environments.

## Server (LanmanServer)
- Description: Supports file, print, and named-pipe sharing over the network for this computer.

## Simple TCP/IP Services (simptcp)
- Description: Supports the following TCP/IP services: Character Generator, Daytime, Discard, Echo, and Quote of the Day.

## Simple Network Management Protocol -OR- SNMP Service (SNMP)
- Description: Enables Simple Network Management Protocol (SNMP) requests to be processed by this computer.

## SNMP Trap (SNMPTRAP)
- Description: Receives trap messages generated by local or remote Simple Network Management Protocol (SNMP) agents.

## SSDP Discovery (SSDPSRV)
- Description: Discovers networked devices and services that use the SSDP discovery protocol, such as UPnP devices.

## Telephony (TapiSrv)
- Description: Provides Telephony API (TAPI) support for programs that control telephony devices on the local computer and, through the LAN, on servers that are also running the service.

## Telnet [Server] (TlntSvr)
- Description: Enables a remote user to log on to this computer and run programs, and supports various TCP/IP Telnet clients.

## UPnP Device Host (upnphost)
- Description: Allows UPnP devices to be hosted on this computer.

## World Wide Web Publishing Service (W3SVC)
- Description: Provides Web connectivity and administration through the Internet Information Services Manager.

## WebClient (WebClient)
- Description: Enables Windows-based programs to create, access, and modify Internet-based files.

## Xbox Live Auth Manager (XblAuthManager)
- Description: Provides authentication and authorization services for interacting with Xbox Live.

## Xbox Live Game Save (XblGameSave)
- Description: This service syncs save data for Xbox Live save-enabled games.

# Services to Enable
# Windows Service Descriptions

## BitLocker Drive Encryption Service (BDESVC)
- Description: BDESVC hosts the BitLocker Drive Encryption service, which provides secure startup for the operating system and full volume encryption for OS, fixed, or removable volumes. This service allows BitLocker to prompt users for various actions related to their volumes when mounted and unlocks volumes automatically without user interaction. It stores recovery information to Active Directory, if available, and ensures the most recent recovery certificates are used. Stopping or disabling the service would prevent users from leveraging this functionality.

## Security Center (wscsvc)
- Description: The WSCSVC (Windows Security Center) service monitors and reports security health settings on the computer, including firewall status, antivirus status, antispyware status, Windows Update settings, User Account Control, and Internet settings. It provides COM APIs for software vendors to register and record the state of their products to the Security Center service. The service is used by the Security and Maintenance UI to provide systray alerts and a graphical view of security health states in the Security and Maintenance control panel. Network Access Protection (NAP) uses the service to report the security health states of clients to the NAP Network Policy Server. The service also has a public API to programmatically retrieve the system's aggregated security health state.

## Windows Defender Service (WinDefend)
- Description: Helps protect users from malware and other potentially unwanted software.

## Windows Event Log (EventLog)
- Description: This service manages events and event logs. It supports logging events, querying events, subscribing to events, archiving event logs, and managing event metadata. It can display events in both XML and plain text format. Stopping this service may compromise the security and reliability of the system.

## Windows Firewall (MpsSvc)
- Description: Windows Firewall helps protect your computer by preventing unauthorized users from gaining access to your computer through the Internet or a network.

## Windows Update (wuauserv)
- Description: Enables the detection, download, and installation of updates for Windows and other programs. If this service is disabled, users of this computer will not be able to use Windows Update or its automatic updating feature, and programs will not be able to use the Windows Update Agent (WUA) API.

## Other Third-Party Update Services
- Description: If an installed program has an update service (like Adobe Acrobat Update Service), it should be started and enabled. These types of services will keep the application up to date or prompt the user to update.

# Special Services
There is 1 service that requires special configuration to Disable it. Task Scheduler is restricted that no one can Disable it using the Services snap-in on Computer Management.

To disable Task Scheduler, open a Run window, and type in the following: regedit

This opens the Registry Editor. Be extremely careful on what you change in the Registry as it can make your system unstable or inaccessible.

Navigate to HKEY_LOCAL_MACHINE > SYSTEM > CurrentControlSet > services > Schedule. Look for the "Start" DWORD item. Double-click it and change the hexadecimal value to 4.

# Quick Reference

# Managing Windows Services and Policies

To manage these policies, follow these steps:

1. Open **Computer Management** by typing the following into a Run window: `compmgmt.msc`.
2. In Computer Management, on the left side, select **Services and Applications**, then **Services**.

## Disabling Services

For services that should be disabled, follow these steps:

1. Stop the service if it's running.
2. Set the **Startup Type** to **Disabled**.

## Enabling Services

For services that should be enabled, follow these steps:

1. Set the **Startup Type** to either **Automatic** or **Manual**, depending on the service.
2. Start the service. If the service stops immediately, set it to **Manual**; it will start when required.

## Services to Disable:

| Display Name                                                  | Service Name      |
|---------------------------------------------------------------|-------------------|
| HomeGroup Listener                                            | HomeGroupListener |
| HomeGroup Provider                                            | HomeGroupProvider |
| LPD Service                                                   | LPDSVC            |
| Microsoft FTP Service                                         | FTPSVC            |
| Net.Tcp Port Sharing Service                                  | NetTcpPortSharing |
| Remote Access Connection Manager                              | RasMan            |
| Remote Desktop Services -OR- Terminal Services                | TermService       |
| Remote Procedure Call (RPC) Locator                           | RpcLocator        |
| Remote Registry                                               | RemoteRegistry    |
| RIP Listener                                                  | IPRIP             |
| Routing and Remote Access                                     | RemoteAccess      |
| Server                                                        | LanmanServer      |
| Simple TCP/IP Services                                        | Simptcp           |
| Simple Network Management Protocol -OR- SNMP Service          | SNMP              |
| SNMP Trap                                                     | SNMPTRAP          |
| SSDP Discovery                                                | SSDPSRV           |
| Task Scheduler *REQUIRES REGISTRY CHANGE*                     | Schedule          |
| Telephony                                                     | TapiSrv           |
| Telnet [Server]                                               | TlntSvr           |
| UPnP Device Host                                              | upnphost          |
| World Wide Web Publishing Service                             | W3SVC             |
| WebClient                                                     | WebClient         |
| Xbox Live Auth Manager                                        | XblAuthManager    |
| Xbox Live Game Save                                           | XblGameSave       |
| Any other malicious and vulnerable services (backdoors, etc.) |

## Services to Enable:

- BitLocker Drive Encryption Service
- Security Center
- Windows Defender (Service)
- Windows Event Log
- Windows Firewall
- Windows Update
- Any other third-party services to update automatically (Adobe Update Service, Mozilla Maintenance Service, etc.)

**Note:** Depending on your version of Windows and installed features, not all services listed may be available. You may have additional malicious or vulnerable services not listed here. There might also be services required for third-party programs to update automatically. Utilize other resources, such as online research, to identify additional services running on your system.

## Registry Location

Services can be enabled or disabled by changing the DWORD "Start" located in the registry at `HKLM\System\CurrentControlSet\Services\<SERVICENAME>`, replacing `<SERVICENAME>` with the service's official name (not to be confused with display names). For example, the service with the display name "Server" has a service name of "LanmanServer".
