# BMC Overview

## What is BMC?

**BMC — Baseboard Management Controller** is a dedicated management controller inside a server.

It operates independently from the main operating system and provides **out-of-band management**.

This means the technician can often manage or inspect a server even when Linux is not running or is not reachable.

## What BMC can provide

Depending on the server platform:

- temperature sensors;
- fan status and RPM;
- voltage and power information;
- PSU status;
- hardware inventory;
- memory-related events;
- PCIe-related events;
- storage/controller information;
- hardware Event Log;
- remote console;
- power on/off/reset;
- management network access.

BMC capabilities are platform-dependent.

## How does BMC get hardware information?

BMC is a separate controller on the motherboard/platform. It receives information through the server's hardware management/sensor infrastructure.

```text
CPU / DIMMs / PSU / Fans / Board sensors / other hardware
                 │
                 │ hardware monitoring information
                 ▼
                BMC
                 │
        ┌────────┼─────────┐
        ▼        ▼         ▼
      Web UI   Redfish    IPMI
        │
        ▼
    Technician
```

The important idea is that Linux does not have to tell the BMC whether a fan is running. The BMC has its own management path and can continue to report hardware information independently of the OS.

## Important limitation

BMC does not automatically detect every possible failure.

For example:

- a physical Ethernet link can be down while the NIC itself is healthy;
- a monitoring pipeline can fail;
- an application can be unavailable while hardware looks normal.

Therefore:

> No BMC alarm does not mean that no problem exists.
