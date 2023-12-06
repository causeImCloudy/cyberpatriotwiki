---
title: Process Monitor
description: 
published: true
date: 2023-06-30T20:14:49.863Z
tags: curriculum, advanced, active directory
editor: markdown
dateCreated: 2023-06-30T20:14:47.681Z
---

# Monitoring File System and Registry Activity with Process Monitor

Process Monitor is an advanced monitoring tool for Windows that provides real-time insight into file system, Registry, and process/thread activity. It combines the functionalities of two legacy Sysinternals utilities, Filemon and Regmon, and offers numerous enhancements, including robust filtering, comprehensive event properties, and more. It's an invaluable tool for system troubleshooting and malware analysis.

## Using Process Monitor for CyberPatriot and Scoring System Analysis

Process Monitor can be a useful tool for CyberPatriot competitions, allowing you to see what the scoring system is inspecting during scans. To use Process Monitor effectively:

1. **Launch Process Monitor:**
   - Open Process Monitor.
   - Immediately, go to the "File" menu and click "Capture Events" to start capturing events. This prevents Process Monitor from scanning before applying filters.

2. **Apply Filters:**
   - Navigate to the "Filter" menu and select "Filter."
   - In the filter dialog, configure the entry boxes as follows:
     - `[Process Name] [is] [CyberPatriotClient.exe]` and click "Include."
   - Click "Add," then "OK" to apply the filter.

3. **Clear Display and Start Capturing:**
   - Go to the "Edit" menu and choose "Clear Display" to clear any existing events.
   - Return to the "File" menu and click "Capture Events" again to start capturing events.

4. **Observe Scoring System Activity:**
   - Wait for the scoring system to complete one full check (which can take up to 10 seconds).
   - Once the check is done, uncheck "Capture Events" to stop capturing events.

5. **Analyze Activity:**
   - Examine the recorded events in Process Monitor.
   - Look through the "Path(s)" to identify files and registry keys that the scoring system is accessing.

Process Monitor provides detailed information about the processes and activities related to the CyberPatriotClient.exe process, helping you gain insights into what the scoring system is inspecting during scans.

By following these steps, you can effectively use Process Monitor for CyberPatriot competitions and gain a better understanding of the system's activity during assessments.
