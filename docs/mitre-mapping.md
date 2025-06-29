# MITRE ATT&CK Technique Mappings

This document provides detailed mappings between Windows Event Logs, Sysmon events, and MITRE ATT&CK techniques.

## Brute Force - T1110.001

- Event ID: 4625
- Description: Detect multiple failed logins
- Detection logic:
    - Monitor for high volume of failed logon attempts
    - Analyze Account Name and IP addresses

## PowerShell - T1059.001

- Event IDs: 4688, Sysmon Event ID 1
- Description: Detect suspicious or encoded PowerShell commands
- Detection logic:
    - Monitor command line arguments for suspicious patterns
    - Look for base64-encoded strings
    - Track parent-child process relationships

## Command and Control (C2) - T1041

- Event ID: Sysmon Event ID 3
- Description: Detect suspicious network connections
- Detection logic:
    - Monitor outbound connections to uncommon ports
    - Analyze destination IPs and domains
    - Correlate with threat intelligence feeds

