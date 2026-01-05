# Detection 05: Combined Timeline Correlation (Windows & Linux)

## Purpose
Provide a unified investigative timeline across Windows and Linux
systems to support SOC event correlation and incident analysis.

## Data Source
- Windows Security Logs
- Linux Authentication Logs
- Sysmon Process Creation Logs

## SPL Query
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

## Detection Logic
- Normalizes user and source IP fields across platforms
- Aggregates security-relevant events into a single timeline
- Enables investigation of multi-stage or cross-platform attacks

## MITRE ATT&CK
T1082 – System Information Discovery  
T1110 – Brute Force  
T1059 – Command and Scripting Interpreter

## Expected False Positives
- Routine administrative activity
- Scheduled jobs and maintenance tasks

## Analyst Actions
- Identify suspicious event sequences
- Pivot to related detections
- Establish incident timelines and scope