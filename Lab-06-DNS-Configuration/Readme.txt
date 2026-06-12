# Lab 06 - FortiGate DNS Configuration

## Objective

The objective of this lab is to understand the Domain Name System (DNS), configure DNS servers on FortiGate, verify DNS functionality, test domain name resolution, and troubleshoot DNS-related issues.

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

The Domain Name System (DNS) is responsible for translating human-readable domain names into IP addresses.

For example:

```text
google.com
```

is translated into:

```text
142.250.x.x
```

Without DNS, users would need to remember IP addresses instead of domain names.

DNS is a critical service used by web browsing, email communication, VPN connectivity, software updates, and security services.

---

## How DNS Works

When a user accesses a website:

```text
User Device
     │
     ▼
DNS Server
     │
     ▼
Domain Name Resolution
     │
     ▼
IP Address Returned
     │
     ▼
Website Access
```

Example:

```text
google.com
     │
     ▼
8.8.8.8
     │
     ▼
142.250.x.x
```

---

## DNS Servers Used

### Primary DNS

```text
8.8.8.8
```

Google Public DNS

### Secondary DNS

```text
1.1.1.1
```

Cloudflare Public DNS

---

## Why Multiple DNS Servers Are Used

Using multiple DNS servers provides:

* Redundancy
* High Availability
* Fault Tolerance

If the primary DNS server becomes unavailable, the secondary DNS server can continue resolving domain names.

---

## Step 1: Access DNS Configuration

Navigated to:

```text
Network
→ DNS
```

or

```text
System
→ Settings
→ DNS
```

depending on the FortiOS layout.

---

## Step 2: Configure DNS Servers

Configured:

### Primary DNS

```text
8.8.8.8
```

### Secondary DNS

```text
1.1.1.1
```

Saved the configuration.

---

## Step 3: Verify DNS Configuration

Executed:

```bash
show system dns
```

Output confirmed the configured DNS servers.

Example:

```text
config system dns
set primary 8.8.8.8
set secondary 1.1.1.1
end
```

---

## Step 4: Test DNS Resolution

Executed:

```bash
execute ping google.com
```

Successful output:

```text
PING google.com (142.250.x.x)
```

This confirms:

* DNS Resolution Working
* Internet Connectivity Working

---

## Step 5: Test Additional Domain Resolution

Executed:

```bash
execute ping fortinet.com
```

Successful responses confirmed proper DNS operation.

---

## Step 6: Simulate DNS Failure

For learning purposes, an incorrect DNS server was configured.

Example:

```text
9.9.9.99
```

Executed:

```bash
execute ping google.com
```

Observed:

```text
DNS resolve failed
```

This demonstrated how DNS failures affect network operations.

---

## Step 7: DNS Troubleshooting

Performed comparison testing.

### Test Internet Connectivity

```bash
execute ping 8.8.8.8
```

Result:

```text
Success
```

### Test DNS Resolution

```bash
execute ping google.com
```

Result:

```text
Failure
```

### Conclusion

```text
Internet Connectivity = Working
DNS Resolution = Failed
```

This is a common troubleshooting scenario in enterprise environments.

---

## Verification Commands

### View DNS Configuration

```bash
show system dns
```

### Test DNS Resolution

```bash
execute ping google.com
```

### Test Fortinet Domain Resolution

```bash
execute ping fortinet.com
```

### Test Raw IP Connectivity

```bash
execute ping 8.8.8.8
```

---

## Screenshots

### Screenshot 1

DNS Configuration Page

### Screenshot 2

Configured DNS Servers

### Screenshot 3

DNS CLI Verification

### Screenshot 4

Google DNS Resolution Test

### Screenshot 5

Fortinet DNS Resolution Test

### Screenshot 6

DNS Failure Demonstration

### Screenshot 7

Internet vs DNS Troubleshooting

---

## Key Concepts Learned

### DNS

Domain Name System used to translate domain names into IP addresses.

### Primary DNS

The main DNS server used for domain resolution.

### Secondary DNS

A backup DNS server used if the primary server becomes unavailable.

### DNS Resolution

The process of converting a domain name into an IP address.

### DNS Failure

A condition where domain names cannot be resolved even though Internet connectivity may still exist.

---

## Real-World Importance

DNS is essential for:

* Website Access
* Email Communication
* VPN Services
* Security Updates
* Cloud Applications
* FortiGuard Services

A DNS failure can impact an entire organization's network operations.

---

## Challenges Faced

* Understanding DNS resolution processes.
* Identifying differences between Internet connectivity and DNS functionality.
* Simulating and troubleshooting DNS failures.
* Verifying DNS configuration using CLI commands.

---

## Outcome

Successfully configured DNS servers on FortiGate, verified domain name resolution, tested DNS functionality, simulated DNS failures, and learned practical DNS troubleshooting techniques.

---

## Skills Acquired

* DNS Configuration
* DNS Troubleshooting
* CLI Verification
* Network Diagnostics
* Connectivity Testing
* FortiGate Administration

---

## Interview Questions

### What is DNS?

DNS (Domain Name System) translates domain names into IP addresses.

### Why do we configure multiple DNS servers?

To provide redundancy and ensure continuous DNS resolution.

### How do you verify DNS configuration on FortiGate?

```bash
show system dns
```

### How do you test DNS resolution?

```bash
execute ping google.com
```

### Internet connectivity works, but websites do not open. What is the first thing you check?

DNS configuration and DNS resolution functionality.

---

## Author

**Lokeshwar V**

Cybersecurity Student | SOC Analyst Aspirant | FortiGate Hands-on Lab Series
