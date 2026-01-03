# Blue Team Homelab

This repository documents my hands-on **Blue Team and SOC engineering projects**.
The goal is to build **realistic, professional-grade security monitoring labs**
that demonstrate **log collection, detection engineering, and incident analysis**
using tools commonly found in real SOC environments.

---

## 📌 Overview

This homelab simulates a small enterprise environment where I practice:

- SIEM deployment and log forwarding
- Detection engineering and alert logic
- Security event analysis and correlation
- SOC-style documentation and reporting

The lab evolves across projects, starting from environment setup and log visibility
and progressing toward **SOC-ready detections and dashboards**.

---

## 🏗️ Lab Architecture

- **SIEM / SOC Platform:**  
  - Splunk Enterprise (Ubuntu Server 24.04)

- **Endpoints:**  
  - Windows 11 Pro  
  - Ubuntu Linux

- **Attacker VM:**  
  - Kali Linux (lab network presence only)

- **Virtualization & Networking:**  
  - VirtualBox  
  - NAT + Host-Only networking

---

## 🚀 Projects

### 🔹 01-lab-setup — Base Lab Environment

This folder contains **step-by-step VM creation and initial security setup**.

**Virtual Machines created:**
- Ubuntu Server 24.04.3 (`ubuntu-24.04.3-live-server-amd64.iso`)
- Windows 11 Pro (`Win11_24H2_English_x64.iso`)
- Kali Linux (`kali-linux-2025.2-virtualbox-amd64.vbox` + `.vdi`)

**Key activities:**
- Installed and configured **Wazuh Manager** on Ubuntu
- Installed **Wazuh Agent** on Windows 11
- Simulated a **brute-force attack against Windows**
- Verified security events were visible in the Wazuh dashboard
- Kali Linux VM was created and assigned a **static IP only**
  (no attacks launched beyond network setup)

This phase focused on **environment validation and visibility**, not detection engineering.

---

### 🔹 02-splunk-projects — SOC Monitoring & Detection Engineering

This folder focuses entirely on **Splunk**, reflecting its widespread use
in **professional and enterprise SOC environments**.

I transitioned to Splunk after understanding its real-world relevance
for SOC operations and detection engineering.

---

#### 🟦 Splunk Project 01 – SOC Homelab

**Focus:** Log ingestion, forwarding, and SOC visibility

**Ubuntu Server:**
- Installed **Splunk Enterprise 10.0.2**
- Installed **Splunk Universal Forwarder 10.0.2**
- Installed and enabled SSH
- Configured `inputs.conf` and `outputs.conf` for forwarding

**Windows 11 Pro:**
- Installed **Splunk Universal Forwarder 10.0.2**
- Installed **Sysmon64**
- Applied `sysmon-config.xml` (SwiftOnSecurity-based)
- Configured `inputs.conf` and `outputs.conf`

**Key outcome:**
- Windows and Linux logs were successfully forwarded
- Events were confirmed **searchable in Splunk Enterprise**
- Kali Linux was **not used** in this project

This project validates **end-to-end log flow before detection creation** —
a core SOC best practice.

---

#### 🟦 Splunk Project 02 – Detection Engineering

**Focus:** Detection logic, SPL queries, reports, and dashboards

Using logs generated from my **own Ubuntu and Windows VMs**, I implemented:

- Windows brute-force login detection
- Privileged account activity monitoring
- Linux SSH failed login detection
- Rare Windows process execution detection (Sysmon-based)
- Cross-platform event correlation timeline

**Professional SOC practices applied:**
- SPL-based detections saved as **reports**
- Proper permissions configuration
- MITRE ATT&CK technique mapping
- SOC-style dashboard creation
- Individual detection panel documentation

All detections are based on **real telemetry generated in the lab**, allowing
meaningful searching, querying, and analysis.

---

## 📂 Repository Structure

```text
01-lab-setup/
  → VM creation and initial security setup (Wazuh-based)

02-splunk-projects/
  → Splunk SOC projects (log ingestion, detections, dashboards)

docs/
  → Diagrams, screenshots, and reports

configs/
  → Splunk, Universal Forwarder, Sysmon, and lab configurations

README.md
  → Repository overview

---

🛠️ Technologies Used
• SIEM: Splunk Enterprise 10.0.2
• Forwarders: Splunk Universal Forwarder 10.0.2
• Operating Systems: Ubuntu Server 24.04, Windows 11 Pro
• Telemetry: Windows Security Events, Sysmon, Linux auth logs
• Virtualization: VirtualBox 7.1.12
• Security Platform (initial phase): Wazuh

🌐 Career Goal
Aspiring Cyber Defense Incident Responder, with a long-term goal of becoming
a Chief Information Security Officer (CISO).

This repository serves as a public SOC portfolio, demonstrating practical,
hands-on skills aligned with real-world security operations.