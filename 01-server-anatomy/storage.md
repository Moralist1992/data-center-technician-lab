# Storage — HDD, SSD and NVMe

## HDD

**HDD = Hard Disk Drive**

HDDs use mechanical components:

- rotating magnetic platters
- moving read/write heads

Characteristics:

- mechanical
- generally slower than SSD/NVMe
- vulnerable to mechanical wear and physical shock

HDDs commonly use SATA or SAS interfaces in server environments.

## SSD

**SSD = Solid-State Drive**

SSD storage uses flash memory and has no moving mechanical parts.

Compared with HDD:

- faster
- lower latency
- no moving mechanical components

A traditional SSD can use SATA.

## NVMe

**NVMe = Non-Volatile Memory Express**

NVMe is a protocol designed for non-volatile storage, typically SSDs, and commonly uses PCIe.

Important:

> NVMe is not simply a "new type of SSD".

Better model:

```text
SSD = type of storage device
NVMe = storage protocol
PCIe = high-speed interface/transport
```

## SATA SSD vs NVMe SSD

```text
SATA SSD:
SSD → SATA → Motherboard

NVMe SSD:
SSD → PCIe → Motherboard
```

NVMe generally provides much higher performance and lower latency than SATA SSDs because it is designed to use PCIe efficiently.

NVMe is also not identical to a single physical form factor. M.2 is common, but server platforms can use other physical implementations such as U.2/U.3 or PCIe add-in cards.

## NVMe troubleshooting

Scenario:

> The server is running, but one NVMe drive is not detected.

Possible causes:

- faulty NVMe drive
- physical connection problem
- PCIe slot/path problem
- riser problem
- power problem
- firmware/BIOS configuration
- PCIe link problem
- motherboard/PCIe controller problem
- backplane problem, if the server uses a backplane

## What each failure category means

### 1. Faulty NVMe drive

The SSD controller or device itself may be defective.

Possible verification steps depend on the platform:

- check system/OS detection
- check BIOS/UEFI
- check BMC if storage visibility is supported
- test another compatible drive or slot according to procedure
- replace the suspected FRU and verify

### 2. PCIe connection / slot / riser

The device may be healthy but the physical PCIe path may have a problem.

A riser is a separate physical board that may contain several PCIe slots. If several devices connected through the same riser fail, the riser/common path becomes more suspicious.

### 3. Power problem

No power means the device may not initialize at all.

Power and data connectivity are separate concepts.

A device can have a correct data connection but no power, or correct power but a failed data/PCIe path.

### 4. Firmware / BIOS configuration

The physical hardware may be healthy while firmware configuration prevents the expected device from being initialized or exposed.

Check according to the documented platform procedure. Do not change BIOS/firmware settings randomly.

### 5. PCIe link problem

The PCIe slot can physically exist while the PCIe link between the device and the platform fails to establish correctly.

This can involve:

- device
- slot
- lanes
- riser
- PCIe controller
- signal/connection issues

For L1, understand the concept first; deep electrical signaling is not required at this stage.

### 6. Motherboard / PCIe controller problem

If multiple PCIe devices show problems, investigate shared infrastructure.

Example:

```text
Motherboard / PCIe infrastructure
          │
      ┌───┼────┐
      │   │    │
    NVMe  NIC  HBA
      ❌   ❌    ❌
```

Multiple devices failing together are evidence for a common fault domain.

### 7. Backplane problem

Some server architectures use a drive backplane instead of connecting every drive directly to the motherboard.

A backplane may provide:

- physical drive connections
- power distribution
- data connectivity
- management/signaling

Example:

```text
NVMe 1 ─┐
NVMe 2 ─┤
NVMe 3 ─┼── Backplane ── Server platform
NVMe 4 ─┘
```

If four drives connected through one backplane fail while four drives on another backplane continue working, the common backplane/path should be investigated before assuming four independent drive failures.

## Diagnostic chain

```text
NVMe drive
    │
    ▼
Physical connection
    │
    ▼
PCIe slot / connector
    │
    ▼
PCIe link/path
    │
    ▼
Riser / backplane
    │
    ▼
Motherboard / PCIe controller
    │
    ▼
Firmware / OS
```

Power is also checked along the relevant hardware path.

## Interview question

### "How would you troubleshoot an NVMe drive that is not detected?"

Good answer:

> I would check the physical connection, power and PCIe path first. Then I would check whether the drive is detected by the BMC, system firmware or operating system, depending on the platform. I would also check for a shared component such as a riser or backplane. If the system side is healthy, I would suspect the drive and replace the FRU according to the procedure, then verify that the new drive is detected.

## Fault isolation examples

### One NVMe fails

> Suspect the drive or its local connection/path.

### Four NVMe drives on one backplane fail

> Suspect the common backplane, power path or data path.

### Many unrelated PCIe devices fail

> Investigate common PCIe infrastructure, controller or motherboard/platform.
