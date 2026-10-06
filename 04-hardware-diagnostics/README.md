# Block 04 — Hardware Diagnostics

## Purpose
Build the L1 diagnostic mindset: do not guess the failed component. Collect evidence, isolate the layer, follow the approved runbook, act safely, verify, and document/escalate.

## Core model
`Symptom → Evidence → Runbook → Isolation → Action → Verification → Documentation/Escalation`

A symptom is not automatically a root cause. `Server unreachable`, `GPU not detected`, `ECC error`, and `PXE-E61` all require investigation.

## Evidence sources
- BMC sensors and hardware inventory
- Hardware Event Log
- Remote Console
- POST / BIOS / UEFI messages
- Storage status
- Linux logs
- Monitoring
- Physical inspection
- Cable/SFP/connection checks

## Verification
A repair is not complete when a part is replaced. Confirm the original error is gone, hardware is detected, temperatures/RPM are normal, the server boots, connectivity returns, and monitoring is healthy.

## L1 mindset
If you do not know the answer: collect information, check the runbook, avoid unsafe actions, ask for help/escalate, and document what you already checked.
