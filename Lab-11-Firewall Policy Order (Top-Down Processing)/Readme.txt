# Lab 11: FortiGate Firewall Policy Order (Top-Down Processing)

## Objective

The objective of this lab is to understand how FortiGate processes firewall policies using the **Top-Down Processing Model**. This lab demonstrates how the order of firewall rules affects traffic flow and how FortiGate applies the first matching rule.

---

## Lab Topology

| Device     | Interface   | IP Address    |
| ---------- | ----------- | ------------- |
| FortiGate  | LAN (Port1) | 192.168.223.1 |
| FortiGate  | WAN (Port2) | 192.168.121.x |
| Kali Linux | eth0        | 192.168.223.x |

---

## Theory

FortiGate evaluates firewall policies from top to bottom.

```text
Policy 1
   ↓
Policy 2
   ↓
Policy 3
   ↓
Implicit Deny
```

When a packet matches a policy:

```text
Match Found
     ↓
Apply Action
     ↓
Stop Processing
```

FortiGate does not evaluate lower policies after a match is found.

---

## Firewall Policies Configured

### Policy 1 – Block FTP

| Parameter   | Value     |
| ----------- | --------- |
| Name        | Block-FTP |
| Action      | DENY      |
| Service     | FTP       |
| Source      | LAN       |
| Destination | WAN       |

Purpose:
Block all FTP traffic from LAN users.

---

### Policy 2 – Allow HTTP

| Parameter   | Value      |
| ----------- | ---------- |
| Name        | Allow-HTTP |
| Action      | ACCEPT     |
| Service     | HTTP       |
| Source      | LAN        |
| Destination | WAN        |

Purpose:
Allow HTTP traffic.

---

### Policy 3 – LAN to WAN

| Parameter | Value      |
| --------- | ---------- |
| Name      | LAN-to-WAN |
| Action    | ACCEPT     |
| Service   | ALL        |
| NAT       | Enabled    |

Purpose:
Allow all remaining Internet traffic.

---

## Policy Order

```text
1. Block-FTP      (DENY)
2. Allow-HTTP     (ALLOW)
3. LAN-to-WAN     (ALLOW)
```

---

## Verification Tests

### Test 1 – FTP Traffic

From Kali Linux:

```bash
ftp ftp.gnu.org
```

Expected Result:

```text
Connection timed out
FTP connection blocked
```

Result:

✅ FTP traffic blocked successfully.

---

### Test 2 – HTTP Traffic

```bash
curl http://example.com
```

Expected Result:

```text
HTTP page retrieved successfully
```

Result:

✅ HTTP traffic allowed.

---

### Test 3 – HTTPS Traffic

```bash
curl https://google.com
```

Expected Result:

```text
HTTPS connection successful
```

Result:

✅ HTTPS traffic allowed.

---

## Log Analysis

Navigate to:

```text
Log & Report
→ Forward Traffic
```

Verify:

### FTP Log

```text
Action : Deny
Service : FTP
Policy : Block-FTP
```

### HTTP Log

```text
Action : Accept
Service : HTTP
Policy : Allow-HTTP
```

---

## Screenshots

### Screenshot 1

Firewall Policy List

### Screenshot 2

Block-FTP Policy

### Screenshot 3

Allow-HTTP Policy

### Screenshot 4

FTP Deny Test from Kali

### Screenshot 5

HTTP Success Test

### Screenshot 6

FortiGate Traffic Logs

---

## Key Concepts Learned

### First Match Rule

FortiGate applies the first policy that matches the traffic.

### Policy Order

Firewall rules must be arranged carefully because order affects security.

### Allow and Deny Policies

Allow policies permit traffic while deny policies block traffic.

### Implicit Deny

If no policy matches, FortiGate automatically drops the traffic.

---

## Interview Questions

### How does FortiGate process firewall policies?

FortiGate processes firewall policies from top to bottom and applies the first matching rule.

### Why should deny policies be placed above allow policies?

Because FortiGate stops processing after the first match.

### What happens if no firewall policy matches?

FortiGate applies an implicit deny and blocks the traffic.

---

## Result

Successfully demonstrated FortiGate firewall policy order and top-down processing. Verified that FTP traffic was blocked by a deny rule while HTTP and HTTPS traffic were allowed through lower-priority policies. This lab provided practical experience with firewall rule evaluation, policy ordering, and traffic log analysis.

## GitHub Repository

[https://github.com/Loke31033/Fortigate-Labs](https://github.com/Loke31033/Fortigate-Labs)

**Skills Practiced:** FortiGate Firewall Policies, Policy Order, Traffic Filtering, Log Analysis, Network Security, FortiGate Administration.
