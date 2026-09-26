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
| 01 | [SSH Brute Force Detection](writeups/01-ssh-bruteforce.md) | Brute Force | T1110 |
| 02 | [RootCheck "Trojaned File" alert](writeups/02-rootcheck-anomaly.md) | Routine Checkup by manager | null | 
| 03 | [Successfull Bruteforce Compromise](writeups/03-bruteforce-compromise.md) | Valid Accounts, Brute Force | T1078, T1110 |
| 04 | [New User Account Alert](writeups/04-new-user-alert.md) | Persistence, Defense Evasion, Privilege Escalation, Initial Access | T1078 , T1136 |
| 05 | [Anti-Forensics — Log Tampering Detection](writeups/05-anti-forensics-log-tampering.md) | Privilege Escalation, Defense Evasion | T1548.003 |

*(More writeups added as the lab expands — malware execution, file integrity monitoring, log anomaly detection, etc.)*

## Tools Used

Wazuh, VirtualBox, Kali Linux, Ubuntu Server, Hydra


