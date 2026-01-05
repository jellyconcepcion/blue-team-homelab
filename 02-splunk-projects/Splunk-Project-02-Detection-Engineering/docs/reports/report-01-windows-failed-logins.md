# Detection 01: Windows Failed Authentication Attempts

## Purpose

Identify brute-force or password-spraying attacks against Windows endpoints.

## Data Source

Windows Security Event Log (EventCode 4625)

## SPL Query

index=windows\_logs EventCode=4625
| bucket \_time span=5m
| stats count by \_time host Account\_Name Source\_Network\_Address
| where count >= 5
| sort -count
| table \_time host Account\_Name Source\_Network\_Address count

## Detection Logic

* Buckets failed logins into 5-minute windows
* Triggers when 5 or more failures occur

## MITRE ATT\&CK

T1110 – Brute Force

## Expected False Positives

* User password mistakes
* Automated scripts

## Analyst Actions

* Validate source IP reputation
* Check for successful logons after failures
* Correlate with privilege events
