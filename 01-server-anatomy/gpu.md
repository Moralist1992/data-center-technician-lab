# GPU

## What is a GPU?

**GPU = Graphics Processing Unit**

In modern AI/data center environments, GPUs are also used for:

- parallel computing
- AI/ML workloads
- high-performance computing

A data center GPU is therefore not necessarily being used for graphics.

## Connection

GPUs commonly connect to the server platform through PCIe.

```text
Motherboard
     │
  PCIe path
     │
     ▼
    GPU
```

High-performance GPU servers may contain multiple GPUs.

## GPU troubleshooting

Example:

> GPU is not detected.

Do not immediately replace the GPU.

Check:

- physical installation
- power
- PCIe slot/path
- riser if present
- system/firmware detection
- BMC / hardware monitoring
- other PCIe devices

## Diagnostic logic

```text
GPU not detected
      ↓
Check physical connection
      ↓
Check power
      ↓
Check PCIe path / slot / riser
      ↓
Check system / firmware / BMC
      ↓
Compare with other PCIe devices
      ↓
Isolate faulty component
      ↓
Replace FRU
      ↓
Verify detection
```

## Why compare other PCIe devices?

Because multiple devices can share parts of the same infrastructure.

For example:

```text
Motherboard
    │
  Riser
 ┌──┼────┐
GPU NIC HBA
```

If only the GPU disappears, the GPU or its local path becomes more suspicious.

If the GPU, NIC and HBA all disappear, investigate the common riser/PCIe path or motherboard/platform before replacing several independent devices.

## Interview question

### "How would you troubleshoot a GPU that is not detected?"

Good answer:

> I would first check the physical connection and power. Then I would check the PCIe path, slot or riser and whether the system or BMC detects the device. I would also compare the behavior of other PCIe devices. If the rest of the PCIe path is healthy, I would suspect the GPU itself and replace it according to the hardware procedure, then verify detection.

## Key principle

**Symptom ≠ root cause**

"GPU not detected" only describes the symptom.
