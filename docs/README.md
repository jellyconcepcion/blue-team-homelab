# Blue Team Homelab — Documentation

This `docs/` folder contains screenshots, diagrams, and short reports for Month 1 (Lab setup).
It is an indexed record of evidence for the homelab build and is safe for public sharing (no passwords/keys).

## Structure
- `reports/` — optional PDF reports (incident reports, VA reports, etc.)
- `screenshots/` — screenshots taken during lab setup (host-only adapter, VM settings, in-VM outputs)
  - `crop/` — cropped images for social posts

## How to reproduce (quick)
1. Create a VirtualBox Host-Only adapter (vboxnet0) and disable DHCP.
2. Create three VMs:
   - `LAB-SIEM-WAZUH-01` (Ubuntu Server 24.04) — Host-Only IP: `192.168.56.10`
   - `LAB-WS11-01` (Windows 11 Pro) — Host-Only IP: `192.168.56.20`
   - `LAB-KALI-01` (Kali Linux) — Host-Only IP: `192.168.56.30`
3. Use two NICs: NAT + Host-Only (vboxnet0). Set Host-Only IPs statically inside each VM.
4. See `screenshots/` for exact GUI steps and verification images.

## Notes
- All sensitive items (passwords, API keys) must be redacted from screenshots before publishing.
- Snapshots are taken after major milestones (M1-01, M1-02, etc.).
