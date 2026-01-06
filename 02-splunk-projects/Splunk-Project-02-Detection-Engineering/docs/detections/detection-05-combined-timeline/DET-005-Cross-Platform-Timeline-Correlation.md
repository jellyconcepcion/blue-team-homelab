# DET-005 — Cross-Platform Timeline Correlation

## Detection Overview
Provides a unified, time-ordered view of Windows and Linux security events, correlating failed logins, privileged activity, and rare process execution to support incident investigation and timeline reconstruction.

## Data Sources
- Windows Security Logs (EventCodes 4625, 4672)
- Linux Authentication Logs (/var/log/auth.log)
- Sysmon Process Create (Event ID 1)
- Splunk indexes: `windows_logs`, `security_logs`

## SPL Query
```spl
(index=windows_logs OR index=security_logs)
| rex field=_raw "<Data Name='Image'>(?<Image>[^<]+)</Data>"
| rex field=_raw "<Data Name='CommandLine'>(?<CommandLine>[^<]*)</Data>"
| rex field=_raw "<Data Name='User'>(?<win_user>[^<]*)</Data>"
| rex "Failed password for (invalid user )?(?<linux_user>\S+)"
| rex "from (?<src_ip>\d+\.\d+\.\d+\.\d+)"
| eval user=coalesce(Account_Name, win_user, linux_user)
| eval source_ip=coalesce(Source_Network_Address, src_ip)
| table _time host user EventCode Image CommandLine source_ip
| sort -_time
```

Detection Logic
• Normalizes fields across Windows and Linux logs
• Correlates multiple event types: failed logins, privileged logons, rare process execution
• Produces a unified timeline for SOC investigation

Severity
Medium

MITRE ATT&CK Mapping
• T1110 – Brute Force
• T1059 – Command and Scripting Interpreter
• T1547 – Persistence

Expected False Positives
• Normal administrative activity
• Legitimate cross-platform user activity

Analyst Response Guidance
1. Review correlated timeline for unusual patterns
2. Identify potential lateral movement or privilege escalation
3. Focus on accounts with multiple suspicious events
4. Escalate if cross-platform suspicious activity persists

Notes
Validated using lab-generated events from both Windows and Linux endpoints.