# Lab 12: FortiGate Source NAT (SNAT) Configuration

## Objective

The objective of this lab is to understand and configure **Source Network Address Translation (SNAT)** on a FortiGate firewall. This lab demonstrates how private IP addresses are translated into a routable WAN IP address to enable Internet access.

---

## Lab Topology

| Device             | Interface   | IP Address      |
| ------------------ | ----------- | --------------- |
| FortiGate          | WAN (Port1) | 192.168.121.x   |
| FortiGate          | LAN (Port2) | 192.168.223.1   |
| Kali Linux         | eth0        | 192.168.223.100 |
| VMware NAT Gateway | VMnet8      | 192.168.121.2   |

---

## Theory

### What is NAT?

Network Address Translation (NAT) is the process of modifying IP address information in network packets while they are passing through a firewall or router.

### Why NAT is Required?

Internal devices use private IP addresses:

```text
192.168.x.x
10.x.x.x
172.16.x.x
```

Private IP addresses cannot be routed on the Internet.

Example:

```text
Kali Linux
192.168.223.100
```

Google cannot send traffic directly back to this private address.

---

## What is Source NAT (SNAT)?

Source NAT changes the source IP address of outgoing traffic before it leaves the firewall.

### Before NAT

```text
Source IP:
192.168.223.100
Destination:
8.8.8.8
```

### After NAT

```text
Source IP:
192.168.121.129
Destination:
8.8.8.8
```

The source IP is translated to the FortiGate WAN IP.

---

## Traffic Flow

```text
Kali Linux
192.168.223.100
        |
        |
FortiGate
        |
Source NAT
        |
        |
192.168.121.129
        |
        |
Internet
```

---

## Configuration Steps

### Step 1: Verify Firewall Policy

Navigate to:

```text
Policy & Objects → Firewall Policy
```

Open the LAN-to-WAN policy.

Verify:

```text
NAT = Enabled
```

---

### Step 2: Test Internet Access with NAT Enabled

On Kali Linux:

```bash
ping 8.8.8.8
```

Expected Result:

```text
Replies received successfully.
```

Internet access should work.

---

### Step 3: Disable NAT

Edit the LAN-to-WAN policy.

Disable:

```text
Enable NAT
```

Save the policy.

---

### Step 4: Test Connectivity Again

On Kali Linux:

```bash
ping 8.8.8.8
```

Expected Result:

```text
Request timed out
```

Internet access should fail because private IP addresses cannot be routed on the Internet.

---

### Step 5: Re-enable NAT

Edit the firewall policy again.

Enable:

```text
Enable NAT
```

Save the configuration.

---

### Step 6: Verify Connectivity

On Kali Linux:

```bash
ping 8.8.8.8
```

Expected Result:

```text
Replies received successfully.
```

Internet access should be restored.

---

## Verification Commands

### Verify Firewall Policy

```bash
show firewall policy
```

Look for:

```text
set nat enable
```

---

### Verify Routing Table

```bash
get router info routing-table all
```

Verify the default route points to the WAN gateway.

---

### Verify Internet Connectivity

```bash
ping 8.8.8.8
```

---

## Screenshots

### Screenshot 1

LAN-to-WAN Firewall Policy with NAT Enabled

### Screenshot 2

LAN-to-WAN Firewall Policy with NAT Disabled

### Screenshot 3

Ping Test with NAT Disabled

```bash
ping 8.8.8.8
```

### Screenshot 4

Ping Test with NAT Enabled

```bash
ping 8.8.8.8
```

### Screenshot 5

Firewall Policy CLI Output

```bash
show firewall policy
```

showing:

```text
set nat enable
```

---

## Key Concepts Learned

### Source NAT (SNAT)

Source NAT modifies the source IP address of outgoing packets.

### Private IP Addresses

Private IP addresses cannot communicate directly on the Internet.

### Internet Access Through Firewalls

Firewalls use NAT to translate private IP addresses into routable addresses.

### Policy-Based NAT

FortiGate performs NAT through firewall policies.

---

## Interview Questions

### What is NAT?

NAT is a process that translates private IP addresses into routable IP addresses.

### What is Source NAT (SNAT)?

Source NAT changes the source IP address before traffic leaves the firewall.

### Why is NAT required?

Private IP addresses cannot be routed on the Internet.

### What happens if NAT is disabled?

Users cannot access Internet resources because their private IP addresses are not routable.

---

## Result

Successfully configured and verified **Source NAT (SNAT)** on a FortiGate firewall. Demonstrated how NAT enables private LAN hosts to access Internet resources by translating private IP addresses into a routable WAN IP address. Verified functionality through connectivity testing and firewall policy inspection.

## GitHub Repository

[FortiGate Labs Repository](https://github.com/Loke31033/Fortigate-Labs?utm_source=chatgpt.com)

### Skills Practiced

* FortiGate Firewall Policies
* Source NAT (SNAT)
* Internet Access Configuration
* Routing Verification
* Network Troubleshooting
* FortiGate Administration
* Network Security Fundamentals
