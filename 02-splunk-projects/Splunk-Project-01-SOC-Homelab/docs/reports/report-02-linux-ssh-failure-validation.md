# Report: Linux SSH Authentication Failure Visibility

## Objective
Validate ingestion of Linux SSH authentication failures.

## Test Activity
- SSH attempted to Ubuntu server
- 4 consecutive incorrect passwords used

## SPL Query
index=security_logs ("Failed password" OR "authentication failure")

## Expected Result
- SSH failure events visible
- Correct host attribution

## Result
SSH authentication failure events were observed in Splunk, confirming Linux
auth.log ingestion.

## Conclusion
Linux SSH telemetry is correctly forwarded and ready for detection engineering.