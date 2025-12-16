# Splunk Project 01 – SOC Home Lab

## Overview
This project simulates a professional Security Operations Center (SOC)
environment using Splunk Enterprise as a SIEM platform.

A centralized Splunk server on Ubuntu collects and analyzes logs from:
- Ubuntu Linux endpoint
- Windows 11 Pro endpoint with Sysmon telemetry

## Objectives
- Deploy Splunk Enterprise on Ubuntu 24.04
- Configure Universal Forwarders on Windows and Linux
- Validate secure log forwarding over TCP 9997
- Perform first SOC detections
- Document the lab professionally with screenshots, SHA verification, and snapshots

## Architecture
See `docs/Splunk-Architecture-Diagram.png`

## Data Sources
- Linux syslog & auth.log
- Windows Event Logs (Security, System, Application)
- Sysmon Operational logs

## Detections Implemented
- Failed Windows logon attempts (Event ID 4625)
- New Windows service creation (Event ID 7045)
- Failed SSH logins on Ubuntu
- sudo usage on Ubuntu

## Evidence
- SHA512 verification for all binaries
- Screenshots for every critical step
- VirtualBox snapshots at major milestones

## Status
✅ Project completed  
🔜 Future enhancements: dashboards, alerting, correlation rules
