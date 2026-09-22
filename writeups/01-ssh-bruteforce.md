## SSH Brute force detection - Home SOC Lab

Simulated a brute force attack using Hydra to gain access to root against a Linux host and detected the resulting alerts in Wazuh

### Setup: 

Attacker: Kali VM(192.168.29.7) and the Target: Ubuntu-server(192.168.29.17)[agent,manager] , Tool: Hydra for targeting root over ssh

### Alert Detected: 

 - **Rule id:** 5758
 - **Level:** 8 (Medium)
 - **Source ip:** 192.168.29.7
 - **Target user:** root
 - Fired 31 times (rule.firedtimes) -- shows repeated attack , not a one-off
 - **MITRE:** T1110 (Brute Force) , tactic: Credential Access

### Analysis/Triage:

 - **True Positive:** Self caused, and also matches real brute force behaviour(rapid and repeated auth failure, [preauth] -- means failed before even establishing a session)
 - No successfull login attempt -- attack did not succeed (MaXAuthTries)
 - **Escalation logic:** In real world scenario,sustained failures from one source(31 attempt) plus no eventual success = block source ip and review if ssh should be exposed

### Recommendations:

 - Disable SSH login and password auth instead make it key-based only.
 - Add fail2ban or similar tool for automated banning of ip
 - Add rate limit