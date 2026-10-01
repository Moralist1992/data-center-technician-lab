# Linux Boot Diagnostics — L1 Runbook

## Golden rule

Do not start by guessing the failed component.

First determine:

> **At which stage did boot stop?**

| Symptom / evidence | Likely stage | First action |
|---|---|---|
| Server has no power | Power | Check power path / BMC |
| BMC available, host console blank | Platform/boot investigation | Open Remote Console, check power and firmware state |
| Firmware screen appears | Firmware | Continue boot diagnostics |
| POST error | POST / hardware initialization | Read exact error, check BMC events |
| Memory initialization failure | POST / memory | Check BMC memory events and memory runbook |
| No bootable device | Boot target selection | Check disk detection and boot order |
| UEFI boot entry missing | UEFI / boot files | Inspect EFI/boot configuration |
| GRUB appears | Bootloader | Diagnose GRUB/kernel path |
| Kernel panic | Kernel | Read panic message and relevant runbook |
| Login prompt appears | Userspace reached console | Investigate service/network if SSH is unavailable |
| SSH connection refused | OS/network/service | Check IP, interface, SSH service and firewall as applicable |
| PXE-E61 | PXE/network boot | Check physical link and why PXE was selected |

## Case 1 — No bootable device

Firmware has progressed far enough to attempt booting, but did not find a usable boot target.

Possible areas:

- storage not detected;
- wrong boot order;
- missing/corrupt boot files;
- missing UEFI boot entry;
- disk/partition problem.

Sequence:

```text
Firmware
 ↓
Check boot target
 ↓
Check storage detection
 ↓
Check boot order / UEFI entry
 ↓
Check EFI / boot files if procedure permits
 ↓
Follow runbook
 ↓
Verify boot
```

Do not immediately conclude that the disk is physically dead.

## Case 2 — POST memory failure

Example:

```text
Memory initialization failed
```

This occurred before Linux.

Sequence:

1. Capture exact message.
2. Check BMC Event Log.
3. Check memory-related events/sensors.
4. Identify affected DIMM/channel if possible.
5. Follow memory runbook.
6. Perform approved reseat/replacement action.
7. Reboot and verify POST.
8. Verify Linux boot.
9. Document.

## Case 3 — Kernel panic

A kernel panic means the Linux kernel has already started.

Sequence:

1. Capture the exact panic message.
2. Determine whether it is repeatable.
3. Check relevant recent changes if applicable.
4. Check storage/root filesystem and boot configuration according to the runbook.
5. Use BMC/console evidence.
6. Escalate when outside L1 scope.
7. Document.

Do not describe a kernel panic as a BIOS failure.

## Case 4 — PXE-E61

```text
PXE-E61: Media test failure, check cable
```

The firmware attempted a PXE network boot and the required network link/media was not available.

"Media" here means network media/link.

Sequence:

```text
Check physical link
 ↓
Check cable / SFP / NIC connection
 ↓
Check switch port
 ↓
Check NIC link state
 ↓
Determine why PXE was attempted
 ↓
Check expected local boot device / boot order
 ↓
Follow runbook
 ↓
Verify
```

Important:

> PXE-E61 does not prove that the NIC is defective.

The NIC can be detected while its Ethernet link is down.

## Case 5 — Server unreachable but BMC works

The BMC is reachable, so the server is powered enough for management and the management path is available.

Use Remote Console to determine whether the server is in firmware, bootloader, Linux startup or login state.

If Linux is running, investigate OS/network/service layer.

## Case 6 — Server unreachable and BMC unavailable

Possible areas include power, management network, BMC itself, physical network path or upstream management infrastructure.

Use the team's runbook and escalation path rather than assuming the host OS is the cause.

## Evidence checklist

Capture:

- exact console message;
- BMC availability;
- power state;
- BMC Event Log;
- storage detection;
- boot mode;
- boot order / UEFI entries when relevant;
- whether POST completes;
- whether GRUB appears;
- whether the kernel starts;
- whether a login prompt appears;
- whether SSH is available.

This creates a timeline of how far the server progressed.
