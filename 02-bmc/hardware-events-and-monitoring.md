# Hardware Events, Monitoring and Evidence

## Hardware Event Log

Hardware Events are a record of hardware-related events reported by the platform/BMC.

Examples:

- fan failure;
- ECC memory error;
- PSU failure;
- PCIe error;
- voltage event;
- thermal event.

The Event Log is evidence used during troubleshooting.

## Storage vs Hardware Events

| BMC area | What it tells you |
|---|---|
| Hardware Events | Events/errors that occurred |
| Storage | Inventory/status of storage devices/controllers/RAID/NVMe/SSD |

Example:

```text
Storage:
NVMe2 — Not Detected

Event Log:
PCIe link failure / storage device error
```

## Monitoring chain

```text
Sensor
  ↓
Telemetry
  ↓
Monitoring system
  ↓
Rule / threshold
  ↓
Alert
  ↓
Notification
  ↓
Ticket
  ↓
Technician
```

A failure anywhere in this chain can prevent a ticket from being generated.

> No alert does not prove that hardware is healthy.

If monitoring itself is suspected, verify the monitoring path or escalate according to the team's procedure.

## Evidence vs hypothesis

**Evidence** = objective information obtained during diagnostics.

Examples:

- BMC reports `Fan 1 = 0 RPM`;
- Event Log contains an ECC error for DIMM B2;
- Remote Console shows POST memory initialization failure;
- Storage page shows NVMe2 not detected.

**Hypothesis** = interpretation based on evidence.

Example:

> DIMM B2 may be faulty.

Do not confuse the two.
