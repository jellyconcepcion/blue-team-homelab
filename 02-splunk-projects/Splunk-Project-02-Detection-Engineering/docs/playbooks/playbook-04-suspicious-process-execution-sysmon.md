# SOC Playbook — Suspicious Process Execution (Sysmon)

## Purpose
Detect abnormal or potentially malicious process execution
on Windows endpoints using Sysmon telemetry.

## Data Sources
- Sysmon Process Creation Logs

## Relevant Indexes
- windows_logs

## Detection Logic
index=windows_logs sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"

## Security Significance
- Detects malware execution
- Identifies living-off-the-land techniques
- Useful for early-stage compromise detection

## Common False Positives
- Legitimate administrative tools
- Software installers or updates

## Triage Questions
- Parent process legitimacy?
- Execution path suspicious?
- Command-line arguments unusual?
- Is the process signed?

## Response Actions
- Validate process legitimacy
- Kill process if malicious
- Isolate endpoint if required
- Collect forensic artifacts

## MITRE ATT&CK Mapping
T1059 – Command and Scripting Interpreter