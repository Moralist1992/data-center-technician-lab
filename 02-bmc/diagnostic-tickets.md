# BMC Diagnostic Tickets

## Ticket 1 — Server is unreachable

**Symptom:** the server is reported as unreachable.

Treat "unreachable" as a symptom, not a diagnosis.

### L1 sequence

1. Check whether BMC is reachable.
2. Check BMC hardware status.
3. Check Event Log.
4. Check power state.
5. Open Remote Console if available.
6. Determine whether the server reached POST / boot / Linux.
7. Follow the relevant runbook.
8. Document evidence and escalate if required.

**Interview:** The server is unreachable. What do you do?

> I would first treat "unreachable" as a symptom and determine which layer is failing. I would check BMC access, hardware status and events, power state, and then use the Remote Console to see how far the server got during boot. Based on the evidence, I would follow the relevant runbook and avoid replacing hardware based only on the initial symptom.

---

## Ticket 2 — Uncorrectable ECC error

**Evidence:**

```text
Uncorrectable ECC error — DIMM B2
```

This identifies an important memory-related event, but does not automatically prove that the DIMM itself is the root cause.

### Sequence

```text
Event
 ↓
Identify affected DIMM
 ↓
Follow memory troubleshooting runbook
 ↓
Check additional evidence
 ↓
Reseat / replace if procedure requires
 ↓
Boot / test
 ↓
Verify
 ↓
Document
```

**Interview:** Would you immediately replace B2?

> No. I would treat the event as evidence and follow the memory troubleshooting procedure. I would check the required diagnostics and only replace or reseat the FRU when the procedure supports that action. After the action I would verify the system and document the result.

---

## Ticket 3 — Fan failure / overheating

**Evidence:**

```text
CPU temperature: 92°C
Fan 1: 0 RPM
```

### Sequence

1. Check BMC sensor data and Event Log.
2. Check the physical fan connection if accessible and permitted.
3. Determine whether the fan is actually failed or disconnected.
4. Correct the confirmed issue according to the runbook.
5. Verify RPM and temperature.
6. Document.

**Interview:** Would you immediately replace the fan?

> Not immediately. I would first confirm the evidence and check the physical connection. If the fan is confirmed faulty, I would replace the appropriate FRU according to the procedure and then verify RPM and temperature.

---

## Ticket 4 — PSU failure

**Evidence:**

```text
PSU2 — Failed
```

The server may continue running if redundant power is available.

### Sequence

1. Confirm PSU state in BMC.
2. Check Event Log.
3. Check whether redundancy is still available.
4. Follow the PSU replacement procedure.
5. Replace the FRU if confirmed.
6. Verify PSU health and server power state.
7. Document.

**Interview:** If one PSU fails, why might the server still be running?

> The server may have redundant power. Another PSU can continue supplying power while the failed PSU is replaced, depending on the platform's design and configuration.

---

## Ticket 5 — GPU not detected

```text
GPU not detected ≠ GPU definitely defective
```

Check:

```text
GPU
 ↓
PCIe connection
 ↓
Riser / backplane if present
 ↓
Motherboard / PCIe slot
 ↓
Power
 ↓
Firmware / platform state
```

Also check whether other PCIe devices are affected.

**Interview:** A GPU is not detected. What would you check?

> I would not immediately conclude that the GPU is faulty. I would check the GPU's physical connection, PCIe path, riser if present, power, BMC information and relevant firmware or platform information. I would also check whether other PCIe devices are affected because that can help isolate the fault.

---

## Ticket 6 — Monitoring shows no alert

The absence of an alert does not prove that hardware is healthy.

Check:

```text
Sensor → telemetry → monitoring → rule → alert → notification
```

If the monitoring path is faulty, escalate according to procedure.
