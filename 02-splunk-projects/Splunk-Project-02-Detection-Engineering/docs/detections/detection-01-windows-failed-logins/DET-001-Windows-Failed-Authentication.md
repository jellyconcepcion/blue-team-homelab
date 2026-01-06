# DET-001 — Windows Failed Authentication (Brute Force)

## Detection Overview
Identifies potential brute-force or password-spraying attacks against Windows endpoints by detecting repeated failed logon attempts within a short time window.

## Data Sources
- Windows Security Event Log
- EventCode: 4625

## SPL Query
```spl
index=windows_logs EventCode=4625
| bucket _time span=5m
| stats count by _time host Account_Name Source_Network_Address
| where count >= 5
| sort -count
| table _time host Account_Name Source_Network_Address count
```

Detection Logic
• Groups failed logons into 5-minute windows
• Triggers when ≥5 failures occur
• Correlates by host, account, and source IP

Severity
Medium → High
(Escalates to High if followed by successful login)

MITRE ATT&CK Mapping
• T1110 – Brute Force

Expected False Positives
• User mistyping password
• Automated scripts using outdated credentials

Analyst Response Guidance
1. Identify source IP reputation
2. Check for successful logon events (4624) after failures
3. Review privilege usage (4672)
4. Escalate if pattern persists or spreads

Notes
Detection validated using simulated brute-force activity in lab environment.