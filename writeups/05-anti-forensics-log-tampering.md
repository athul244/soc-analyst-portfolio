## Anti-Forensics — Log Tampering Detection

Simulated commands to clear system logs (`auth.log`). Wazuh logged the log-clearing attempt via sudo's own audit trial, before being able to destroy the evidence.

## Setup

 - **Agent:** Kali (agent 002)
 - **Action:** Tried to clear logs of a session.

## Alert Detected: 

 - **Rule id:** 5402
 - **Level:** 3 (Low)
 - **Agent ip:** 192.168.29.7
 - Captured the exact command which attempted of clearing logs: truncate -s 0 /var/log/auth.log
 - **MITRE Techniques:** T1548.003(Sudo and Sudo Caching)
 - **Tactics:** Privilege Escalation, Defense Evasion

## Analysis / Triage

 - **Verdict:** True Positive
 - **Key point:** the attempt to erase evidence was itself logged, before the target log file could be wiped — sudo's own audit mechanism operates independently of the file being tampered with.
 - **Real-world relevance:** attackers clear logs post-compromise to avoid detection (classic anti-forensics / Defense Evasion).

## Recommendations

 - Forward logs to a remote/centralized SIEM in real-time (already in place here via Wazuh) so local tampering can't erase what's already been received.
 - Alert immediately on any `truncate`, `rm`, or similar command targeting log files via sudo.
 - Restrict/monitor who has sudo access to log directories at all.