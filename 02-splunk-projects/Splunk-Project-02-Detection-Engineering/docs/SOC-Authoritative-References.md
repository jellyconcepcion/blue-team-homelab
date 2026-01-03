# SOC Authoritative References

This document contains links to **official, authoritative sources** that SOC analysts rely on for accurate interpretation of security events, threat behaviors, and telemetry. These references are not third-party blogs or summaries — they are the source of truth for investigations, detection engineering, and reporting.

When documenting security investigations, detections, or SIEM behavior, referencing these materials demonstrates professionalism, accuracy, and alignment with industry standards.

---

## 📌 What “Authoritative Reference” Means

An *authoritative reference* is a source that:
- Is maintained by the original vendor or standards body
- Accurately describes log events or threat behaviors
- Can be relied on in incident investigations and compliance reporting
- Is widely used in real SOC environments

These are used to:
- Validate evidence during investigations
- Build and tune detections
- Map logs and alerts to known attacker behaviors
- Communicate findings to technical and non-technical audiences

---

## 🔹 Microsoft Windows Security Event IDs

Windows logs generate numeric Event IDs for specific security events. These events are widely used in SIEM detection logic and SOC investigations because they represent discrete, auditable actions on Windows systems.

### Key References

- **Event ID 4625 — Failed Logon Attempts**  
  https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/auditing/event-4625  
  **Use:** Explains the meaning and fields for a failed authentication attempt event.  
  **SOC Value:** Used to detect brute-force attacks, credential misuse, and attempted access.

- **Event ID 4672 — Special Privileges Assigned**  
  https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/auditing/event-4672  
  **Use:** Describes event generated when a user with administrative or special privileges logs on.  
  **SOC Value:** Used to detect high-privilege logons and potential privilege escalation.

### Why It’s Important
SOC analysts often investigate suspicious activity by referencing official Event ID documentation to:
- Confirm the meaning of observed activity
- Extract relevant fields for triage
- Cite official descriptions in reports and alerts

These official pages serve as **vendor-maintained documentation** and are trusted across SOC teams.

---

## 🔹 Sysmon Event Reference

Sysmon (System Monitor) is a Windows telemetry tool that enhances logging beyond standard Windows logs. Sysmon logs are commonly ingested into SIEMs to detect malicious behaviors.

- **Sysmon Events Overview (Microsoft Sysinternals)**  
  https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon#events  
  **Use:** Lists Sysmon Event IDs and explains their purpose.  
  **SOC Value:** Sysmon events are used to detect malware execution, process relationships, registry changes, network connections, and persistence mechanisms.

### Why It’s Important
- Sysmon provides visibility into detailed endpoint activity not available in standard Windows logs.
- Analysts refer to the official Sysmon event reference to:
  - Understand what each Sysmon ID represents
  - Build accurately scoped detections
  - Interpret alerts during investigations

Examples of Sysmon Event IDs:
- **1** – Process Create  
- **3** – Network Connection  
- **7** – Image Loaded  
- **11** – File Created  
- **13** – Registry Change  
- **22** – DNS Query

These form the basis for many detection rules in enterprise SOCs.

---

## 🔹 MITRE ATT&CK Framework

MITRE ATT&CK is a globally adopted behavioral framework used by defenders to map attacker techniques, not individual log IDs. It describes *what* adversaries do and *why*, enabling high-level correlation with events observed in SIEM.

### Official Resources

- **Enterprise ATT&CK Matrix**  
  https://attack.mitre.org/matrices/enterprise/  
  **Use:** Visual representation of attacker tactics and techniques used across enterprise environments.

- **ATT&CK Techniques (Searchable)**  
  https://attack.mitre.org/techniques/enterprise/  
  **Use:** Comprehensive list of attacker techniques, enabling lookup by name, ID, or platform.

### Why It’s Important
SOC teams map SIEM detections to MITRE ATT&CK to:
- Standardize detection coverage
- Communicate threat behavior in analyst reports
- Understand adversary tactics at a behavioral level

Example mappings:
| Behavior | ATT&CK Technique |
|----------|------------------|
| Brute-force login attempts | **T1110** |
| Persistence via services | **T1547** |
| Privilege escalation | **T1068** |
| Command execution | **T1059** |

These mappings help analysts organize threats by **behavior**, not just by log labels.

---

## 🧠 How SOC Analysts Use These References

### During Detection Development
- Validate event semantics (e.g., “Does 4625 really mean a failed login?”)
- Identify additional relevant fields
- Map logs to attacker behaviors (MITRE)

### During Incident Investigation
- Cite official documentation in investigation notes
- Cross-reference observed events with expected behaviors
- Support alert accuracy and reproducibility

### During Reporting & Communication
- Provide authoritative links in reports
- Explain alerts using vendor definitions
- Justify detection logic to technical/non-technical stakeholders

SOC analysts do **not memorize full lists** of Event IDs or techniques. They memorize **core common behaviors**, refer to official docs for details, and use frameworks like ATT&CK for context.

---

## 📝 Summary

| Resource | What it Is | Why It Matters |
|----------|------------|----------------|
| **Microsoft Windows Security Events** | Vendor documentation of security Event IDs | Trusted source for log semantics |
| **Sysmon Event Reference** | Official list of Sysmon telemetry events | Deep endpoint detection visibility |
| **MITRE ATT&CK** | Behavioral framework for attacker activity | Standardized threat mapping used across SOCs |

These authoritative references ensure that your analysis, detections, and reports are **accurate, defensible, and consistent with industry practice**.

---