# IR-001 — Authentication Brute Force (RDP)

**Author:** Abdelrhman Ali Saleh  
**Incident ID:** IR-001  
**Date/Time:** 2026-02-23 13:54:27 UTC (Wazuh event timestamp)  
**Severity:** High  
**Category:** Credential Access / Brute Force  
**Status:** Closed — controlled lab simulation

## Summary

A controlled RDP brute-force simulation was launched from the Kali security-testing VM against the monitored Windows endpoint. Hydra generated repeated RDP authentication attempts, while Wazuh correlated Windows Security Event ID 4625 failures and displayed the activity as a multiple-logon-failures alert.

## Evidence

| Field | Observed value |
|---|---|
| Source | `192.168.62.4` — Kali lab VM |
| Target | `192.168.62.5` — Windows endpoint |
| Service | RDP / TCP 3389 |
| Detection | Wazuh Security Events |
| Windows Event ID | `4625` — failed logon |
| Wazuh Rule | `60204` — Multiple Windows logon failures |
| Authentication package | `NTLM` |
| Logon type | `3` — Network |
| Source port | `0` in the captured Wazuh event |
| Observed alert time | `2026-02-23T09:54:27.678Z` |

The Hydra evidence shows six password attempts against the Windows RDP service. The tool output also reports that the tested account was not active for remote desktop, so the lab run did not establish successful RDP access.

## Timeline

1. **03:56:14** — Hydra starts the RDP test against `192.168.62.5:3389`.
2. **03:56:14–03:56:17** — Multiple password attempts are generated.
3. Windows records failed authentication activity as Event ID `4625`.
4. Wazuh correlates repeated failures and displays Rule `60204`.
5. The analyst reviews source, target, authentication package and logon type.
6. The activity is documented as an authorized lab simulation.

## Analyst Assessment

The pattern is consistent with brute-force authentication behavior: repeated failed authentication attempts from one source against the same RDP target. Because the activity originated from the designated Kali lab host, it is classified as **True Positive — Authorized Security Test**, rather than an external compromise.

## Recommended SOC Actions

- Verify whether the source is authorized before escalating.
- Search for successful Event ID `4624` from the same source to rule out successful access.
- Review other accounts targeted by the source.
- Apply account lockout/rate-limiting controls where appropriate.
- Restrict RDP exposure and prefer controlled administrative access paths.

## MITRE ATT&CK Mapping

- **T1110 — Brute Force**
- **T1021.001 — Remote Services: RDP**

## Evidence Files

- `screenshots/11_bruteforce_attack_running.png`
- `screenshots/13_bruteforce_alert_detail.jpg`
- `screenshots/22_sample_incident_report.png`
