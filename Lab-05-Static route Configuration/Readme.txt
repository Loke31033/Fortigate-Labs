# Lab 05 - FortiGate Static Routing

## Objective

The objective of this lab is to understand how routing works in FortiGate, examine the routing table, identify the default route, create a static route, and verify network connectivity using routing diagnostic commands.

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

Routing is the process of determining the path that network traffic takes from a source to a destination.

FortiGate uses a routing table to decide where packets should be forwarded. Without proper routing configuration, devices cannot communicate with external networks, VPN sites, or the Internet.

In this lab, static routes and the routing table were explored to understand how FortiGate makes forwarding decisions.

---

## Network Architecture

```text
Internet
   │
Gateway Router
   │
port1 (WAN)
   │
FortiGate Firewall
   │
port2 (LAN)
   │
Internal Network
```

---

## Understanding Routing

When a packet arrives at FortiGate, the firewall checks its routing table to determine:

* Where the destination network exists
* Which gateway should be used
* Which interface should forward the traffic

The best matching route is selected and used to forward the packet.

---

## Understanding Static Routes

A static route is a manually configured route created by an administrator.

Static routes are commonly used for:

* Internet access
* Site-to-site VPNs
* Internal network communication
* Backup routing paths

---

## Understanding the Default Route

A default route is used when no specific route matches the destination network.

Default Route:

```text
0.0.0.0/0
```

Meaning:

```text
Any Destination Network
```

Example:

```text
Destination: 0.0.0.0/0
Gateway: 192.168.185.2
Interface: port1
```

This tells FortiGate to forward all unknown traffic to the specified gateway.

---

## Step 1: View Existing Static Routes

Navigated to:

```text
Network
→ Static Routes
```

Observed:

* Destination Networks
* Gateway Addresses
* Interfaces
* Administrative Distance

---

## Step 2: Examine the Default Route

Observed the existing default route.

Parameters reviewed:

### Destination

```text
0.0.0.0/0
```

### Gateway

```text
192.168.185.2
```

### Interface

```text
port1
```

### Purpose

Allows FortiGate to reach external networks and the Internet.

---

## Step 3: Verify Routing Table Using CLI

Executed:

```bash
get router info routing-table all
```

Example Output:

```text
S* 0.0.0.0/0 [10/0] via 192.168.185.2, port1
```

### Interpretation

| Symbol | Meaning            |
| ------ | ------------------ |
| S      | Static Route       |
| *      | Default Route      |
| via    | Gateway            |
| port1  | Outgoing Interface |

---

## Step 4: Verify Connectivity

Executed:

```bash
execute ping 8.8.8.8
```

Purpose:

* Verify Internet Access
* Verify Routing Functionality
* Verify Gateway Reachability

Successful replies confirmed that routing was functioning correctly.

---

## Step 5: Perform Traceroute

Executed:

```bash
execute traceroute 8.8.8.8
```

Purpose:

* Identify packet path
* Verify gateway traversal
* Troubleshoot routing problems

Traceroute displayed multiple network hops between FortiGate and the destination.

---

## Step 6: Create a Test Static Route

Created a test route:

### Destination Network

```text
10.10.10.0/24
```

### Gateway

```text
192.168.185.2
```

### Interface

```text
port1
```

Purpose:

To understand how FortiGate handles manually configured routes.

---

## Step 7: Verify New Route

Executed:

```bash
get router info routing-table all
```

Verified:

```text
S 10.10.10.0/24
```

appeared in the routing table.

---

## Verification Commands

### View Routing Table

```bash
get router info routing-table all
```

### Test Connectivity

```bash
execute ping 8.8.8.8
```

### Trace Network Path

```bash
execute traceroute 8.8.8.8
```

### View Interface Information

```bash
get system interface physical
```

---

## Screenshots

### Screenshot 1

Static Routes Overview

### Screenshot 2

Default Route Configuration

### Screenshot 3

Routing Table Output

### Screenshot 4

Ping Verification

### Screenshot 5

Traceroute Output

### Screenshot 6

Test Static Route Configuration

### Screenshot 7

Routing Table Verification

---

## Key Concepts Learned

### Routing

The process of forwarding packets toward their destination.

### Static Route

A manually configured route created by the administrator.

### Default Route

A route used when no more specific route exists.

### Gateway

The next-hop router used to reach another network.

### Routing Table

A database containing route information used for packet forwarding.

### Traceroute

A diagnostic tool used to identify the path packets take through a network.

---

## Real-World Importance

Routing is essential for:

* Internet Connectivity
* VPN Communication
* Branch Office Connectivity
* Internal Network Communication
* Traffic Engineering

Improper routing configuration can cause complete communication failures.

---

## Challenges Faced

* Understanding default route concepts.
* Interpreting routing table entries.
* Identifying gateway functionality.
* Understanding traceroute output.

---

## Outcome

Successfully explored FortiGate routing functionality, examined the routing table, identified the default route, created a static route, verified connectivity, and performed routing diagnostics using CLI tools.

---

## Skills Acquired

* FortiGate Routing Administration
* Static Route Configuration
* Routing Table Analysis
* Connectivity Testing
* Traceroute Analysis
* Basic Network Troubleshooting

---

## Interview Questions

### What is a Static Route?

A manually configured route that tells FortiGate how to reach a specific destination network.

### What is a Default Route?

A route used when no specific route matches the destination network.

### What does 0.0.0.0/0 represent?

It represents all destination networks and is commonly used as the default route.

### How do you view the FortiGate routing table?

```bash
get router info routing-table all
```

### How do you verify routing functionality?

```bash
execute ping 8.8.8.8
execute traceroute 8.8.8.8
```

---

## Author

**Lokeshwar V**

Cybersecurity Student | SOC Analyst Aspirant | FortiGate Hands-on Lab Series
