# Case 006 – Privilege Escalation via Unquoted Windows Service Path

## Detection Overview

This project demonstrates the detection of an **Unquoted Windows Service Path Privilege Escalation** using Microsoft Sysmon telemetry.

The attack abuses a Windows service configured with an **unquoted executable path** containing spaces. Windows attempts to resolve the executable by checking each portion of the path sequentially. An attacker can exploit this behavior by placing a malicious executable such as **C:\program.exe**, causing Windows to execute the attacker's payload instead of the intended service binary.

During the investigation, Sysmon recorded the creation of **C:\program.exe** followed by its execution through **services.exe** under the **NT AUTHORITY\SYSTEM** account, confirming successful privilege escalation.

The detection was implemented using a custom Sigma rule, converted into Splunk SPL, and validated against a Sysmon dataset.

---

## MITRE ATT&CK

| Technique | ID |
|-----------|----|
| Exploitation for Privilege Escalation | T1068 |

### Tactic

- Privilege Escalation

---

## Dataset

- Source: Microsoft Sysmon Operational Log
- Dataset: `privesc_unquoted_svc_sysmon_1_11.evtx`
- Event IDs:
  - 1 (Process Create)
  - 11 (File Create)
- SIEM: Splunk Enterprise

---

## Detection Workflow

1. Imported the Sysmon dataset into Splunk Enterprise.
2. Identified suspicious File Create (Event ID 11) events.
3. Detected creation of `C:\program.exe`.
4. Investigated Process Create (Event ID 1) events.
5. Confirmed execution by `services.exe`.
6. Verified execution under `NT AUTHORITY\SYSTEM`.
7. Correlated both events to reconstruct the attack timeline.
8. Validated the privilege escalation scenario.

---

## Detection Logic

The detection identifies:

- Sysmon Event ID 11 (File Create)
- Creation of `C:\program.exe`
- Sysmon Event ID 1 (Process Create)
- Parent process `services.exe`
- Execution under `NT AUTHORITY\SYSTEM`
- Sysmon RuleName indicating Potential Unquoted Service Exploit

The combination of these indicators strongly suggests exploitation of an Unquoted Windows Service Path vulnerability.

---

## Files

- `sigma.yml`
- `splunk-query.spl`
- `attack-analysis.md`
- `validation.md`
- `event-analysis.md`