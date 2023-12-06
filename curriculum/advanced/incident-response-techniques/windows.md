---
title: Windows
description: 
published: true
date: 2023-06-30T20:14:49.863Z
tags: curriculum, advanced, active directory
editor: markdown
dateCreated: 2023-06-30T20:14:47.681Z
---
# Introduction

Here are a collection of techniques or procedures you can use to find information for Forensic questions or just investigating the system.


## Get SID of a Local User

In a Windows environment, each user is assigned a unique identifier known as a Security ID (SID). This SID is crucial for controlling access to various resources such as files, registry keys, and network shares. You can obtain the SID of a user using the `WMIC USERACCOUNT` command.

To retrieve the SID of a specific user, follow these steps in a command prompt window:

1. Open a command prompt.

2. Enter the following command, replacing `USERNAME` with the username of the user whose SID you want to obtain:

```
wmic useraccount where name='USERNAME' get sid
```

## Finding Who Created/Modified/Deleted An Object (File or Folder)
In Windows Event Viewer, you can access the Security Log to review important security-related events. One event of interest is **Event ID 4663**, which corresponds to "An attempt was made to access an object." This event provides valuable information about access attempts to various objects on your system.

To analyze Event ID 4663 and understand which permissions were exercised during the event, follow these steps:

1. Open **Event Viewer**:

   - Press `Win + R` to open the Run dialog.
   - Type `eventvwr.msc` and press Enter.

2. In Event Viewer, expand the "Windows Logs" section and select **Security**. This is where you'll find security-related events.

3. Filter for Event ID 4663:

   - In the right-hand pane, click on **Filter Current Log**.
   - In the "Filter Current Log" dialog, enter **4663** in the "Event sources" field. This filters the log to display only events with Event ID 4663.
   - Click **OK** to apply the filter.

4. View the AccessList Details:

   - Double-click on an event with Event ID 4663 to view its details.
   - Within the event's detailed information, locate and click on the **AccessList** portion.
   - This section provides a list of permissions exercised during the event.

To search for specific permissions within the AccessList, such as those mentioned, you can use the **Ctrl + F** keyboard shortcut and enter the desired permission keyword:

- **Read File**: Search for **%%1538**.
- **Read Attributes**: Search for **%%4423**.
- **Create File**: Search for **%%4418**.
- **Write File**: Search for **%%4417**.
- **Write Attributes**: Search for **%%1539**.
- **Delete File**: Search for **%%1537**.

Using this approach, you can efficiently analyze Event ID 4663 entries in the Security Log to identify specific access attempts and the permissions exercised during those events.

## Using netstat

`netstat`, short for network statistics, is a command-line network utility tool commonly used to display network connections and related information. In the context of Cybersecurity, it can be a valuable tool for identifying which programs or processes are opening specific network ports and accepting internet traffic on your system.

To use `netstat` for monitoring network connections and identifying potentially suspicious processes, follow these steps:

1. **Open a Command Prompt Window:**
   - Press `Win + R` to open the Run dialog.
   - Type `cmd` and press Enter. This opens a Command Prompt window.

2. **Run `netstat` with the `-ano` Flag:**
   - In the Command Prompt window, enter the following command:
     ```sh
     netstat -ano
     ```
     Ensure that there is a space between "netstat" and "-ano." Press Enter to execute the command.

3. **Review the `netstat` Output:**
   - The output will display a list of network connections, including information about the local and remote addresses, protocol, and the status of each connection.

4. **Key Items to Note:**
   - **Port Number:** Look for the port number associated with each network connection. It appears next to the first IP address after the colon. For example, "127.0.0.1:80" indicates that port 80 is open.
   - **Process State:** Determine whether the process is in a "Listening" or "Established" state.
     - A "Listening" process has opened a port and is actively accepting incoming traffic. These ports should be regularly monitored.
     - An "Established" process has opened a port to communicate with an outside service and is awaiting a reply. This is normal for network communication but can also be a sign of potential malware.

5. **Identify the Process ID (PID):**
   - Find the PID associated with the process in question. This PID is a numerical identifier.
   - You can use the PID to track down the specific program or process that is responsible for opening the port.

6. **Investigate the Program:**
   - To investigate the program associated with a PID, you can use tools like "Process Explorer" or Task Manager.
   - In Task Manager, you can enable the display of the PID column to match PIDs from `netstat` with running processes.

By following these steps, you can effectively use `netstat` to monitor network connections, identify open ports, and assess the processes associated with those ports. This can help you detect and investigate potential security issues or suspicious network activity on your system.


## Using msconfig

`msconfig`, short for Microsoft System Configuration Utility, is a system utility tool in Microsoft Windows designed to troubleshoot and manage the startup process. It allows users to disable or re-enable software, device drivers, and Windows services that run during the system startup, as well as modify boot parameters.

For optimal system performance and security, it's important to ensure that only essential programs and services run at boot time. By using `msconfig`, you can control which items are allowed to start automatically with your Windows operating system.

To manage startup programs and services using `msconfig`, follow these steps:

1. **Open the Run Command:**
   - Press `Win + R` to open the Run dialog.

2. **Access `msconfig`:**
   - In the Run dialog, type `msconfig` and press Enter. This will open the System Configuration utility.

3. **Review the Startup Tab:**
   - In the System Configuration utility, navigate to the "Startup" tab.
   - Here, you'll find a list of programs and applications that launch automatically when your computer boots.

4. **Uncheck Unnecessary Startup Programs:**
   - Carefully review the list of startup items.
   - Uncheck (disable) any items that are not required for your system's normal operation.
   - Focus on leaving essential programs checked, such as antivirus software or essential system utilities.

5. **Check the Services Tab:**
   - Switch to the "Services" tab within the System Configuration utility.
   - You can click the "Hide all Microsoft services" checkbox to filter the list and view only non-Microsoft services.

6. **Uncheck Unnecessary Services:**
   - Similar to the startup programs, uncheck (disable) any non-essential services that you don't require.
   - Be cautious and ensure you don't disable critical system services.

7. **Apply Changes and Restart:**
   - Once you've made your selections, click the "OK" button.
   - You'll be prompted to either "Exit without restart" or "Restart." Choose "Restart" to apply the changes.

After restarting your computer, only the selected startup programs and services will run automatically during the boot process. This can help improve system performance and security by reducing unnecessary background processes.

Keep in mind that while disabling unnecessary items can be beneficial, exercise caution when modifying startup configurations to avoid disabling critical services that your system relies on.

## Search the File System

Malware scans may not always detect hidden files or malicious software on a system, as attackers can attempt to hide them. It may be necessary to manually search through the file system, but please be aware that this should be done in accordance with security policies to avoid violating them.

### Methods for Searching Hidden Files

#### 1. Use a Specialized Program
You can employ a specialized program to conduct a specific search for hidden files. One example is CCleaner, which includes a Disk Analyzer (formerly File Finder) that can list files based on your criteria and display their paths.

#### 2. Utilize Windows Explorer Search
Windows Explorer, the built-in file manager in Windows, provides a search function. You can use it to look for specific files or patterns within your system. 

#### 3. Manually Check Folders
Another method is to manually inspect folders one by one. To enable the viewing of hidden files and folders, follow these steps:
- Press the Alt key on your keyboard to reveal the top bar menu.
- Select "Tools" and then "Folder Options."
- Navigate to the "View" tab.
- Select "Show hidden files, folders, and drives."

### Tips for Manual File Inspection

When searching for hidden files, exercise caution and avoid removing anything critical to the system's functionality. Here are some common file types and locations to consider:

#### Common File Types to Look For
1. Media Files (Music, Videos, Pictures, etc.)
2. Hacking/Remote Access Tools (e.g., netcat/nc, VNC servers, etc.)
3. Non-Business Related Software (e.g., media downloaders, toolbars, coupon savers, etc.)
4. Sensitive Company Files (Employee data, passwords, credit card numbers, etc.)

#### Common Locations to Search
- All users' home directories (usually under C:\Users)
- Any critical shared directories
- C:\Program Files
- C:\Program Files (x86)
- C:\Windows
- C:\Windows\system32

Remember that attackers may attempt to disguise files as regular system files to deceive you during your search. Therefore, it's essential to be cautious and thorough when investigating hidden files and potential malware.


## External Links:

### [Using Process Explorer](/process-explorer)

### [Using Process Monitor](process-monitor)