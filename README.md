# 🛡️ SOC Tier 1 Detection Lab

A hands-on Security Operations Center (SOC) Tier 1 lab demonstrating SIEM monitoring, alert triage, log analysis, network reconnaissance detection, authentication attack detection, PowerShell monitoring, and incident documentation.

**Author:** Abdelrhman Ali Saleh  
**Role:** Cybersecurity / SOC Tier 1  
**Focus:** Wazuh • SIEM • Alert Triage • Incident Response • Windows Security • Linux • Network Security

---

## 🎯 Project Overview

This project demonstrates a controlled SOC lab built with virtual machines and Wazuh. Kali Linux is used as the authorized security-testing host, while Windows is monitored through the Wazuh agent and Ubuntu hosts the Wazuh platform.

The project follows a Tier 1 workflow:

**Detect → Validate → Scope → Investigate → Classify → Prioritize → Escalate/Respond → Document**

### Detection scenarios

- 🔐 Authentication Brute Force against RDP
- 🌐 Network Reconnaissance / Port Scanning
- ⚠️ Suspicious PowerShell Activity
- 📤 Simulated Data Exfiltration

---

## 🏗️ Lab Architecture

```text
                    ┌─────────────────────┐
                    │    SOC / SIEM       │
                    │       Wazuh         │
                    │   Ubuntu Server     │
                    └──────────┬──────────┘
                               │
                     Isolated Lab Network
                               │
             ┌─────────────────┴─────────────────┐
             │                                   │
   ┌─────────▼─────────┐              ┌─────────▼─────────┐
   │ Windows Endpoint  │              │   Kali Linux      │
   │   Wazuh Agent     │              │ Authorized Tester │
   │   Monitored Host  │              │ Recon / Simulation│
   └───────────────────┘              └───────────────────┘
```

### Components

| Component | Role |
|---|---|
| Ubuntu Server | Wazuh SIEM / manager / dashboard |
| Windows 10 | Monitored endpoint |
| Kali Linux | Authorized attack simulation |
| VirtualBox | Virtualization and lab isolation |
| Wazuh Agent | Endpoint telemetry |

---

## 🧰 Technologies & Tools

- Wazuh SIEM
- Ubuntu Server 22.04
- Windows 10
- Kali Linux
- VirtualBox
- Nmap 7.95
- Hydra 9.6
- PowerShell
- Windows Event Logs
- Windows Firewall logs
- Linux command-line utilities

---

## 🔎 Detection Scenarios

### 1. 🔐 Authentication Brute Force

Hydra generated repeated RDP authentication attempts from `192.168.62.4` against `192.168.62.5`. Windows Event ID `4625` was observed and Wazuh Rule `60204` identified multiple Windows logon failures.

**MITRE ATT&CK:** T1110, T1021.001

📄 [IR-001 — Authentication Brute Force](incident-reports/IR-001-authentication-bruteforce.md)

### 2. 🌐 Network Reconnaissance

Nmap `7.95` performed `-sV -p 1-100` against `192.168.62.5`. The evidence identified TCP `135`, `139`, and `445` as open. Windows firewall telemetry also showed dropped connections involving the same lab source and target.

**MITRE ATT&CK:** T1046

📄 [IR-002 — Network Reconnaissance](incident-reports/IR-002-network-reconnaissance.md)

### 3. ⚠️ Suspicious PowerShell

PowerShell activity on the Windows endpoint included process discovery and simulated malware activity. Wazuh displayed repeated Rule `91815` alerts describing PowerShell executing process discovery.

**MITRE ATT&CK:** T1059.001, T1057

📄 [IR-003 — Suspicious PowerShell](incident-reports/IR-003-suspicious-powershell.md)

### 4. 📤 Simulated Data Exfiltration

The lab demonstrated a controlled file transfer from the Windows endpoint to the Kali testing VM over TCP `4444`. The receiving host saved `employee_records.txt` to `/tmp/received_data.txt`.

**MITRE ATT&CK context:** T1041 / T1048

📄 [IR-004 — Simulated Data Exfiltration](incident-reports/IR-004-data-exfiltration.md)

---

## 🧠 SOC Tier 1 Analyst Workflow

```text
Alert
  ↓
Validate
  ↓
Collect Evidence
  ↓
Identify Source / Target
  ↓
Investigate
  ↓
Classify
  ↓
Determine Severity
  ↓
Respond / Escalate
  ↓
Document
  ↓
Close
```

---

## 📊 Evidence Matrix

See [Evidence Matrix](documentation/evidence-matrix.md) for the relationship between each incident, screenshot evidence, detection signal and MITRE ATT&CK technique.

---

## 📸 Lab Evidence

The following screenshots document the lab environment, detection activity, Wazuh alerts, and investigation evidence.

### VirtualBox Lab

<p align="center">
  <img src="https://raw.githubusercontent.com/Abdelrhman216/SOC-Tier1-Detection-Lab/main/screenshots/01_virtualbox_installed.png" alt="VirtualBox Lab" width="900">
</p>

### Ubuntu Wazuh Server

<p align="center">
  <img src="https://raw.githubusercontent.com/Abdelrhman216/SOC-Tier1-Detection-Lab/main/screenshots/03_ubuntu_server_running.png" alt="Ubuntu Wazuh Server" width="900">
</p>

### Wazuh Dashboard

<p align="center">
  <img src="https://raw.githubusercontent.com/Abdelrhman216/SOC-Tier1-Detection-Lab/main/screenshots/08_wazuh_dashboard_login.png" alt="Wazuh Dashboard" width="900">
</p>

### Windows Wazuh Agent

<p align="center">
  <img src="https://raw.githubusercontent.com/Abdelrhman216/SOC-Tier1-Detection-Lab/main/screenshots/09_agent_installed_windows.png" alt="Windows Wazuh Agent" width="900">
</p>

### Network Connectivity

<p align="center">
  <img src="https://raw.githubusercontent.com/Abdelrhman216/SOC-Tier1-Detection-Lab/main/screenshots/06_network_connectivity.png" alt="Network Connectivity" width="900">
</p>

### Hydra RDP Simulation

<p align="center">
  <img src="https://raw.githubusercontent.com/Abdelrhman216/SOC-Tier1-Detection-Lab/main/screenshots/11_bruteforce_attack_running.png" alt="Hydra RDP Simulation" width="900">
</p>

### Wazuh Brute Force Alert

<p align="center">
  <img src="https://raw.githubusercontent.com/Abdelrhman216/SOC-Tier1-Detection-Lab/main/screenshots/13_bruteforce_alert_detail.jpg" alt="Wazuh Brute Force Alert" width="900">
</p>

### Nmap Reconnaissance Scan

<p align="center">
  <img src="https://raw.githubusercontent.com/Abdelrhman216/SOC-Tier1-Detection-Lab/main/screenshots/14_nmap_scan_running.png" alt="Nmap Reconnaissance Scan" width="900">
</p>

### Windows Firewall Drops

<p align="center">
  <img src="https://raw.githubusercontent.com/Abdelrhman216/SOC-Tier1-Detection-Lab/main/screenshots/15_portscan_firewall_drops.png" alt="Windows Firewall Drops" width="900">
</p>

### Suspicious PowerShell Commands

<p align="center">
  <img src="https://raw.githubusercontent.com/Abdelrhman216/SOC-Tier1-Detection-Lab/main/screenshots/16_suspicious_commands_windows.png" alt="Suspicious PowerShell Commands" width="900">
</p>

### Wazuh PowerShell Alert

<p align="center">
  <img src="https://raw.githubusercontent.com/Abdelrhman216/SOC-Tier1-Detection-Lab/main/screenshots/17_suspicious_process_alert.jpg" alt="Wazuh PowerShell Alert" width="900">
</p>

### Simulated Data Transfer

<p align="center">
  <img src="https://raw.githubusercontent.com/Abdelrhman216/SOC-Tier1-Detection-Lab/main/screenshots/20_exfiltration_kali_received.png" alt="Simulated Data Transfer" width="900">
</p>

### Incident Report Evidence

<p align="center">
  <img src="https://raw.githubusercontent.com/Abdelrhman216/SOC-Tier1-Detection-Lab/main/screenshots/22_sample_incident_report.png" alt="Incident Report Evidence" width="900">
</p>

## 📁 Project Structure

```text
SOC-Tier1-Detection-Lab/
├── README.md
├── LICENSE
├── incident-reports/
│   ├── IR-001-authentication-bruteforce.md
│   ├── IR-002-network-reconnaissance.md
│   ├── IR-003-suspicious-powershell.md
│   └── IR-004-data-exfiltration.md
├── documentation/
│   ├── lab-architecture.md
│   ├── setup-plan.md
│   ├── analyst-workflow.md
│   └── evidence-matrix.md
├── detections/
│   ├── README.md
│   └── detection-mapping.md
└── screenshots/
    └── lab evidence
```

---

## 🎓 Skills Demonstrated

- SIEM Monitoring
- Alert Triage
- Log Analysis
- Windows Security Events
- Authentication Attack Detection
- Network Reconnaissance Detection
- PowerShell Security Monitoring
- Basic Detection Engineering
- MITRE ATT&CK Mapping
- Incident Documentation
- SOC Tier 1 Investigation Workflow

---

## 👨‍💻 Author

**Abdelrhman Ali Saleh**  
Cybersecurity Engineer | SOC Tier 1 | Network Security

- GitHub: https://github.com/Abdelrhman216
- LinkedIn: https://www.linkedin.com/in/abdelrhmanalii/

---

## 📌 Disclaimer

This project is a controlled cybersecurity lab for educational and defensive security purposes. All testing was performed against systems within the authorized lab environment.

**Building. Securing. Learning. 🔐**
