# Incident Report — INC-004 Windows Rare Process Execution

## Detection Reference
- Detection ID: DET-004
- Title: Windows Rare Process Execution
- Severity: Low–Medium
- Category: Endpoint Behavior
- MITRE ATT&CK: T1059, T1547

## Date Observed
2026-01-06

## Incident Summary
A rarely observed process was executed on a Windows endpoint. The activity required validation to determine if it was benign or malicious.

## Detection Trigger
Splunk Report: DET-004-Windows-Rare-Process-Execution  
Sysmon Event ID: 1

## Timeline of Events
| Time (UTC) | Host | User | Process |
|-----------|------|------|--------|
| 12:10 | WIN11-LAB-01 | WIN11-LAB-01\labuser | Uncommon binary execution |

## Investigation Steps
1. Reviewed process name and path
2. Inspected command-line arguments
3. Verified user context
4. Checked digital signature

## Screenshots Collected
- `INC-004-01-Rare-Process-Alert.png`
- `INC-004-02-CommandLine-Details.png`
- `INC-004-03-User-Context.png`

## Severity Assessment
**Low–Medium**
- Rare does not equal malicious
- Requires analyst judgment

## Analyst Decision
• Known benign tool  
• Admin testing  
• **Requires monitoring**

## Response Actions
- Add to baseline if confirmed benign
- Monitor future executions

## Escalation
Not escalated

## Final Disposition
**Benign rare activity — documented**