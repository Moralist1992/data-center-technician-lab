# FRU and Hot-Swap

## FRU

**FRU = Field Replaceable Unit**

A FRU is a component designed to be replaced separately in the field without replacing the entire system.

Possible FRUs depend on the server platform.

Examples may include:

- PSU
- fan
- drive
- NVMe
- NIC
- GPU
- DIMM
- riser
- motherboard

## Hot-Swap

Hot-swap means a supported component can be replaced while the system remains powered on and operational.

Important:

> FRU does NOT automatically mean hot-swappable.

A component can be a FRU but still require the server to be powered down before replacement.

## Examples

Common hot-swappable components on supported server platforms may include:

- PSUs
- drives
- fans

Always verify the specific server's documentation.

## PSU example

```text
PSU 1 ✓
PSU 2 ✓
    │
    ▼
  Server
```

If PSU 1 fails:

```text
PSU 1 ❌
PSU 2 ✓
    │
    ▼
Server continues operating
```

A supported hot-swap PSU can then be replaced while the server remains running.

## GPU warning

A GPU may be a FRU without being hot-swappable.

The fact that a server has multiple GPUs does **not** automatically mean one can be physically removed while the server is running.

Always verify the hardware platform and service procedure.

## CPU warning

A CPU may be replaceable as a FRU during servicing, but normal CPU replacement requires the server to be powered down.

Multiple CPUs do not automatically make CPUs hot-swappable.

## FRU vs Hot-Swap

```text
FRU
=
Field Replaceable Unit

Hot-Swap
=
Can be replaced while the system remains operational
```

## Interview questions

### "What is a FRU?"

> FRU means Field Replaceable Unit. It is a component designed to be replaced separately in the field.

### "What is hot-swap?"

> Hot-swap means a supported component can be replaced while the system remains powered on and operational.

### "Does FRU automatically mean hot-swappable?"

> No. A component can be a FRU but still require the system to be powered down before replacement.

## Important interview principle

Never assume that a component is hot-swappable just because the server has redundant copies of it.

Always check the server platform and documented service procedure.
