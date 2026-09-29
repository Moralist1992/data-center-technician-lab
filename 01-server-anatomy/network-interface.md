# Network Interface — NIC

## NIC

**NIC = Network Interface Controller**

A NIC provides network connectivity between the server and the network.

Important:

> A NIC does not necessarily provide "Internet". It provides network connectivity.

A server may use a NIC for:

- internal network
- management network
- storage network
- cluster network
- Internet connectivity

## Basic path

```text
Server
  │
  ▼
 NIC
  │
  │ cable / fiber
  ▼
Switch
  │
  ▼
Network
  │
  ▼
Destination
```

## Important diagnostic distinction

```text
NIC detected
      ≠
Interface UP
      ≠
Physical link UP
      ≠
End-to-end connectivity
```

## Troubleshooting sequence

### 1. NIC detected?

Does the system see the NIC hardware at all?

If not, investigate:

- power
- physical installation
- PCIe connection
- riser
- firmware
- motherboard/platform
- NIC failure

At the Linux level, a command such as `lspci` can be used to look for a network controller, but the exact diagnostic tool depends on the environment.

### 2. Is the interface up?

The OS may see the NIC while the network interface is down.

`UP` means the interface is enabled/operational from the OS perspective. It does not mean that Internet access is working.

### 3. Is the physical link up?

A NIC can be enabled while the physical Ethernet/fiber link is down.

Possible causes:

- cable
- transceiver / SFP
- switch port
- NIC port
- physical connection

Key distinction:

> **Interface UP ≠ Link UP**

### 4. Is the cable connected properly?

Check both ends.

Possible issues:

- cable disconnected
- damaged cable
- bad connector
- wrong port
- fiber/SFP connection issue

In a data center, physical cable tracing and correct port identification are part of L1 troubleshooting.

### 5. Is the switch port up?

The server and switch are two endpoints of the same physical connection.

A switch port may be:

- administratively disabled
- physically down
- misconfigured
- connected to the wrong port
- affected by a transceiver/module problem
- faulty

### 6. Do both sides show link?

The expected state is:

```text
Server NIC  ───── cable/fiber ───── Switch port
    │                                  │
   LINK UP                            LINK UP
```

Good terminology:

> "The link is up on both sides."

This establishes physical connectivity, but it does not prove end-to-end communication.

### 7. Can the server reach the expected destination?

At this point the physical path may be healthy, but communication can still fail because of:

- wrong IP address
- wrong subnet mask
- wrong default gateway
- VLAN problem
- routing problem
- DNS problem
- firewall
- remote host unavailable

Depending on the troubleshooting scope, tools such as `ping`, `ip route` and `nslookup` may be used.

The key point is not the command itself, but the diagnostic layer being tested.

## Full troubleshooting chain

```text
NIC detected?
     ↓
Interface UP?
     ↓
Physical link UP?
     ↓
Cable connected?
     ↓
Switch port UP?
     ↓
Link up on both sides?
     ↓
End-to-end communication?
```

## Fault domain examples

### One server is affected

Investigate:

- server NIC
- cable
- switch port
- local configuration

### Many servers fail simultaneously

Investigate common/shared network infrastructure, such as:

- switch
- upstream network
- aggregation layer
- routing
- other shared infrastructure

Do not immediately assume an Internet Service Provider problem. The fault may be entirely inside the data center's own network.

## Interview question

### "How would you troubleshoot a server that lost network connectivity?"

Good answer:

> First, I would check whether the NIC is detected by the system. Then I would check whether the interface is up and whether the physical link is established. I would check the cable and the switch port. If the physical link is working, I would test connectivity to the expected network destination and then investigate configuration, routing or other network issues if necessary.

## Useful interview terminology

Prefer:

- "The NIC is detected."
- "The interface is down."
- "The physical link is down."
- "The switch port is down."
- "The link is up on both sides."
- "There is end-to-end connectivity."
- "I would isolate the fault domain."
