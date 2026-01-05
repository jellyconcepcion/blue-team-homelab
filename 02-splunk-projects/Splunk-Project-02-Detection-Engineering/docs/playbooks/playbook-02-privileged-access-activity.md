# SOC Playbook — Privileged Access Activity

## Purpose
Identify suspicious or unauthorized use of administrative privileges
that may indicate privilege escalation or account abuse.

## Data Sources
- Windows Security Event Log
- Linux Authentication Logs

## Relevant Indexes
- windows_logs
- security_logs

## Detection Logic

### Windows (High Privilege Logon)
index=windows_logs EventCode=4672

### Linux (sudo Usage)
index=security_logs sudo

## Security Significance
- Privileged access allows full system control
- Often follows initial access
- High-risk when performed by non-admin users

## Common False Positives
- System administrators performing routine tasks
- Scheduled maintenance activities

## Triage Questions
- Who performed the action?
- Is this user authorized?
- Was the activity expected?
- Did it occur outside business hours?

## Response Actions
- Validate user authorization
- Review command history
- Correlate with prior authentication events
- Escalate if suspicious

## MITRE ATT&CK Mapping
T1068 – Privilege Escalation