# Learning Log

This file is a high-level record of the technical areas covered by the learning lab.

It focuses on knowledge and learning outcomes rather than a dated study timeline.

---

# Server Anatomy

Covered:

- server architecture
- CPU
- RAM
- DIMM
- ECC
- NUMA
- motherboard
- PCIe
- PCIe slots
- risers
- GPU
- HDD
- SSD
- SATA
- NVMe
- NIC
- HBA
- RAID
- backplane
- PSU
- PDU
- UPS
- cooling
- FRU
- Hot-Swap

Key outcome:

> Understand the role of the main server components, how they connect to each other, and how to reason about hardware failures.

---

# Hardware Troubleshooting

Covered:

- symptom identification
- evidence collection
- fault isolation
- common failure points
- physical connection checks
- power checks
- PCIe path checks
- firmware checks
- shared infrastructure checks
- component replacement
- verification after repair

Core troubleshooting model:

```text
Symptom
   ↓
Collect evidence
   ↓
Isolate the fault
   ↓
Identify faulty component
   ↓
Replace / repair
   ↓
Verify
```

Key outcome:

> Do not assume that the component associated with the symptom is automatically the faulty component.

---

# Storage Troubleshooting

Covered:

- HDD architecture
- SSD architecture
- SATA
- NVMe
- PCIe storage path
- drive detection
- backplanes
- shared failure analysis

Example reasoning:

```text
One drive fails
→ investigate the drive and local path

Several drives sharing one backplane fail
→ investigate the common backplane/path
```

---

# Network Troubleshooting

Covered:

- NIC
- interface state
- physical link
- cable
- switch port
- network path
- end-to-end connectivity
- external network dependencies

Diagnostic chain:

```text
NIC detected?
      ↓
Interface UP?
      ↓
Physical link UP?
      ↓
Cable connected?
      ↓
Switch port UP?
      ↓
Link established on both sides?
      ↓
End-to-end communication?
```

Key outcome:

> NIC detected does not automatically mean that network connectivity is working.

---

# Power and Cooling

Covered:

- PSU
- redundant PSUs
- PDU
- UPS
- fan monitoring
- airflow
- thermal events
- BMC-based thermal monitoring

Key outcome:

> Understand the difference between server power supplies, rack-level power distribution and power continuity systems.

---

# Server Hardware Management

Covered:

- BMC
- hardware sensors
- hardware events
- remote management concepts
- out-of-band management

Key outcome:

> Understand how a technician can monitor and diagnose server hardware independently of the operating system.

---

# Replaceable Hardware

Covered:

- FRU
- Hot-Swap
- redundant components
- hardware replacement
- post-replacement verification
- RMA concept

Key outcome:

> Understand that FRU and Hot-Swap are different concepts. A field-replaceable component is not automatically hot-swappable.

---

# Interview Preparation

Technical answers practiced around:

- server architecture
- CPU / RAM / ECC / NUMA
- PCIe
- GPU troubleshooting
- NVMe troubleshooting
- NIC troubleshooting
- PSU / PDU / UPS
- thermal problems
- FRU / Hot-Swap
- structured troubleshooting methodology

General answer pattern:

> Explain the component → explain its role → identify possible failure points → describe a diagnostic process → explain replacement → verify the result.

---

# Current Knowledge Direction

The learning lab continues toward:

- BMC
- server boot process
- hardware diagnostics
- Linux command line
- networking fundamentals
- data center operations
- ticket workflow
- incident troubleshooting
- technical interview preparation
