# IR-002 — Network Reconnaissance / Port Scanning

**Author:** Abdelrhman Ali Saleh  
**Incident ID:** IR-002  
**Date/Time:** 2026-02-24 02:11 EST  
**Severity:** Medium  
**Category:** Reconnaissance / Network Scanning  
**Status:** Closed — controlled lab simulation

## Summary

A controlled Nmap service/version scan was launched from the Kali lab VM against the monitored Windows endpoint. The scan targeted TCP ports 1–100. The captured result identified the Windows host as reachable and exposed three services in the scanned range.

## Evidence

| Field | Observed value |
|---|---|
| Source | `192.168.62.4` — Kali lab VM |
| Target | `192.168.62.5` — Windows endpoint |
| Scan command | `nmap -sV -p 1-100 192.168.62.5` |
| Scan scope | TCP ports `1–100` |
| Host status | Up; ~0.00145 s latency |
| Open ports observed | `135/tcp`, `139/tcp`, `445/tcp` |
| 135/tcp | Microsoft Windows RPC / msrpc |
| 139/tcp | NetBIOS Session Service |
| 445/tcp | Microsoft-DS / SMB |
| Scan duration | 7.88 seconds |
| Nmap version | 7.95 |

The Windows firewall evidence also shows dropped TCP connection attempts from `192.168.62.4` to `192.168.62.5` on ports `135`, `139`, and `445`, supporting correlation between reconnaissance traffic and host firewall telemetry.

## Timeline

1. **02:11 EST** — Nmap starts the service/version scan.
2. The target is identified as an active Windows host.
3. Ports 135, 139 and 445 are identified as open in the scan range.
4. Windows firewall telemetry records dropped connection attempts involving the same source and destination.
5. The analyst correlates the network test with the lab's authorized Kali source.

## Analyst Assessment

The traffic is consistent with network reconnaissance because one source enumerated services across a range of destination ports. In this lab, the source is an authorized testing VM, so the event is classified as **True Positive — Authorized Security Test**.

## Recommended SOC Actions

- Identify the scanning source and confirm authorization.
- Review firewall and endpoint telemetry around the scan time.
- Identify exposed services and confirm they are required.
- Investigate any follow-on exploitation attempts.
- Escalate if scanning originates from an unauthorized asset.

## MITRE ATT&CK Mapping

- **T1046 — Network Service Scanning**

## Evidence Files

- `screenshots/14_nmap_scan_running.png`
- `screenshots/15_portscan_firewall_drops.png`
