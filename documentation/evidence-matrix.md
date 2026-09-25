# Evidence Matrix

**Author:** Abdelrhman Ali Saleh

| Incident | Primary Evidence | Key Observations | Disposition |
|---|---|---|---|
| IR-001 Brute Force | 11, 13, 22 | Hydra RDP attempts; Event ID 4625; Wazuh Rule 60204 | Authorized lab simulation |
| IR-002 Reconnaissance | 14, 15 | Nmap `-sV -p 1-100`; ports 135/139/445; firewall drops | Authorized lab simulation |
| IR-003 PowerShell | 16, 17 | PowerShell execution; process discovery; Rule 91815 | Authorized lab simulation |
| IR-004 Exfiltration | 20 | TCP 4444 listener; `employee_records.txt` received | Authorized lab simulation |

## Evidence Integrity Notes

- Evidence is sourced from the screenshots included in this repository.
- IP addresses and timestamps are reported only where visible in the captured evidence.
- No third-party screenshots are required for the four documented scenarios.
