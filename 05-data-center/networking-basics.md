# Data Center Networking Basics

## NIC
NIC means Network Interface Controller. It provides network connectivity.

## SFP
SFP means Small Form-factor Pluggable. It is a removable transceiver; depending on the module it can use optical fiber or copper. It is not the cable.

`NIC → SFP → fiber/copper → SFP → switch`

## PCIe detection vs link
PCIe detection only shows that the server sees the NIC/device. Ethernet link can still be down. Possible causes include cable, SFP, switch port or the other side.

## Basic checks
1. Is the NIC detected?
2. Is the interface enabled?
3. Is physical link up?
4. Check cable/SFP.
5. Check switch side through the proper process.
6. Verify end-to-end connectivity.

## PXE
PXE is network boot. A PXE link error requires checking the physical network path and also why PXE was attempted.
