# Hardware Diagnostic Interview Scenarios

## Server unreachable
**Question:** A server is unreachable. What would you check first?

**Answer:** First, I would check power and BMC access. Then I would check hardware events and the remote console. I would try to understand if the problem is hardware, the operating system, or the network.

## ECC error
**Question:** BMC shows an uncorrectable ECC error on DIMM B2. What do you do?

**Answer:** I would check the hardware event log and the internal runbook. The error is evidence, but I would not immediately assume the DIMM itself is faulty. I would follow the diagnostic steps and verify the result.

## Fan failure
**Question:** CPU temperature is high and one fan shows 0 RPM.

**Answer:** I would check BMC, the fan connection and airflow. If the fan is confirmed faulty, I would replace it according to the runbook and verify temperature and fan speed.

## GPU
**Question:** A GPU is not detected. Would you replace it?

**Answer:** No. I would check BMC, PCIe detection, power, physical connections and the PCIe riser if there is one. I would use evidence before replacing the GPU.

## PSU
**Question:** One PSU failed but the server is still running.

**Answer:** Yes, that is possible. Servers can have redundant power supplies.

## Monitoring
**Question:** Monitoring did not create an alert. Does that mean there is no problem?

**Answer:** No. The monitoring system itself can have a problem. I would check the monitoring path and use another source, such as BMC, to verify the server state.
