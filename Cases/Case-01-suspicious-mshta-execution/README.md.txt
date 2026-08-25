# Detection Case 001 — Suspicious MSHTA Execution

## Overview

Detection of suspicious execution of mshta.exe, a legitimate
Windows binary frequently abused by attackers to execute HTA
content and scripts.

## Detection Objective

Identify process creation events where mshta.exe is executed.

## Attack Technique

MITRE ATT&CK:
T1218.005 — Mshta

## Data Source

Dataset:
EVTX-ATTACK-SAMPLES

Sample:
sysmon_mshta_sharpshooter_stageless_meterpreter.evtx

Log Source:
Windows / Sysmon Process Creation

Event ID:
1 — Process Creation

## Detection Workflow

EVTX Attack Sample
→ Splunk
→ Event Analysis
→ Sigma
→ Sigma-to-SPL
→ Detection
→ Investigation
→ Validation

## Detection Logic

The detection identifies execution of:

C:\Windows\System32\mshta.exe