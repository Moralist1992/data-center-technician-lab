# BMC Management Interfaces

## Web UI

The BMC commonly provides a web interface with hardware inventory, sensors, Event Log, storage, memory, power, fans, temperatures, remote console and power controls.

## Redfish

**Redfish** is a modern API-based standard for server management.

For L1:

> Redfish is a standard API for managing and monitoring server hardware through the BMC.

## IPMI

**IPMI — Intelligent Platform Management Interface** is a standard for server management through a BMC.

For this stage, remember the concept rather than commands.

## Remote Console

Remote Console provides remote access to the physical server console.

It can show:

- BIOS/UEFI;
- POST messages;
- bootloader;
- Linux startup;
- a console after Linux has started.

It can therefore be used when SSH is unavailable.

It may feel similar to RDP, but it is not RDP technically.

## SSH vs BMC

| SSH | BMC |
|---|---|
| Talks to the OS | Talks to the management controller |
| Usually requires OS/network services | Can work independently of OS |
| Linux shell | Hardware management |
| Useful after Linux has booted | Useful before Linux boots |
| Services/logs/configuration | Sensors/events/inventory/console/power |

Interview phrase:

> SSH gives me access to the Linux operating system. BMC gives me out-of-band access to the server hardware and console, independently of the OS.
