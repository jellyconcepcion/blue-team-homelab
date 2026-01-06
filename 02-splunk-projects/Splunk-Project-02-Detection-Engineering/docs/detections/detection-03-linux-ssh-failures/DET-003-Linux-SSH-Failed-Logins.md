# DET-003 — Linux SSH Failed Logins

## Detection Overview
Detects repeated SSH authentication failures on Linux hosts, indicating potential brute-force or credential-guessing attacks.

## Data Sources
- Linux Authentication Logs (`/var/log/auth.log`)
- Splunk index: `security_logs`

## SPL Query
```spl
index=security_logs sourcetype=linux_secure ("Failed password" OR "Invalid user")
| rex "Failed password for (invalid user )?(?<user>\S+)"
| rex "from (?<src_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by host user src_ip
| where count >= 3
| sort -count
```

Detection Logic
• Groups failed SSH login attempts by host, user, and source IP
• Triggers when ≥3 failures occur
• Helps identify brute-force attempts or unauthorized access

Severity
Medium

MITRE ATT&CK Mapping
• T1110 – Brute Force

Expected False Positives
• Legitimate mistyped passwords
• Service or automation scripts attempting authentication

Analyst Response Guidance
1. Identify offending source IP addresses
2. Check for successful SSH logins after failures
3. Review account privileges and login history
4. Escalate if repeated attempts persist or originate externally

Notes
Detection validated in Ubuntu lab; threshold set to minimize noise while capturing suspicious activity.
