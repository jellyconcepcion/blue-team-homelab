# SPL (Search Processing Language) — SOC Analyst Core Essentials

SPL is **not a programming language** — it is the **primary investigation and detection language inside a SIEM**.  
SOC analysts use SPL to **triage alerts, investigate incidents, tune detections, and document evidence**.

---

## SOC Mental Model

**SEARCH → FILTER → AGGREGATE → THRESHOLD → INVESTIGATE → DECIDE**

This document reflects **how SPL is used in real SOC investigations** within this project.

---

## Phase A — MUST-KNOW SPL COMMANDS (SOC Core)

These commands cover **80–90% of daily SOC analyst work**.

---

### 1. `search` — Event Filtering

**Purpose:** Retrieve relevant telemetry from the SIEM

```spl
index=windows_logs EventCode=4625
```

SOC Usage
- Alert validation
- Initial triage
- Narrowing investigation scope

---

### 2. `table` — Evidence Presentation
```spl
Purpose: Make logs readable and report-ready
index=windows_logs EventCode=4625
| table _time host user SourceIp
```

SOC Usage
- Incident timelines
- Screenshots for case notes
- Analyst handoff documentation
Rule: If you can’t explain it → **table** it.

---

### 3. `stats` — Event Aggregation (Most Important)
Purpose: Summarize activity patterns
```spl
| stats count by user SourceIp
```

SOC Usage
- Brute-force detection
- Identifying top offenders
- Threshold-based alerts
Once **stats** is used, raw events are aggregated — analysts must decide when to aggregate vs when to inspect raw logs.

---

### 4. `sort` — Prioritization
```spl
| sort -count
```

SOC Usage
- Identify highest-risk users or IPs
- Focus investigation efficiently

---

### 5. `where` — Detection Logic
```spl
| where count > 5
```

SOC Usage
- Alert thresholds
- Noise reduction
- Detection tuning

---

### 6. `timechart` — Trend & Spike Analysis
```spl
index=windows_logs EventCode=4625
| timechart count
```

SOC Usage
- Attack timelines
- Burst activity detection
- Dashboard panels

---

### 7. `bucket` — Time-Window Correlation
```spl
| bucket _time span=5m
```

SOC Usage
- “X events in Y minutes” detections
- Brute-force and anomaly logic

---

## Phase B — Core SOC Detection Patterns (Used in This Project)

Pattern 1 — Windows Brute Force Authentication
```spl
index=windows_logs EventCode=4625
| bucket _time span=5m
| stats count by _time host user SourceIp
| where count > 5
```

SOC Meaning
- More than 5 failed logins from the same source in 5 minutes

Used in
- DET-001 — Windows Failed Authentication
- INC-003 — Linux & Windows Login Abuse

---

Pattern 2 — Linux SSH Brute Force
```spl
index=linux_logs sourcetype=linux_secure "Failed password"
| bucket _time span=5m
| stats count by _time host user src_ip
| where count > 5
```

SOC Meaning
- SSH brute-force activity on Linux endpoints

Used in
- INC-003 — Linux SSH Failed Logins

---

Pattern 3 — Privileged Activity
```spl
index=security_logs EventCode=4672
| stats count by user host
```

SOC Meaning
- Special privileges assigned to a user session

Used in
- INC-002 — Windows Privileged Logon Investigation

---

Phase C — Fields SOC Analysts Must Understand

SOC analysts always answer:
**WHO → FROM WHERE → DID WHAT → WHEN**

| Field               | Meaning                     |
| ------------------- | --------------------------- |
| `_time`             | Event timestamp             |
| `host`              | System generating the event |
| `user`              | Account involved            |
| `SourceIp / src_ip` | Origin of activity          |
| `Image`             | Executable path             |
| `CommandLine`       | Execution context           |
| `sourcetype`        | Log format                  |
| `index`             | Data category               |

---

Example Investigation Query
```spl
index=windows_logs EventCode=4625
| table _time host user SourceIp
| sort _time
```

Answers
- Who attempted access?
- From where?
- When did it occur?
- On which system?

---

🧩 SOC Analyst Workflow (Memorize This)

search
→ bucket (optional)
→ stats
→ where
→ table
→ sort

This workflow is applied consistently across detections, dashboards, and incident investigations in this project.