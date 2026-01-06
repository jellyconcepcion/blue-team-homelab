# Incident Report — INC-005 Cross-Platform Correlation

## Detection Reference
- Detection ID: DET-005
- Title: Cross-Platform Timeline Correlation
- Severity: Medium
- Category: Investigation
- MITRE ATT&CK: T1110, T1059, T1547

## Date Observed
2026-01-06

## Incident Summary
Correlated Windows and Linux security events revealed a sequence of authentication failures and suspicious activity across platforms.

## Detection Trigger
Splunk Report: DET-005-Cross-Platform-Timeline-Correlation

## Unified Timeline
| Time (UTC) | Host | User | Event |
|-----------|------|------|------|
| 12:20 | WIN11-LAB-01 | WIN11-LAB-01\labuser | Privileged logon |
| 12:19 | splunk-lab-01 | labadmin | SSH failures |
| 12:15 | WIN11-LAB-01 | WIN11-LAB-01\labuser | Rare process execution |

## Investigation Steps
1. Built cross-platform timeline
2. Normalized users and IP addresses
3. Checked for lateral movement
4. Reviewed privilege usage

## Screenshots Collected
- `INC-005-01-Unified-Timeline.png`
- `INC-005-02-Windows-Events.png`
- `INC-005-03-Linux-Events.png`

## Severity Assessment
**Medium**
- Multi-stage behavior
- No confirmed compromise

## Analyst Decision
• Coincidental activity  
• Misconfiguration  
• **Suspicious pattern detected**

## Response Actions
- Monitor affected accounts
- Enhance correlation rules
- Document findings

## Escalation
Escalated for visibility only

## Final Disposition
**Suspicious but contained**