# Detection: Rare Process Execution

**Purpose:**  
Identify processes that execute rarely on Windows endpoints, which may indicate malware, suspicious activity, or abnormal user behavior.

**Data Source:**  
Windows Sysmon Event Logs

**Detection Logic:**  
- Extracts the process executable path (`Image`), full command line (`CommandLine`), and the user (`User`) from Sysmon event logs.  
- Counts occurrences of each executable (`Image`) to find rare or unusual executions.  
- Analysts investigate processes that appear infrequently or unexpectedly.  

**SPL Query:**
```spl
index=windows_logs sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
| rex field=_raw "<Data Name='Image'>(?<Image>[^<]+)</Data>"
| rex field=_raw "<Data Name='CommandLine'>(?<CommandLine>[^<]*)</Data>"
| rex field=_raw "<Data Name='User'>(?<User>[^<]*)</Data>"
| table _time host Image CommandLine User
| sort -_time

MITRE ATT&CK:
T1059 – Command and Scripting Interpreter

Expected False Positives:
One-time admin scripts
Software updates
Scheduled maintenance tasks

Analyst Actions:
Verify executable location and file hash
Compare against whitelist and known software
Correlate with network connections, logon activity, and process ancestry