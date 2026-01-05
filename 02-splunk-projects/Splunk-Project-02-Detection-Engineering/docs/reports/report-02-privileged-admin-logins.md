# Detection 02: Privileged Admin Logins (Non-System)

## Purpose
Detect potential privilege escalation or misuse by identifying logins performed by non-system accounts with administrative privileges.

## Data Source
Windows Security Event Log (EventCode 4672)

## SPL Query
index=windows_logs EventCode=4672
| search NOT Account_Name="SYSTEM" AND NOT Account_Name="LOCAL SERVICE" AND NOT Account_Name="NETWORK SERVICE"
| table _time host Account_Name
| sort -_time

## Detection Logic
- Monitors privileged logon events (EventCode 4672)
- Filters out routine SYSTEM and service accounts
- Highlights administrative access by human users

## MITRE ATT&CK
T1078 – Valid Accounts

## Expected False Positives
- Legitimate administrative logins
- Scheduled maintenance activity

## Analyst Actions
- Verify if the account normally performs admin actions
- Correlate with process creation or service installation events
- Confirm change management or ticket approval