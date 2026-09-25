# Lab Architecture

**Author:** Abdelrhman Ali Saleh

## Overview

The SOC lab uses an isolated virtual network containing a SIEM server, a monitored Windows endpoint, and a Kali Linux security testing host.

## Components

| Component | Purpose |
|---|---|
| Ubuntu Server | Wazuh SIEM and monitoring |
| Windows Endpoint | Endpoint telemetry and security events |
| Kali Linux | Authorized attack simulation and reconnaissance |
| VirtualBox | Virtualization and isolated networking |
| Wazuh Agent | Endpoint telemetry collection |

## Traffic Flow

```text
Kali Linux
    │
    │ Authorized Security Testing
    ▼
Windows Endpoint
    │
    │ Logs / Events
    ▼
Wazuh Agent
    │
    ▼
Wazuh SIEM
    │
    ▼
SOC Tier 1 Analyst
```

The environment is intentionally isolated to keep security testing inside the lab.
