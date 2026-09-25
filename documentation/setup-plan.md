# Lab Setup

**Author:** Abdelrhman Ali Saleh

## Platform

The lab is built with VirtualBox using isolated virtual machines.

## Virtual Machines

- Ubuntu Server — Wazuh SIEM
- Windows 10 — monitored endpoint
- Kali Linux — authorized security testing host

## Core Tools

- Wazuh
- Wazuh Agent
- Nmap
- Hydra
- PowerShell
- Windows Event Viewer
- Linux command-line utilities

## Security Design

The virtual machines communicate through an isolated host-only network. Testing is restricted to the lab environment.

## Analyst Preparation

The SOC analyst validates endpoint connectivity, confirms telemetry ingestion, and verifies that security events are visible in the SIEM before beginning each investigation.
