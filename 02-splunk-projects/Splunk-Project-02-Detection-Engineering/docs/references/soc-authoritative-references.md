# SOC Authoritative References

This document contains **official, authoritative sources** that SOC analysts rely on for accurate interpretation of security events, threat behaviors, and telemetry. These references are the **source of truth** for investigations, detection engineering, and reporting.

When documenting security investigations, detections, or SIEM behavior, referencing these materials demonstrates professionalism, accuracy, and alignment with industry standards.

---

## 📌 What “Authoritative Reference” Means

An *authoritative reference* is a source that:

- Is maintained by the original vendor or standards body
- Accurately describes log events, telemetry, or threat behaviors
- Can be relied on in incident investigations and compliance reporting
- Is widely used in professional SOC environments

**Use Cases:**

- Validate evidence during investigations
- Build and tune detections
- Map logs and alerts to known attacker behaviors
- Communicate findings to technical and non-technical audiences

---

## 🔹 Microsoft Windows Security Event IDs

Windows logs generate numeric Event IDs for security-relevant events. These events are widely used in SIEM detection logic and SOC investigations because they represent discrete, auditable actions on Windows systems.

### Key References

- **Event ID 4625 — Failed Logon Attempts**  
  [Microsoft Docs](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/auditing/event-4625)  
  **Use:** Explains fields for a failed authentication attempt  
  **SOC Value:** Detect brute-force attacks, credential misuse, and attempted access

- **Event ID 4672 — Special Privileges Assigned**  
  [Microsoft Docs](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/auditing/event-4672)  
  **Use:** Logged when a user with administrative privileges logs on  
  **SOC Value:** Detect high-privilege logons and potential privilege escalation

- **Other Essential Event IDs:**  
  4624 – Successful login (Account activity)  
  4634 – Logoff (Session tracking)  
  4648 – Explicit credentials used (Lateral movement)  
  7045 – New service installed (Persistence)  
  4697 – Service installed (Persistence)  
  4798 / 4799 – Group membership changes (Privilege escalation)

---

## 🔹 Sysmon Event Reference

Sysmon (System Monitor) is a Windows telemetry tool that provides detailed endpoint visibility beyond standard Windows logs. Sysmon logs are commonly ingested into SIEMs like Splunk to detect suspicious or malicious behavior.

- **Sysmon Events Overview (Microsoft Sysinternals)**  
  [Sysmon Docs](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon#events)  
  **Use:** Lists Sysmon Event IDs and explains their purpose  
  **SOC Value:** Detect malware execution, process relationships, registry changes, network connections, and persistence mechanisms

### Core Sysmon Event IDs

| Sysmon ID | Meaning | SOC Relevance |
|-----------|--------|---------------|
| 1 | Process creation | Detect malware or abnormal processes |
| 3 | Network connection | Command-and-control (C2) detection |
| 7 | Image loaded | DLL hijacking / suspicious module loading |
| 11 | File created | Payload drops |
| 13 | Registry change | Persistence tracking |
| 22 | DNS query | Beaconing or data exfiltration |

---

## 🔹 MITRE ATT&CK Framework

MITRE ATT&CK is a **behavioral framework** used globally to map attacker techniques. It focuses on *what adversaries do* and *why*, enabling correlation with SIEM events and SOC detections.

### Official Resources

- **Enterprise ATT&CK Matrix**  
  [MITRE ATT&CK Enterprise](https://attack.mitre.org/matrices/enterprise/)  
  **Use:** Visual representation of attacker tactics and techniques in enterprise environments

- **ATT&CK Techniques (Searchable)**  
  [MITRE ATT&CK Techniques](https://attack.mitre.org/techniques/enterprise/)  
  **Use:** Lookup attacker techniques by name, ID, or platform

### Example Mapping

| Behavior | MITRE Technique |
|----------|----------------|
| Brute-force login attempts | T1110 |
| Persistence via services | T1547 |
| Privilege escalation | T1068 |
| Command execution / scripting | T1059 |

---

## 🧠 How SOC Analysts Use Authoritative References

**Detection Development**
- Validate event semantics (e.g., “Does 4625 really mean failed login?”)
- Identify additional relevant fields
- Map logs to attacker behaviors (MITRE ATT&CK)

**Incident Investigation**
- Cite official documentation in investigation notes
- Cross-reference observed events with expected behaviors
- Support alert accuracy and reproducibility

**Reporting & Communication**
- Include authoritative links in SOC reports
- Explain alerts using vendor definitions
- Justify detection logic to technical and non-technical stakeholders

**SOC Practice Tip:**  
Analysts **do not memorize all Event IDs**. They memorize **common behaviors** and reference official sources for accuracy.

---

## 📝 Summary Table

| Resource | Type | SOC Relevance |
|----------|------|---------------|
| Microsoft Windows Security Events | Vendor documentation | Trusted source for Windows log semantics |
| Sysmon Event Reference | Official telemetry reference | Deep endpoint detection visibility |
| MITRE ATT&CK | Behavioral framework | Standardized mapping of attacker activity |

These authoritative references ensure that your **analysis, detections, and reports** are accurate, defensible, and consistent with industry practice.