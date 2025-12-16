# Splunk Project 01 — First Detection Summary

## Objective
Demonstrate basic SOC detections using collected endpoint logs.

## Detections Implemented

### 1. Failed Login Attempts
- Index: security_logs
- Platform: Ubuntu
- Use Case: Detect brute-force or credential misuse

Example Query:
index=security_logs "Failed password"


### 2. Successful Sudo Usage
- Index: security_logs
- Platform: Ubuntu
- Use Case: Detect privilege escalation

### 3. New Windows Service Creation
- Index: windows_logs
- Platform: Windows 11
- Use Case: Detect persistence mechanisms

## Findings
- Logs were successfully detected in real time
- Host and user attribution visible
- Events correlated across endpoints

## SOC Relevance
These detections form the baseline for:
- Brute-force monitoring
- Privilege abuse detection
- Persistence detection