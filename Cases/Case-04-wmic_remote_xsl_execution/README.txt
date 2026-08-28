# Case 005 – Suspicious WMIC Remote XSL Execution

## Detection Overview

This project demonstrates the detection of suspicious abuse of the Windows **WMIC (Windows Management Instrumentation Command-line)** utility using the `process list /format:` functionality with a remotely hosted XSL file.

Attackers may abuse WMIC and remotely hosted XSL files to perform process discovery and execute or process potentially malicious content while using legitimate Windows components.

The detection was implemented using a custom Sigma rule, converted into Splunk SPL, and validated against a Sysmon dataset containing Process Creation, Network Connection, Image Load, and File Creation events.

---

## MITRE ATT&CK

| Technique | ID |
|-----------|----|
| Windows Management Instrumentation | T1047 |
| Process Discovery | T1057 |

**Tactics**

- Execution
- Discovery

---

## Dataset

- Source: Sysmon
- Dataset: `sysmon_mshta_sharpshooter_stageless_meterpreter.evtx`
- Platform: Windows 7
- SIEM: Splunk Enterprise

---

## Detection Workflow

1. Imported the Sysmon dataset into Splunk.
2. Identified suspicious WMIC process creation activity.
3. Developed a Sigma detection rule targeting WMIC execution with a remote XSL resource.
4. Converted the Sigma rule into Splunk SPL.
5. Executed the detection query in Splunk.
6. Validated the detection against matching Sysmon events.
7. Correlated process, file, image-load, and network activity.
8. Performed event and attack-path analysis.
9. Documented the investigation and supporting evidence.

---

## Detection Logic

The detection identifies:

- `wmic.exe` execution
- `process list` command
- `/format:` parameter
- HTTP/HTTPS remote resource
- `.xsl` file reference

The combination of these indicators is significantly more suspicious than normal WMIC execution alone.

---

## Files

- `sigma.yml`
- `splunk-query.spl`
- `attack-analysis.md`
- `validation.md`
- `event-analysis.md`