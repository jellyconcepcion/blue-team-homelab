# SOC Runbook — Investigating Suspicious Process Execution

## Objective
Analyze unusual or rare process execution to identify potential malware
or unauthorized activity.

## Step-by-Step Investigation

1. Identify suspicious process event
   - Use Sysmon Process Create logs
   - Review process name, path, and command line

2. Examine execution context
   - Parent process
   - Executing user
   - Time of execution

3. Validate process legitimacy
   - Is the binary in a standard path?
   - Is it digitally signed?
   - Does it align with expected system behavior?

4. Search for similar executions
   - Same process on other hosts?
   - One-time execution or repeated?

5. Correlate with other detections
   - Failed logins
   - Privileged access
   - Network activity

6. Document findings
   - Process details
   - Host and user
   - Supporting evidence

7. Response Actions
   - Kill process if malicious
   - Isolate endpoint if necessary
   - Preserve evidence for escalation

## Escalation Criteria
- Unsigned binary
- Execution from user-writable directories
- Correlation with authentication anomalies

## Related MITRE Technique
T1059 – Command and Scripting Interpreter