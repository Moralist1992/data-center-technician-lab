# Server Boot — Interview Scenarios

## Scenario A — BMC works, server unavailable

**Interviewer:** A server is powered on, BMC is reachable, but the server is unavailable. What do you check?

> I would use the BMC Remote Console to determine the current state. I would check whether the server completed POST, whether a boot device was found, whether the bootloader appeared and whether Linux started. I would also check BMC events and storage status. The evidence would determine the next runbook.

## Scenario B — Memory initialization failed

**Interviewer:** What does this tell you?

> It tells me the failure occurred during the firmware or POST stage, before Linux started. I would check BMC memory events and identify the affected memory path according to the platform's troubleshooting procedure.

## Scenario C — No bootable device

**Interviewer:** Does that mean the SSD is dead?

> No. It only tells me that the firmware did not find a usable boot target. The cause could be storage detection, boot order, a missing UEFI entry, boot files or a storage problem. I would gather evidence before replacing hardware.

## Scenario D — PXE-E61

**Interviewer:** Is the NIC broken?

> Not necessarily. PXE-E61 indicates a problem with the network link during a PXE boot attempt. I would check the cable, SFP, switch port and link state, and also check why PXE was selected.

## Scenario E — Kernel panic

**Interviewer:** Is this a BIOS problem?

> No. A kernel panic means the Linux kernel has already started. I would investigate the kernel-level failure and continue according to the appropriate OS or boot troubleshooting procedure.

## Scenario F — Why use BMC if SSH is unavailable?

> BMC provides an out-of-band management path that is independent of the operating system. It can give me hardware status, event information and a Remote Console, so I can determine whether the server is powered and where the boot process stopped.

## Scenario G — Prove your Ubuntu VM uses UEFI

> I enabled UEFI in the VM firmware settings and verified it from Linux with `test -d /sys/firmware/efi && echo "UEFI" || echo "BIOS"`, which returned `UEFI`. The installation also created an EFI System Partition mounted at `/boot/efi`.
