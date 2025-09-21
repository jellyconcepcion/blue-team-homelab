# Windows Endpoint Integration (Wazuh Agent)

## Overview
This section demonstrates how a Windows 11 Pro endpoint can be integrated with the Wazuh SIEM for log collection and threat detection.  
By deploying the Wazuh agent on the endpoint and simulating failed login attempts, we validated that authentication failures are detected and logged centrally in the SIEM.

## Lab Environment
- **Virtualization:** Oracle VirtualBox 7.1.12
- **VM Name:** `LAB-WS11-01`
- **Hostname / Computer Name:** `WIN11-LAB-01`
- **IP Address (Host-Only):** `192.168.56.20/24`
- **Resources:** 2 vCPUs, 4 GB RAM, 60 GB disk
- **Networking:**
  - Adapter 1: NAT (Internet updates)
  - Adapter 2: Host-Only (192.168.56.0/24)

## Key Steps
1. Installed Windows 11 Pro VM with static Host-Only IP.  
2. Deployed Wazuh Windows agent (MSI package).  
3. Configured agent to report to Wazuh manager (`192.168.56.10`).  
4. Verified agent connectivity in Wazuh dashboard.  
5. Simulated brute-force attempts (5 failed logins, Event ID **4625**).  
6. Observed authentication failure alerts within the Wazuh dashboard (Threat Hunting module).

## Screenshots
- Windows VM setup and hostname  
- Wazuh agent installation (PowerShell)  
- Wazuh dashboard showing active Windows agent  
- Threat Hunting dashboard with Event ID 4625 detections  
- Windows Event Viewer confirming local 4625 entries  

## Key Takeaways
- Validated endpoint visibility in the SIEM.  
- Confirmed that authentication failures are correlated across Windows Event Logs and Wazuh alerts.  
- Built confidence in using Wazuh Threat Hunting queries for log analysis.  
- Prepared the environment for offensive testing (Kali Linux attacker integration).
