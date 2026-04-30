# SOC Lab 1: Splunk Failed Logon Detection - Event ID 4625

## Overview

This lab demonstrates how to use Splunk Enterprise to detect failed Windows logon attempts using Windows Event Logs.

The goal of this lab was to build a basic SOC-style detection workflow by ingesting Windows logs into Splunk, generating failed login activity, and identifying Event ID 4625.

## Objectives

- Create a virtual lab environment
- Install and configure Splunk Enterprise
- Ingest Windows Event Logs into Splunk
- Generate failed logon attempts
- Detect failed authentication events using Splunk
- Analyze Windows Event ID 4625

## Lab Environment

- Virtualization Platform: VirtualBox
- SIEM: Splunk Enterprise
- Target Machine: Windows 10 VM
- Additional VM: Kali Linux
- Log Source: Windows Event Logs

## Environment Setup

- Created a Windows 10 virtual machine in VirtualBox
- Created a Kali Linux virtual machine in VirtualBox
- Configured VM networking for lab use
- Installed Splunk Enterprise on the Windows 10 VM
- Accessed Splunk locally through:
---text
https://localhost:8000

## Data Ingestion

Windows Event Logs were configured and ingested into Splunk for monitoring and analysis.
The following configuration was used:
- Host: windows10
- Index: default
- Data Source: Windows Event Logs
Local event log collection was enabled in Splunk, allowing the platform to ingest logs from the Windows system.

## Logs Collected

The following Windows logs were collected:
-Security
-System
-Application

## Test Activity

-Failed logon attempts were manually generated on the Windows 10 VM.
-The purpose was to create failed authentication events that could be detected in Splunk.

-Expected Windows Event:

Event ID: 4625
Meaning: Failed logon attempt

## Attack Simulation

-The Windows system was locked, and incorrect passwords were entered multiple times.
-This generated Windows Security Event ID 4625, which represents failed logon activity.

## Detection

-Splunk was used to search for failed logon events.

-Search query used:
-index=* 4625

## Result:

-Successfully identified approximately 20 failed logon attempts

## Analysis:

-Multiple Event ID 4625 entries were observed in Splunk.
-Each event represented a failed login attempt. The activity was intentionally generated through repeated incorrect password entries.
-This confirmed that Windows Security logs were successfully ingested into Splunk and could be analyzed for authentication-related activity.

## Security Relevance

-Windows Event ID 4625 is important for detecting:

-Failed authentication attempts
-Possible brute force activity
-Unauthorized access attempts
-Suspicious login behavior
Monitoring this event is a basic but important task for SOC analysts.

## Conclusion

-This lab demonstrates how a SIEM such as Splunk can be used to detect failed authentication attempts using Windows Event Logs.
-By analyzing Event ID 4625, analysts can identify suspicious login behavior that may indicate brute force attacks or unauthorized access attempts.
-This foundational detection is a critical task in real-world SOC environments.
