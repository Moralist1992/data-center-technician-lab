# Linux Server Boot — Step by Step

## 1. Power-on

The server receives power and begins platform initialization.

Linux is not running yet.

Simplified power path:

```text
Utility / UPS
    ↓
PDU
    ↓
Server PSU(s)
    ↓
Motherboard / power rails
```

The BMC may already be available independently of the host OS, depending on platform and power state.

## 2. Firmware starts

Modern servers commonly use **UEFI**. Older systems may use BIOS/legacy firmware.

Firmware initializes the platform and prepares the system for boot.

## 3. POST

**POST — Power-On Self-Test** is the firmware-driven hardware initialization/check phase.

Depending on the platform, firmware checks or initializes CPU, memory, memory controller, PCIe devices, storage controllers and other platform hardware.

If POST fails, Linux has not started yet.

Example:

```text
Memory initialization failed
```

This is a hardware/firmware-stage problem.

## 4. Boot target selection

Firmware determines what it should boot:

- local disk;
- removable media;
- network/PXE;
- another boot entry.

In UEFI, the firmware can use named boot entries.

## 5. EFI System Partition

UEFI systems commonly use an **EFI System Partition (ESP)**.

In Linux it is often mounted at:

```text
/boot/efi
```

The ESP is normally a FAT32 partition containing EFI boot files.

## 6. Bootloader

The firmware launches the bootloader.

Ubuntu commonly uses **GRUB**:

```text
UEFI
  ↓
EFI boot entry
  ↓
GRUB
  ↓
Linux kernel
```

GRUB can present a boot menu and load the Linux kernel and required early-boot files.

## 7. Linux kernel

The kernel is the core of Linux.

At this point Linux itself is beginning to run. The kernel initializes hardware and core OS functions.

A **kernel panic** means the Linux kernel started but encountered a fatal condition.

This is different from:

```text
No bootable device
```

because in the latter case Linux may not have started at all.

## 8. initramfs / early userspace

**initramfs** is an initial filesystem and early userspace environment loaded during boot.

It contains tools and drivers needed to continue booting before the real root filesystem is fully available.

```text
GRUB
 ↓
Kernel + initramfs
 ↓
Early userspace
 ↓
Root filesystem
```

## 9. Root filesystem and userspace

Linux mounts the real root filesystem and continues starting userspace.

Modern Ubuntu systems use **systemd** as the main system/service manager.

```text
Kernel
  ↓
systemd / userspace
  ↓
services
```

## 10. Network and SSH

Once Linux userspace is running, network interfaces and services can become available.

If OpenSSH server is installed and running, remote access can be provided through SSH.

Important:

```text
BMC Remote Console ≠ SSH
```

Remote Console can work before Linux is running.

SSH requires a functioning OS, network path and SSH service.

## 11. Final state

A server can boot successfully while an application or network service is still broken.

For a technician, "Linux booted" and "service is working" are different states.
