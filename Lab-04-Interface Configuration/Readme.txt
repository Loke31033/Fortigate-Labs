# Lab 04 - FortiGate Interface Configuration

## Objective

The objective of this lab is to understand FortiGate network interfaces, identify WAN and LAN interfaces, examine interface settings, verify connectivity, and learn how FortiGate communicates with external and internal networks.

---

## Lab Environment

| Component       | Details                |
| --------------- | ---------------------- |
| Firewall        | FortiGate VM           |
| FortiOS Version | v7.4.12                |
| Hypervisor      | VMware Workstation Pro |
| License         | Evaluation License     |
| Host OS         | Windows 11             |

---

## Introduction

Network interfaces are the foundation of FortiGate communication.

Every packet entering or leaving the firewall passes through an interface. Understanding interface configuration is essential before learning routing, NAT, firewall policies, VPNs, and security profiles.

In this lab, the WAN and LAN interfaces were explored and verified using both GUI and CLI methods.

---

## Network Architecture

```text
Internet
   │
WAN Interface (port1)
   │
FortiGate Firewall
   │
LAN Interface (port2)
   │
Internal Users
```

---

## Understanding WAN and LAN Interfaces

### WAN Interface

The WAN (Wide Area Network) interface connects FortiGate to external networks such as the Internet.

Common Functions:

* Internet Connectivity
* VPN Termination
* External Traffic Reception
* Routing to Public Networks

In this lab:

```text
Interface: port1
Role: WAN
```

---

### LAN Interface

The LAN (Local Area Network) interface connects FortiGate to internal devices and users.

Common Functions:

* Internal User Connectivity
* Local Network Access
* Internal Traffic Inspection

In this lab:

```text
Interface: port2
Role: LAN
```

---

## Step 1: Access Interface Configuration

Navigate to:

```text
Network
→ Interfaces
```

The interface page displays:

* Interface Name
* Role
* IP Address
* Administrative Access
* Status

---

## Step 2: Examine WAN Interface

Selected:

```text
port1
```

Observed:

* Interface Name
* Role
* Addressing Mode
* Administrative Access
* IP Address

### Administrative Access Options

#### HTTPS

Allows browser-based GUI access.

Example:

```text
https://192.168.x.x
```

#### PING

Allows ICMP traffic for connectivity testing.

#### SSH

Allows remote command-line administration.

---

## Step 3: Verify WAN IP Address

Observed the IP address assigned to the WAN interface.

Example:

```text
192.168.185.129/24
```

Subnet:

```text
255.255.255.0
```

This IP address allows FortiGate to communicate with the external network.

---

## Step 4: Examine LAN Interface

Selected:

```text
port2
```

Observed:

* Interface Name
* Role
* IP Address
* Administrative Access
* Status

The LAN interface is intended for internal network communication.

---

## Step 5: Verify Interfaces Using CLI

Executed:

```bash
show system interface
```

The command displayed:

* Interface Configuration
* IP Addresses
* Administrative Settings
* Access Permissions

Example:

```text
config system interface
edit "port1"
set ip 192.168.x.x 255.255.255.0
next
end
```

---

## Step 6: Connectivity Testing

Executed:

```bash
execute ping 8.8.8.8
```

Purpose:

* Verify Internet Connectivity
* Verify Interface Functionality
* Verify Routing

Successful responses confirmed that the WAN interface was operational.

---

## Step 7: Verify Interface Status

Executed:

```bash
get system interface physical
```

Observed:

```text
port1
status: up

port2
status: up
```

### Status Meaning

#### Up

* Interface Active
* Physical Link Available
* Traffic Can Pass

#### Down

* Interface Disabled
* No Link Available
* Communication Failure

---

## Verification Commands

### View Interface Configuration

```bash
show system interface
```

### View Physical Interface Status

```bash
get system interface physical
```

### Test Internet Connectivity

```bash
execute ping 8.8.8.8
```

### View System Information

```bash
get system status
```

---

## Screenshots

### Screenshot 1

Interfaces Overview Page

### Screenshot 2

WAN Interface Configuration

### Screenshot 3

LAN Interface Configuration

### Screenshot 4

CLI Interface Configuration Output

### Screenshot 5

Ping Verification

### Screenshot 6

Physical Interface Status

---

## Key Concepts Learned

### Interface

A network connection point that allows FortiGate to communicate with other devices and networks.

### WAN Interface

Connects FortiGate to external networks such as the Internet.

### LAN Interface

Connects FortiGate to internal users and devices.

### Administrative Access

Controls how administrators manage the firewall using protocols such as HTTPS, SSH, and PING.

### Interface Status

Indicates whether an interface is operational and able to transmit traffic.

---

## Real-World Importance

Network administrators use interface configuration to:

* Establish Internet Connectivity
* Configure Internal Networks
* Enable Firewall Management
* Troubleshoot Connectivity Issues
* Support VPN and Security Services

Incorrect interface configuration can result in complete network outages.

---

## Challenges Faced

* Understanding WAN and LAN roles.
* Identifying administrative access options.
* Interpreting interface status information.
* Verifying connectivity using CLI commands.

---

## Outcome

Successfully explored FortiGate network interfaces, identified WAN and LAN roles, verified interface configurations, tested Internet connectivity, and examined interface status using both GUI and CLI methods.

---

## Skills Acquired

* FortiGate Interface Management
* WAN and LAN Configuration
* Connectivity Testing
* Interface Monitoring
* CLI Verification
* Basic Network Troubleshooting

---

## Interview Questions

### What is a FortiGate Interface?

An interface is a network connection point used by FortiGate to communicate with internal and external networks.

### What is the difference between WAN and LAN?

WAN connects to external networks such as the Internet, while LAN connects to internal users and devices.

### How do you verify interface configuration from the CLI?

```bash
show system interface
```

### How do you test connectivity from FortiGate?

```bash
execute ping 8.8.8.8
```

### How do you verify physical interface status?

```bash
get system interface physical
```

---

## Author

**Lokeshwar V**

Cybersecurity Student | SOC Analyst Aspirant | FortiGate Hands-on Lab Series
