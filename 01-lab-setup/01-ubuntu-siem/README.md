# Ubuntu SIEM Setup (Wazuh)

## Overview
This section documents the deployment of a Security Information and Event Management (SIEM) system using **Wazuh 4.12** on **Ubuntu Server 24.04** within VirtualBox.  
The Wazuh all-in-one installation (manager, indexer, dashboard) forms the foundation of the Blue Team SOC Homelab.  
This SIEM enables centralized log collection, monitoring, and detection of security events.

## Lab Environment
- **Virtualization:** Oracle VirtualBox 7.1.12
- **VM Name:** `LAB-SIEM-WAZUH-01`
- **Hostname:** `wazuh-lab-01`
- **IP Address (Host-Only):** `192.168.56.10/24`
- **Resources:** 2 vCPUs, 4 GB RAM, 40 GB disk
- **Networking:**
  - Adapter 1: NAT (Internet updates)
  - Adapter 2: Host-Only (192.168.56.0/24)

## Key Steps
1. Configured static IP networking via Netplan.  
2. Updated and secured Ubuntu system packages.  
3. Installed Wazuh via official quick installer (`wazuh-install.sh -a`).  
4. Verified Wazuh services (`wazuh-manager`, `wazuh-indexer`, `wazuh-dashboard`).  
5. Accessed Wazuh web dashboard over Host-Only network:  
   - URL: `https://192.168.56.10`  
   - User: `admin`  

## Screenshots
- VM configuration summary  
- Successful Ubuntu installation and login  
- Wazuh installer completion  
- Wazuh services running  
- Wazuh dashboard (web access)  

## Key Takeaways
- Successfully built a working SIEM environment in a contained lab.  
- Learned how to configure VirtualBox networking (NAT + Host-Only) for realism.  
- Gained hands-on experience installing and managing Wazuh.  
- Established a solid foundation for future endpoint integrations.
