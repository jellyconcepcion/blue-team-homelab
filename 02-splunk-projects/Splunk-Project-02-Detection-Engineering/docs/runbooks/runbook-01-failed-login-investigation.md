# SOC Runbook — Investigating Failed Authentication Attempts

## Objective
Investigate repeated failed authentication attempts to determine whether
activity represents brute-force behavior or benign user error.

## Step-by-Step Investigation

1. Run the failed authentication detection query in Splunk
   - index=windows_logs EventCode=4625
   - index=security_logs ("Failed password" OR "Invalid user")

2. Adjust time range
   - Review last 15–60 minutes
   - Expand window if activity appears persistent

3. Identify source IP address
   - Determine if failures originate from a single or multiple IPs
   - Check if IP is internal or external

4. Count failures per user
   - Identify targeted accounts
   - Note if privileged accounts are affected

5. Check for successful authentication after failures
   - Search for EventCode 4624 (Windows) or successful SSH logins (Linux)
   - Determine if brute force succeeded

6. Assess attack pattern
   - High volume in short timeframe?
   - Sequential usernames?
   - Repeated attempts from same source?

7. Document findings
   - Time range
   - Source IP(s)
   - Affected users
   - Outcome (failed only vs successful compromise)

8. Escalation Criteria
   - Successful login after failures
   - Privileged account targeted
   - External IP with high failure volume

## Outcome
- False Positive: User error or expected behavior
- True Positive: Brute-force or credential attack

## Related MITRE Technique
T1110 – Brute Force