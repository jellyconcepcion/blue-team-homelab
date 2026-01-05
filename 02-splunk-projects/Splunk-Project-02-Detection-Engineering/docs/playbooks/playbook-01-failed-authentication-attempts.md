# SOC Playbook — Failed Authentication Attempts

## Purpose
Detect and investigate repeated failed authentication attempts that may indicate brute-force attacks, credential stuffing, or account misuse.

## Data Sources
- Windows Security Event Log
- Linux Authentication Logs
- Sysmon (optional enrichment)

## Relevant Indexes
- windows_logs
- security_logs

## Detection Logic

### Windows
index=windows_logs EventCode=4625

### Linux
index=security_logs ("Failed password" OR "Invalid user")

## Security Significance
- Indicates potential brute-force activity
- May precede account compromise
- Often a precursor to lateral movement

## Common False Positives
- Users mistyping passwords
- Outdated service account credentials
- Users returning after long inactivity

## Triage Questions
- How many failures occurred?
- Over what time window?
- Same source IP or multiple?
- Same username or multiple accounts?
- Is the account privileged?

## Response Actions
- Monitor if low volume
- Lock account if threshold exceeded
- Block source IP if malicious
- Escalate if a successful login follows

## MITRE ATT&CK Mapping
T1110 – Brute Force