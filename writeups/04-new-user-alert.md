## Context-Based Triage — New User Account Alert

Created a new user account for legitimate personal use which caused Wazuh to generate a new alert same as it would if it was a real attacker which shows alert triage requires context, not just the log entry.

## Setup

 - **Agent:** Kali (agent 002)
 - **Action:** Created a new user "tester" via useradd, set a password, logged in as that user — for genuine personal use, not attack simulation.

## Alert Detected: 

 - **Rule id:** 5501, 5902
 - **Level:** 3 & 8(Low & Medium)
 - **Agent ip:** 192.168.29.7
 - New user added to the system.
 - **MITRE Techniques:** T1078(Valid Accounts), T1136(Create Account)
 - **Tactics:** Defense Evasion, Persistence, Privilege Escalation, Initial Access

## Analysis / Triage

 - **Verdict:** True Positive detection
 - **Key point:** *useradd* looks identical in the logs whether run by the system owner or by an attacker who gained access and wants to persist. 
 - **Real-world persistence relevance:** attackers commonly create new accounts after initial compromise, so they can keep access even if the original entry point (stolen password, exploited service) is later discovered and closed. That's why this rule exists and why it's mapped to MITRE T1136 (Persistence).
 - The actual analyst skill here is judgment, not detection: deciding whether an account-creation alert is authorized requires checking context outside the log.

## Recommendations

 - Maintain a record of authorized account creations so alerts like this can be quickly confirmed as expected. 
 - Regularly audit existing accounts against what's actually authorized.
 - Restrict who can run useradd in shared/production environments (least privilege)