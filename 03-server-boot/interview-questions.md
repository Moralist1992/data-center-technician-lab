# Server Boot — Interview Questions

### Walk me through the Linux boot process.

> First the server powers on and firmware starts. The firmware initializes the platform and performs POST. Then it selects a boot target. In UEFI mode it uses an EFI boot entry and the EFI System Partition to start the bootloader, commonly GRUB. GRUB loads the Linux kernel and initramfs. The kernel initializes the operating system, the root filesystem and userspace are started, systemd starts services, and eventually networking and services such as SSH become available.

### BIOS vs UEFI?

> They are firmware environments used to initialize the platform and start the boot process. UEFI is the modern firmware model and commonly uses an EFI System Partition and UEFI boot entries.

### What is POST?

> POST stands for Power-On Self-Test. It is the firmware-driven hardware initialization and checking stage that happens before the operating system starts.

### If POST fails, has Linux started?

> No. A POST failure occurs before normal Linux startup.

### What is an EFI System Partition?

> It is a special partition used by UEFI to store EFI boot files. In Linux it is commonly mounted at `/boot/efi` and is normally formatted as FAT32.

### What is GRUB?

> GRUB is a bootloader commonly used by Ubuntu. It is started by the firmware and loads the Linux kernel and required early-boot files.

### What is the Linux kernel?

> The kernel is the core of the Linux operating system. It initializes hardware and provides the core operating-system functions needed to run userspace.

### What is initramfs?

> initramfs is an initial filesystem and early userspace environment loaded during boot. It contains tools and drivers needed to continue the boot process before the real root filesystem is fully available.

### What does kernel panic mean?

> It means the Linux kernel started but encountered a fatal condition and could not continue normally.

### What does "No bootable device" mean?

> It generally means the firmware could not find a usable boot target. I would check storage detection, boot order, UEFI boot entries and the boot files according to the runbook.

### What does PXE-E61 mean?

> It indicates that the system attempted a PXE network boot and the required network link or media was not available. I would check the physical link, cable or SFP, switch port, and also determine why PXE was selected instead of the expected local boot device.

### The server is unreachable. What do you do?

> I would first determine how far the server got. I would check BMC access, power state and hardware events, then use Remote Console to see whether the system is in firmware, POST, bootloader, Linux startup or a login state. I would use that evidence to select the correct troubleshooting path.

### Remote Console vs SSH?

> Remote Console provides access to the physical server console through the management controller and can work before Linux starts. SSH provides remote access to the Linux operating system after the OS and network services are available.

### How do you prove that Linux booted through UEFI?

```bash
test -d /sys/firmware/efi && echo "UEFI" || echo "BIOS"
```

Expected result:

```text
UEFI
```

> The presence of `/sys/firmware/efi` indicates that Linux was booted through the EFI firmware interface.

### What is your troubleshooting philosophy for a boot problem?

> I first identify the last stage that completed successfully. Then I collect objective evidence from the console, BMC, storage and system state. I follow the relevant runbook, isolate the fault instead of guessing, perform the approved action, verify the result and document the incident.
