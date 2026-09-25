# Detection Engineering Notes

**Author:** Abdelrhman Ali Saleh

This directory documents the detection logic and analyst reasoning used in the lab.

## Detection Coverage

### Authentication Brute Force

Signal: repeated Windows failed-logon events from the same source against a monitored endpoint.

Evidence in this lab: Event ID `4625`, Wazuh Rule `60204`.

### Network Reconnaissance

Signal: one source generating connection attempts across multiple destination ports.

Evidence in this lab: Nmap service/version scan plus Windows firewall drop telemetry.

### Suspicious PowerShell

Signal: PowerShell execution associated with process discovery and simulated suspicious activity.

Evidence in this lab: Wazuh Rule `91815` and Windows process/command-line evidence.

### Simulated Exfiltration

Signal: unexpected outbound transfer from a monitored endpoint to a testing host.

Evidence in this lab: TCP/4444 listener and received file evidence.

## Analyst Principle

A detection is only the beginning of the investigation. Tier 1 analysis validates the alert, identifies the affected asset, establishes scope, checks for successful compromise, determines disposition, and escalates when required.
