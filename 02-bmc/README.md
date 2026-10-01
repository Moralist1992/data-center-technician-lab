# Block 02 — BMC & Out-of-Band Management

## Core model

```text
                    SERVER
                       │
        ┌──────────────┴──────────────┐
        │                             │
      HOST OS                        BMC
     (Linux)                 (Baseboard Management
        │                       Controller)
        │                             │
       SSH                 Web UI / Redfish / IPMI
        │                             │
   OS & services             Hardware telemetry
                              Events / sensors
                              Remote Console
                              Power control
```

| Access path | What it talks to | Typical purpose |
|---|---|---|
| SSH | Linux/Unix OS | Commands, services, logs, configuration |
| BMC Web UI | BMC | Hardware status, sensors, events, inventory |
| Redfish | BMC API | Programmatic hardware management |
| IPMI | BMC management interface | Monitoring and management |
| Remote Console | Physical server console via BMC | BIOS/UEFI, POST, bootloader, OS console |

## Technician mindset

```text
Symptom
  ↓
Evidence
  ↓
Isolation
  ↓
Identify faulty component / FRU
  ↓
Action according to runbook
  ↓
Verification
  ↓
Documentation / escalation
```

A BMC event is evidence. It is not automatically proof that the named component itself is defective.
