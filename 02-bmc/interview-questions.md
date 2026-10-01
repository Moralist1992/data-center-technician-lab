# BMC — Interview Questions

### What is BMC?

> BMC stands for Baseboard Management Controller. It is a dedicated management controller that provides out-of-band access to server hardware, including sensors, events, inventory, power control and often a remote console.

### What does out-of-band management mean?

> It means managing or monitoring the server through a management path that is independent of the main operating system.

### Can BMC work if Linux is down?

> Yes. The BMC is independent of the operating system, so it can often remain accessible when Linux is not running.

### What is the difference between SSH and BMC?

> SSH gives access to the operating system, usually the Linux command line. BMC provides hardware-level management independently of the OS.

### What is Redfish?

> Redfish is a modern API-based standard for managing and monitoring server hardware through the management controller.

### What is IPMI?

> IPMI is a standard for interacting with and managing server hardware through a BMC.

### What is Remote Console?

> It provides remote access to the physical server console. It can be used to see BIOS or UEFI, POST, bootloader and operating-system startup even when SSH is unavailable.

### Does BMC detect every possible hardware or network problem?

> No. It provides valuable hardware telemetry and events, but not every failure is visible through BMC. For example, a physical Ethernet link can be down while the NIC itself is healthy.

### What is an FRU?

> FRU means Field Replaceable Unit — a component that can be replaced in the field according to the service procedure.

### Is every FRU hot-swappable?

> No. FRU describes replaceability in the field; hot-swap describes whether the component can be replaced while the system remains powered. They are different concepts.

## Strong L1 troubleshooting answer

> I would start with evidence rather than assumptions. I would check BMC status, hardware events, sensors and inventory, use the Remote Console when necessary, identify the affected subsystem, follow the relevant runbook, perform the approved action, verify the result and document the outcome.
