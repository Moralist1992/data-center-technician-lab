# Data Center Technician Learning Roadmap

This roadmap defines the technical areas covered by this self-directed Data Center Technician learning lab.

The lab focuses on the knowledge required to understand, troubleshoot and support modern server and data center infrastructure.

---

# 01 — Server Anatomy

Understand the physical and logical architecture of a server.

Topics:

- server chassis
- CPU
- RAM / DIMM / ECC
- NUMA
- motherboard
- PCIe
- PCIe slots
- risers
- GPU
- NIC
- HBA
- HDD
- SSD
- NVMe
- SATA
- RAID
- backplanes
- PSU
- PDU
- UPS
- cooling
- FRU
- hot-swap

Core skill:

> Understand what each component does, how it connects to the rest of the system, and what can cause it to fail.

---

# 02 — BMC and Hardware Management

Understand out-of-band server management.

Topics:

- BMC
- IPMI
- Redfish
- hardware sensors
- temperature monitoring
- fan monitoring
- PSU monitoring
- hardware events
- remote console
- remote power control
- hardware inventory

Core skill:

> Use hardware management information to identify and isolate server problems.

---

# 03 — Server Boot

Understand what happens between pressing the power button and loading the operating system.

Topics:

- power-on sequence
- BIOS / UEFI
- POST
- hardware initialization
- PCIe device detection
- boot devices
- bootloader
- operating system startup

Core skill:

> Understand where a failure occurs during the boot chain.

---

# 04 — Hardware Diagnostics

Develop a structured hardware troubleshooting methodology.

Topics:

- symptom identification
- evidence collection
- fault isolation
- component comparison
- logs and events
- sensor information
- physical inspection
- component replacement
- verification
- escalation

Core troubleshooting model:

```text
Symptom
   ↓
Collect evidence
   ↓
Isolate the fault
   ↓
Identify the faulty component
   ↓
Replace / repair
   ↓
Verify
```

---

# 05 — Data Center

Understand the physical environment in which servers operate.

Topics:

- racks
- rack units
- power infrastructure
- UPS
- PDU
- cooling
- airflow
- cabling
- patch panels
- fiber
- SFP / QSFP
- server installation
- hardware replacement
- RMA

Core skill:

> Understand how individual servers fit into the larger data center infrastructure.

---

# 06 — Linux for Technicians

Develop practical Linux command-line knowledge for server support.

Topics:

- Linux basics
- Ubuntu
- Bash
- CLI
- filesystem
- files and directories
- permissions
- processes
- services
- system logs
- networking commands
- SSH
- storage commands
- hardware detection

Core skill:

> Use the command line to inspect a server, collect evidence and perform basic troubleshooting.

---

# 07 — Ticket Workflow

Understand how technical incidents are handled in a professional environment.

Topics:

- ticket intake
- identifying symptoms
- gathering evidence
- troubleshooting
- documenting actions
- component replacement
- verification
- escalation
- RMA
- incident closure

Core skill:

> Perform technical work in a structured and traceable way.

---

# 08 — Interview Preparation

Convert technical knowledge into clear interview answers.

Topics:

- server architecture questions
- hardware questions
- Linux questions
- networking questions
- troubleshooting scenarios
- BMC questions
- escalation scenarios
- L1/L2 support questions

Core skill:

> Explain technical concepts clearly and describe a logical troubleshooting process.

---

# 09 — Troubleshooting Scenarios

Practice realistic technician scenarios such as:

- GPU not detected
- NVMe not detected
- NIC not detected
- network link down
- high CPU temperature
- failed PSU
- memory errors
- server boot failure
- multiple components failing through a shared path

Core skill:

> Identify the fault domain instead of immediately replacing the most obvious component.

---

# 10 — Technical Progression

The learning path moves from individual components toward complete system troubleshooting:

```text
Component Knowledge
        ↓
System Architecture
        ↓
Hardware Management
        ↓
Boot Process
        ↓
Troubleshooting
        ↓
Linux
        ↓
Networking
        ↓
Data Center Operations
        ↓
Ticket Workflow
        ↓
Technical Interview
```

The objective is not to memorize isolated commands.

The objective is to understand **how infrastructure works and how to troubleshoot it systematically**.
