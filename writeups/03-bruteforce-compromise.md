## Successfull Bruteforce Login - SSH Compromise Simulation

Simulated a full SSH brute-force attack that succeeded, escalating from failed attempts to a confirmed compromised login, and analyzed the resulting Wazuh detection.

## Setup: 

**Attacker:** Kali VM(192.168.29.104) and the **Manager:** Ubuntu-server(192.168.29.17)[manager] , **Target:** Kali VM(192.168.29.7)

## Alert Detected: 

 - **Rule id:** 40112
 - **Level:** 12 (High)
 - **Source ip:** 192.168.29.104
 - **Target user:** root
 - Multiple authentication failures followed by a success. Accepted password for root from 192.168.29.104 port 57112 ssh2
 - **MITRE Techniques:** T1110 (Brute Force) → T1078 (Valid Accounts)
 - **Tactics:** Credential Access, Initial Access, Persistence, Privilege Escalation, Defense Evasion

## Analysis/Triage:

 - **True Positive:** This differs from a plain failed-login alert: Wazuh correlated repeated failures with an eventual success correctly escalating severity from Medium (failed attempts alone) to High (confirmed compromise)
 - The chained MITRE mapping (T1110 → T1078) reflects real attacker behavior: brute force is the method, valid account access is the outcome, which then enables further malicious activity

## Recommendations:

 - Disable SSH login and password auth instead make it key-based only.
 - Add fail2ban or similar tool for automated banning of ip
 - Enforce strong, unique passwords / rate-limit login attempts
 - Enable automatic response (e.g. IP block) on rule 40112
 - Since rule.mail is enabled for this rule, confirm real email alerting is configured in production