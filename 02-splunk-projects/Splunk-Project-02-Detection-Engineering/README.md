# Splunk Project 02 – Detection Engineering (SOC-Mature)

## Overview
This project builds on **Splunk Project 01** (log ingestion & UF configuration) and focuses on **detection engineering, incident simulation, reporting, and dashboards**.  
The goal is to create **SOC-style detections** across Windows and Linux endpoints, correlate events, and visualize them in a **unified SOC monitoring dashboard** for investigation and documentation.

This project demonstrates end-to-end SOC analyst workflows from detection creation to incident investigation.

---

## Core Features

### 1. SOC Detections Implemented
Five SOC-grade detections were created, validated, and documented:

| # | Detection | Platform / Data Source |
|---|----------|----------------------|
| 1 | Windows Failed Logins (Brute Force) | Windows Security Event Log, EventCode 4625 |
| 2 | Privileged Admin Logins (Non-System Accounts) | Windows Security Event Log, EventCode 4672 |
| 3 | Linux SSH Failed Logins | Linux Auth / Security Logs |
| 4 | Rare Process Execution | Windows Sysmon Event Log |
| 5 | Combined Windows & Linux Event Timeline | Cross-platform log correlation |

Each detection includes:
- SPL query with field extraction (`rex`, `eval`, `coalesce`)
- Thresholds and aggregation for **noise reduction**
- MITRE ATT&CK mapping
- Expected false positives and severity level
- Analyst response guidance

---

### 2. Detection Maturity & SOC Enhancements
Beyond building detections, the project demonstrates SOC maturity by including:

- **Improved Detection Quality**  
  - Refined thresholds to reduce false positives  
  - Added context fields (`user`, `host`, `source_ip`, `commandline`)  
  - Proper naming conventions for reports and dashboard panels  
  - Severity assessment and MITRE mapping for each detection

- **Correlation Thinking**  
  - Time-based correlation across events  
  - Multi-event context for incident investigation  
  - Combined Windows & Linux timeline for cross-platform attack visualization  

- **Incident Simulation & Reporting**  
  - Simulated attacks for each detection  
  - Documented raw events, bucketed timelines, and correlated activity  
  - Screenshots captured for dashboards, detection reports, and raw events  
  - Written SOC-style incident reports with timelines, affected assets, and response actions

---

### 3. Dashboards & Screenshots
The **SOC monitoring dashboard** consolidates all five detections:

- **Dashboard-Overview.png** – high-level overview of key panels  
- Individual panel screenshots (DET-001 to DET-005) for documentation and evidence  
- Panels designed to support **alert triage, investigation, and reporting**

---

### 4. How to Use
1. Open **Splunk Enterprise**.  
2. Run the **saved reports** for each detection to verify logic.  
3. View the **SOC dashboard** for consolidated event correlation.  
4. Reference individual panel screenshots for **documentation or reporting purposes**.  
5. Use **incident simulation files** to practice SOC analyst investigation workflow.

---

### 5. SOC Analyst Capabilities Demonstrated
This project showcases the following real-world SOC analyst skills:

- End-to-end **alert detection and validation**
- **Log correlation** across Windows and Linux endpoints
- **Incident investigation** and **timeline reconstruction**
- SOC-style **documentation and reporting**
- **Alignment with MITRE ATT&CK framework**
- Threshold tuning and **false-positive reduction**
- Multi-event **context awareness** for escalation decisions

---

### 6. Notes
- Some dashboard screenshots (Dashboard-Overview.png) only show three panels due to browser zoom/viewport limitations. Individual panels are captured separately.  
- Lab environment uses NAT; source IPs may appear identical across local VMs.  
- All activity is simulated and does not involve production data.