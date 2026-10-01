# Boot Investigation — Practical Commands

## Check boot mode

```bash
test -d /sys/firmware/efi && echo "UEFI" || echo "BIOS"
```

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

## Inspect disks and partitions

```bash
lsblk -f
```

## Inspect UEFI boot entries

If available:

```bash
sudo efibootmgr -v
```

## Inspect current kernel

```bash
uname -a
```

## Check systemd boot state

```bash
systemctl is-system-running
```

Useful states include `running`, `degraded`, `starting` and `stopping`.

## Inspect current boot journal

```bash
journalctl -b
```

For page-by-page viewing:

```bash
journalctl -b | less
```

Press:

```text
q
```

to exit `less`.

## Previous boot

```bash
journalctl -b -1
```

This requires previous-boot logs to be available.

## Kernel messages

```bash
dmesg
```

or:

```bash
dmesg | less
```

## Important

Command output is evidence, not automatically a diagnosis.

Correlate:

```text
symptom
+
timestamp
+
system state
+
hardware evidence
+
logs
```
