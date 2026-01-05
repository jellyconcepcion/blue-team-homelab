# SOC Runbook — Investigating Privileged Access Activity

## Objective
Determine whether elevated privilege usage is authorized or represents
potential privilege escalation.

## Step-by-Step Investigation

1. Identify privileged access event
   - Windows: EventCode 4672
   - Linux: sudo activity in authentication logs

2. Confirm user identity
   - Verify username and associated role
   - Check if account is expected to have admin privileges

3. Review previous user activity
   - Look for prior authentication failures
   - Check for suspicious logins before elevation

4. Validate business justification
   - Was activity during business hours?
   - Is task consistent with user role?

5. Correlate with additional events
   - Process execution (Sysmon)
   - Service creation
   - Configuration changes

6. Document findings
   - User
   - Host
   - Commands or actions performed
   - Time of activity

7. Escalation Criteria
   - Non-admin user with elevated privileges
   - Privilege use following failed login attempts
   - Unusual timing or system targeted

## Outcome
- Authorized administrative activity
- Unauthorized privilege escalation

## Related MITRE Technique
T1068 – Privilege Escalation