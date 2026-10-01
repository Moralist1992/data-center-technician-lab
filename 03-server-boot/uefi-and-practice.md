# UEFI — Practical Lab

The lab VM was configured with UEFI.

## Check boot mode

```bash
test -d /sys/firmware/efi && echo "UEFI" || echo "BIOS"
```

Expected result:

```text
UEFI
```

The presence of `/sys/firmware/efi/` indicates that Linux was booted through the EFI firmware interface.

## Inspect EFI interface

```bash
ls -la /sys/firmware/efi
```

## Inspect EFI System Partition

```bash
ls -la /boot/efi
```

## Check how it is mounted

```bash
findmnt /boot/efi
```

## Inspect block devices

```bash
lsblk -f
```

Useful for seeing disks, partitions, filesystems and mount points.

## Inspect UEFI boot entries

If installed:

```bash
sudo efibootmgr -v
```

This can show UEFI boot entries and their paths.

## What the lab demonstrates

```text
UEFI enabled
   ↓
EFI System Partition
   ↓
Ubuntu boot files
   ↓
GRUB
   ↓
Linux
```

The practical command returned `UEFI`, confirming the running Ubuntu instance was booted through UEFI.
