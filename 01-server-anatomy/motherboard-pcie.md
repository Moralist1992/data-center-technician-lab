# Motherboard and PCIe

## Motherboard

The motherboard is the main circuit board of the server.

It provides the connections and interfaces required for:

- CPU
- RAM
- PCIe devices
- storage connections
- power
- management components

## PCIe

**PCIe = Peripheral Component Interconnect Express**

PCIe is a high-speed interface/interconnect used to connect devices to the server platform.

Common PCIe devices:

- GPU
- NIC
- HBA
- RAID controller
- NVMe devices/adapters

Important distinction:

> PCIe is an interface/interconnect, not a separate replaceable component.

## PCIe slot

A **PCIe slot** is the physical connector where a PCIe device can be installed.

Simple explanation:

> PCIe is the interface, while the PCIe slot is the physical connector.

## Riser

A **PCIe riser card** is a separate board that provides or repositions PCIe slots.

Example:

```text
Motherboard
     │
     ▼
 Riser card
     │
 ├── PCIe slot
 ├── PCIe slot
 └── PCIe slot
```

A riser is a replaceable physical component on supported systems.

This is where it is easy to confuse PCIe itself with a separate component. A server can have a replaceable riser card, but the PCIe architecture is still part of the platform rather than a single removable "PCIe component".

## Why a GPU failure does not automatically mean the GPU is faulty

Example:

> GPU is not detected.

Possible causes include:

- GPU itself
- physical seating/connection
- power
- PCIe slot
- PCIe link/path
- riser
- firmware/BIOS
- motherboard/platform

Therefore, compare other PCIe devices and look for a common point of failure.

## PCIe troubleshooting

Check:

1. Is the device physically connected?
2. Is the slot/riser healthy?
3. Is the device receiving power?
4. Does the system/firmware detect it?
5. Are other PCIe devices working?
6. Is there evidence of a common PCIe or motherboard problem?

## Fault isolation example

```text
GPU not detected
     │
     ├── Only GPU fails
     │      → suspect GPU / local connection
     │
     └── GPU + NIC + HBA fail
            → investigate common PCIe path,
              riser or motherboard/platform
```

## Important diagnostic principle

PCIe itself is normally not treated as a separate replaceable part.

Instead, investigate:

- PCIe slot
- PCIe lanes/path
- riser
- PCIe controller
- motherboard
- connected device

## Interview question

### "Why does a missing GPU not automatically mean the GPU is faulty?"

Good answer:

> Because the problem could be in the PCIe connection, slot, riser, power delivery, firmware or motherboard. I would compare the behavior of other PCIe devices and isolate the fault before replacing the GPU.

## Interview wording

A strong general sentence is:

> PCIe is a high-speed interface used to connect devices to the motherboard or server platform. A PCIe slot is the physical connector where a PCIe device can be installed.
