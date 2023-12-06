---
title: Group Policy Security Options
description: 
published: true
tags: curriculum, basic, windows
editor: markdown
---
# Introduction


The security options can be found at the following path in the Local Group Policy Editor: Computer Configuration > Windows Settings > Security Settings > Local Policies > Security Options.

Accounts: Administrator account status

This security setting determines whether the local Administrator account is enabled or disabled.

The default is Disabled, and that is what it should be.

Registry Key: NOT A REGISTRY KEY

Accounts: Guest account status

This security setting determines whether the local Guest account is enabled or disabled.

The default is Disabled, and that is what it should be.

Registry Key: NOT A REGISTRY KEY

Accounts: Limit local account use of blank passwords to console logon only

This security setting determines whether local accounts that are not password protected can be used to log on from locations other than the physical computer console. If enabled, local accounts that are not password protected will only be able to log on at the computer's keyboard.

The default is Enabled, and that is what it should be.

Registry Key: HKLM\System\CurrentControlSet\Control\Lsa\LimitBlankPasswordUse

Audit: Audit the access of global system objects

This security setting determines whether to audit the access of global system objects.

The default is Disabled, however, it should be Enabled.

Registry Key: HKLM\System\CurrentControlSet\Control\Lsa\AuditBaseObjects

Audit: Force audit policy subcategory settings (Windows Vista or later) to override audit policy category settings.

Windows Vista and later versions of Windows allow audit policy to be managed in a more precise way using audit policy subcategories. Setting audit policy at the category level will override the new subcategory audit policy feature. Group Policy only allows audit policy to be set at the category level, and existing group policy may override the subcategory settings of new machines as they are joined to the domain or upgraded to Windows Vista or later versions. To allow audit policy to be managed using subcategories without requiring a change to Group Policy, there is a new registry value in Windows Vista and later versions, SCENoApplyLegacyAuditPolicy, which prevents the application of category-level audit policy from Group Policy and from the Local Security Policy administrative tool.

If the category level audit policy set here is not consistent with the events that are currently being generated, the cause might be that this registry key is set.

The default is Not Defined, however, it should be Enabled.

Registry Key: HKLM\System\CurrentControlSet\Control\Lsa\SCENoApplyLegacyAuditPolicy

Audit: Shut down system immediately if unable to log security audits

This security setting determines whether the system shuts down if it is unable to log security events.

If this security setting is enabled, it causes the system to stop if a security audit cannot be logged for any reason. Typically, an event fails to be logged when the security audit log is full and the retention method that is specified for the security log is either Do Not Overwrite Events or Overwrite Events by Days.

If the security log is full and an existing entry cannot be overwritten, and this security option is enabled, the following Stop error appears:

STOP: C0000244 {Audit Failed}
An attempt to generate a security audit failed.

To recover, an administrator must log on, archive the log (optional), clear the log, and reset this option as desired. Until this security setting is reset, no users, other than a member of the Administrators group will be able to log on to the system, even if the security log is not full.

Note: On Windows versions prior to Windows Vista configuring this security setting, changes will not take effect until you restart Windows.

The default is Disabled, and that is what it should be.

Registry Key: HKLM\System\CurrentControlSet\Control\Lsa\CrashOnAuditFail

Devices: Prevent users from installing print drivers

For a computer to print to a shared printer, the driver for that shared printer must be installed on the local computer. This security setting determines who is allowed to install a printer driver as part of connecting to a shared printer. If this setting is enabled, only Administrators can install a printer driver as part of connecting to a shared printer. If this setting is disabled, any user can install a printer driver as part of connecting to a shared printer.

The default is Disabled, however, it should be Enabled.

Registry Key: HKLM\System\CurrentControlSet\Control\Print\Providers\LanMan Print Services\Servers\AddPrinterDrivers

Devices: Restrict CD-ROM access to locally logged-on user only

This security setting determines whether a CD-ROM is accessible to both local and remote users simultaneously.

If this policy is enabled, it allows only the interactively logged-on user to access removable CD-ROM media. If this policy is enabled and no one is logged on interactively, the CD-ROM can be accessed over the network.

The default is Not Defined, however, it should be Enabled.

Registry Key: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\AllocateCDRoms

Devices: Restrict floppy access to locally logged-on user only

This security setting determines whether removable floppy media are accessible to both local and remote users simultaneously.

If this policy is enabled, it allows only the interactively logged-on user to access removable floppy media. If this policy is enabled and no one is logged on interactively, the floppy can be accessed over the network.

The default is Not Defined, however, it should be Enabled.

Registry Key: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\AllocateFloppies

Domain Member: Digitally encrypt or sign secure channel data (always)

This security setting determines whether all secure channel traffic initiated by the domain member must be signed or encrypted.

If this policy is enabled, then the secure channel will not be established unless either signing or encryption of all secure channel traffic is negotiated.

If this policy is disabled, then encryption and signing of all secure channel traffic is negotiated with the Domain Controller in which case the level of signing and encryption depends on the version of the Domain Controller and the settings of the following two policies:

Domain member: Digitally encrypt secure channel data (when possible)
Domain member: Digitally sign secure channel data (when possible)
The default is Enabled, and that is what it should be.

Registry Key: HKLM\System\CurrentControlSet\Services\Netlogon\Parameters\RequireSignOrSeal

Interactive Logon: Do not display last user name

This security setting determines whether the name of the last user to log on to the computer is displayed in the Windows logon screen. If this policy is enabled, the name of the last user to successfully log on is not displayed in the Logon Screen. If this policy is disabled, the name of the last user to log on is displayed.

The default is Disabled, however, it should be Enabled.

Registry Key: HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System\DontDisplayLastUserName

Interactive Logon: Do not require CTRL+ALT+DEL

This security setting determines whether pressing CTRL+ALT+DEL is required before a user can log on.

If this policy is enabled on a computer, a user is not required to press CTRL+ALT+DEL to log on. Not having to press CTRL+ALT+DEL leaves users susceptible to attacks that attempt to intercept the users' passwords. Requiring CTRL+ALT+DEL before users log on ensures that users are communicating by means of a trusted path when entering their passwords.

If this policy is disabled, any user is required to press CTRL+ALT+DEL before logging on to Windows (unless they are using a smart card for Windows logon).

The default is Enabled, however, it should be Disabled.

Registry Key: HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System\DisableCAD

Interactive Logon: Message text for users attempting to logon

This security setting specifies a text message that is displayed to users when they log on.

This text is often used for legal reasons, for example, to warn users about the ramifications of misusing company information or to warn them that their actions may be audited.

The default is Not Defined, however, it should be the following: "This system is for authorized users only. Auditing and Monitoring may occur."

Registry Key: HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System\LegalNoticeText

Interactive Logon: Message title for users attempting to logon

This security setting allows the specification of a title to appear in the title bar of the window that contains the Interactive logon: Message text for users attempting to log on.

The default is Not Defined, however, it should be the following: "Unauthorized Users Prohibited"

Registry Key: HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System\LegalNoticeCaption

<br>

The security options can be found at the following path in the Local Group Policy Editor: Computer Configuration > Windows Settings > Security Settings > Local Policies > Security Options.

Microsoft network client: Send unencrypted password to third-party SMB servers

If this security setting is enabled, the Server Message Block (SMB) redirector is allowed to send plaintext passwords to non-Microsoft SMB servers that do not support password encryption during authentication.

The default is Disabled, and that is what it should be.

Registry Key: HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\EnablePlainTextPassword

Microsoft network server: Digitally sign communications (always)

This security setting determines whether packet signing is required by the SMB server component.

The server message block (SMB) protocol provides the basis for Microsoft file and print sharing and many other networking operations, such as remote Windows administration. To prevent "man-in-the-middle" attacks that modify SMB packets in transit, the SMB protocol supports the digital signing of SMB packets. This policy setting determines whether SMB packet signing must be negotiated before further communication with an SMB client is permitted.

If this setting is enabled, the Microsoft network server will not communicate with a Microsoft network client unless that client agrees to perform SMB packet signing. If this setting is disabled, SMB packet signing is negotiated between the client and server.

The default is Disabled, however, it should be Enabled.

Registry Key: HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\RequireSecuritySignature

Network access: Allow anonymous SID/Name translation

This policy setting determines whether an anonymous user can request security identifier (SID) attributes for another user.

If this policy is enabled, an anonymous user can request the SID attribute for another user. An anonymous user with knowledge of an administrator's SID could contact a computer that has this policy enabled and use the SID to get the administrator's name. This setting affects both the SID-to-name translation as well as the name-to-SID translation.

If this policy setting is disabled, an anonymous user cannot request the SID attribute for another user.

The default is Disabled, and that is what it should be.

Registry Key: NOT A REGISTRY KEY

Network access: Do not allow anonymous enumeration of SAM accounts

This security setting determines what additional permissions will be granted for anonymous connections to the computer.

Windows allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. This is convenient, for example, when an administrator wants to grant access to users in a trusted domain that does not maintain a reciprocal trust.

This security option allows additional restrictions to be placed on anonymous connections as follows:

Enabled: Do not allow enumeration of SAM accounts. This option replaces Everyone with Authenticated Users in the security permissions for resources. Disabled: No additional restrictions. Rely on default permissions.

The default is Enabled, and that is what it should be.

Registry Key: HKLM\System\CurrentControlSet\Control\Lsa\RestrictAnonymousSAM

Network access: Do not allow anonymous enumeration of SAM accounts and shares

This security setting determines whether anonymous enumeration of SAM accounts and shares is allowed.

Windows allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. This is convenient, for example, when an administrator wants to grant access to users in a trusted domain that does not maintain a reciprocal trust. If you do not want to allow anonymous enumeration of SAM accounts and shares, then enable this policy.

The default is Disabled, however, it should be Enabled.

Registry Key: HKLM\System\CurrentControlSet\Control\Lsa\RestrictAnonymous

Network access: Do not allow storage of passwords and credentials for network authentications

This security setting determines whether Credential Manager saves passwords and credentials for later use when it gains domain authentication.

If you enable this setting, Credential Manager does not store passwords and credentials on the computer. If you disable or do not configure this policy setting, Credential Manager will store passwords and credentials on this computer for later use for domain authentication.

Note: When configuring this security setting, changes will not take effect until you restart Windows.

The default is Disabled, however, it should be Enabled.

Registry Key: HKLM\System\CurrentControlSet\Control\Lsa\DisableDomainCreds

Network access: Let Everyone permissions apply to anonymous users

This security setting determines what additional permissions are granted for anonymous connections to the computer.

Windows allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. This is convenient, for example, when an administrator wants to grant access to users in a trusted domain that does not maintain a reciprocal trust. By Default, the Everyone security identifier (SID) is removed from the token created for anonymous connections. Therefore, permissions granted to the Everyone group do not apply to anonymous users. If this option is set, anonymous users can only access those resources for which the anonymous user has been explicitly given permission.

If this policy is enabled, the Everyone SID is added to the token that is created for anonymous connections. In this case, anonymous users are able to access any resource for which the Everyone group has been given permissions.

The default is Disabled, and that is what it should be.

Registry Key: HKLM\System\CurrentControlSet\Control\Lsa\EveryoneIncludesAnonymous

Network access: Named pipes that can be access anonymously

This security setting determines which communication sessions (pipes) will have attributes and permissions that allow anonymous access.

The default is Not Defined (Blank), and that is what it should be.

Registry Key: HKLM\System\CurrentControlSet\Services\LanManServer\Parameters\NullSessionPipes

Network access: Remotely accessible registry paths

This security setting determines which registry keys can be accessed over the network, regardless of the users or groups listed in the access control list (ACL) of the winreg registry key.

The default is:

System\CurrentControlSet\Control\ProductOptions
System\CurrentControlSet\Control\Server Applications
Software\Microsoft\Windows NT\CurrentVersion
However, this should be Not Defined (Blank)

Registry Key: HKLM\System\CurrentControlSet\Control\SecurePipeServers\Winreg\AllowedPaths\Machine

Network access: Remotely accessible registry paths and sub-paths

This security setting determines which registry paths and subpaths can be accessed over the network, regardless of the users or groups listed in the access control list (ACL) of the winreg registry key.

The default is:

System\CurrentControlSet\Control\Print\Printers
System\CurrentControlSet\Services\Eventlog
Software\Microsoft\OLAP Server
Software\Microsoft\Windows NT\CurrentVersion\Print
Software\Microsoft\Windows NT\CurrentVersion\Windows
System\CurrentControlSet\Control\ContentIndex
System\CurrentControlSet\Control\Terminal Server
System\CurrentControlSet\Control\Terminal Server\UserConfig
System\CurrentControlSet\Control\Terminal Server\DefaultUserConfiguration
Software\Microsoft\Windows NT\CurrentVersion\Perflib
System\CurrentControlSet\Services\SysmonLog
However, this should be Not Defined (Blank)

Registry Key: HKLM\System\CurrentControlSet\Control\SecurePipeServers\Winreg\AllowedPaths\Machine

Network access: Restrict anonymous access to Named Pipes and Shares

When enabled, this security setting restricts anonymous access to shares and pipes to the settings for:

Network access: Named pipes that can be accessed anonymously
Network access: Shares that can be accessed anonymously
The default is Enabled, and that is what it should be.

Registry Key: HKLM\System\CurrentControlSet\Services\LanManServer\Parameters\NullSessionShares

Network access: Shares that can be accessed anonymously

This security setting determines which network shares can accessed by anonymous users.

The default is Not Defined (Blank), and that is what it should be.

Registry Key: HKLM\System\CurrentControlSet\Services\LanManServer\Parameters\NullSessionShares

Network security: Do not store LAN Manager hash value on next password change

This security setting determines if, at the next password change, the LAN Manager (LM) hash value for the new password is stored. The LM hash is relatively weak and prone to attack, as compared with the cryptographically stronger Windows NT hash. Since the LM hash is stored on the local computer in the security database the passwords can be compromised if the security database is attacked.

The default is Enabled, and that is what it should be.

Registry Key: HKLM\System\CurrentControlSet\Control\Lsa\NoLMHash

<br>

The security options can be found at the following path in the Local Group Policy Editor: Computer Configuration > Windows Settings > Security Settings > Local Policies > Security Options.

Recovery Console: Allow automatic administrative logon

This security setting determines if the password for the Administrator account must be given before access to the system is granted. If this option is enabled, the Recovery Console does not require you to provide a password, and it automatically logs on to the system.

The default is Disabled, and that is what it should be.

Registry Key: HKLM\Software\Microsoft\Windows NT\CurrentVersion\Setup\RecoveryConsole\SecurityLevel

Shutdown: Allow system to be shutdown without having to log on

This security setting determines whether a computer can be shut down without having to log on to Windows.

When this policy is enabled, the Shut Down command is available on the Windows logon screen.

When this policy is disabled, the option to shut down the computer does not appear on the Windows logon screen. In this case, users must be able to log on to the computer successfully and have the Shut down the system user right before they can perform a system shutdown.

The default is Enabled, however, it should be Disabled.

Registry Key: HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System\ShutdownWithoutLogon

Shutdown: Clear virtual memory pagefile

This security setting determines whether the virtual memory pagefile is cleared when the system is shut down.

Virtual memory support uses a system pagefile to swap pages of memory to disk when they are not used. On a running system, this pagefile is opened exclusively by the operating system, and it is well protected. However, systems that are configured to allow booting to other operating systems might have to make sure that the system pagefile is wiped clean when this system shuts down. This ensures that sensitive information from process memory that might go into the pagefile is not available to an unauthorized user who manages to directly access the pagefile.

When this policy is enabled, it causes the system pagefile to be cleared upon clean shutdown. If you enable this security option, the hibernation file (hiberfil.sys) is also zeroed out when hibernation is disabled.

The default is Disabled, however, it should be Enabled.

Registry Key: MACHINE\System\CurrentControlSet\Control\Session Manager\Memory Management\ClearPageFileAtShutdown

System objects: Strengthen default permissions of internal system objects

This security setting determines the strength of the default discretionary access control list (DACL) for objects.

Active Directory maintains a global list of shared system resources, such as DOS device names, mutexes, and semaphores. In this way, objects can be located and shared among processes. Each type of object is created with a default DACL that specifies who can access the objects and what permissions are granted.

If this policy is enabled, the default DACL is stronger, allowing users who are not administrators to read shared objects but not allowing these users to modify shared objects that they did not create.

The default is Enabled, and that is what it should be.

Registry Key: MACHINE\System\CurrentControlSet\Control\Session Manager\ProtectionMode

User Account Control: Admin Approval Mode for the Built-In Administrator account

This policy setting controls the behavior of Admin Approval Mode for the built-in Administrator account.

The options are:

Enabled: The built-in Administrator account uses Admin Approval Mode. By default, any operation that requires elevation of privilege will prompt the user to approve the operation.
Disabled: The built-in Administrator account runs all applications with full administrative privilege.
The default is Disabled, however, it should be Enabled

Registry Key: HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\FilterAdministratorToken

User Account Control: Allow UIAccess applications to prompt for elevation without using the secure desktop

This policy setting controls whether User Interface Accessibility (UIAccess or UIA) programs can automatically disable the secure desktop for elevation prompts used by a standard user.

The options are:

Enabled: UIA programs including Windows Remote Assistance can automatically disable the secure desktop for elevation prompts. Unless you have also disabled elevation prompts, the prompts will appear on the interactive user's desktop instead of the secure desktop.
Disabled: the secure desktop can only be disabled by the user of the interactive desktop or by disabling the "User Account Control: Switch to the secure desktop when prompting for elevation" setting.
The default is Disabled, and that is what it should be.

Registry Key: HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\EnableUIADesktopToggle

User Account Control: Behavior of the elevation prompt for administrators in Admin Approval Mode

This policy setting controls the behavior of the elevation prompt for administrators.

The options are:

Elevate without prompting: Allows privileged accounts to perform an operation that requires elevation without requiring consent or credentials. Note: Use this option only in the most constrained environments.
Prompt for credentials on the secure desktop: When an operation requires elevation of privilege, the user is prompted on the secure desktop to enter a privileged user name and password. If the user enters valid credentials, the operation continues with the user's highest available privilege.
Prompt for consent on the secure desktop: When an operation requires elevation of privilege, the user is prompted on the secure desktop to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege.
Prompt for credentials: When an operation requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege.
Prompt for consent: When an operation requires elevation of privilege, the user is prompted to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege.
Prompt for consent for non-Windows binaries: (Default) When an operation for a non-Microsoft application requires elevation of privilege, the user is prompted on the secure desktop to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege.
The default is Prompt for consent for non-Windows binaries, however, it should be Prompt for consent on the secure desktop.

Registry Key: HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\ConsentPromptBehaviorAdmin

User Account Control: Behavior of the elevation prompt for standard users

This policy setting controls the behavior of the elevation prompt for standard users.

The options are:

Prompt for credentials: When an operation requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege.
Automatically deny elevation requests: When an operation requires elevation of privilege, a configurable access denied error message is displayed. An enterprise that is running desktops as standard user may choose this setting to reduce help desk calls.
Prompt for credentials on the secure desktop: (Default) When an operation requires elevation of privilege, the user is prompted on the secure desktop to enter a different user name and password. If the user enters valid credentials, the operation continues with the applicable privilege.
The default is Prompt for credentials on the secure desktop, and that is what it should be.

Registry Key: HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\ConsentPromptBehaviorUser

User Account Control: Run all administrators in Admin Approval Mode

This policy setting controls the behavior of all User Account Control (UAC) policy settings for the computer. If you change this policy setting, you must restart your computer.

The options are:

Enabled: (Default) Admin Approval Mode is enabled. This policy must be enabled and related UAC policy settings must also be set appropriately to allow the built-in Administrator account and all other users who are members of the Administrators group to run in Admin Approval Mode.
Disabled: Admin Approval Mode and all related UAC policy settings are disabled. Note: If this policy setting is disabled, the Security Center notifies you that the overall security of the operating system has been reduced.
The default is Enabled, and that is what it should be.

Registry Key: HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\EnableLUA

User Account Control: Switch to the secure desktop when prompting for elevation

This policy setting controls whether the elevation request prompt is displayed on the interactive user's desktop or the secure desktop.

The options are:

Enabled: (Default) All elevation requests go to the secure desktop regardless of prompt behavior policy settings for administrators and standard users.
Disabled: All elevation requests go to the interactive user's desktop. Prompt behavior policy settings for administrators and standard users are used.
The default is Enabled, and that is what it should be.

Registry Key: HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\PromptOnSecureDesktop

<br>

Add the 8 items listed in the table below with the Recommend Settings.

To help prevent denial of service (DoS) attacks, keep your computer updated with the latest security fixes and harden the TCP/IP protocol stack on your Windows Server 2003-based and Windows Vista-based computers that are exposed to potential attackers. The default TCP/IP stack configuration is tuned to handle standard intranet traffic. If you connect a computer directly to the Internet, we recommend that you harden the TCP/IP stack to protect against DoS attacks.

DoS attacks that are directed at the TCP/IP stack tend to be of two classes: attacks that use an excessive number of system resources (one way to do this is to open numerous TCP connections) or attacks that send specially crafted packets that cause the network stack or the entire operating system to fail. The following registry settings help to protect against the attacks that are directed at the TCP/IP stack.

The registry settings in the following table can be added to the HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Tcpip\Parameters\ subkey.

More detailed information about each of the settings is provided in the subsections that follow the table and in Microsoft Windows Server 2003 TCP/IP Implementation Details (http://go.microsoft.com/fwlink/?LinkID=59670).

Note

Windows Vista is the first operating system to implement next-generation TCP/IP support, which improves the reliability and connectivity of both IPv4 and IPv6 networks.

Registry entry	Format	Windows Vista default setting	Windows Server 2003 default setting	Recommended setting
DisableIPSourceRouting	DWORD	Not available	1	2
EnableDeadGWDetect	DWORD	Not available	1	0
EnabledICMPRedirect	DWORD	Not available	1	0
KeepAliveTime	DWORD	Not available	1	2
PerformRouterDiscover	DWORD	Not available	2	0
SynAttackProtect	DWORD	Not available	1	1
TCPMaxConnectReponseRetransmissions	DWORD	Not available	2	1
TCPMaxDatRetransmissions	DWORD	Not available	5	3
DisableIPSourceRouting
This entry appears as MSS: (DisableIPSourceRouting) IP source routing protection level (protects against packet spoofing) in the Group Policy Object Editor. IP source routing is a mechanism that allows the sender to determine the IP route that a datagram should follow through the network.

Possible values:

Registry value	Corresponding Group Policy Object Editor option
0	No additional protection, source routed packets are allowed
1	Medium, source routed packets ignored when IP forwarding is enabled
2	Highest protection, source routing is completely disabled
<Null>	Not Defined
The default configuration in Windows Server 2003 is 1.

Vulnerability

Source routing allows a computer that sends a packet to specify the route that the packet takes. Attackers can use source routed packets to obscure their identity and location.

Countermeasure

Configure the DisableIPSourceRouting entry to a value of 2.

Potential impact

If you configure this value to 2, all incoming source routed packets will be dropped.

EnableDeadGWDetect
This entry appears as MSS: (EnableDeadGWDetect) Allow automatic detection of dead network gateways (could lead to DoS) in Group Policy Object Editor. When this setting is enabled, the IP may change to a backup gateway if a number of connections experience difficulty.

Possible values:

Registry value	Corresponding Group Policy Object Editor option
0	Disabled
1	Enabled
<Null>	Not Defined
The default configuration is 1 (enabled) on Windows Server 2003.

Vulnerability

An attacker could force the server to switch gateways, potentially to an unintended one. This would be very difficult to do, so the amount of additional security imparted by implementing this setting is minimal.

Countermeasure

Configure the EnableDeadGWDetect entry to 0 - Disabled.

Potential impact

If you configure this value to 0, Windows cannot detect dead gateways and automatically switches to alternate gateways.

EnableICMPRedirect
This entry appears as MSS: (EnableICMPRedirect) Allow ICMP redirects to override OSPF generated routes in the Group Policy Object Editor. Internet Control Message Protocol (ICMP) redirects cause the stack to plumb host routes. These routes override the Open Shortest Path First (OSPF)-generated routes.

Possible values:

Registry value	Corresponding Group Policy Object Editor option
0	Disabled
1	Enabled
<Null>	Not Defined
The default configuration is 1 (enabled).

Vulnerability

This behavior is expected. The problem is that the 10 minute timeout period for the ICMP redirect-plumbed routes temporarily creates a network situation in which traffic is not routed properly for the affected host.

Countermeasure

Configure the EnableICMPRedirect entry to 0 (disabled).

Potential impact

When Routing and Remote Access Service (RRAS) is configured as an autonomous system boundary router (ASBR), it does not correctly import connected interface subnet routes. Instead, this router injects host routes into the OSPF routes. However, the OSPF router cannot be used as an ASBR router, and when connected interface subnet routes are imported into OSPF, the result is confusing routing tables with strange routing paths that can result in higher network latency and inability to connect to network resources.

KeepAliveTime
This entry appears as MSS: (KeepAliveTime) How often keep-alive packets are sent in milliseconds (300,000 is recommended) in the Group Policy Object Editor and is stored in the HKLM\System\CurrentControlSet\Services|Tcpip\Parameters\KeepAliveTime registry key. This setting controls how often TCP sends a keep-alive packet to verify that an idle connection is still intact. If the remote computer is still reachable, it acknowledges the keep-alive packet.

Possible values:

Registry value	Corresponding Group Policy Object Editor option
150000	150000 or 2.5 minutes
300000	300000 or 5 minutes (recommended)
600000	600000 or 10 minutes
1200000	1200000 or 20 minutes
2400000	2400000 or 40 minutes
3600000	3600000 or 1 hour
7200000	7200000 or 2 hours (default value)
<Null>	Not Defined
You can specify settings with values 1 through 0xFFFFFFFF in the registry. The values identified in the Group Policy Object Editor UI and in the preceding table are provided as an aid in choosing the most useful keep-alive time periods. The default configuration is 7,200,000 (two hours).

Vulnerability

An attacker who is able to connect to network applications could establish numerous connections to cause a DoS condition.

Countermeasure

Configure the KeepAliveTime entry to a value of 300000 or 5 minutes.

Potential impact

Keep-alive packets are not sent by default by Windows. However, some applications may configure the TCP stack flag that requests keep-alive packets. For such configurations, lowering this value from the default setting of two hours to five minutes helps disconnect inactive sessions more quickly.

PerformRouterDiscovery
This entry appears as MSS: (PerformRouterDiscovery) Allow IRDP to detect and configure Default Gateway addresses (could lead to DoS) in the Group Policy Object Editor. It enables or disables the Internet Router Discovery Protocol (IRDP). IRDP allows the computer to detect and configure default gateway addresses automatically (as described in RFC 1256) on a per-interface basis.

Possible values:

Registry value	Corresponding Group Policy Object Editor option
0	0 (Disabled)
1	1 (Enabled)
2	2 (enable only if DHCP sends the Perform Router Discovery option)
<Null>	Not Defined
The default configuration is 2.

Vulnerability

An attacker who has gained control of a computer on the same network segment as a router could configure a computer on the network to impersonate the router. Other computers with IRDP enabled would then attempt to route their traffic through the already compromised computer.

Countermeasure

Configure the PerformRouterDiscovery entry to a value of 0 - Disabled.

Potential impact

If you disable this entry, Windows Server 2003 (which supports the IRDP) cannot automatically detect and configure default gateway addresses on the computer.

SynAttackProtect
This entry appears as MSS: (SynAttackProtect) Syn attack protection level (protects against DoS) in the Group Policy Object Editor. This entry causes TCP to adjust retransmission of SYN-ACKs. When you configure this entry, the overhead of incomplete transmissions in a connect request (SYN) attack is reduced.

You can use this entry to configure Windows to send router discovery messages as broadcasts instead of multicasts, as described in RFC 1256. By default, if router discovery is enabled, router discovery solicitations are sent to the all-routers multicast group (224.0.0.2).

Possible values:

Registry value	Corresponding Group Policy Object Editor option
0	No additional protection, use default settings
1	Connections time out more quickly if a SYN attack is detected
<Null>	Not Defined
The default configuration is 1 for Windows Server 2003 with Service Pack 1 (SP1).

Vulnerability

In a SYN flood attack, the attacker sends a continuous stream of SYN packets to a server. The server leaves the half-open connections open until it is overwhelmed and is no longer able to respond to legitimate requests

Countermeasure

Configure SynAttackProtect entry to a value 1.

Potential impact

Configuring this setting to 1 adds more delays to connection indications, and TCP connection requests quickly time out when a SYN attack is in progress. If you configure this registry entry, the scalable windows and TCP parameters that are configured on each adapter (including Initial Round Trip Time (RTT) and window size), socket options no longer work. When the computer is attacked, the scalable windows (RFC 1323) and per-adapter configured TCP parameters (Initial RTT, window size) options on any socket can no longer be enabled. These options cannot be enabled because when protection is functioning, the route cache entry is not queried before the SYN-ACK is sent and the Winsock options are not available at this stage of the connection.

TcpMaxConnectResponseRetransmissions
This entry appears as MSS: (TcpMaxConnectResponseRetransmissions) SYN-ACK retransmissions when a connection request is not acknowledged in the Group Policy Object Editor. This entry determines the number of times that TCP retransmits a SYN before it aborts the attempt. The retransmission timeout is doubled with each successive retransmission in a given connect attempt. The initial timeout value is three seconds.

Possible values:

Registry value	Corresponding Group Policy Object Editor option
0	No retransmission, half-open connections dropped after 3 seconds
1	3 seconds, half-open connections dropped after 9 seconds
2	3 & 6 seconds, half-open connections dropped after 21 seconds
3	3, 6, & 9 seconds, half-open connections dropped after 45 seconds
<Null>	Not Defined
The default configuration is 1.

Vulnerability

In a SYN flood attack, the attacker sends a continuous stream of SYN packets to a server. The server leaves the half-open connections open until it is overwhelmed and no longer is able to respond to legitimate requests.

Countermeasure

Configure the TcpMaxConnectResponseRetransmissions entry to 1.

Potential impact

If you configure this value to greater than or equal to 2, the stack will employ SYN-ATTACK protection internally. If you configure this entry to less than 2, the stack cannot read the registry values at all for SYN-ATTACK protection. This entry shortens the default amount of time that is needed to close a half-open TCP connection. If you are administering a site that is routinely under heavy attack, you might benefit from setting the value to 1 or 0. However, if this parameter is set to 0, SYN-ACKs will not be retransmitted at all and will time out in three seconds. When using such a limited response time, there is a chance that legitimate connection attempts from distant clients may fail.

TcpMaxDataRetransmissions
This entry appears as MSS: (TcpMaxDataRetransmissions) How many times unacknowledged data is retransmitted (3 recommended, 5 is default) in the Group Policy Object Editor. This entry controls the number of times that TCP retransmits an individual data segment (non-connect segment) before it aborts the connection. The retransmission timeout is doubled with each successive retransmission on a connection. It is reset when responses resume. The base timeout value is dynamically determined by the measured round-trip time on the connection.

Possible values:

0 to 0xFFFFFFFF
The default configuration is 5.

In the Group Policy Object Editor UI, this setting can be adjusted using a text entry box:

A user-defined number
Not Defined
Vulnerability

A malicious user could exhaust a target computer's resources if it never sent any acknowledgment messages for data that was transmitted by the target computer.

Countermeasure

Configure the TcpMaxDataRetransmissions entry to a value of 3.

Potential impact

TCP starts a retransmission timer when each outbound segment is passed to the IP. If no acknowledgment is received for the data in a given segment before the timer expires, the segment is retransmitted up to three times.