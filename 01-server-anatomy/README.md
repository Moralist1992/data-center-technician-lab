# Block 1 — Server Anatomy

This section covers the main components of a modern server and the basic troubleshooting logic used by a Data Center Technician.

## Core troubleshooting principle

Always move from symptom to evidence:

**Symptom → Check → Isolate → Identify faulty component → Replace → Verify**

Do not replace a component immediately just because it is associated with the symptom.

When several devices fail at the same time, look for a **common component or common path**.

Example:

```text
One NVMe fails
→ suspect the drive or its local connection

Four NVMe drives fail
→ check the common backplane / power / PCIe path
```

Another useful principle:

> **Symptom ≠ root cause.**

A message such as `GPU not detected`, `NVMe not detected`, or `network down` describes the symptom. The technician's job is to isolate the fault domain.

## Components covered

- Server chassis and rack
- CPU
- RAM / DIMM / ECC / NUMA
- Motherboard
- PCIe / PCIe slots / risers
- GPU
- Storage: HDD / SATA SSD / NVMe
- NIC
- PSU
- PDU
- UPS
- Cooling and fans
- FRU
- Hot-Swap

## Key distinctions

### PCIe

**PCIe = interface / interconnect**

**PCIe slot = physical connector**

**Riser = separate board used to provide or reposition PCIe slots**

PCIe itself is normally not treated as a separate replaceable part. When a PCIe device is not detected, investigate the device, physical connection, slot, riser, PCIe path, controller and motherboard/platform as appropriate.

### Storage

**SSD = type of storage device**

**NVMe = storage protocol designed for non-volatile memory devices, commonly using PCIe**

A traditional SATA SSD uses SATA. An NVMe SSD normally uses PCIe.

### FRU and Hot-Swap

**FRU = Field Replaceable Unit**

A FRU is a component that can be replaced separately in the field.

**Hot-Swap = the component can be replaced while the system remains powered and operational, if the platform supports it.**

FRU does **not** automatically mean hot-swappable.

## Interview mindset

A technician should be able to explain:

1. What the component is
2. What it does
3. How it connects to the rest of the system
4. What can fail
5. How to isolate the fault
6. What to replace
7. How to verify the repair

## General fault-isolation examples

```text
GPU not detected
→ check physical installation
→ check power
→ check PCIe slot/path/riser
→ check system/firmware/BMC
→ compare other PCIe devices
→ isolate faulty FRU
→ replace
→ verify
```

```text
One NVMe not detected
→ check drive / local path

Several NVMe drives on one common path not detected
→ suspect common backplane / riser / power / data path
```

```text
Network connectivity lost
→ NIC detected?
→ interface up?
→ physical link up?
→ cable connected?
→ switch port up?
→ link up on both sides?
→ end-to-end communication?
```

## Block 1 completion

The following topics were studied and practiced:

- Server architecture
- CPU
- RAM, DIMM, ECC, NUMA
- Motherboard, PCIe and risers
- GPU
- HDD, SATA SSD and NVMe
- NIC and network troubleshooting layers
- PSU, PDU and UPS
- Cooling and thermal troubleshooting
- FRU and Hot-Swap
- Basic hardware fault isolation
