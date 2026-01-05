# SOC Playbook — Linux SSH Failed Logins

## Purpose
Detect repeated SSH authentication failures that may indicate
external brute-force or credential-guessing attacks.

## Data Sources
- Linux Authentication Logs (/var/log/auth.log)

## Relevant Indexes
- security_logs

## Detection Logic
index=security_logs ("Failed password" OR "Invalid user")

## Security Significance
- SSH is a common external attack vector
- May lead to unauthorized system access
- Often automated by bots

## Common False Positives
- User typing errors
- Misconfigured SSH clients
- Automation or monitoring tools

## Triage Questions
- Source IP reputation?
- Targeted usernames?
- Frequency and duration?
- Any successful login afterward?

## Response Actions
- Monitor if low volume
- Block malicious IPs
- Disable targeted accounts if needed
- Escalate if compromise suspected

## MITRE ATT&CK Mapping
T1110 – Brute Force