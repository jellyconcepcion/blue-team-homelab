# Incident Report — INC-003 Linux SSH Failed Logins

## Detection Reference
- Detection ID: DET-003
- Title: Linux SSH Failed Logins
- Severity: Medium
- Category: Authentication
- MITRE ATT&CK: T1110

## Date Observed
2026-01-06

## Incident Summary
Multiple SSH authentication failures were detected against a Linux host, indicating a possible brute-force attempt.

## Detection Trigger
Splunk Report: DET-003-Linux-SSH-Failed-Logins  
Threshold: ≥3 failed attempts

## Timeline of Events
| Time (UTC) | Host | User | Source IP | Event |
|-----------|------|------|-----------|------|
| 09:13 | splunk-lab-01 | labadmin | 192.168.56.10 | Failed SSH login |

## Investigation Steps
1. Identified source IP
2. Counted authentication failures
3. Checked for successful SSH logins
4. Verified user account legitimacy

## Screenshots Collected
- `INC-003-01-SSH-Failures-Panel.png`
- `INC-003-02-Source-IP-Analysis.png`
- `INC-003-03-Auth-Log-Correlation.png`

## Severity Assessment
**Medium**
- No confirmed compromise
- Repeated attempts indicate malicious intent

## Analyst Decision
• Benign user error  
• Misconfigured service  
• **Brute-force attempt** 

## Response Actions
- Block offending IP (if external)
- Harden SSH configuration
- Continue monitoring

## Escalation
Not escalated — monitored per SOC policy

## Final Disposition
**Attempted brute-force — no compromise**