# Case 008 – IIS Protocol Tunneling Detection

## Overview

This project detects suspicious IIS (`w3wp.exe`) network connections to RDP (TCP/3389) and SMB (TCP/445) using Sysmon Event ID 3.

Such behavior may indicate protocol tunneling, where a compromised web server is used to relay internal network traffic.

---

## MITRE ATT&CK

- **Technique:** T1572 – Protocol Tunneling
- **Tactic:** Command and Control

---

## Dataset

- **Dataset:** `tunna_iis_rdp_smb_tunneling_sysmon_3.evtx`
- **Platform:** Windows
- **SIEM:** Splunk Enterprise
- **Index:** `detection9`

---

## Detection Summary

The detection identifies:

- Sysmon Event ID 3
- IIS Worker Process (`w3wp.exe`)
- Destination Port **3389 (RDP)**
- Destination Port **445 (SMB)**

---

## Repository Contents

- Sigma Rule
- Splunk SPL Query
- Attack Analysis
- Event Analysis
- Validation