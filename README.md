# Detection Engineering Portfolio

A collection of practical Windows detection engineering projects focused on identifying adversary techniques using **Sigma rules**, **Splunk SPL**, and **MITRE ATT&CK**.

Each detection case follows a structured workflow—from analyzing raw Windows event logs to developing Sigma rules, validating detections in Splunk, and documenting the investigation.

---

## Repository Structure

```
Detection-Engineering-Portfolio/
│
├── README.md
├── LICENSE
│
├── cases/
│   ├── 001-regsvr32-remote-scriptlet/
│   ├── 002-rundll32-advpack-registerocx/
│   ├── 003-wmic-remote-xsl/
│   ├── 004-service-command-shell-named-pipe/
│   └── ...
│
└── sigma-rules/
    ├── defense-evasion/
    ├── execution/
    ├── persistence/
    ├── discovery/
    └── ...
```

---

## Detection Workflow

Each case follows a consistent detection engineering methodology:

1. Import Windows event log datasets into Splunk.
2. Analyze the raw event telemetry.
3. Identify suspicious behavior.
4. Extract relevant fields.
5. Develop a Sigma detection rule.
6. Convert the Sigma rule into Splunk SPL.
7. Validate the detection.
8. Perform event and attack analysis.
9. Document the investigation.

---

## Detection Cases

| Case | Detection | MITRE ATT&CK | Tactic | Status |
|------|-----------|--------------|---------|--------|
| 001 | Regsvr32 Remote Scriptlet Execution | T1218.010 | Defense Evasion | ✅ |
| 002 | Rundll32 Advpack RegisterOCX Abuse | T1218.011 | Defense Evasion | ✅ |
| 003 | WMIC Remote XSL Execution | T1047, T1057 | Execution, Discovery | ✅ |
| 004 | Suspicious Service Creation Using Command Shell & Named Pipe | T1543.003 | Persistence | ✅ |

> More detections will be added as I continue over the time

---

## What Each Case Includes

Every detection case contains:

- Detection Overview
- MITRE ATT&CK Mapping
- Sigma Detection Rule
- Splunk SPL Query
- Detection Validation
- Event Analysis
- Attack Analysis
- Investigation Screenshots

---

## Skills Demonstrated

- Detection Engineering
- Sigma Rule Development
- Splunk SPL
- Windows Event Log Analysis
- Sysmon Analysis
- MITRE ATT&CK Mapping
- Threat Detection
- Security Event Investigation
- Detection Validation

---

## Technologies

- Splunk Enterprise
- Sigma
- Windows Event Logs
- Sysmon
- MITRE ATT&CK

---

## Repository Goal

The purpose of this repository is to demonstrate practical detection engineering skills by creating behavior-based detections using real Windows event log datasets. The focus is on building reusable Sigma rules, validating detections in Splunk, and documenting investigations in a structured and repeatable manner.

---
