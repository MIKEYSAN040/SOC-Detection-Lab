# Case 007 – Mimikatz LSASS Credential Dumping Detection

## Detection Overview

This project demonstrates the detection of credential dumping using Mimikatz by monitoring Sysmon Process Access (Event ID 10) targeting the Windows Local Security Authority Subsystem Service (LSASS).

Attackers abuse Mimikatz to access the memory of the LSASS process and extract authentication material such as plaintext passwords, NTLM hashes, Kerberos tickets, and cached credentials. Sysmon Event ID 10 provides visibility into process access operations, making it an effective data source for detecting credential dumping attempts.

The detection was implemented using a custom Sigma rule, converted into Splunk SPL, and validated against a Sysmon dataset containing Process Access events.

---

## MITRE ATT&CK

| Technique | ID |
|-----------|----|
| OS Credential Dumping: LSASS Memory | T1003.001 |

**Tactics**

- Credential Access

---

## Dataset

- Source: Sysmon
- Dataset: `sysmon_10_lsass_mimikatz_sekurlsa_logonpasswords.evtx`
- Platform: Windows
- SIEM: Splunk Enterprise
- Splunk Index: `detection8`

---

## Detection Workflow

1. Imported the Sysmon dataset into Splunk.
2. Identified Sysmon Process Access (Event ID 10).
3. Developed a Sigma rule to detect unauthorized access to LSASS by Mimikatz.
4. Converted the Sigma rule into Splunk SPL.
5. Executed the detection query in Splunk.
6. Validated the detection against matching Sysmon events.
7. Correlated source process, target process, access rights, and call trace.
8. Performed event and attack-path analysis.
9. Documented the investigation and supporting evidence.

---

## Detection Logic

The detection identifies:

- Sysmon Event ID 10
- Source process (`mimikatz.exe`)
- Target process (`lsass.exe`)
- Granted Access (`0x1010`)
- Call Trace

The combination of these indicators provides high-confidence evidence of credential dumping via LSASS memory access.

---

## Files

- `T1003.001_sysmon_lsass_mimikatz_process_access.yml`
- `splunk-query.spl`
- `attack-analysis.md`
- `validation.md`
- `event-analysis.md`