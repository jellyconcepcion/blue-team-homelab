# Report: Windows Brute-Force Log Visibility Validation

## Objective
Validate that failed Windows authentication attempts are successfully collected and searchable in Splunk Enterprise.

## Test Activity
- Windows 11 Pro VM
- Screen locked and 6 consecutive incorrect passwords entered

## SPL Query
index=windows_logs EventCode=4625

## Expected Result
- Multiple EventCode 4625 entries
- Correct host attribution
- Account and source information present

## Result
Failed authentication events were successfully ingested and visible in Splunk, confirming correct Windows Security Event log forwarding.

## Conclusion
Windows authentication telemetry is correctly collected and suitable for
brute-force detection logic.