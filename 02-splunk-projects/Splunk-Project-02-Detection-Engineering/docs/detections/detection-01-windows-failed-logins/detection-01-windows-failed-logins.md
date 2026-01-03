### Detection: Windows Failed Authentication Attempts

Purpose:
Identify brute-force or password-spraying attacks against Windows endpoints.

Data Source:
Windows Security Event Log (EventCode 4625)

Detection Logic:
Counts failed login attempts per account and source IP within a 5-minute window.
Triggers when 5 or more failures occur.

SPL Query:
index=windows\_logs EventCode=4625
| bucket \_time span=5m
| stats count by \_time host Account\_Name Source\_Network\_Address
| where count >= 5
| sort -count
| table \_time host Account\_Name Source\_Network\_Address

MITRE ATT\&CK:
T1110 – Brute Force

Expected False Positives:
• Users mistyping passwords
• Automated login scripts

Analyst Actions:
• Validate source IP reputation
• Check for successful logons following failures
• Correlate with admin privilege events

