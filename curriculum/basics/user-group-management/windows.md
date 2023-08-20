---
title: User and Group Management for Windows
description: 
published: true
date: 2023-07-15T14:43:11.474Z
tags: curriculum, basic, user management, group management, windows
editor: markdown
dateCreated: 2023-07-15T14:42:04.653Z
---

# User Management

<br>

## Navigating to Computer Management
To manage Windows user navigate to computer management by pressing

<kbd>WINDOWS KEY + R</kbd>

Then typing `compmgmt.msc` into the Windows Run box that appears in the bottom left

![compmgmt.png](/documents/compmgmt.png =x300)

In Computer Management navigate to the `Local User and Groups` section on the left and then click on the `Users` folder

![usermgmt.png](/documents/usermgmt.png =x400)

From here you can now mange all Users who are present on the system.

> The remaining notes assume you present within the Users tab in Computer Managment following the above instructions.
{.is-success}


<br>

## Remove Unauthorized users

Each Cyber Patriot competition will have a list of authorized users located in a gray block within the Read Me link located on the Desktop of the VM. You should verify the list of authorized user/adminsitrators to the actual list of user. If you find an unauthorized user you should disable the account.

Disable an account:
1. Right click on the User
2. Click `Properties`
3. Check `Account is disabled`
4. Click `Okay`


Delete an account:
1. Right click on the User
2. Click `Delete`
4. Click `Yes`




> Typically we only disable accounts for Cyber Patriot so you can restore the account very easily if needed.
{.is-info}

<br>

## Securing a User account

In order to secure a user account you should set a secure password, ensure no unsecure settings are enabled (e.g. Password never Expires), and force the user to change their password on next logon.

You should perform these actions for all authorized users and administrators except your active user.

<br>

### Setting a User password

> DO NOT change your user's (the default user) password. If you change your password you may lock your self out and brake the VM.
{.is-warning}

Within Computer Management
1. Right click on the User
2. Click `Set Password`
3. Enter a secure password.
4. Click `Okay`


> For the purposes of Cyber Patriot you should write down this password. It is also recommended to use the same password for all accounts.
These are bad practices outside of the Cyber Patriot competition.
{.is-info}

### Disabling Unsecure Settings

Within Computer management:
1. Right click on the User
2. Click `Properties`
3. Uncheck `Password never expires`
4. Check the `User must change password at next logon`
5. Click `Okay`


<br>

## Securing or disable the Guest account

Guest accounts are meant to be used by everyone other than authorized users. This means anyone could access the system. By default, these accounts have very limited access to the system, however, they can be given more permission than required. It is best practice to disable this account if it is not required.

For CyberPatriot, unless the specifically state in the README to allow guests, you should disable this account. If the README says to allow guests, secure it as much as possible.

To disable the account from within Computer Management:
1. Right click on Guest
2. Click `Properties`
3. Check `Account is disabled`.
4. Click `Okay`

To secure the guest account:
1. Right click on Guest
2. Click `Properties`
3. Navigate to the `Member Of` tab
4. Verify only the **Guests** group exists
5. If other Groups exists not specified by the Read Me for each:
    1. Click the Group
2. Click `Remove`
6. Click `Okay`

<br>

## Creating a User

Occasionally the Cyber Patriot Read Me may require you to create a new User. They will provide you with the name of the User and what permissions they should have.

Create the User Account:
1. Click `More Actions` located under the `Users` heading in `Actions` panel
2. Click `New User`
3. Fill in the username provided from the Read Me
4. Enter a secure password
5. Check `User must change password at next logon`

Follow  to provision access through groups.

<br>

## Checklist
- [ ] Verify only authorized users exist.
- [ ] Set a secure password for each users.
- [ ] Ensure the Password never expire setting is NOT set for any user.
- [ ] Force a password reset on next logon for each user
- [ ] Secure the Guest account
- [ ] Create Users if specified in the Read Me

<br>

# Group Management

<br>

## Navigating to Computer Management
To manage Windows user navigate to computer management by pressing

<kbd>WINDOWS KEY + R</kbd>

Then typing `compmgmt.msc` into the Windows Run box that appears in the bottom left

![compmgmt.png](/documents/compmgmt.png =x300)

In Computer Management navigate to the `Local User and Groups` section on the left and then click on the `Groups` folder

![groupmgmgt.png](/documents/groupmgmgt.png =x400)

From here you can now mange all Groups present on the system.

> The remaining notes assume you present within the Groups tab in Computer Managment following the above instructions.
{.is-success}

<br>

## Audit Group Members
Ensuring account types are set correctly is very important. A standard user accidentally given administrative permissions can accidentally or purposefully cause significant damage to a system because they would have access to all files on the system, not just their own.

You should review all Groups to ensure no unauthorized users exist, but the main group to review should be the **Administrators** group; only those users who exists in the `Administrator` section of the read me should be in this group.

Removing a User from a Group:
1. Double click the Group
2. Select the unathorized User
3. Click `Remove`
4. Click `Okay`

Add a User to a Group:
1. Double click the Group
2. Click `Add`
3. Enter the name of the User to add in the text box
4. Click `Check Names` to ensure the user exists
5. Click `Okay`

<br>

## Create a new Group
Occasionally, you may be required to provision a new group. If you are required to do this the Read Me will tell you what to name the group and which users to add to the group.

Create a new Group:
1. Click `More Actions` located under the `Groups` heading in `Actions` panel
2. Click `New Group`
3. Fill in the group name provided from the Read Me
4. Click `Create`

<br>

## Checklist
- [ ] Verify groups only contain the authorized users for that group
- [ ] Add missing users to groups
- [ ] Create groups if specified in Read Me

