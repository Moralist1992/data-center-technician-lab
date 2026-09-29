# Memory — RAM, DIMM, ECC and NUMA

## RAM

**RAM = Random Access Memory**

RAM is temporary working memory used by the CPU and running applications/services.

It stores data and program state that the system needs while it is running.

Unlike storage, RAM is not intended for permanent data storage.

```text
Storage
   ↓
Load data / program
   ↓
  RAM
   ↓
  CPU
```

## RAM vs storage

### RAM

- temporary
- used by running processes
- fast
- loses its contents when power is removed

### Storage

- permanent
- HDD / SSD / NVMe
- stores files and system data

## DIMM

**DIMM = Dual Inline Memory Module**

A DIMM is the physical memory module installed into a motherboard memory slot.

Important distinction:

- RAM = memory technology/capacity
- DIMM = physical memory module

## ECC

**ECC = Error-Correcting Code**

ECC is a hardware-based technology that can detect and correct certain memory errors.

It uses additional information/bits to provide error detection and correction.

Important:

> ECC is NOT a software utility.

The ECC logic is implemented in the hardware/memory subsystem. The OS or BMC can report ECC-related errors, but ECC itself is not a program that a technician runs.

Good interview answer:

> ECC is a hardware-based technology that detects and corrects certain memory errors.

## NUMA

**NUMA = Non-Uniform Memory Access**

In multi-CPU server architectures, memory is associated with CPU sockets.

A CPU can access:

- local memory — generally lower latency
- remote memory — generally higher latency

```text
CPU 1 ─── Local RAM 1
  │
  │
  └────── Remote RAM 2

CPU 2 ─── Local RAM 2
```

## Interview questions

### "What is RAM?"

> RAM is the system's working memory. It stores data and program state that the CPU and running applications are actively using.

### "What is DIMM?"

> A DIMM is the physical memory module installed in a server's memory slot.

### "What is ECC?"

> ECC is a hardware-based technology that detects and corrects certain memory errors.

### "Why is memory associated with CPUs in NUMA systems?"

> In NUMA architectures, memory is associated with CPU sockets. Accessing local memory is generally faster than accessing memory associated with another CPU socket.

## Troubleshooting hints

If a DIMM or memory channel is reported as faulty, do not immediately assume the DIMM itself is bad. Consider:

- DIMM seating
- slot/channel
- memory population rules
- CPU socket association in NUMA systems
- motherboard/platform
- hardware error logs
- BMC information

The same fault-isolation principle applies:

**symptom → evidence → isolate → replace → verify**
