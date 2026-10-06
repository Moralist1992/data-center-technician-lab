# Troubleshooting Scenarios for an L1 Interview

## Server unreachable
> First, I would check if the server has power and if the BMC is reachable. Then I would check BMC hardware events and the remote console. I would identify whether the problem is power, hardware, boot, the operating system, or the network.

## GPU missing
> No. First, I would check BMC, PCIe detection, power, physical connections, and the PCIe riser if there is one. I would use evidence before replacing the GPU.

## Memory error
> I would check the hardware event log and the memory runbook. I would not immediately assume the DIMM is faulty. I would follow the diagnostic steps and verify the result.

## High temperature
> I would check BMC, the fan connection and airflow. If the fan is confirmed faulty, I would replace it according to the runbook and verify temperature and fan speed.

## No bootable device
> I would check boot order and whether the expected storage device is detected. I would also check BMC storage information and follow the boot/storage runbook.

## Kernel panic
> It means the Linux kernel has started but has encountered a serious problem and cannot continue normally.

## PXE-E61
> It usually means the server tried network boot but the required network link was not available. I would check cable/SFP, NIC link, switch side through the correct process, and why PXE was attempted.

## BMC works, SSH does not
> I would use the remote console to see whether Linux is running. Then I would check OS, network state and SSH service if I have access.

## Monitoring has no alert
> No. The monitoring system itself can have a problem. I would check the monitoring path and use another source such as BMC.

## Unknown problem
> I would not guess. I would collect information, check the runbook or documentation, and ask for help or escalate when needed. I would document what I already checked.
