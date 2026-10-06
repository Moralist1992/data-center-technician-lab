# Block 05 — Data Center Fundamentals

## Purpose
Understand the physical and operational environment in which servers run.

## Basic model
```text
Facility power → UPS / distribution → PDU → Server PSU → Server components

Server NIC → SFP → Fiber/Copper → SFP → Switch

Technician → Management network → BMC → Server hardware
```

## Rack
A rack is a standard frame for servers, switches, PDUs, storage and other infrastructure. `U` is a standard rack-height unit; a 1U server occupies one unit.

## Power redundancy
A server may have two PSUs connected to separate power paths. Redundancy reduces the chance that one failed component stops the server.

## Cooling
Servers turn electrical power into heat. Fans and controlled airflow keep components within safe temperatures. Watch temperature, RPM, airflow direction, blocked vents and failed fans.

## Operational principle
Connect the ticket to the physical system, management interface, diagnostics, action, verification and documentation.
