# Case 002 — Suspicious Regsvr32 Scriptlet Execution

## Overview

This detection identifies suspicious use of the Windows Regsvr32 utility to execute remote scriptlets through scrobj.dll using the `/i:` parameter. This technique, commonly known as Squiblydoo, abuses a trusted Microsoft-signed binary to execute attacker-controlled content while bypassing traditional application control mechanisms.

## MITRE ATT&CK

- Technique: T1218.010 – Regsvr32
- Tactic: Defense Evasion

## Detection Logic

The Sigma rule detects:

- Process Image ending with `regsvr32.exe`
- `/i:` parameter
- `scrobj.dll`
- Remote HTTP reference

## Data Source

- Microsoft Sysmon
- Event ID 1 (Process Creation)

## Dataset

EVTX-ATTACK-SAMPLES

Sample:

exec_sysmon_lobin_regsvr32_sct.evtx

## Severity

High

## Status

Validated