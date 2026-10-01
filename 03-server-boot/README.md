# Block 03 — Server Boot

## Boot chain

```text
Power on
   ↓
Firmware: BIOS / UEFI
   ↓
Hardware initialization / POST
   ↓
Boot target selection
   ↓
Bootloader
   ↓
Linux kernel
   ↓
Early userspace / initramfs
   ↓
Linux userspace
   ↓
Services
   ↓
SSH / applications
```

The key diagnostic question is:

> **How far did the server get?**

| Evidence | Approximate stage |
|---|---|
| No power / no console | Before normal firmware progress |
| Firmware screen | BIOS/UEFI stage |
| POST error | Hardware initialization |
| "No bootable device" | Firmware could not find a usable boot target |
| GRUB menu/error | Bootloader stage |
| Kernel panic | Kernel started, then failed |
| Login prompt | Linux userspace reached console |
| SSH unavailable | Could be OS/network/service layer |

This is a diagnostic model; exact messages vary by platform.
