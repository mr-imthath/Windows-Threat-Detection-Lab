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
