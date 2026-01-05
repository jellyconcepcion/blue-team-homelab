# Report: Cross-Platform Log Visibility

## Objective
Validate centralized visibility of Windows and Linux logs in Splunk.

## SPL Query
index=* (host="splunk-lab-01" OR host="WIN11-LAB-01")
| table _time host index sourcetype EventCode message
| sort -_time

## Result
Events from both Windows and Linux hosts were visible in a unified timeline.

## Conclusion
Splunk Enterprise successfully centralizes logs across platforms.