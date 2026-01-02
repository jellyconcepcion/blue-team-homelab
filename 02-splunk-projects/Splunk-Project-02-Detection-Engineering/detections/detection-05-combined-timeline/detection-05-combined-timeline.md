# Detection: Combined Timeline Correlation

**Purpose:**  
Provide a unified timeline of Windows and Linux security events to support investigation and incident triage.

**Data Source:**  
• Windows Security Event Logs  
• Windows Sysmon Logs  
• Linux Authentication Logs (`/var/log/auth.log`)

**Detection Logic:**  
Normalizes user and source IP fields across Windows and Linux logs to present a single chronological event timeline.  
This view enables analysts to correlate authentication events, process execution, and suspicious activity across hosts.

**Field Availability Notes:**  
Not all events contain `source_ip` or `EventCode` fields.  
This is expected behavior depending on the log type:
- Local system and service events do not generate network source IPs
- Linux authentication logs only include IP addresses for remote (SSH) activity  
Missing fields indicate normal log behavior, not detection failure.

**SPL Query:**
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

**MITRE ATT&CK:**  
Multiple techniques depending on correlated activity

**Expected False Positives:**  
• Normal system operations  
• Scheduled tasks and maintenance activity  

**Analyst Actions:**  
• Identify suspicious sequences of events  
• Correlate failed logins with privileged access  
• Use as starting point for incident investigation