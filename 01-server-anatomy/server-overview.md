# Server Overview

## What is a server?

A server is a computer designed to provide services, applications, storage, networking or computing resources to other systems.

A typical server contains:

- CPU
- RAM
- motherboard
- PCIe devices
- storage
- NICs
- power supplies
- cooling system
- BMC / management controller

## Rack

Servers are commonly installed in racks.

A rack provides:

- physical mounting
- power distribution
- network connectivity
- airflow organization
- cable management

## Basic server architecture

```text
                    Server
                      │
          ┌───────────┴───────────┐
          │                       │
      Motherboard              Power
          │                       │
    ┌─────┼─────┐             PSU(s)
    │     │     │
   CPU   RAM   PCIe
                │
        ┌───────┼────────┐
        │       │        │
       GPU     NIC      HBA
        │       │
        │       ▼
        │    Network
        │
        ▼
     Compute

Storage may connect through:
- SATA
- PCIe / NVMe
- HBA / RAID controller
- backplane
```

## Main architecture idea

Do not think only about individual components. Think about the **connections between components**.

A troubleshooting problem can be caused by:

- the component itself
- its physical connection
- power
- the interface/path
- a shared component
- firmware
- the motherboard/platform

## Interview question

### "Can you explain the main components of a server?"

Good answer:

> A server has a motherboard that connects the main components, including the CPU and RAM. PCIe is used to connect high-speed devices such as GPUs, NICs and HBAs. The server also has storage, power supplies and cooling. A dedicated management controller called the BMC provides out-of-band hardware management.

## Interview mindset

A strong answer should show both **component knowledge** and **system relationships**.

For example, a GPU is not an isolated object. It is connected through a PCIe path and also depends on power, system firmware, the motherboard/platform and cooling.
