# Lab 08 - FortiGate Service Objects

## Objective

The objective of this lab is to understand Service Objects in FortiGate, explore built-in services, create custom service objects, verify service configurations, and learn how services are used in firewall policies.

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

Service Objects are used in FortiGate to identify specific network services based on protocols and port numbers.

Instead of manually entering port numbers in firewall policies, administrators use predefined or custom Service Objects.

This improves:

* Readability
* Policy Management
* Troubleshooting
* Security Administration

---

## Why Service Objects Are Important

Consider the following firewall rule:

Without Service Objects:

```text
Allow TCP Port 443
```

With Service Objects:

```text
Allow HTTPS
```

The second approach is much easier to understand and manage.

---

## Understanding Services

Every network application communicates through a protocol and port number.

Examples:

| Service | Protocol | Port |
| ------- | -------- | ---- |
| HTTP    | TCP      | 80   |
| HTTPS   | TCP      | 443  |
| SSH     | TCP      | 22   |
| FTP     | TCP      | 21   |
| DNS     | UDP      | 53   |
| RDP     | TCP      | 3389 |

FortiGate uses Service Objects to represent these applications.

---

## Common Built-in Services

### HTTP

Protocol:

```text
TCP
```

Port:

```text
80
```

Purpose:

Used for unencrypted web browsing.

---

### HTTPS

Protocol:

```text
TCP
```

Port:

```text
443
```

Purpose:

Used for secure web browsing.

---

### SSH

Protocol:

```text
TCP
```

Port:

```text
22
```

Purpose:

Used for secure remote administration.

---

### DNS

Protocol:

```text
UDP
```

Port:

```text
53
```

Purpose:

Used for domain name resolution.

---

## Step 1: Access Service Objects

Navigate to:

```text
Policy & Objects
→ Services
```

Observed various built-in FortiGate service objects.

Examples:

```text
HTTP
HTTPS
SSH
DNS
FTP
```

---

## Step 2: Explore HTTP Service

Selected:

```text
HTTP
```

Observed:

### Protocol

```text
TCP
```

### Port

```text
80
```

Purpose:

Supports standard web traffic.

---

## Step 3: Explore HTTPS Service

Selected:

```text
HTTPS
```

Observed:

### Protocol

```text
TCP
```

### Port

```text
443
```

Purpose:

Supports encrypted web traffic.

---

## Step 4: Create Custom Service Object

Created:

### Name

```text
Custom_Web_App
```

### Protocol

```text
TCP
```

### Destination Port

```text
8080
```

Purpose:

Represents a web application running on TCP port 8080.

---

## Step 5: Create SSH Custom Service

Created:

### Name

```text
SSH_Custom
```

### Protocol

```text
TCP
```

### Destination Port

```text
22
```

Purpose:

Represents SSH administrative traffic.

---

## Step 6: Verify Service Objects

Verified that the following services were successfully created:

```text
Custom_Web_App
SSH_Custom
```

These services appeared in the FortiGate Services list.

---

## Step 7: Verify Using CLI

Executed:

```bash
show firewall service custom
```

Output displayed the custom services.

Example:

```text
config firewall service custom

edit "Custom_Web_App"

edit "SSH_Custom"

end
```

---

## Verification Commands

### View Custom Services

```bash
show firewall service custom
```

### View Complete Service Configuration

```bash
show full-configuration firewall service custom
```

### View Service List

```bash
show firewall service group
```

---

## Screenshots

### Screenshot 1

Services Overview Page

### Screenshot 2

HTTP Service Details

### Screenshot 3

HTTPS Service Details

### Screenshot 4

Custom_Web_App Service Configuration

### Screenshot 5

SSH_Custom Service Configuration

### Screenshot 6

Custom Service Verification

### Screenshot 7

CLI Service Verification

---

## Key Concepts Learned

### Service Object

A Service Object represents a protocol and port combination used by network applications.

Example:

```text
HTTPS
=
TCP/443
```

---

### Custom Service

A user-defined service object.

Example:

```text
Custom_Web_App
=
TCP/8080
```

---

### Protocol

Rules used for communication between devices.

Examples:

```text
TCP
UDP
```

---

### Port

A logical communication endpoint used by applications.

Examples:

```text
80 = HTTP
443 = HTTPS
22 = SSH
53 = DNS
```

---

## Real-World Importance

Service Objects are widely used in:

* Firewall Policies
* NAT Rules
* Security Policies
* VPN Configurations
* Application Access Control

Without Service Objects, managing large firewall deployments becomes difficult.

---

## Challenges Faced

* Understanding the relationship between protocols and ports.
* Differentiating between built-in and custom services.
* Creating custom service definitions.
* Verifying services using CLI commands.

---

## Outcome

Successfully explored built-in FortiGate services, created custom Service Objects, verified configurations through GUI and CLI, and gained practical knowledge of how services are used in firewall administration.

---

## Skills Acquired

* Service Object Management
* Custom Service Creation
* Port and Protocol Understanding
* FortiGate GUI Administration
* CLI Verification
* Firewall Policy Preparation

---

## Interview Questions

### What is a Service Object?

A Service Object is a predefined or custom definition of a protocol and port used in firewall policies.

### Why are Service Objects used?

To simplify firewall rule creation and improve configuration readability.

### What is the difference between TCP and UDP?

TCP is connection-oriented and reliable, while UDP is connectionless and faster.

### What service uses port 443?

HTTPS.

### How do you verify custom services in FortiGate?

```bash
show firewall service custom
```

### What is the purpose of a custom service object?

To define applications that use non-standard or organization-specific ports.

---

## Author

**Lokeshwar V**

Cybersecurity Student | SOC Analyst Aspirant | FortiGate Hands-on Lab Series
