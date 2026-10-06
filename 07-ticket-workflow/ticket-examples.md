# Ticket Examples

## GPU not detected
**Symptom:** GPU 2 is not detected.

**Evidence:** BMC inventory, PCIe status, power, physical connection, riser.

**Action:** follow GPU/PCIe runbook.

**Verification:** GPU appears, no related event, monitoring returns to normal.

## ECC error
**Symptom:** uncorrectable ECC on DIMM B2.

**Evidence:** BMC Event Log, memory inventory, POST status, related events.

**Action:** follow memory procedure; do not assume the DIMM is automatically the root cause.

## Fan failure
**Symptom:** Fan 1 = 0 RPM.

**Evidence:** BMC sensor, temperature, event, physical connection.

**Action:** repair/replace according to runbook.

## Server unreachable
**Evidence:** power, BMC, BMC events, Remote Console, boot state, network state.

**Key point:** `Server unreachable` is a symptom, not a diagnosis.
