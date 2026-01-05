# Event Codes and Linux Detection Patterns
This document serves as a SOC analyst reference for commonly used
Windows Security EventCodes, Sysmon Event IDs, and Linux log patterns.
It is intended as a lookup guide, not a memorization requirement.

---

## 🔑 Core Windows Security EventCodes (Must-Know)

| EventCode | Meaning | SOC Use |
|---------|--------|--------|
| 4625 | Failed logon | Brute-force detection |
| 4624 | Successful logon | Account activity validation |
| 4672 | Special privileges assigned | Admin logon detection |
| 4634 | Logoff | Session tracking |
| 4648 | Explicit credentials used | Lateral movement detection |
| 7045 | New service installed | Persistence |
| 4697 | Service installed | Persistence |
| 4798 | Group membership changed | Privilege escalation |
| 4799 | Group membership enumerated | Recon / privilege validation |

📌 **SOC Note:**  
Windows detections often start with EventCodes, then expand into
behavioral correlation (time, user, source IP).

---

## 🧬 Sysmon Event IDs (Very Important)

Sysmon provides enhanced endpoint telemetry beyond standard Windows logs.
These Event IDs are **core to modern SOC detection engineering**.

| Sysmon ID | Meaning | Why SOCs Care |
|---------|--------|--------------|
| 1 | Process creation | Malware execution |
| 3 | Network connection | Command-and-control traffic |
| 7 | Image loaded | DLL hijacking |
| 11 | File created | Payload drops |
| 13 | Registry modification | Persistence |
| 22 | DNS query | Beaconing & C2 |

📌 **SOC Note:**  
Sysmon IDs are **not** Windows Security EventCodes.
They are mapped to attacker behavior and MITRE ATT&CK techniques.

---

## 🐧 Linux Detection Patterns (Pattern-Based, Not EventCodes)

Linux logging relies on **context and patterns**, not numeric event IDs.
SOC analysts detect threats using message content, frequency, and behavior.

---

### 🔐 Authentication & Access (High Priority)

| Purpose | SPL Query | SOC Value |
|------|---------|----------|
| Failed SSH logins | `index=security_logs "Failed password"` | Brute-force attacks |
| Invalid users | `index=security_logs "Invalid user"` | Enumeration attempts |
| Successful SSH login | `index=security_logs "Accepted password"` | Account activity |
| Root login | `index=security_logs "session opened for user root"` | Privilege abuse |
| Login from new IP | `index=security_logs "Accepted password"` | Lateral movement |

---

### 👤 Privilege Escalation

| Purpose | SPL Query | SOC Value |
|------|---------|----------|
| sudo usage | `index=security_logs sudo` | Administrative activity |
| sudo failures | `index=security_logs "authentication failure" sudo` | Escalation attempts |
| su to root | `index=security_logs "session opened for user root"` | Unauthorized access |

---

### ⚙️ System & Persistence Indicators

| Purpose | SPL Query | SOC Value |
|------|---------|----------|
| New user created | `index=security_logs "useradd"` | Persistence |
| User added to sudo | `index=security_logs "usermod" sudo` | Privilege escalation |
| Cron job creation | `index=security_logs "CRON"` | Scheduled persistence |
| System service start | `index=os_logs systemd` | Malware persistence |
| Package installation | `index=os_logs apt install` | Unauthorized software |

---

### 🌐 Network & Recon (Basic)

| Purpose | SPL Query | SOC Value |
|------|---------|----------|
| SSH activity | `index=security_logs sshd` | Connection tracking |
| Connection refused | `index=os_logs "connection refused"` | Recon activity |
| DNS resolution | `index=os_logs named` | C2 detection (advanced) |

---

## 🧠 Analyst Guidance

- You do **not** memorize all event codes
- You memorize **patterns**, not numbers
- Use this reference during investigations
- Always correlate:
  - Time
  - User
  - Host
  - Source IP
  - Behavior

---

## 🔗 Authoritative References
- Microsoft Windows Security Auditing
- Sysinternals Sysmon Documentation
- MITRE ATT&CK Enterprise Framework