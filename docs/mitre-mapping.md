# 🗺️ MITRE ATT&CK Technique Mappings

This document provides detailed mappings between Windows Event Logs, Sysmon events, and MITRE ATT&CK techniques observed during simulations in the **Windows Threat Detection Lab**.

---

## 🔐 T1110.001 – Brute Force

- **Technique:** [T1110.001 - Password Guessing](https://attack.mitre.org/techniques/T1110/001/)
- **Event ID(s):**
  - `4625` (Windows Security)
- **Description:**
  - Detect multiple failed logon attempts that may indicate brute-force activity against local or domain accounts.

### Detection Logic

- Monitor `4625` events for:
  - High volume of failures from the same user or IP
  - Unusual timeframes for logon attempts
- Fields of interest:
  - Account Name
  - Source IP Address
  - Failure Reason
- Recommended aggregation:
  - Count failures per account or IP in short timeframes (e.g. 5-10 minutes)

---

## ⚙️ T1059.001 – PowerShell

- **Technique:** [T1059.001 - PowerShell](https://attack.mitre.org/techniques/T1059/001/)
- **Event ID(s):**
  - `4688` (Windows Security) – Process Creation
  - Sysmon Event ID `1` – Process Create
- **Description:**
  - Detect usage of PowerShell for script execution, particularly when obfuscated or encoded commands are used to evade detection.

### Detection Logic

- Monitor command-line arguments for:
  - `-EncodedCommand`
  - `-Command` with suspicious strings
  - Base64-encoded strings
- Correlate parent-child process relationships:
  - E.g. suspicious processes spawning `powershell.exe`
- Key fields to analyze:
  - ParentProcessName
  - CommandLine
  - User
- Possible detection rules:
  - Alert on encoded PowerShell unless explicitly authorized
  - Monitor PowerShell launched by unusual parent processes

---

## 🌐 T1041 – Exfiltration Over C2 Channel

- **Technique:** [T1041 - Exfiltration Over Command and Control Channel](https://attack.mitre.org/techniques/T1041/)
- **Event ID(s):**
  - Sysmon Event ID `3` – Network Connection
- **Description:**
  - Detect suspicious outbound network connections that could indicate data exfiltration over C2 channels.

### Detection Logic

- Monitor Sysmon Event ID `3` for:
  - Connections to:
    - Uncommon external IPs
    - High-risk countries
    - Non-standard ports
  - Long-lived or repetitive connections
- Enrich logs with threat intelligence feeds for:
  - Malicious domains
  - Suspicious IP ranges
- Fields to review:
  - Destination IP
  - Destination Port
  - Process initiating connection
  - Protocol used
- Possible detection strategies:
  - Block or alert on connections matching threat intel
  - Investigate processes with unexpected network activity

---

## 🔎 Recommendations

- **Log centralization:** Forward logs to a SIEM for correlation and alerting.
- **Baselining:** Establish normal behavior to reduce false positives.
- **Threat intelligence:** Integrate feeds to enrich detection rules.
- **Regular testing:** Periodically simulate attacks to validate detection logic.

---

**Return to the main documentation:** [README.md](../README.md)
