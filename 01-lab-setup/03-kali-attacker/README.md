# Kali Linux Attacker VM Setup

## Overview
This section documents the deployment of the **Kali Linux 2025.2** attacker VM within VirtualBox.  
The VM simulates adversarial activity in the Blue Team SOC lab, enabling practical threat detection, monitoring, and incident response exercises.  

## Lab Environment
- **Virtualization:** Oracle VirtualBox 7.1.12
- **VM Name:** `LAB-KALI-01`
- **Hostname:** `kali-lab-01`
- **IP Address (Host-Only):** `192.168.56.30/24` (no default gateway)
- **Resources:** 2 vCPUs, 4 GB RAM
- **Networking:**
  - Adapter 1: NAT (internet access / updates)
  - Adapter 2: Host-Only (192.168.56.0/24)

## Key Steps
1. Imported Kali `.vbox` and `.vdi` files into VirtualBox and renamed VM.  
2. Configured Host-Only adapter with static IP (`192.168.56.30/24`).  
3. Set hostname to `kali-lab-01` and updated `/etc/hosts`.  
4. Verified network connectivity:
   - `ping -c 2 kali-lab-01` (self)
   - `ping -c 4 192.168.56.10` (Ubuntu SIEM)
   - `ping -c 4 192.168.56.20` (Windows endpoint)
5. Created new administrative user `labkali` and removed default `kali` user.  
6. Optional: Installed VirtualBox Guest Additions for improved display and clipboard support.  
7. Created evidence file linking VM state to GitHub commit.  
8. Took VirtualBox snapshot: `M1-Kali-Evidence-019fee6`.  

## Screenshots
- Initial login and desktop: `kali-first-login.png`  
- Hostname configuration: `kali-hostnamectl.png`  
- Network IP assignment: `kali-nmcli-set-ip.png`  
- Final verification: `kali-hostname-ip-route.png`  
- Evidence file: `kali-evidence-file.png`  
- VirtualBox snapshot: `vb-kali-snapshot.png`  
- Guest Additions verified: `kali-guest-additions-installed.png`  

## Key Takeaways
- Kali Linux VM successfully integrated into the host-only lab network.  
- Ready to simulate attacker activities for detection and monitoring.  
- Evidence and snapshots ensure reproducibility and auditability.  
