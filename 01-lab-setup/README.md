# Month 1: Lab Setup - Ubuntu SIEM, Windows Endpoint, Kali Attacker

## Overview
This repository documents the **Month 1 build of my Blue-Team SOC Lab** using VirtualBox.  
The lab consists of three VMs:  
1. Ubuntu Server 24.04 + Wazuh SIEM (manager, indexer, dashboard)  
2. Windows 11 Pro endpoint with Wazuh agent  
3. Kali Linux attacker VM for testing and threat simulation  

## Lab Environment Summary
| VM Name | OS | Hostname | Host-Only IP | vCPUs | RAM | Disk |
|---------|----|----------|--------------|-------|-----|------|
| LAB-SIEM-WAZUH-01 | Ubuntu 24.04 | wazuh-lab-01 | 192.168.56.10 | 2 | 4GB | 40GB |
| WIN11-LAB-01 | Windows 11 Pro | WIN11-LAB-01 | 192.168.56.20 | 2 | 4GB | 60GB |
| LAB-KALI-01 | Kali Linux 2025.2 | kali-lab-01 | 192.168.56.30 | 2 | 4GB | N/A |

## Key Steps
### Ubuntu SIEM
- Installed Ubuntu Server 24.04  
- Configured host-only static IP (192.168.56.10) and NAT for updates  
- Installed Wazuh all-in-one (manager + indexer + dashboard)  
- Verified services and accessed dashboard via host-only network  

### Windows Endpoint
- Installed Windows 11 Pro VM  
- Deployed Wazuh agent and configured to communicate with SIEM (`192.168.56.10`)  
- Simulated failed logins (Event ID 4625)  
- Verified detection in Wazuh Threat Hunting dashboard  

### Kali Attacker
- Imported Kali Linux VM and configured host-only static IP (192.168.56.30)  
- Created administrative user `labkali` and removed default `kali` user  
- Verified connectivity with Ubuntu SIEM and Windows endpoint  
- Optional: Installed VirtualBox Guest Additions  
- Created evidence file linking VM state to GitHub commit  

## Evidence & Snapshots
- Ubuntu: `M1-Ubuntu-Evidence-b3d2839`  
- Windows: `M1-Win11-Evidence-eff3a26`  
- Kali: `M1-Kali-Evidence-019fee6`  

## Key Takeaways
- Built a fully isolated SOC lab with SIEM, endpoint, and attacker VM.  
- Configured VirtualBox networking (NAT + Host-Only) for realistic lab scenarios.  
- Lab provides a safe environment to simulate attacks and monitor detection workflows.  
- Evidence and snapshots ensure reproducibility and traceability of lab state.
