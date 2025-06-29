# 🛠️ Detection Playbooks

This document provides **detailed detection and response workflows** for adversary techniques simulated in the **Windows Threat Detection Lab**. Use these playbooks to guide security operations, threat hunting, and incident response.

---

## 🔐 Brute-Force Login Attacks

### Technique
- **MITRE ATT&CK:** [T1110.001 - Password Guessing](https://attack.mitre.org/techniques/T1110/001/)
- **Relevant Events:**
  - Windows Security Event ID `4625`

### Detection Steps
✅ Search for excessive failed logon attempts within short time frames.  
✅ Correlate:
- Account Name
- Source IP Address
- Workstation name
- Failure Reason

### Example Detection Logic

- **Windows Event Log Search (pseudo-query):**

    ```
    EventID == 4625
    | stats count by AccountName, IpAddress, WorkstationName
    | where count > threshold
    ```

- Investigate:
  - Many failures for the same user
  - Logons from new or foreign IPs
  - Unusual login hours

### Response Actions

- Lock affected accounts if brute force is confirmed
- Check for successful logons following failures
- Review domain controllers for suspicious activity
- Block malicious IPs at the firewall or VPN
- Reset passwords and enforce stronger policies

---

## ⚙️ PowerShell-Based Attacks

### Technique
- **MITRE ATT&CK:** [T1059.001 - PowerShell](https://attack.mitre.org/techniques/T1059/001/)
- **Relevant Events:**
  - Windows Security Event ID `4688`
  - Sysmon Event ID `1`

### Detection Steps
✅ Look for PowerShell processes with suspicious command lines:
- `-EncodedCommand`
- Long Base64 strings
- Download cradle patterns (e.g., `IEX (New-Object Net.WebClient).DownloadString(...)`)

✅ Check process ancestry:
- Suspicious parent processes spawning PowerShell

✅ Search for signs of:
- Fileless execution
- In-memory script execution

### Example Detection Logic

- **Sysmon Process Command Line Search:**

    ```
    EventID == 1
    Image ends with powershell.exe
    CommandLine contains "-EncodedCommand" OR suspicious keywords
    ```

- **Windows Security Process Creation:**

    ```
    EventID == 4688
    NewProcessName ends with powershell.exe
    CommandLine contains suspicious patterns
    ```

### Response Actions

- Investigate the exact script or command executed
- Check for:
  - Malicious downloads
  - Lateral movement
  - Credential dumping tools
- Capture memory or forensic images if compromise is suspected
- Block identified scripts or hashes
- Inform users if phishing was involved

---

## 🐛 Malware Drops & Execution

### Techniques
- Commonly related MITRE ATT&CK:
  - [T1204.002 - Malicious File Execution](https://attack.mitre.org/techniques/T1204/002/)
  - [T1059 - Command and Scripting Interpreter](https://attack.mitre.org/techniques/T1059/)

- **Relevant Events:**
  - Sysmon Event ID `11` – File Create
  - Sysmon Event ID `1` – Process Create

### Detection Steps
✅ Detect suspicious file writes:
- Files dropped in unusual directories
- Executable files in temporary folders
- Random or suspicious file names

✅ Detect process execution:
- Suspicious new processes immediately after a file drop
- Correlate hashes with threat intelligence

### Example Detection Logic

- **Sysmon File Create Query:**

    ```
    EventID == 11
    TargetFilename ends with .exe OR .dll OR .ps1
    AND Path contains suspicious folders (e.g. Temp, AppData\Roaming)
    ```

- **Sysmon Process Execution:**

    ```
    EventID == 1
    Image ends with suspicious executables
    OR matches known malicious hashes
    ```

### Response Actions

- Quarantine the endpoint
- Isolate suspicious files
- Submit files to sandbox or antivirus for analysis
- Investigate parent process responsible for drop
- Check lateral movement activity
- Clean or rebuild the host if compromised

---

## 📌 General Response Best Practices

- **Document all actions and findings.**
- **Update detection rules** based on newly discovered TTPs.
- **Communicate with stakeholders** about potential impacts.
- **Review similar systems** for signs of related activity.
- **Use threat intel** to track attacker infrastructure or methods.

---

**Return to the main documentation:** [README.md](../README.md)
