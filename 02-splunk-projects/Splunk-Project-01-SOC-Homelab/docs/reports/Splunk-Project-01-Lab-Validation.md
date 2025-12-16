# Splunk Project 01 — Lab Validation Report

## Objective
Validate that the Splunk SIEM lab is fully operational and receiving logs
from both Windows and Linux endpoints.

## Lab Overview
- SIEM: Splunk Enterprise 10.x (Ubuntu Server 24.04)
- Endpoints:
  - Windows 11 Pro (Universal Forwarder + Sysmon)
  - Ubuntu Server (rsyslog / UF)
- Network: VirtualBox Host-only + NAT

## Log Sources Validated
| Host | OS | Index | Log Type |
|----|----|------|---------|
| win11-endpoint | Windows 11 | windows_logs | WinEventLog, Sysmon |
| ubuntu-endpoint | Ubuntu 24.04 | security_logs | auth, sudo, syslog |

## Validation Steps
1. Confirmed UF services running on endpoints
2. Verified receiving port (9997) active on Splunk
3. Queried indexes in Splunk Web UI
4. Confirmed host and sourcetype visibility

## Evidence
- Splunk search showing Windows logs
- Splunk search showing Linux authentication logs
- Combined dashboard view

## Result
The SIEM lab is fully operational and ready for detection engineering.

## Next Steps
- Develop detection logic
- Build dashboards
- Simulate attack activity