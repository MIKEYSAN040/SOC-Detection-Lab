# Case 007 – Active Directory Discovery Using BloodHound Enumeration

## Detection Overview

This project demonstrates the detection of **Active Directory reconnaissance** performed using BloodHound. The dataset contains Windows Security Event ID **5145**, which records access to network share objects through the administrative `IPC$` share.

The investigation identified repeated access to multiple Remote Procedure Call (RPC) interfaces, including **SAMR**, **LSARPC**, **NETLOGON**, and **SRVSVC**, from the same source host and user account within a short period. This access pattern is consistent with automated Active Directory enumeration tools such as BloodHound/SharpHound, which collect information about users, groups, domain trusts, computers, and sessions to identify privilege escalation and lateral movement paths. :contentReference[oaicite:0]{index=0}

The detection was implemented using a custom Sigma rule, converted into Splunk SPL, and validated against a Windows Security Event Log dataset.

---

## MITRE ATT&CK

| Technique | ID |
|-----------|----|
| Account Discovery | T1087 |
| Remote System Discovery | T1018 |

### Tactic

- Discovery

---

## Dataset

- Source: Windows Security Event Log
- Dataset: `discovery_bloodhound.evtx`
- Event ID: 5145
- SIEM: Splunk Enterprise

---

## Detection Workflow

1. Imported the Windows Security Event Log dataset into Splunk Enterprise.
2. Identified Event ID 5145 (Detailed File Share).
3. Filtered events involving the administrative `IPC$` share.
4. Analyzed RPC endpoint access.
5. Identified repeated access to `samr`, `lsarpc`, `NETLOGON`, and `srvsvc`.
6. Correlated multiple events originating from the same source host and user.
7. Validated the behavior against known BloodHound discovery techniques.
8. Documented the attack timeline.

---

## Detection Logic

The detection identifies:

- Windows Event ID 5145
- Administrative share `IPC$`
- RPC endpoints:
  - `samr`
  - `lsarpc`
  - `NETLOGON`
  - `srvsvc`
- Repeated requests from the same source host and user account

This combination represents Active Directory reconnaissance rather than normal administrative activity.

---

## Files

- `sigma.yml`
- `splunk-query.spl`
- `attack-analysis.md`
- `validation.md`
- `event-analysis.md`]