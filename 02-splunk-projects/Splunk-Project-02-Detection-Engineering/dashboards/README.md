# SOC Security Monitoring Dashboard

This dashboard consolidates five core security detections across Windows and Linux systems into a single SOC monitoring view.  
It enables analysts to quickly identify authentication attacks, privilege escalation, suspicious process execution, and correlate events across platforms during investigations.

## Included Detections

| Panel | Purpose |
|-------|---------|
| Windows Failed Logins | Detect brute-force and password-spraying attempts |
| Privileged Admin Logins | Identify non-system accounts with admin privileges |
| Linux SSH Failed Logins | Detect repeated SSH login failures on Linux hosts |
| Rare Process Execution | Highlight unusual Windows processes via Sysmon |
| Combined Timeline Correlation | Unified, time-ordered view for cross-platform correlation |

All panels use **Statistics Table visualization** for clear SOC-style analysis.  
Individual panel screenshots are provided in this folder.