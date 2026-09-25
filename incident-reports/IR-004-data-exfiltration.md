# IR-004 — Simulated Data Exfiltration

**Author:** Abdelrhman Ali Saleh  
**Incident ID:** IR-004  
**Date/Time:** 2026-02-25 03:41 (lab evidence)  
**Severity:** High  
**Category:** Collection / Exfiltration  
**Status:** Closed — controlled lab simulation

## Summary

A controlled data-transfer simulation was performed between the Windows lab endpoint and the Kali testing VM. The Kali host listened on TCP port `4444` and received a file named `employee_records.txt` from the Windows endpoint.

## Evidence

| Field | Observed value |
|---|---|
| Receiving host | Kali lab VM — `192.168.62.4` |
| Sending host | Windows endpoint — `192.168.62.5` |
| Destination port | TCP `4444` |
| Receiving command | `nc -lvp 4444 > /tmp/received_data.txt` |
| Received file | `employee_records.txt` |
| Received file size | `281` bytes |
| Evidence time | `03:41` on Feb 25 |

The captured Kali terminal shows a connection from `192.168.62.5` to the listener on `192.168.62.4:4444`, followed by creation and inspection of `/tmp/received_data.txt`.

## Analyst Assessment

The transfer demonstrates a controlled exfiltration pattern: data is sent from a monitored endpoint to an external testing host over a listening TCP service. In a production environment, an unexpected transfer of employee records would require immediate investigation and containment. In this lab, it is **True Positive — Authorized Security Test**.

## Recommended SOC Actions

- Identify the source process responsible for the connection.
- Preserve the transferred-file metadata and relevant logs.
- Review outbound network connections from the source host.
- Determine whether sensitive data was involved.
- Escalate suspected real-world data exfiltration to the appropriate incident-response tier.

## MITRE ATT&CK Mapping

- **T1041 — Exfiltration Over C2 Channel** (conceptual lab mapping)
- **T1048 — Exfiltration Over Alternative Protocol** (network-transfer context)

## Evidence Files

- `screenshots/20_exfiltration_kali_received.png`
