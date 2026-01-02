# Splunk Project 02 – Detection Engineering

## Overview
This project builds on Splunk Project 01 (log ingestion & UF configuration) and focuses on **detection engineering, reporting, and dashboards**.  
The goal is to create **SOC-style detections** across Windows and Linux endpoints and visualize them in a unified dashboard for monitoring and investigation.

---

## Core Features
1. **Five SOC Detections Implemented:**
   - Windows Failed Logins (Brute Force)
   - Privileged Admin Logins (Non-System Accounts)
   - Linux SSH Failed Logins
   - Rare Process Execution (Sysmon / Windows)
   - Combined Windows & Linux Event Timeline (Correlation View)

2. **Reports & SPL Queries**
   - Each detection saved as a **Splunk report** with proper permissions.
   - SPL queries include field extraction and normalization (rex, eval, coalesce) for SOC-grade analysis.
   - MITRE ATT&CK mappings included for each detection.

3. **Dashboard**
   - Consolidates all five detections into a **SOC monitoring dashboard**.
   - **Dashboard-Overview.png** shows an overview of three panels; individual screenshots for each panel included to capture all five detections.

---

## How to Use
1. Open **Splunk Enterprise**.
2. Run the **saved reports** for each detection to verify the logic.
3. Open the **dashboard** to view consolidated security events.
4. Use individual panel screenshots for analysis or documentation reference.

---

## Notes
- Some dashboard screenshots (Dashboard-Overview.png) only show three panels due to browser zoom/viewport limitations.
- Individual panels are captured separately to document all five detections.
- Lab environment uses NAT; source IPs may appear identical on local VMs.

---

## Author
**Jelly Concepcion**  
Aspiring Cyber Defense Incident Responder | Future CISO  
[GitHub](https://github.com/jellyconcepcion/blue-team-homelab) | [LinkedIn](https://www.linkedin.com/in/jellyconcepcion/)