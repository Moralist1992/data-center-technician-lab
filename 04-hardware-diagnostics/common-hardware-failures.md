# Common Hardware Failures

## Memory / ECC
Check BMC Event Log, identify the reported DIMM/channel, follow the memory runbook, and verify after the approved action. An ECC error does not automatically prove the DIMM itself is the root cause.

## Fan / cooling
Check BMC temperature, RPM, events, physical connection and airflow. Replace only when confirmed by the procedure. Verify RPM and temperature.

## PSU
Check BMC power status and both PSUs. Redundant power may keep the server running after one PSU fails. Follow the replacement procedure and verify redundancy.

## GPU / PCIe
Check BMC, PCIe detection, power, physical seating and riser. A missing GPU does not automatically mean a dead GPU.

## Storage
Trace: `Drive → connector/slot → backplane/riser → PCIe/controller → motherboard`. Power and firmware can also matter.

## NIC / link
A NIC can be detected through PCIe while Ethernet link is down. Check interface state, cable, SFP, switch side and both ends of the connection.
