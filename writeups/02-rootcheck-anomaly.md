## Rootcheck "Trojaned File" Alert

Rootcheck is a Wazuh agent module that scans the endpoint for: Rootkits, Malware signatures, System anomalies, Policy violations. It runs periodically (not real-time)

## Setup: 

**Attacker:** Kali VM(192.168.29.104) and the **Manager:** Ubuntu-server(192.168.29.17)[manager] , **Target:** Kali VM(192.168.29.7)

## Alert Detected: 

 - **Rule id:** 510
 - **Level:** 7 (Medium)
 - Trojaned version of file '/usr/bin/md5sum' detected.
 - based on a generic signature match (string patterns like bash, /bin/sh found in the binary).

## Analysis/Triage:

 - Ran dpkg -V coreutils on Ubuntu to verify installed package files against known-good checksums.
 - No output returned — meaning no modified files detected in that package.

## Verdict:

 - **False Positive:** The signature-based heuristic flagged legitimate shell-related strings inside a standard system binary.
 - Package verification confirms the file is unmodified. 

## Conclusion:

Demonstrates ability to investigate before escalating, not every alert is a real threat, and blindly treating signature matches as confirmed compromise leads to alert fatigue and wasted response effort.