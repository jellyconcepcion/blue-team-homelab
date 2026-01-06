# Incident Report — INC-002 Windows Privileged Logon

## Detection Reference
- Detection ID: DET-002
- Title: Windows Privileged Logon (Non-System Accounts)
- Severity: High
- Category: Privilege Escalation
- MITRE ATT&CK: T1078, T1068

## Date Observed
2026-01-06

## Incident Summary
A non-system Windows account was observed logging in with administrative privileges. This activity may indicate privilege escalation or misuse of valid credentials.

## Detection Trigger
Splunk Report: DET-002-Windows-Privileged-Logon  
EventCode: 4672

## Timeline of Events
| Time (UTC) | Host | User | Event |
|-----------|------|------|------|
| 09:59 | WIN11-LAB-01 | labuser | Privileged logon detected |
| 08:03 | WIN11-LAB-01 | labuser | Privileged logon detected |
| 08:03 | WIN11-LAB-01 | SplunkForwarder | Privileged logon detected |
| 08:03 | WIN11-LAB-01 | DWM-1 | Privileged logon detected |
| 08:03 | WIN11-LAB-01 | DWM-1 | Privileged logon detected |

## Investigation Steps
1. Reviewed account name and privileges
2. Checked for prior failed authentication attempts
3. Searched for lateral movement indicators
4. Reviewed post-login activity (process execution)

## Screenshots Collected
- `INC-002-01-Privileged-Logon-Alert.png`
- `INC-002-02-Account-Context.png`
- `INC-002-03-Post-Login-Activity.png`

## Severity Assessment
**High**
- Administrative privileges significantly increase impact
- Requires validation of authorization

## Analyst Decision
• Authorized admin activity  
• Suspicious but inconclusive  
• **Unauthorized privilege use**

## Response Actions
- Validate account ownership
- Reset credentials if unauthorized
- Monitor account for further activity

## Escalation
Escalated to SOC Lead for confirmation and access review.

## Final Disposition
**Confirmed suspicious privileged access — escalated**
