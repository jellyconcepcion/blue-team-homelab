# Detection 03: Linux SSH Failed Authentication Attempts

## Purpose
Identify potential brute-force or credential-guessing attacks
against Linux systems via SSH.

## Data Source
Linux authentication logs (`/var/log/auth.log`)

## SPL Query
index=security_logs sourcetype=linux_secure ("Failed password" OR "Invalid user")
| rex "Failed password for (invalid user )?(?<user>\S+)"
| rex "from (?<src_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by host user src_ip
| where count >= 3
| sort -count

## Detection Logic
- Extracts usernames and source IPs from SSH failure messages
- Counts repeated failures per user and IP
- Triggers on 3 or more failed attempts

## MITRE ATT&CK
T1110 – Brute Force

## Expected False Positives
- User mistyping passwords
- Configuration or automation errors

## Analyst Actions
- Check source IP reputation
- Verify targeted usernames
- Correlate with successful SSH logins