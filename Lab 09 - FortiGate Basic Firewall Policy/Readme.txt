# Lab 09 - FortiGate Basic Firewall Policy (Allow LAN to Internet)

## Objective

The objective of this lab is to understand how FortiGate Firewall Policies work, create a basic Allow LAN to Internet policy, enable NAT, verify policy operation, and analyze traffic logs.

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

Firewall Policies are the core component of FortiGate security administration.

Every packet entering the firewall is evaluated against configured firewall policies to determine whether it should be:

* Allowed
* Denied
* Logged
* Inspected

Without a firewall policy, traffic cannot pass through the FortiGate firewall.

---

## Traffic Flow Overview

The objective of this policy is to allow internal users to access the Internet.

```text
Internal User
     │
     ▼
LAN Interface (port2)
     │
     ▼
FortiGate Firewall Policy
     │
     ▼
WAN Interface (port1)
     │
     ▼
Internet
```

---

## Understanding Firewall Policies

A firewall policy consists of several key components:

### Source Interface

Where traffic enters the firewall.

Example:

```text
port2
```

---

### Destination Interface

Where traffic exits the firewall.

Example:

```text
port1
```

---

### Source Address

The device or network initiating communication.

Example:

```text
Employees
```

or

```text
all
```

---

### Destination Address

The destination network.

Example:

```text
all
```

representing Internet destinations.

---

### Service

The application or protocol allowed.

Examples:

```text
HTTP
HTTPS
DNS
```

or

```text
ALL
```

---

### Action

Determines whether traffic is:

```text
ACCEPT
```

or

```text
DENY
```

---

### NAT

Network Address Translation converts private IP addresses into routable public addresses.

---

## Step 1: Access Firewall Policies

Navigate to:

```text
Policy & Objects
→ Firewall Policy
```

Observed the existing firewall policy list.

---

## Step 2: Create New Firewall Policy

Selected:

```text
Create New
```

Configured:

### Policy Name

```text
Allow_LAN_to_Internet
```

### Incoming Interface

```text
port2
```

### Outgoing Interface

```text
port1
```

### Source

```text
all
```

or

```text
Employees
```

### Destination

```text
all
```

### Service

```text
HTTP
HTTPS
DNS
```

or

```text
ALL
```

### Action

```text
ACCEPT
```

---

## Step 3: Enable NAT

Enabled:

```text
NAT
```

### Why NAT is Required

Internal IP addresses such as:

```text
192.168.10.10
```

cannot communicate directly on the Internet.

FortiGate performs Network Address Translation by replacing internal addresses with the firewall's external address.

Example:

```text
192.168.10.10
     ↓
Public WAN IP
```

---

## Step 4: Save the Policy

Saved the firewall policy.

The new policy appeared in the Firewall Policy list.

---

## Step 5: Understand Policy Order

Firewall policies are processed from top to bottom.

Example:

```text
Policy 1 → Allow
Policy 2 → Deny
```

If traffic matches Policy 1, FortiGate stops processing additional policies.

This behavior is known as:

```text
First Match Wins
```

---

## Step 6: Verify Traffic Logs

Navigated to:

```text
Log & Report
→ Forward Traffic
```

Observed:

* Source IP
* Destination IP
* Service
* Policy ID
* Action

These logs confirm whether traffic was allowed or denied.

---

## Step 7: Verify Policy Using CLI

Executed:

```bash
show firewall policy
```

Example Output:

```text
config firewall policy

edit 1

set name "Allow_LAN_to_Internet"

next

end
```

Verified that the policy was successfully created.

---

## Verification Commands

### View Firewall Policies

```bash
show firewall policy
```

### View Full Firewall Policy Configuration

```bash
show full-configuration firewall policy
```

### Test Connectivity

```bash
execute ping 8.8.8.8
```

### Verify Routing

```bash
get router info routing-table all
```

---

## Screenshots

### Screenshot 1

Firewall Policy Page

### Screenshot 2

Policy Configuration

### Screenshot 3

Created Firewall Policy

### Screenshot 4

Policy Order Demonstration

### Screenshot 5

Traffic Log Verification

### Screenshot 6

CLI Policy Verification

---

## Key Concepts Learned

### Firewall Policy

A rule that determines whether traffic is allowed or denied.

### Source Interface

The interface where traffic enters the firewall.

### Destination Interface

The interface where traffic exits the firewall.

### Service

The application or protocol being controlled.

### NAT

Network Address Translation used to convert private addresses into routable addresses.

### Policy Order

FortiGate processes policies from top to bottom and applies the first matching rule.

---

## Real-World Importance

Firewall Policies are used to:

* Allow Internet Access
* Restrict User Access
* Control Application Usage
* Enforce Security Policies
* Protect Internal Resources

Every organization relies on firewall policies to secure network communication.

---

## Challenges Faced

* Understanding traffic flow through FortiGate.
* Understanding NAT functionality.
* Learning policy order processing.
* Interpreting traffic logs.

---

## Outcome

Successfully created a basic Allow LAN to Internet firewall policy, enabled NAT, verified policy operation, examined traffic logs, and gained practical experience with one of the most important FortiGate administration tasks.

---

## Skills Acquired

* Firewall Policy Configuration
* NAT Configuration
* Traffic Flow Analysis
* Policy Verification
* Log Analysis
* FortiGate GUI Administration
* CLI Verification

---

## Interview Questions

### What is a Firewall Policy?

A firewall policy is a rule that controls whether network traffic is allowed or denied.

### Why is NAT required?

Private IP addresses cannot be routed on the public Internet. NAT translates private addresses into routable public addresses.

### How does FortiGate process firewall policies?

FortiGate processes policies from top to bottom and applies the first matching rule.

### What is meant by "First Match Wins"?

Once traffic matches a policy, FortiGate stops evaluating additional policies.

### How do you verify firewall policies using CLI?

```bash
show firewall policy
```

### How do you verify traffic passing through a policy?

```text
Log & Report
→ Forward Traffic
```

---

## Author

**Lokeshwar V**

Cybersecurity Student | SOC Analyst Aspirant | FortiGate Hands-on Lab Series
