# Detection 04	: Rare Process Execution (Sysmon – Windows)

## Purpose
Detect potentially malicious or abnormal process executions
that occur infrequently on Windows systems.

## Data Source
Sysmon Operational Logs  
(Microsoft-Windows-Sysmon/Operational)

## SPL Query
index=windows_logs sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
| rex field=_raw "<Data Name='Image'>(?<Image>[^<]+)</Data>"
| rex field=_raw "<Data Name='CommandLine'>(?<CommandLine>[^<]*)</Data>"
| rex field=_raw "<Data Name='User'>(?<User>[^<]*)</Data>"
| table _time host Image CommandLine User
| sort -_time

## Detection Logic
- Captures process path, command line, and executing user
- Enables identification of low-frequency or unusual executions
- Supports hunting for malware and living-off-the-land techniques

## MITRE ATT&CK
T1059 – Command and Scripting Interpreter  
T1204 – User Execution

## Expected False Positives
- Legitimate one-time administrative tools
- Software installers or updates

## Analyst Actions
- Validate process legitimacy and path
- Investigate command-line arguments
- Correlate with network or privilege events