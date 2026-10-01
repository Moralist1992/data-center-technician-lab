# Network Hardware Basics

## NIC

**NIC — Network Interface Controller** provides network connectivity.

For basic troubleshooting, separate:

1. hardware detection;
2. interface state;
3. physical link;
4. network path;
5. end-to-end communication.

## PCIe detection is not the same as link

A NIC can be correctly detected while its Ethernet link is down.

```text
NIC detected
    +
Ethernet link DOWN
```

does not automatically mean that the NIC is defective.

Possible causes include cable, SFP/transceiver, switch-side port, remote-side configuration or physical connection.

## SFP

**SFP — Small Form-factor Pluggable** is a removable transceiver module used in network ports.

It is not the cable.

```text
NIC
 │
 ▼
SFP
 │
 │ fiber/copper depending on module
 ▼
SFP
 │
 ▼
Switch
```

Possible failure points:

```text
NIC → SFP → cable/fiber → SFP → switch port
```

For L1:

> SFP is a replaceable network transceiver module. It can be used with fiber or copper depending on the module.

| Module | Typical class |
|---|---|
| SFP | ~1 GbE |
| SFP+ | ~10 GbE |
| SFP28 | ~25 GbE |
| QSFP+/QSFP28 | Higher-speed / multiple-lane applications |
