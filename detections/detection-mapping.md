# Detection & MITRE Mapping

**Author:** Abdelrhman Ali Saleh

| Scenario | Detection Signal | Wazuh / Windows Evidence | MITRE ATT&CK |
|---|---|---|---|
| Authentication brute force | Repeated failed logons | Event ID 4625; Wazuh Rule 60204 | T1110; T1021.001 |
| Network reconnaissance | Multiple port/service probes | Nmap + Windows firewall telemetry | T1046 |
| Suspicious PowerShell | PowerShell process discovery | Wazuh Rule 91815 | T1059.001; T1057 |
| Simulated exfiltration | Unexpected outbound file transfer | TCP/4444 transfer evidence | T1041 / T1048 context |

## Tier 1 Triage Questions

1. Is the source authorized?
2. What asset and user are affected?
3. Did the activity succeed or fail?
4. Is there evidence of persistence, privilege escalation or lateral movement?
5. What related alerts occurred before and after the event?
6. Does the event require escalation?
