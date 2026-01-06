# DET-002 — Windows Privileged Logon (Non-System Accounts)

## Detection Overview
Identifies non-system Windows accounts that logged in with administrative privileges, which may indicate privilege escalation or misuse of high-privilege accounts.

## Data Sources
- Windows Security Logs
- EventCode: 4672

## SPL Query
```spl
index=windows_logs EventCode=4672
| search NOT Account_Name="SYSTEM" AND NOT Account_Name="LOCAL SERVICE" AND NOT Account_Name="NETWORK SERVICE"
| table _time host Account_Name
| sort -_time
```

Detection Logic
• Excludes system accounts to reduce noise
• Flags logins by non-system accounts with administrative privileges
• Supports investigation of potential privilege escalation attempts

Severity
High — administrative access misuse can lead to full system compromise

MITRE ATT&CK Mapping
• T1078 – Valid Accounts
• T1068 – Privilege Escalation

Expected False Positives
• Legitimate administrative logins
• Service accounts performing authorized tasks

Analyst Response Guidance
1. Verify the account’s role and authorization
2. Correlate with recent failed logins or suspicious activity
3. Check for lateral movement or high-risk actions post-login
4. Escalate if unauthorized or anomalous activity detected

Notes
Detection validated with Windows lab environment; patterns match typical SOC escalation alerts.