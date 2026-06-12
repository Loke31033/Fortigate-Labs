# Lab 07 - FortiGate Address Objects and Address Groups

## Objective

The objective of this lab is to understand Address Objects and Address Groups in FortiGate, create host and network objects, organize them into groups, and verify their configuration using both GUI and CLI.

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

Address Objects are one of the most important building blocks in FortiGate administration.

Instead of using raw IP addresses directly in firewall policies, administrators create Address Objects with meaningful names.

This approach:

* Simplifies firewall management
* Improves readability
* Reduces configuration errors
* Makes troubleshooting easier

---

## Why Address Objects Are Important

Consider the following firewall policy:

Without Address Objects:

```text
Source: 192.168.10.0/24
Destination: 192.168.20.0/24
```

After several months, administrators may not remember which network these IP addresses represent.

Using Address Objects:

```text
Source: HR_Network
Destination: Finance_Network
```

The policy becomes much easier to understand and manage.

---

## Types of Address Objects

### Host Object

Represents a single device.

Example:

```text
Finance_Server
=
192.168.1.100
```

Subnet Mask:

```text
255.255.255.255
```

or

```text
/32
```

---

### Network Object

Represents an entire subnet.

Example:

```text
HR_Network
=
192.168.10.0/24
```

This includes:

```text
192.168.10.1
to
192.168.10.254
```

---

### Address Group

Represents multiple Address Objects combined into a single logical group.

Example:

```text
Employees
```

Contains:

```text
HR_Network
IT_Network
Finance_Network
```

---

## Network Design Used

```text
HR Network
192.168.10.0/24

IT Network
192.168.20.0/24

Finance Server
192.168.1.100

Address Group:
Employees
```

---

## Step 1: Access Address Objects

Navigate to:

```text
Policy & Objects
→ Addresses
```

This section displays all configured Address Objects.

---

## Step 2: Create a Host Object

Created:

### Name

```text
Finance_Server
```

### Type

```text
Subnet
```

### IP Address

```text
192.168.1.100
```

### Subnet Mask

```text
255.255.255.255
```

Purpose:

Represents a single server.

---

## Step 3: Create a Network Object

Created:

### Name

```text
HR_Network
```

### Type

```text
Subnet
```

### Network

```text
192.168.10.0
```

### Mask

```text
255.255.255.0
```

Purpose:

Represents the Human Resources subnet.

---

## Step 4: Create Another Network Object

Created:

### Name

```text
IT_Network
```

### Network

```text
192.168.20.0/24
```

Purpose:

Represents the Information Technology subnet.

---

## Step 5: Create an Address Group

Navigate to:

```text
Policy & Objects
→ Address Groups
```

Created:

### Name

```text
Employees
```

Added Members:

```text
HR_Network
IT_Network
```

Purpose:

Combines multiple networks into a single object for easier policy management.

---

## Step 6: Verify Address Objects

Verified that the following objects were successfully created:

```text
Finance_Server
HR_Network
IT_Network
```

---

## Step 7: Verify Using CLI

Executed:

```bash
show firewall address
```

Output displayed all configured Address Objects.

Example:

```text
config firewall address

edit "Finance_Server"

edit "HR_Network"

edit "IT_Network"

end
```

---

## Step 8: Verify Address Group

Executed:

```bash
show firewall addrgrp
```

Verified:

```text
Employees
```

Address Group was successfully created.

---

## Verification Commands

### View Address Objects

```bash
show firewall address
```

### View Address Groups

```bash
show firewall addrgrp
```

### View Full Configuration

```bash
show full-configuration firewall address
```

---

## Screenshots

### Screenshot 1

Address Objects Page

### Screenshot 2

Finance_Server Host Object

### Screenshot 3

HR_Network Object

### Screenshot 4

Employees Address Group

### Screenshot 5

Address Object Verification

### Screenshot 6

CLI Address Object Verification

### Screenshot 7

CLI Address Group Verification

---

## Key Concepts Learned

### Address Object

A named representation of an IP address, host, or subnet.

### Host Object

Represents a single IP address.

Example:

```text
Finance_Server
```

### Network Object

Represents an entire subnet.

Example:

```text
HR_Network
```

### Address Group

A collection of Address Objects used as a single entity.

Example:

```text
Employees
```

---

## Real-World Importance

Address Objects are heavily used in:

* Firewall Policies
* NAT Rules
* VPN Configurations
* Security Profiles
* Access Control Policies

Large organizations may have hundreds or thousands of Address Objects.

Proper naming conventions improve security administration and troubleshooting.

---

## Challenges Faced

* Understanding the difference between Host Objects and Network Objects.
* Selecting correct subnet masks.
* Organizing multiple objects into Address Groups.
* Verifying Address Objects through CLI.

---

## Outcome

Successfully created Host Objects, Network Objects, and Address Groups within FortiGate. Verified the configuration using both GUI and CLI, and gained practical experience with one of the most commonly used FortiGate administration features.

---

## Skills Acquired

* Address Object Management
* Address Group Configuration
* FortiGate GUI Administration
* CLI Verification
* Network Object Design
* Firewall Policy Preparation

---

## Interview Questions

### What is an Address Object?

A named representation of an IP address, host, or network used in FortiGate configurations.

### Why use Address Objects instead of IP addresses directly?

To improve readability, simplify management, and reduce configuration errors.

### What is the difference between a Host Object and a Network Object?

A Host Object represents a single device, while a Network Object represents an entire subnet.

### What is an Address Group?

A collection of multiple Address Objects that can be used as a single object in firewall policies.

### How do you verify Address Objects using CLI?

```bash
show firewall address
```

### How do you verify Address Groups using CLI?

```bash
show firewall addrgrp
```

---

## Author

**Lokeshwar V**

Cybersecurity Student | SOC Analyst Aspirant | FortiGate Hands-on Lab Series
