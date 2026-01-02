# Detection: Linux SSH Failed Authentication Attempts

## Purpose
Detect repeated SSH authentication failures against Linux systems that may indicate brute-force or credential-guessing attacks.

## Data Source
Ubuntu Linux security logs (`/var/log/auth.log`) collected and forwarded to Splunk using **Splunk Universal Forwarder 10.0.2**.

## Detection Logic
Counts failed SSH login attempts grouped by host, user, and source IP address.  
Triggers when **three (3) or more failed authentication attempts** are observed within the selected time range.

## SPL Query
```spl
index=security_logs sourcetype=linux_secure ("Failed password" OR "Invalid user")
| rex "Failed password for (invalid user )?(?<user>\S+)"
| rex "from (?<src_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by host user src_ip
| where count >= 3
| sort -count

MITRE ATT&CK Mapping

T1110 – Brute Force

Expected False Positives

Users mistyping passwords

Automated scripts or monitoring tools

Misconfigured services attempting authentication

Analyst Actions

Validate the source IP reputation and ownership

Check for successful logins following repeated failures

Correlate with other authentication or privilege-related events

Assess whether the activity aligns with normal administrative behavior

Lab Notes

In this lab environment, the source IP may appear identical to the host IP due to NAT and single-host virtualization.
In production environments, this detection typically reveals external attacker IP addresses targeting SSH services.