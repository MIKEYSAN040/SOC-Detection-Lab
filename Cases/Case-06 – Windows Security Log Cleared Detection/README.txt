# Case 006 – Windows Security Log Cleared Detection

## Detection Overview

This project demonstrates the detection of Windows Security Event Log clearing using Windows Security Event ID 1102.

Attackers frequently clear Windows event logs after gaining privileged access to remove forensic evidence and hinder incident response. Event ID 1102 is generated whenever the Security Event Log is successfully cleared, making it a strong indicator of Defense Evasion.

The detection was implemented using a custom Sigma rule, converted into Splunk SPL, and validated against a Windows Security Event Log dataset containing Security Audit events.

---

## MITRE ATT&CK

| Technique | ID |
|-----------|----|
| Indicator Removal on Host: Clear Windows Event Logs | T1070.001 |

**Tactics**

- Defense Evasion

---

## Dataset

- Source: Windows Security Event Log
- Dataset: `DE_1102_security_log_cleared.evtx`
- Platform: Windows
- SIEM: Splunk Enterprise

---

## Detection Workflow

1. Imported the Security Event Log dataset into Splunk.
2. Identified Security Event ID 1102.
3. Developed a Sigma rule to detect Security Log clearing.
4. Converted the Sigma rule into Splunk SPL.
5. Executed the detection query in Splunk.
6. Validated the detection against matching events.
7. Correlated user account, host, and logon information.
8. Performed attack-path analysis.
9. Documented the investigation and supporting evidence.

---

## Detection Logic

The detection identifies:

- Event ID 1102
- Windows Security Log cleared
- User responsible for clearing the log
- Computer where the log was cleared
- Logon Session ID

The combination of these indicators provides strong evidence of Windows Event Log tampering.

---

## Files

- `T1070.001_windows_security_log_cleared.yml`
- `splunk-query.spl`
- `attack-analysis.md`
- `validation.md`
- `event-analysis.md`