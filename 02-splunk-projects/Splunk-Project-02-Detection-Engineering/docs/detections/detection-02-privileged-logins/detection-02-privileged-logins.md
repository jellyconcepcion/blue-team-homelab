\# Detection: Privileged / Admin Logins (Excluding System Accounts)



\*\*Purpose:\*\*

Detect potential privilege escalation by identifying non-system accounts obtaining administrative privileges.



\*\*Data Source:\*\*

Windows Security Event Log (EventCode 4672)



\*\*Detection Logic:\*\*

\- Counts logins by non-standard admin accounts

\- Filters out routine SYSTEM, LOCAL SERVICE, and NETWORK SERVICE logins

\- Triggers when any unusual admin account logs in



\*\*SPL Query:\*\*

index=windows\_logs EventCode=4672

| search NOT Account\_Name="SYSTEM" AND NOT Account\_Name="LOCAL SERVICE" AND NOT Account\_Name="NETWORK SERVICE"

| table \_time host Account\_Name

| sort -\_time





\*\*MITRE ATT\&CK:\*\*

\- T1078 – Valid Accounts

\- T1548 – Abuse Elevation Control Mechanism



\*\*Expected False Positives:\*\*

\- Admin accounts logging in during routine maintenance windows

\- Scheduled automation using privileged accounts



\*\*Analyst Actions:\*\*

\- Validate unusual admin account logins

\- Correlate with failed login attempts or suspicious activity

\- Confirm legitimacy with endpoint owner or IT team

