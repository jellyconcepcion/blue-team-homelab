# Evidence Mapping — SOC Skill Validation

This document maps SOC analyst job requirements to **direct, verifiable evidence** inside this project.  
Each capability is demonstrated through hands-on detections, investigations, simulations, and SOC-style documentation using real telemetry.

| SOC Skill / Requirement | Evidence in This Project | Where to Find It |
|-------------------------|--------------------------|------------------|
| SIEM & Log Analysis | SPL searches across Windows & Linux telemetry | https://github.com/jellyconcepcion/blue-team-homelab/blob/main/02-splunk-projects/Splunk-Project-02-Detection-Engineering/docs/references/spl-essentials.md |
| Windows Event Log Analysis | Authentication & privilege events (4625, 4672) | https://github.com/jellyconcepcion/blue-team-homelab/blob/main/02-splunk-projects/Splunk-Project-02-Detection-Engineering/docs/references/event-codes-and-linux-patterns.md |
| Linux Log Analysis | SSH brute-force investigation | https://github.com/jellyconcepcion/blue-team-homelab/blob/main/02-splunk-projects/Splunk-Project-02-Detection-Engineering/docs/incident-simulations/INC-003-Linux-SSH-Failed-Logins/INC-003-Linux-SSH-Failed-Logins.md |
| Detection Engineering | Threshold-based SPL detections | https://github.com/jellyconcepcion/blue-team-homelab/blob/main/02-splunk-projects/Splunk-Project-02-Detection-Engineering/docs/detections/detection-01-windows-failed-logins/DET-001-Windows-Failed-Authentication.md |
| Noise Reduction | False-positive analysis and tuning | https://github.com/jellyconcepcion/blue-team-homelab/tree/main/02-splunk-projects/Splunk-Project-02-Detection-Engineering/docs/detections |
| MITRE ATT&CK Mapping | ATT&CK techniques mapped per detection & incident | https://github.com/jellyconcepcion/blue-team-homelab/tree/main/02-splunk-projects/Splunk-Project-02-Detection-Engineering/docs/detections |
| Incident Investigation & Triage | End-to-end investigations with timelines | https://github.com/jellyconcepcion/blue-team-homelab/tree/main/02-splunk-projects/Splunk-Project-02-Detection-Engineering/docs/incident-simulations |
| Cross-Platform Correlation | Unified Windows + Linux timeline | https://github.com/jellyconcepcion/blue-team-homelab/blob/main/02-splunk-projects/Splunk-Project-02-Detection-Engineering/docs/incident-simulations/INC-005-Cross-Platform-Timeline-Correlation/INC-005-Cross-Platform-Timeline-Correlation.md |
| EDR / Sysmon Telemetry | Rare process execution (Sysmon Event ID 1) | https://github.com/jellyconcepcion/blue-team-homelab/blob/main/02-splunk-projects/Splunk-Project-02-Detection-Engineering/docs/detections/detection-04-sysmon-rare-process/DET-004-Windows-Rare-Process-Execution.md |
| Privilege Escalation Detection | Privileged logon investigation (4672) | https://github.com/jellyconcepcion/blue-team-homelab/blob/main/02-splunk-projects/Splunk-Project-02-Detection-Engineering/docs/incident-simulations/INC-002-Windows-Privileged-Logon/INC-002-Windows-Privileged-Logon.md |
| SOC Documentation | Detections, incidents, runbooks, playbooks | https://github.com/jellyconcepcion/blue-team-homelab/tree/main/02-splunk-projects/Splunk-Project-02-Detection-Engineering/docs |
| Analyst Decision-Making | Severity, escalation, response justification | https://github.com/jellyconcepcion/blue-team-homelab/tree/main/02-splunk-projects/Splunk-Project-02-Detection-Engineering/docs/incident-simulations |