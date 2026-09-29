# Power and Cooling

## PSU

**PSU = Power Supply Unit**

A PSU provides the electrical power required by the server's internal components.

It powers components such as:

- motherboard
- CPU
- RAM
- storage
- PCIe devices
- fans

## Redundant PSUs

Servers often have two or more PSUs for power redundancy.

Example:

```text
PSU 1 ─────┐
           ├── Server
PSU 2 ─────┘
```

Both PSUs may operate simultaneously. Do not assume that one PSU is always completely passive while the other does all the work.

If one fails:

```text
PSU 1 ❌
PSU 2 ✓
   │
   ▼
Server continues operating
```

The exact power architecture depends on the server platform.

## PDU

**PDU = Power Distribution Unit**

A PDU distributes electrical power to equipment in a rack.

Important distinction:

**PSU**
- inside the server
- provides/conditions power for server components

**PDU**
- at rack level
- distributes electrical power to servers and other equipment

```text
Power infrastructure
       │
   ┌───┴───┐
   ▼       ▼
 PDU A   PDU B
   │       │
  PSU 1  PSU 2
   │       │
   └───┬───┘
       ▼
     Server
```

A PDU is not normally responsible for switching between redundant PSUs. Both PSU paths can receive power through the rack power infrastructure.

This arrangement can provide additional redundancy when separate power paths are used.

## UPS

**UPS = Uninterruptible Power Supply**

A UPS provides power continuity/backup during certain power events.

Simplified:

```text
Grid
  ↓
 UPS
  ↓
 PDU
  ↓
 PSU
  ↓
Server
```

Remember:

- UPS = power continuity / backup
- PDU = power distribution
- PSU = power supply for the equipment

## Cooling

Servers generate significant heat.

The cooling system may use:

- fans / air cooling
- liquid cooling
- hybrid cooling

The exact design depends on the server platform.

## Thermal troubleshooting

Scenario:

> CPU temperature is above the normal range.

First check:

- CPU/system temperature sensors
- fan status
- fan RPM
- failed or missing fans
- airflow
- physical obstruction
- cooling system status
- BMC hardware events
- workload
- liquid cooling components if the platform uses liquid cooling

Do not immediately replace a fan only because the CPU is hot.

High temperature may have many causes:

- failed fan
- abnormal fan speed
- insufficient airflow
- blocked airflow
- heatsink problem
- thermal interface problem
- liquid cooling problem, if applicable
- unusually high workload
- high ambient temperature
- another cooling component failure

## BMC and cooling

BMC may provide:

- temperature sensors
- fan status
- RPM
- thermal warnings
- hardware events

Good interview wording:

> I would check the BMC for temperature sensors, fan status and hardware events.

BMC is not simply "a terminal". Depending on the platform, it can be accessed through a web interface, CLI, Redfish/API or vendor-specific management tools.

## Fan-control caution

Do not say that your first action is to manually set fan RPM in software.

As an L1 technician, the priority is to diagnose the condition and follow the documented platform procedure. Fan speed may be managed automatically by the BMC/firmware/thermal control system.

If a fan is failed or abnormal, verify the fault and replace the appropriate FRU if the procedure requires it.

## Thermal troubleshooting flow

```text
High CPU temperature
        ↓
Check BMC / sensors
        ↓
Check fan status / RPM
        ↓
Check airflow / physical condition
        ↓
Check cooling architecture
        ↓
Identify faulty component
        ↓
Replace FRU if required
        ↓
Verify temperature and fan status
```

## Interview question

### "What would you check if a server's CPU temperature is too high?"

Good answer:

> First, I would check the BMC for temperature sensors, fan status, RPM and thermal events. Then I would check airflow and the cooling system. If a fan or another cooling component is reported as failed, I would follow the hardware procedure and replace the appropriate FRU if necessary. After the replacement, I would verify that the cooling system and temperature return to normal.
