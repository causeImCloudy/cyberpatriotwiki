---
title: Group Policy
description: 
published: true
tags: curriculum, basic, windows
editor: markdown
---
# Introduction

# Computer Policies

## Password Policy
Enforce Password History

This policy enables administrators to enhance security by ensuring that old passwords are not reused continually.

This security setting determines the number of unique new passwords that have to be associated with a user account before an old password can be reused. The value must be between 0 and 24 passwords.

The default is 0, however it should be set to at least 8.

Command Prompt Command: net accounts /uniquepw:NUMBER

Maximum Password Age

This security setting determines the period of time (in days) that a password can be used before the system requires the user to change it. You can set passwords to expire after a number of days between 1 and 999, or you can specify that passwords never expire by setting the number of days to 0. If the maximum password age is between 1 and 999 days, the Minimum password age must be less than the maximum password age. If the maximum password age is set to 0, the minimum password age can be any value between 0 and 998 days.

It is a security best practice to have passwords expire every 30 to 90 days, depending on your environment. This way, an attacker has a limited amount of time in which to crack a user's password and have access to your network resources.

The default is 0, however it should be set between 30 and 60.

Command Prompt Command: net accounts /maxpwage:DAYS

Minimum Password Age

This security setting determines the period of time (in days) that a password must be used before the user can change it. You can set a value between 1 and 998 days, or you can allow changes immediately by setting the number of days to 0.

The minimum password age must be less than the Maximum password age, unless the maximum password age is set to 0, indicating that passwords will never expire. If the maximum password age is set to 0, the minimum password age can be set to any value between 0 and 998.

Configure the minimum password age to be more than 0 if you want Enforce password history to be effective. Without a minimum password age, users can cycle through passwords repeatedly until they get to an old favorite. The default setting does not follow this recommendation, so that an administrator can specify a password for a user and then require the user to change the administrator-defined password when the user logs on. If the password history is set to 0, the user does not have to choose a new password. For this reason, Enforce password history is set to 1 by default.

The default is 0, however it should be set between 5 and 10.

Command Prompt Command: net accounts /minpwage:NUMBER

Minimum Password Length

This security setting determines the least number of characters that a password for a user account may contain. You can set a value of between 1 and 14 characters, or you can establish that no password is required by setting the number of characters to 0.

The default is 0, however it should be set to at least 10.

Command Prompt Command: net accounts /minpwlen:LENGTH

Passwords must meet complexity requirements

This security setting determines whether passwords must meet complexity requirements.

If this policy is enabled, passwords must meet the following minimum requirements:

Not contain the user's account name or parts of the user's full name that exceed two consecutive characters
Be at least six characters in length
Contain characters from three of the following four categories:
English uppercase characters (A through Z)
English lowercase characters (a through z)
Base 10 digits (0 through 9)
Non-alphabetic characters (for example, !, $, #, %)
Complexity requirements are enforced when passwords are changed or created.

The default is Disabled, however it should be set to Enabled.

Store passwords using reversible encryption

This security setting determines whether the operating system stores passwords using reversible encryption.

This policy provides support for applications that use protocols that require knowledge of the user's password for authentication purposes. Storing passwords using reversible encryption is essentially the same as storing plaintext versions of the passwords. For this reason, this policy should never be enabled unless application requirements outweigh the need to protect password information.

This policy is required when using Challenge-Handshake Authentication Protocol (CHAP) authentication through remote access or Internet Authentication Services (IAS). It is also required when using Digest Authentication in Internet Information Services (IIS).

The default is Disabled, and it is supposed to be set to Disabled.

<br>

## Account Policies 

Account Lockout Duration

This security setting determines the number of minutes a locked-out account remains locked out before automatically becoming unlocked. The available range is from 0 minutes through 99,999 minutes. If you set the account lockout duration to 0, the account will be locked out until an administrator explicitly unlocks it.

If an account lockout threshold is defined, the account lockout duration must be greater than or equal to the reset time.

The default is None, because this policy setting only has meaning when an Account lockout threshold is specified. It should be set to 30 minutes, once the threshold has been set.

Command Prompt Command: net accounts /lockoutduration:MINUTES

Account Lockout Threshold

This security setting determines the number of failed logon attempts that causes a user account to be locked out. A locked-out account cannot be used until it is reset by an administrator or until the lockout duration for the account has expired. You can set a value between 0 and 999 failed logon attempts. If you set the value to 0, the account will never be locked out.

Failed password attempts against workstations or member servers that have been locked using either CTRL+ALT+DELETE or password-protected screen savers count as failed logon attempts.

The default is 0, however it should be set to at least 5.

Command Prompt Command: net accounts /lockoutthreshold:ATTEMPTS

Reset account lockout counter after

This security setting determines the number of minutes that must elapse after a failed logon attempt before the failed logon attempt counter is reset to 0 bad logon attempts. The available range is 1 minute to 99,999 minutes.

If an account lockout threshold is defined, this reset time must be less than or equal to the Account lockout duration.

The default is None, because this policy setting only has meaning when an Account lockout threshold is specified. It should be set to 30 minutes, once the threshold has been set.

Command Prompt Command: net accounts /lockoutwindow:MINUTES

<br>

## Windows Defender Firewall with Advanced Security

Computer Configuration > Windows Settings > Security Settings > Windows Firewall with Advanced Security > Windows Firewall with Advanced Security - Local Group Policy Object

In the right panel, click Windows Firewall Properties under the Overview section.

Set the following for Domain Profile, Private Profile, and Public Profile:

Firewall State: On (Recommended)
Inbound connections: Block (default)
Outbound connections: Allow (default)
Logging > Name: %systemroot%\system32\logfiles\firewall\pfirewall.log
Logging > Size limit (KB): 4,096
Uncheck Not configured on both options
Logging > Log dropped packets: Yes
Logging > Log successful connections: Yes

## Administrative Templates
Check All Previously Configured Settings

Within both Computer Configuration and User Configuration, go to All Settings within the Administrative Templates.

Sort the State column so the Enabled/Disabled items are at the top of the list.

Review the list of settings and change the incorrectly configured settings.

Turn Off AutoPlay

The Turn Off AutoPlay policy can be found at the following path in the Local Group Policy Editor: Computer Configuration > Administrative Templates > Windows Components > AutoPlay Policies

This policy setting allows you to turn off the Autoplay feature.

Autoplay begins reading from a drive as soon as you insert media in the drive. As a result, the setup file of programs and the music on audio media start immediately.

Prior to Windows XP SP2, Autoplay is disabled by default on removable drives, such as the floppy disk drive (but not the CD-ROM drive), and on network drives.

Starting with Windows XP SP2, Autoplay is enabled for removable drives as well, including Zip drives and some USB mass storage devices.

If you enable this policy setting, Autoplay is disabled on CD-ROM and removable media drives, or disabled on all drives.

This policy setting disables Autoplay on additional types of drives. You cannot use this setting to enable Autoplay on drives on which it is disabled by default.

If you disable or do not configure this policy setting, AutoPlay is enabled.

Note: This policy setting appears in both the Computer Configuration and User Configuration folders. If the policy settings conflict, the policy setting in Computer Configuration takes precedence over the policy setting in User Configuration.

The default is not configured, however, it should be set to Enabled and the option set to All Drives.

Registry Item: HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\NoDriveTypeAutoRun

Enumerate administrator accounts on elevation

The Credential User Interface policies can be found at the following path in the Local Group Policy Editor: Computer Configuration > Administrative Templates > Windows Components > Credential User Interface

This policy setting controls whether administrator accounts are displayed when a user attempts to elevate a running application. By default, administrator accounts are not displayed when the user attempts to elevate a running application.

If you enable this policy setting, all local administrator accounts on the PC will be displayed so the user can choose one and enter the correct password.

If you disable this policy setting, users will always be required to type a user name and password to elevate.

The default is not configured, however, it should be set to Disabled.

Registry Item: HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\CredUI\EnumerateAdministrators

Turn Off Desktop Gadgets

The Turn Off Desktop Gadgets policy can be found at the following path in the Local Group Policy Editor: Computer Configuration > Administrative Templates > Windows Components > Desktop Gadgets

This policy setting allows you to turn off desktop gadgets. Gadgets are small applets that display information or utilities on the desktop.

If you enable this setting, desktop gadgets will be turned off.

If you disable or do not configure this setting, desktop gadgets will be turned on.

The default is not configured, however, it should be set to Enabled.

Registry Item: HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\Windows\Sidebar\TurnOffSidebar

Configure Windows SmartScreen

The SmartScreen policies can be found at the following path in the Local Group Policy Editor: Computer Configuration > Administrative Templates > Windows Components > File Explorer

This policy setting allows you to manage the behavior of Windows SmartScreen. Windows SmartScreen helps keep PCs safer by warning users before running unrecognized programs downloaded from the Internet. Some information is sent to Microsoft about files and programs run on PCs with this feature enabled. If you enable this policy setting, Windows SmartScreen behavior may be controlled by setting one of the following options: Require approval from an administrator before running downloaded unknown software, Give user a warning before running downloaded unknown software or Turn off SmartScreen. If you disable or do not configure this policy setting, Windows SmartScreen behavior is managed by administrators on the PC by using Windows SmartScreen Settings in Action Center.

The default is not configured, however, it should be set to Enabled.

Registry Item: HKLM\Software\Policies\Microsoft\Windows\System!EnableSmartScreen

HKLM\Software\Policies\Microsoft\Windows\System\ShellSmartScreenLevel

Do not allow supported Plug and Play device redirection

The Do not allow supported Plug and Play device redirection policy can be found at the following path in the Local Group Policy Editor: Computer Configuration > Administrative Templates > Windows Components > Remote Desktop Services > Remote Desktop Session Host > Device and Resource Redirection

This policy setting lets you control the redirection of supported Plug and Play and RemoteFX USB devices, such as Windows Portable Devices, to the remote computer in a Remote Desktop Services session.

By default, Remote Desktop Services does not allow redirection of supported Plug and Play and RemoteFX USB devices.

If you disable this policy setting, users can redirect their supported Plug and Play devices to the remote computer. Users can use the More option on the Local Resources tab of Remote Desktop Connection to choose the supported Plug and Play devices to redirect to the remote computer.

If you enable this policy setting, users cannot redirect their supported Plug and Play devices to the remote computer.If you do not configure this policy setting, users can redirect their supported Plug and Play devices to the remote computer only if it is running Windows Server 2012 R2 and earlier versions.

Note: You can disable redirection of specific types of supported Plug and Play devices by using Computer Configuration\Administrative Templates\System\Device Installation\Device Installation Restrictions policy settings.

The default is not configured, however, it should be set to Enabled.

Registry Item: HKLM\SOFTWARE\Policies\Microsoft\Windows NT\Terminal Services\fDisablePNPRedir

Require Secure RPC Communication

The Require Security RPC Communication policy can be found at the following path in the Local Group Policy Editor: Computer Configuration > Administrative Templates > Windows Components > Remote Desktop Services > Remote Desktop Session Host > Security

Specifies whether a Remote Desktop Session Host server requires secure RPC communication with all clients or allows unsecured communication.

You can use this setting to strengthen the security of RPC communication with clients by allowing only authenticated and encrypted requests.

If the status is set to Enabled, Remote Desktop Services accepts requests from RPC clients that support secure requests, and does not allow unsecured communication with untrusted clients.

If the status is set to Disabled, Remote Desktop Services always requests security for all RPC traffic. However, unsecured communication is allowed for RPC clients that do not respond to the request.

If the status is set to Not Configured, unsecured communication is allowed.

Note: The RPC interface is used for administering and configuring Remote Desktop Services.

The default is not configured, however, it should be set to Enabled.

Registry Item: HKLM\SOFTWARE\Policies\Microsoft\Windows NT\Terminal Services\EncryptRPCTraffic

## Audit Policies

The audit policies can be found at the following path in the Local Group Policy Editor: Computer Configuration > Windows Settings > Security Settings > Local Policies > Audit Policy

Audit Account Logon Events

This security setting determines whether the OS audits each time this computer validates an account’s credentials.

Account logon events are generated whenever a computer validates the credentials of an account for which it is authoritative. Domain members and non-domain-joined machines are authoritative for their local accounts; domain controllers are all authoritative for accounts in the domain. Credential validation may be in support of a local logon, or, in the case of an Active Directory domain account on a domain controller, may be in support of a logon to another computer. Credential validation is stateless so there is no corresponding logoff event for account logon events.

The default is not auditing, however, it should be set to Success and Failure.

Audit Account Management

This security setting determines whether to audit each event of account management on a computer. Examples of account management events include:

A user account or group is created, changed, or deleted.
A user account is renamed, disabled, or enabled.
A password is set or changed.
The default is not auditing, however, it should be set to Success and Failure.

Audit Logon Events

This security setting determines whether the OS audits each instance of a user attempting to log on to or to log off to this computer.

Log off events are generated whenever a logged on user account's logon session is terminated.

The default is not auditing, however, it should be set to Success and Failure.

Audit Policy Change

This security setting determines whether the OS audits each instance of attempts to change user rights assignment policy, audit policy, account policy, or trust policy.

The default is not auditing, however, it should be set to Success and Failure.

Audit Process Tracking

This security setting determines whether the OS audits process-related events such as process creation, process termination, handle duplication, and indirect object access.

The default is not auditing, however, it should be set to Success and Failure.

Audit System Events

This security setting determines whether the OS audits any of the following events:

Attempted system time change
Attempted security system startup or shutdown
Attempt to load extensible authentication components
Loss of audited events due to auditing system failure
Security log size exceeding a configurable warning threshold level.
The default is not auditing, however, it should be set to Success and Failure.

## User Rights Assignments
The audit policies can be found at the following path in the Local Group Policy Editor: Computer Configuration > Windows Settings > Security Settings > Local Policies > User Rights Assignments\

Access this computer from the network

This user right determines which users and groups are allowed to connect to the computer over the network. Remote Desktop Services are not affected by this user right.

The default is "Administrators, Backup Operators, Users, Everyone", but it should NOT contain "Everyone"

Create global objects

This security setting determines whether users can create global objects that are available to all sessions. Users can still create objects that are specific to their own session if they do not have this user right. Users who can create global objects could affect processes that run under other users' sessions, which could lead to application failure or data corruption.

The default is "Administrators, LOCAL SERVICE, NETWORK SERVICE, & SERVICE", and that is what it should be.

Deny access to this computer from the network

This security setting determines which users are prevented from accessing a computer over the network. This policy setting supersedes the Access this computer from the network policy setting if a user account is subject to both policies.

The default is "Guest", and that is what it should be.

Manage auditing and security log

This security setting determines which users can specify object access auditing options for individual resources, such as files, Active Directory objects, and registry keys.

The default is "Administrators", and that is what it should be.

User Rights Assignments Policy security settings are not registry keys.

## Advanced Audit Policies
The audit policies can be found at the following path in the Local Group Policy Editor: Computer Configuration > Windows Settings > Security Settings > Advanced Audit Policy Configuration > System Audit Policies.

Set all the audit policies under the following sub-categories should be set to audit Success and Failure:

Account Logon
Account Management
Logon/Logoff
Object Access
Policy Change
Privilege Use
System

# User Policies

Unless required by the ReadMe you should always us computer policies. By default, the user policy is run after computer policy therefore it is the policy that remains if there is a conflict between the computer policy and the user policy. 

The policy settings are identical to computer policies, refer to the above section for the topic you are attempting to review. 


