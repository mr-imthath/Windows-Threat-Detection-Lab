# 🛡️ Windows Threat Detection Lab

This project simulates adversary behavior in a Windows 10 lab to generate and analyze Windows Event Logs. It uses Sysmon, PowerShell, and the MITRE ATT&CK framework to build detection rules and playbooks for real-world incident response scenarios.

---

## 🧰 Tools & Technologies

- **Windows Event Viewer**
- **Sysmon (System Monitor)**
- **PowerShell**
- **MITRE ATT&CK**
- **Event IDs**: 4625, 4688, Sysmon Event 1, 3, 11

---

## 🧪 Lab Overview

1. Set up a Windows 10 virtual lab environment.
2. Installed Sysmon with a custom configuration.
3. Simulated adversary TTPs:
   - Brute Force Login Attempts
   - Encoded PowerShell Commands
   - Malware Drop and Execution
4. Collected and analyzed generated logs.

---

## 📊 Detection Logic & Mapping

| MITRE ATT&CK Technique | Event ID(s) | Description |
|------------------------|-------------|-------------|
| `T1110.001` – Brute Force | 4625 | Detect multiple failed logins |
| `T1059.001` – PowerShell | 4688, Sysmon 1 | Detect encoded PowerShell use |
| `T1041` – C2 Exfiltration | Sysmon 3 | Detect suspicious outbound traffic |

See [`docs/mitre-mapping.md`](docs/mitre-mapping.md) for detailed mappings.

---

## 📘 Detection Playbooks

Includes detection and response workflows for:
- Brute-force logins
- PowerShell-based attacks
- Malware drops

➡️ Check [`docs/detection-playbooks.md`](docs/detection-playbooks.md)

---

## 🚀 Outcome

- Built a detection lab using industry tools
- Mapped events to ATT&CK TTPs
- Developed detection rules for SOC operations
- Authored response workflows and documentation

---

## 📝 License

This project is licensed under the MIT License. See `LICENSE` for more.

---

# 🛡️ Windows Threat Detection Lab

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

Simulate adversary behavior in a Windows 10 lab to **generate and analyze Windows Event Logs**. This project leverages [Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon), PowerShell, and the [MITRE ATT&CK](https://attack.mitre.org/) framework to build detection rules and incident response playbooks for real-world scenarios.

---

## 📦 Features

✅ Simulate adversary TTPs (MITRE ATT&CK)  
✅ Generate Windows Event Logs for detection testing  
✅ Create detection logic mapped to ATT&CK  
✅ Document incident response playbooks

---

## 🧰 Tools & Technologies

- **[Windows Event Viewer](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/event-viewer-security-logs)**
- **[Sysmon (System Monitor)](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)**
- **PowerShell**
- **[MITRE ATT&CK Framework](https://attack.mitre.org/)**
- **Event IDs**:
  - `4625` → Failed Logon
  - `4688` → Process Creation
  - Sysmon:
    - Event `1` → Process Create
    - Event `3` → Network Connection
    - Event `11` → File Create

---

## 🧪 Lab Overview

1. Set up a Windows 10 virtual lab environment.
2. Install Sysmon with a custom configuration.  
   ➡️ **Download Sysmon:** [Sysmon Download Page](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)
3. Simulate adversary techniques:
   - Brute Force Login Attempts
   - Encoded PowerShell Commands
   - Malware Drop and Execution
4. Collect and analyze generated Windows Event Logs.

---

## 📊 Detection Logic & MITRE Mapping

| MITRE ATT&CK Technique         | Event ID(s)         | Description                            |
|--------------------------------|---------------------|----------------------------------------|
| [`T1110.001`](https://attack.mitre.org/techniques/T1110/001/) Brute Force        | 4625                | Detect multiple failed login attempts  |
| [`T1059.001`](https://attack.mitre.org/techniques/T1059/001/) PowerShell         | 4688, Sysmon 1      | Detect encoded PowerShell commands     |
| [`T1041`](https://attack.mitre.org/techniques/T1041/) C2 Exfiltration        | Sysmon 3            | Detect suspicious outbound traffic     |

🔗 **See full mappings in:** [`docs/mitre-mapping.md`](docs/mitre-mapping.md)

---

## 📘 Detection Playbooks

Detailed detection and response workflows for:

- Brute-force login attacks
- PowerShell-based attacks
- Malware drops

➡️ **Check out:** [`docs/detection-playbooks.md`](docs/detection-playbooks.md)

---

## 🚀 Outcomes

- Built a detection lab using industry-standard tools
- Mapped logs and events to MITRE ATT&CK TTPs
- Developed detection rules for SOC operations
- Authored response workflows and technical documentation

---

## 📝 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to open an [Issue](https://github.com/your-repo/issues) or submit a [Pull Request](https://github.com/your-repo/pulls).

