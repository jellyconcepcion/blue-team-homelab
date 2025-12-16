# Configuration Files – Splunk Project 01

This folder contains all configuration files used in Splunk Project 01.
They are organized by system role to reflect real SOC environments.

## Splunk Server
- `inputs.conf` – Enables TCP receiving on port 9997

## Ubuntu Universal Forwarder
- `inputs.conf` – Monitors syslog and auth logs
- `outputs.conf` – Forwards logs to Splunk Enterprise

## Windows Universal Forwarder
- `inputs.conf` – Collects Security, System, Application, and Sysmon logs
- `outputs.conf` – Forwards logs to Splunk Enterprise

## Sysmon
- `sysmon-config.xml` – SwiftOnSecurity configuration used to enhance Windows telemetry

## Supply Chain Integrity
- SHA512 files verify integrity of Splunk Enterprise, Universal Forwarder, and Sysmon binaries

Indexes were created via Splunk Web UI and validated through ingestion and searches.