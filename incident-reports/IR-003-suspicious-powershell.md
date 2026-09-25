# IR-003 — Suspicious PowerShell Activity

**Author:** Abdelrhman Ali Saleh  
**Incident ID:** IR-003  
**Date/Time:** 2026-02-25 11:32–11:33 (Wazuh dashboard)  
**Severity:** Medium  
**Category:** Execution / Discovery / PowerShell  
**Status:** Closed — controlled lab simulation

## Summary

PowerShell activity was generated on the monitored Windows endpoint as part of a controlled malware-simulation exercise. The captured Windows console shows a simulated process named `SmalwareSim`, PowerShell execution, encoded-data handling, and process enumeration. Wazuh generated repeated PowerShell process-discovery alerts.

## Evidence

| Field | Observed value |
|---|---|
| Host | Windows monitored endpoint |
| Process | `powershell.exe` |
| Simulated process | `SmalwareSim` |
| Wazuh technique | Discovery |
| Wazuh description | PowerShell executing process discovery |
| Wazuh Rule ID | `91815` |
| Alert window | 2026-02-25 around 11:32–11:33 |
| Observed activity | PowerShell process execution and process enumeration |

The Windows screenshot also shows encoded-data handling using PowerShell/.NET conversion methods and a process listing containing `powershell` and other Windows processes.

## Timeline

1. **11:32:53.747** — Wazuh records a PowerShell process-discovery alert.
2. **11:32:57.428** — Additional alert for the same technique.
3. **11:33:37.529** — Additional PowerShell discovery alert.
4. **11:33:39.805** — Additional PowerShell discovery alert.
5. The analyst reviews the Windows process/command-line evidence and correlates the repeated alerts.

## Analyst Assessment

PowerShell is a legitimate Windows administration tool, but the observed combination of simulated malware execution, encoded-data handling and process discovery is suspicious in an enterprise context. Within this project it is intentionally generated lab activity, so the final disposition is **True Positive — Authorized Security Test**.

## Recommended SOC Actions

- Validate the user, host and parent process.
- Review the full PowerShell command line and script contents.
- Check for persistence, network connections and child processes.
- Correlate with Windows Security and Sysmon telemetry when available.
- Escalate suspicious production activity for deeper endpoint investigation.

## MITRE ATT&CK Mapping

- **T1059.001 — Command and Scripting Interpreter: PowerShell**
- **T1057 — Process Discovery**

## Evidence Files

- `screenshots/16_suspicious_commands_windows.png`
- `screenshots/17_suspicious_process_alert.jpg`
