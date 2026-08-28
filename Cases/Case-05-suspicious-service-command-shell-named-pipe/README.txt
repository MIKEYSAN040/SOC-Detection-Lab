# Case 005 – Suspicious Windows Service Creation Using Command Shell and Named Pipe

## Detection Overview

This project demonstrates the detection of suspicious Windows service creation using **Windows Event ID 7045**.

The observed service executes the Windows command interpreter (`%COMSPEC%`) and references a named pipe while running under the **LocalSystem** account. This combination is uncommon for legitimate services and may indicate malicious persistence.

The detection was implemented using a custom Sigma rule, converted into Splunk SPL, and validated against a Windows System Event Log dataset.

---

## MITRE ATT&CK

| Technique | ID |
|-----------|----|
| Create or Modify System Process: Windows Service | T1543.003 |

**Tactic**

- Persistence

---

## Dataset

- Source: Windows System Event Log
- Dataset: `System_7045_namedpipe_privesc.evtx`
- Event ID: 7045
- SIEM: Splunk Enterprise

---

## Detection Workflow

1. Imported the Windows Event Log dataset into Splunk.
2. Identified Windows Event ID 7045.
3. Extracted service-related fields.
4. Developed a Sigma detection rule.
5. Converted the Sigma rule into Splunk SPL.
6. Executed the detection query.
7. Validated the detection against the dataset.
8. Performed event analysis.

---

## Detection Logic

The detection identifies:

- Windows Event ID 7045
- `%COMSPEC%`
- `/c`
- Named pipe (`\\.\pipe\`)
- LocalSystem service account

The combination of these indicators is more suspicious than normal service installation.

---

## Files

- `sigma.yml`
- `splunk-query.spl`
- `attack-analysis.md`
- `validation.md`
- `event-analysis.md`