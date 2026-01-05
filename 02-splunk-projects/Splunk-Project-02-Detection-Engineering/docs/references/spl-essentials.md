# SPL (Search Processing Language) — SOC Analyst Core Essentials

SPL is **not a programming language** — it’s a **pipeline for searching, transforming, summarizing, and analyzing events** in a SIEM.  
Think of it as:
SEARCH → FILTER → GROUP → COUNT → DECIDE


This guide condenses the SPL essentials every SOC analyst must know.

---

## Phase A — MUST-KNOW SPL COMMANDS

These **7 commands** cover 80%+ of SOC searches.

### 1️⃣ `search` (Implicit but critical)
**Purpose:** Filters events  
**Example:**  
```spl
index=windows_logs EventCode=4625

SOC Usage:
• Initial triage
• Narrowing alerts
• Validation


2️⃣ table — Make logs human-readable

Purpose: Selects fields for output
Example:
index=windows_logs EventCode=4625
| table _time host user SourceIp

SOC Usage:
• Incident timelines
• Reporting
• Screenshots for evidence
💡 Rule of thumb: If you can’t explain it, table it.


3️⃣ stats — Aggregate events (Most important)
Purpose: Summarizes multiple events into counts or stats
Basic Examples:
| stats count
| stats count by host
| stats count by user SourceIp

Meaning:
• count = number of matching events
• count by host = events grouped per host
• count by user SourceIp = events grouped per user and source IP

SOC Usage:
• Brute-force detection
• Activity summarization
• Alert thresholds
⚠️ Tip: Once you use stats, raw event details are lost. Think: aggregate before inspecting individual events.


4️⃣ sort — Prioritize results
Purpose: Order results
Example:
| sort -count

SOC Usage:
• Spot worst offenders
• Focus investigations quickly


5️⃣ where — Apply logic / filter after aggregation
Purpose: Filter aggregated results
Example:
| where count > 5
SOC Usage:
• Threshold-based detections
• Reduce noise


6️⃣ timechart — Trend analysis
Purpose: Visualize counts over time
Example:
index=windows_logs EventCode=4625
| timechart count

SOC Usage:
• Attack timelines
• Spike detection
• Dashboards


7️⃣ bucket — Group events by time
Purpose: Aggregate events into time windows
Example:
| bucket _time span=5m

• Groups events in 5-minute windows
• Enables “X events within Y minutes” detections
SOC Usage: Detection logic for brute force, anomaly detection, and alert thresholds


Phase B — CORE SOC DETECTION PATTERNS
Memorize patterns, not queries.

🔴 Pattern 1 — Brute Force Login
index=windows_logs EventCode=4625
| bucket _time span=5m
| stats count by _time host user
| where count > 5

Meaning: >5 failed logins in 5 minutes
SOC Use: Alert, investigation, ticket creation

Order Matters:
1️⃣ bucket → 2️⃣ stats → 3️⃣ where

🔴 Pattern 2 — Rare / Suspicious Process Execution
index=windows_logs
| stats count by Image
| sort count

Image: Executable path (C:\Windows\System32\cmd.exe)
Meaning: Rare executions that may indicate abnormal or malicious activity
SOC Use: Investigate low-frequency processes, identify anomalies

🔴 Pattern 3 — Privileged / Admin Activity
index=security_logs EventCode=4672
| stats count by user host

Meaning: Who logged in with special privileges
SOC Use: Privilege escalation detection, insider threat monitoring

Phase C — FIELDS YOU MUST UNDERSTAND
SOC analysts think in WHO → FROM WHERE → DID WHAT → WHEN
| Field         | Meaning                      |
| ------------- | ---------------------------- |
| `_time`       | When event occurred          |
| `host`        | Machine generating the event |
| `user`        | Account involved             |
| `SourceIp`    | Origin of activity           |
| `Image`       | Executable path              |
| `CommandLine` | How the process was executed |
| `sourcetype`  | Log format                   |
| `index`       | Log storage category         |

Example Investigation Query:
index=windows_logs EventCode=4625
| table _time host user SourceIp
| sort _time

Answers: Who? From where? When? On which system?


SOC Mental Model (MEMORIZE THIS)
search → bucket (optional) → stats → where → table → sort

This is the standard flow for SOC detection and incident analysis.