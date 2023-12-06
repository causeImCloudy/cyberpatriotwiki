---
title: Process Explorer
description: 
published: true
date: 2023-06-30T20:14:49.863Z
tags: curriculum, advanced, active directory
editor: markdown
dateCreated: 2023-06-30T20:14:47.681Z
---
# Analyzing Processes with Process Explorer

Process Explorer is a powerful system utility provided by Microsoft's SysInternals. It is designed to provide detailed information about running processes, including the handles and DLLs they have opened or loaded. This tool is invaluable for troubleshooting and gaining insights into how Windows and applications work.

## Getting Started

To start using Process Explorer, follow these steps:

1. **Download Process Explorer:**
   - Download Process Explorer from the official SysInternals website [here](https://technet.microsoft.com/en-us/sysinternals/bb896653.aspx).

2. **Extract and Launch:**
   - Extract the downloaded `procexp.exe` (or `procexp64.exe` for 64-bit systems) file to your preferred location, such as your Desktop.

3. **Run as Administrator:**
   - Right-click on the `procexp.exe` (or `procexp64.exe`) file and select "Run as administrator."
   - Running as administrator ensures that Process Explorer has the necessary privileges to gather detailed system information.

## Understanding the Process Explorer Interface

The Process Explorer interface consists of two main sub-windows:

- **Top Window:** This window displays a list of currently active processes. It includes information about the names of their owning accounts.

- **Bottom Window:** The content of this window depends on the mode Process Explorer is in:
   - In "Handle Mode," you'll see the handles that the selected process in the top window has opened.
   - In "DLL Mode," you'll see the DLLs and memory-mapped files that the selected process has loaded.

## Features of Process Explorer

- **Powerful Search:** Process Explorer includes a robust search capability that helps you quickly identify processes with specific handles or loaded DLLs.

- **Troubleshooting:** It is particularly useful for tracking down issues such as DLL version problems or handle leaks within processes.

## How to Use Process Explorer

1. Launch Process Explorer with administrator privileges.

2. Browse the list of active processes in the top window.

3. Select a process of interest to view its details in the bottom window. You can double-click on a process for more information.

4. Use the search functionality to find processes with particular handles or loaded DLLs.

## Conclusion

Process Explorer is a valuable tool for system administrators, developers, and anyone interested in understanding the inner workings of processes on a Windows system. It provides detailed insights into the behavior of running applications and system components, making it an essential utility for diagnosing and troubleshooting issues.
