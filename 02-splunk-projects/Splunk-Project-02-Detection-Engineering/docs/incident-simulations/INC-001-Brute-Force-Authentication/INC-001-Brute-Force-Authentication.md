# Incident Report — INC-001

## Detection Reference
- Detection ID: DET-001
- Title: Brute Force Authentication
- Severity: Medium → High (Escalates to High if followed by successful login)
- Category: Authentication
- MITRE ATT&CK: T1110

## Incident Type
Suspected Brute-Force Authentication Attempt

## Date Observed
2026-01-06

## Detection Source
Splunk — DET-001 Windows Failed Authentication

## Summary
Multiple failed authentication attempts were observed against a Windows endpoint within a 5-minute window, originating from a single source IP. Activity pattern is consistent with brute-force behavior.

## Timeline of Events
| Time | Event |
|----|-----|
| 08:08 | Failed logon attempt |
| 08:08 | Failed logon attempt |
| 08:08 | Failed logon attempt |
| 08:09 | Failed logon attempt |
| 08:09 | Failed logon attempt |
| 08:09 | Failed logon attempt |

## Affected Assets
- Host: WIN11-LAB-01
- Account(s): labuser
- Source IP: 127.0.0.1

## Investigation Findings
- No successful authentication observed after failures
- No privilege escalation detected
- Activity confirmed as lab-generated
- Detection mapped to MITRE ATT&CK T1110 (Brute Force)

"## Screenshots Collected
- `INC-001-01-detection-trigger.png`
- `INC-001-02-raw-events.png`
- `INC-001-03-time-window.png`
- `INC-001-04-source-ip.png`
- `INC-001-05-dashboard-panel.png`

## Severity Assessment
Medium → High (Escalates to High if followed by successful login)

## Response Actions Taken
- Continued monitoring
- No containment required (lab environment)

## Lessons Learned
Detection logic validated. Thresholds appropriate for reducing noise.