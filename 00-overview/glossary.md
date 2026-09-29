# Data Center Technician Glossary

This glossary is a quick-reference guide to the main hardware, infrastructure, networking, Linux and data center terminology used throughout this learning lab.

The goal is not to provide exhaustive definitions, but to make technical terminology easy to recall before troubleshooting or an interview.

---

# 1. Server Hardware

## CPU — Central Processing Unit

The main processing unit of the server. It executes instructions and performs calculations required by the operating system, applications and services.

**Think:** compute / instructions.

---

## RAM — Random Access Memory

Temporary working memory used by the CPU and running applications.

**Think:** active data and program state.

---

## DIMM — Dual Inline Memory Module

The physical memory module installed in a server's RAM slot.

**Important distinction:**
- RAM = memory
- DIMM = physical memory module

---

## ECC — Error-Correcting Code

A hardware-based technology that detects and corrects certain memory errors.

**Think:** memory reliability.

---

## NUMA — Non-Uniform Memory Access

A memory architecture commonly used in multi-CPU servers where each CPU has local memory and can also access memory associated with another CPU.

**Think:** local vs remote memory access.

---

## Motherboard

The main circuit board of the server. It provides the connections and interfaces required by the CPU, memory, PCIe devices, storage, power and management components.

**Think:** main platform connecting the hardware.

---

## PCIe — Peripheral Component Interconnect Express

A high-speed interface/interconnect used to connect devices to the server platform.

Common PCIe devices include:

- GPU
- NIC
- HBA
- RAID controller
- NVMe devices/adapters

**Think:** high-speed device interconnect.

---

## PCIe Slot

The physical connector where a PCIe device can be installed.

**Important distinction:**

> PCIe = interface  
> PCIe slot = physical connector

---

## Riser

A PCIe riser is a separate board used to provide or reposition PCIe slots inside a server chassis.

**Think:** PCIe extension / repositioning.

---

## GPU — Graphics Processing Unit

A processor designed for highly parallel workloads.

In data centers GPUs are widely used for:

- AI / ML
- high-performance computing
- parallel workloads

**Think:** parallel compute.

---

## HBA — Host Bus Adapter

An adapter used to connect a server to storage devices or storage systems.

A common example is a SAS HBA.

**Think:** server-to-storage connectivity.

---

# 2. Storage

## HDD — Hard Disk Drive

A mechanical storage device using rotating magnetic platters and moving read/write heads.

Compared with SSDs, HDDs generally have:

- lower performance
- higher latency
- moving mechanical parts

HDDs commonly use SATA or SAS interfaces in server environments.

---

## SSD — Solid-State Drive

A storage device using flash memory with no moving mechanical parts.

SSD is a type of storage device, not a specific interface.

An SSD may use different interfaces or protocols.

---

## SATA — Serial ATA

A storage interface commonly used with SATA HDDs and SATA SSDs.

Example:

```text
SATA SSD
    ↓
  SATA
    ↓
Motherboard
```

---

## NVMe — Non-Volatile Memory Express

A storage protocol designed for non-volatile memory devices, commonly SSDs, and usually used over PCIe.

Important distinction:

> SSD = storage device  
> NVMe = storage protocol  
> PCIe = high-speed interface

Example:

```text
NVMe SSD
    ↓
  PCIe
    ↓
Motherboard
```

---

## RAID — Redundant Array of Independent Disks

A method of combining multiple drives for redundancy, performance, or both.

Common concepts:

- RAID 0 — performance, no redundancy
- RAID 1 — mirroring
- RAID 5 — distributed parity
- RAID 6 — dual parity
- RAID 10 — mirroring + striping

Exact RAID capabilities depend on the hardware or software implementation.

**Think:** storage redundancy / performance.

---

## Backplane

A server board used to connect multiple drives to the rest of the system.

Depending on the platform, a backplane may provide:

- drive connectivity
- power distribution
- data paths
- management/signaling

**Think:** shared connection point for multiple drives.

---

# 3. Networking

## NIC — Network Interface Controller

A hardware component that provides network connectivity between the server and a network.

A NIC can be used for:

- internal network
- management network
- storage network
- cluster network
- Internet connectivity

**Think:** server network interface.

---

## MAC Address

A hardware-level network identifier associated with a network interface.

**Think:** identity of a network interface at Layer 2.

---

## IP Address

A logical network address assigned to a network interface.

**Think:** address used for network communication.

---

## VLAN — Virtual Local Area Network

A logical network segmentation mechanism used to separate traffic within network infrastructure.

**Think:** logical network separation.

---

## Switch

A network device that connects multiple devices and forwards Ethernet frames between them.

**Think:** connects network endpoints.

---

## Port

A physical or logical connection point.

In data center terminology, "port" may refer to:

- physical switch port
- NIC port
- TCP/UDP port

Context matters.

---

## Link

The active connection between two network interfaces.

Example:

```text
Server NIC
    │
    │ physical link
    │
Switch port
```

**Link UP** means the physical/network interface relationship is established.

---

## TCP — Transmission Control Protocol

A connection-oriented transport protocol that provides reliable, ordered delivery of data.

---

## UDP — User Datagram Protocol

A connectionless transport protocol with lower overhead than TCP and no built-in guarantee of delivery.

---

## DNS — Domain Name System

A system used to resolve names into IP addresses and other DNS records.

Example:

```text
server01.example.com
        ↓
    DNS lookup
        ↓
    IP address
```

---

## DHCP — Dynamic Host Configuration Protocol

A protocol used to automatically provide network configuration such as:

- IP address
- subnet mask
- default gateway
- DNS servers

---

## Default Gateway

The network device a host uses to reach networks outside its local subnet.

**Think:** path out of the local network.

---

# 4. Server Management

## BMC — Baseboard Management Controller

A dedicated hardware management controller used for out-of-band monitoring and management of a server.

BMC may provide:

- temperature monitoring
- fan monitoring
- PSU status
- hardware events
- remote console
- power control
- hardware inventory

Common vendor implementations include:

- Dell iDRAC
- HPE iLO
- Lenovo XClarity Controller

**Think:** independent hardware management.

---

## IPMI — Intelligent Platform Management Interface

A standard for monitoring and managing server hardware through a management controller such as a BMC.

**Think:** hardware management interface.

---

## Redfish

A modern RESTful API standard for server hardware management.

It can be used to query or manage hardware through a BMC.

**Think:** API for server management.

---

## BIOS — Basic Input/Output System

Firmware responsible for low-level hardware initialization and system startup.

---

## UEFI — Unified Extensible Firmware Interface

Modern firmware architecture used to initialize hardware and start the operating system.

**Think:** firmware before the OS.

---

## Firmware

Low-level software stored on hardware devices and used to control or initialize the device.

Examples:

- motherboard firmware
- NIC firmware
- SSD firmware
- BMC firmware
- RAID controller firmware

---

# 5. Power and Cooling

## PSU — Power Supply Unit

The server's internal power supply.

It converts incoming electrical power into the power required by the server's components.

**Think:** power inside the server.

---

## PDU — Power Distribution Unit

A device used at rack level to distribute electrical power to servers and other equipment.

**Think:** rack-level power distribution.

---

## UPS — Uninterruptible Power Supply

A system that provides power continuity during certain electrical failures or interruptions.

Simplified power path:

```text
Power source
     ↓
    UPS
     ↓
    PDU
     ↓
    PSU
     ↓
  Server
```

---

## Redundant Power

A design where multiple power supplies or power paths allow the server to continue operating if one component or path fails.

**Think:** avoid single power failure taking down the server.

---

## Airflow

The movement of air through the server chassis to remove heat from components.

Common cooling components include:

- fans
- heatsinks
- airflow channels

---

## Thermal Event

A hardware or system event related to abnormal temperature conditions.

Possible causes include:

- failed fan
- blocked airflow
- cooling component failure
- high workload
- high ambient temperature
- liquid cooling issue

---

# 6. Replaceable Hardware

## FRU — Field Replaceable Unit

A component designed to be replaced separately in the field.

Examples may include:

- PSU
- fan
- drive
- NIC
- GPU
- DIMM
- riser
- motherboard

**Important:**

> FRU does not automatically mean hot-swappable.

---

## Hot-Swap

A supported component can be replaced while the system remains powered on and operational.

Common examples on supported platforms:

- PSU
- drives
- some fans

Always check the specific server documentation.

---

## RMA — Return Merchandise Authorization

A process used to return a faulty hardware component to the vendor or manufacturer for replacement or repair.

**Think:** hardware replacement workflow.

---

# 7. Server Boot and Diagnostics

## POST — Power-On Self-Test

Initial hardware checks performed during system startup.

POST can help identify problems with:

- CPU
- RAM
- motherboard
- PCIe devices
- other hardware

**Think:** initial hardware check during boot.

---

## Boot

The process of initializing hardware and loading the operating system.

Simplified:

```text
Power on
   ↓
Firmware / UEFI
   ↓
Hardware initialization
   ↓
Bootloader
   ↓
Operating system
```

---

## Hardware Detection

The process by which firmware or the operating system identifies connected hardware devices.

---

## Fault Domain

The area of the system in which the problem is likely located.

Examples:

- server hardware
- PCIe path
- network connection
- switch infrastructure
- storage subsystem
- power infrastructure

**Think:** where the failure actually lives.

---

## Common Failure Point

A component or path shared by several affected devices.

Example:

```text
NVMe 1 ─┐
NVMe 2 ─┤
NVMe 3 ─┼── Backplane
NVMe 4 ─┘

All four fail
→ investigate the shared backplane
```

---

# 8. Linux and Command Line

## Linux

An open-source operating system kernel used by many server and data center systems.

Ubuntu is one Linux distribution.

---

## Distribution / Distro

A complete operating system built around the Linux kernel.

Examples:

- Ubuntu
- Debian
- Red Hat Enterprise Linux
- Rocky Linux

---

## CLI — Command-Line Interface

An interface where the user interacts with the system by entering commands.

---

## Shell

A program that interprets and executes commands.

A common Linux shell is **Bash**.

Important distinction:

> Linux = operating system environment  
> Bash = shell

---

## SSH — Secure Shell

A protocol used for secure remote command-line access to another system.

Typical workflow:

```text
Technician
    ↓
   SSH
    ↓
Linux server
    ↓
Shell
```

---

# 9. Troubleshooting

## Troubleshooting

A systematic process of identifying the cause of a technical problem and restoring normal operation.

---

## Fault Isolation

Narrowing the problem down to a specific component, connection, subsystem or external dependency.

---

## Evidence

Information collected during troubleshooting.

Examples:

- BMC status
- system logs
- sensor values
- link status
- hardware detection
- error messages
- comparison with another working system

---

## Verification

Checking that the problem has been resolved after a repair.

Typical pattern:

```text
Problem
  ↓
Diagnosis
  ↓
Repair
  ↓
Verification
```

---

## Common Troubleshooting Principle

Do not replace the most obvious component immediately.

Instead:

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

---

# 10. Support Levels

## L1 — Level 1 Support

First-line technical support.

Typical responsibilities may include:

- initial diagnosis
- standard troubleshooting
- hardware checks
- ticket handling
- documented procedures
- escalation when required

---

## L2 — Level 2 Support

More advanced technical troubleshooting.

L2 technicians may handle:

- deeper hardware diagnostics
- advanced troubleshooting
- workarounds
- component replacement
- more complex incidents

Exact responsibilities depend on the organization.

---

## L3 — Level 3 Support

Highly specialized engineering or expert-level support.

Often involved in:

- complex technical problems
- engineering-level investigation
- system design
- advanced root-cause analysis

---

## Escalation

Passing a problem to a more appropriate technical level or team when it exceeds the current support scope.

A good escalation includes:

- symptoms
- checks already performed
- evidence collected
- affected equipment
- suspected fault domain
- relevant logs or screenshots
- actions already taken

---

# 11. Data Center Operations

## Rack

A physical structure used to mount servers and other equipment.

---

## Server Chassis

The physical enclosure containing server components.

---

## Patch Cable

A short cable used to connect network or other infrastructure ports.

---

## Fiber Optic Cable

A cable that transmits data using light.

Common in high-speed data center networking.

---

## SFP — Small Form-factor Pluggable

A removable transceiver module used in network equipment.

---

## SFP+

An SFP form factor commonly associated with higher-speed Ethernet links such as 10 GbE.

---

## QSFP — Quad Small Form-factor Pluggable

A larger transceiver form factor used for high-speed networking.

---

# 12. Interview Vocabulary

## Detected

The hardware or operating system can identify the device.

Example:

> "The NIC is detected by the system."

---

## Link Up

A network link has been successfully established between interfaces.

Example:

> "The NIC and switch port both show link."

---

## Faulty

Not functioning correctly.

Example:

> "The drive appears to be faulty."

---

## Suspect

A component is considered a possible cause but has not yet been proven faulty.

Example:

> "I would suspect the backplane because several drives share it."

---

## Replace

Remove a faulty component and install a known-good replacement.

---

## Verify

Confirm that the system is functioning correctly after the repair.

---

## Root Cause

The underlying reason why a problem occurred.

---

## Symptom

The observable result of a problem.

Important distinction:

> A symptom is not necessarily the root cause.

Example:

```text
Symptom:
NVMe is not detected.

Possible root cause:
- faulty drive
- PCIe path
- power
- backplane
- firmware
- motherboard
```

---

# Quick Reference: Important Distinctions

| Concept | Meaning |
|---|---|
| PCIe | High-speed interface/interconnect |
| PCIe slot | Physical connector |
| Riser | Separate board providing/repositioning PCIe slots |
| SSD | Solid-state storage device |
| NVMe | Storage protocol |
| SATA | Storage interface |
| NIC | Network interface hardware |
| BMC | Dedicated server hardware management controller |
| PSU | Server power supply |
| PDU | Rack-level power distribution |
| UPS | Power continuity / backup system |
| FRU | Field-replaceable component |
| Hot-swap | Replaceable while system remains operational |
| RAM | Working memory |
| DIMM | Physical memory module |
| ECC | Hardware memory error correction technology |
| CPU | Main processing unit |
| GPU | Parallel compute processor |
| HBA | Storage connectivity adapter |
| Backplane | Shared drive connection board |
| L1 | First-level support |
| L2 | More advanced support |
| L3 | Expert / engineering support |
| CLI | Command-line interface |
| Bash | Common Linux shell |
| SSH | Secure remote shell access |
