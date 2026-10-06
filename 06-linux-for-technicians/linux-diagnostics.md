# Basic Linux Diagnostic Thinking

## SSH unavailable
Possible layers: power → BMC → Linux boot → NIC → IP configuration → network path → SSH service.

Useful checks when access is available:
```bash
ip addr
ip link
ip route
systemctl status ssh
journalctl -b
```

## High CPU
```bash
top
ps aux
```
Identify processes consuming unusual CPU.

## Disk space
```bash
df -h
lsblk -f
```
Do not delete files without an approved procedure.

## Boot investigation
```bash
journalctl -b
dmesg
lsblk -f
```
Previous boot when available: `journalctl -b -1`.

## UEFI check
```bash
test -d /sys/firmware/efi && echo "UEFI" || echo "BIOS"
```
If `/sys/firmware/efi` exists, the current system booted using UEFI.

Linux command output is evidence, not automatically a root cause.
