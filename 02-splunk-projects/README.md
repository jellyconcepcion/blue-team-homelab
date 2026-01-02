# Splunk Projects

This folder contains hands-on **Splunk SIEM projects** focused on **SOC operations, log ingestion, detection engineering, and incident visibility**.

## Projects

### 1️⃣ Splunk Project 01 – SOC Home Lab
**Focus:** Centralized log collection and visibility  
- Collect logs from **Windows 11** and **Ubuntu Linux endpoints** using **Splunk Universal Forwarder**  
- Enhance Windows telemetry with **Sysmon (SwiftOnSecurity config)**  
- Create dedicated security indexes for structured ingestion  
- Implement initial SOC detections:
  - Failed Windows logon attempts  
  - New Windows service creation  
  - Failed SSH logins on Ubuntu  
  - sudo usage monitoring  
- Apply professional practices:
  - SHA512 verification for all binaries  
  - Snapshot-based rollback strategy  
  - Clean documentation and evidence collection  

### 2️⃣ Splunk Project 02 – Detection Engineering
**Focus:** SOC-style detection logic, reporting, and dashboards  
- Build **five core SOC detections** across Windows and Linux:
  1. Windows failed logins (brute-force detection)  
  2. Privileged Windows account monitoring (non-system admin logins)  
  3. Linux SSH failed login attempts  
  4. Rare Windows process execution (Sysmon)  
  5. Unified cross-platform event timeline for correlation  
- Save each detection as a **Splunk report** with proper permissions  
- Map detections to **MITRE ATT&CK techniques**  
- Build a **SOC monitoring dashboard** consolidating all five detections  
- Include **individual panel screenshots** for documentation clarity  
- PDF guide and full documentation included for SOC-ready lab replication

---

**Next Steps:**  
More Splunk projects will be added progressively, expanding SOC visibility, detection engineering, and security analytics capabilities.