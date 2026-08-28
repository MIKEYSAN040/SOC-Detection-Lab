# Case 003 – Suspicious Rundll32 Advpack RegisterOCX Abuse

## Detection Overview

This project demonstrates the detection of suspicious abuse of the Windows signed binary **rundll32.exe** using the **advpack.dll,RegisterOCX** function. Attackers frequently abuse Rundll32 as a Living-off-the-Land Binary (LOLBIN) to execute malicious code while bypassing application control mechanisms.

The detection was implemented using a custom Sigma rule, converted into Splunk SPL, and validated against a Sysmon Event ID 1 dataset.

---

## MITRE ATT&CK

| Technique | ID |
|-----------|----|
| Signed Binary Proxy Execution: Rundll32 | T1218.011 |

**Tactic**

- Defense Evasion

---

## Dataset

- Source: Sysmon Event ID 1
- Dataset: `rundll32_cmd_schtask.evtx`
- Platform: Windows
- SIEM: Splunk Enterprise

---

## Detection Workflow

1. Imported Sysmon dataset into Splunk.
2. Extracted relevant process creation fields.
3. Developed a Sigma detection rule.
4. Converted the Sigma rule into Splunk SPL.
5. Executed the detection query.
6. Validated the suspicious Rundll32 execution.
7. Performed event analysis.

---

## Files

- attack-analysis.md
- validation.md
- event-analysis.md