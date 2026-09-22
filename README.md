# SOC Analyst Portfolio — Home Lab

This repo documents hands-on detection and incident-investigation work from a self-built home SOC lab

## Lab Setup 

- **SIEM:** Wazuh (manager + dashboard)
- **Manager host:** Ubuntu Server (VirtualBox VM) — also selfmonitored as a local agent
- **Monitored endpoint:** Kali Linux (VirtualBox VM, Wazuh agent)
- **Network:** Bridged adapter (both VMs on local network)

## What This Demonstrates

- SIEM deployment and troubleshooting (manager/agent architecture, networking, service management)
- Attack simulations on monitored endpoints
- Alert triage and log analysis (Wazuh rules, severity levels)
- Incident documentation in analyst report format

## Writeups

| # | Title | Technique | MITRE ID |
|---|-------|-----------|----------|
| 01 | 	SSH Brute Force Detection | Brute Force | T1110 |

*(More writeups added as the lab expands — malware execution, file integrity monitoring, log anomaly detection, etc.)*

## Tools Used

Wazuh, VirtualBox, Kali Linux, Ubuntu Server, Hydra


