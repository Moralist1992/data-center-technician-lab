# Common Technical Interview Questions

## Hardware
**What are the main components inside a server?**
> The main components are the CPU, RAM, storage, network interface, power supplies, and motherboard. A server can also have GPUs and other PCIe devices.

**What is ECC?**
> ECC is a technology that can detect and correct some memory errors.

**What is PCIe?**
> PCIe is a high-speed connection between the motherboard and devices such as GPUs, NICs, storage controllers, and NVMe devices.

**PSU vs PDU?**
> A PSU is inside the server and provides power. A PDU is usually in the rack and distributes power to equipment.

**What is FRU?**
> FRU means Field Replaceable Unit. It is a component that can be replaced in the field.

## BMC
**What is BMC?**
> BMC is a separate management controller in a server. It can monitor hardware and provide remote management and console access.

**SSH vs BMC?**
> SSH accesses the operating system, usually Linux. BMC manages the physical server and hardware.

**What is Redfish?**
> Redfish is a modern standard for managing server hardware through an API.

**What is IPMI?**
> IPMI is a standard for monitoring and managing server hardware through a management controller such as a BMC.

## Boot
**What is POST?**
> POST means Power-On Self-Test. It is an early hardware check before the operating system starts.

**What is a bootloader?**
> A bootloader is software that starts the operating system. Ubuntu commonly uses GRUB.

**What is kernel panic?**
> It means the Linux kernel has started but has encountered a serious problem and cannot continue normally.

**No bootable device?**
> I would check boot order and whether the expected storage device is detected. I would also check BMC storage information and follow the runbook.

**PXE-E61?**
> It usually means the server tried network boot but the required network link was not available. I would check the network path and why PXE was attempted.

## Linux
**What is Bash?**
> Bash is a common command-line shell used on Linux systems.

**How do you check the current user?**
> `whoami`

**Kernel version?**
> `uname -r`

**Logs?**
> I can use `journalctl`, for example `journalctl -b` for the current boot.

**If you do not know a command?**
> I would check the documentation or help, use the internal runbook if available, and test carefully. I would not guess on a production system.
