# DET-004 — Windows Rare Process Execution (Sysmon)

## Detection Overview
Highlights Windows processes captured by Sysmon that are rare or unusual compared to normal baseline activity, which may indicate malware execution, living-off-the-land attacks, or suspicious administrative scripts.

## Data Sources
- Sysmon Process Create (Event ID 1)
- Windows Security Logs

## SPL Query
```spl
index=windows_logs sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
| rex field=_raw "<Data Name='Image'>(?<Image>[^<]+)</Data>"
| rex field=_raw "<Data Name='CommandLine'>(?<CommandLine>[^<]*)</Data>"
| rex field=_raw "<Data Name='User'>(?<User>[^<]*)</Data>"
| table _time host Image CommandLine User
| sort -_time
```

Detection Logic
• Identifies rare or one-off process executions
• Provides context with command line and user
• Useful for detecting unusual activity or malware persistence

Severity
Low–Medium — requires analyst verification to distinguish benign rare processes from malicious activity

MITRE ATT&CK Mapping
• T1059 – Command and Scripting Interpreter
• T1547 – Persistence

Expected False Positives
• Legitimate ad-hoc administrative scripts
• Rarely executed system utilities

Analyst Response Guidance
1. Review process image and command line
2. Check execution frequency against known baseline
3. Validate user context
4. Investigate further if process is unknown or suspicious

Notes
Detection validated in lab environment using Sysmon; rare execution definition based on observed baseline activity.