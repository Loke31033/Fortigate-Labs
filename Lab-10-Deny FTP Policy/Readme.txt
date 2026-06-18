# Lab 10: FortiGate Deny Policy – Blocking FTP Traffic

## Objective

The objective of this lab is to understand how FortiGate firewall policies can be used to block specific network services. In this lab, FTP traffic from the LAN network to the Internet was denied while allowing other services such as HTTP and HTTPS.

---

## Lab Topology

| Device          | IP Address    | Role             |
| --------------- | ------------- | ---------------- |
| FortiGate Port1 | LAN Interface | Internal Network |
| FortiGate Port2 | WAN Interface | Internet Access  |
| Kali Linux      | LAN Client    | Test Machine     |

---

## Configuration Steps

### Step 1: Verify Internet Access

Before creating the deny policy, verify that Internet access is working from the Kali Linux client.

```bash
ping 8.8.8.8
```

Expected Result:

```text
Replies received successfully.
```

---

### Step 2: Create FTP Deny Policy

Navigate to:

```text
Policy & Objects → Firewall Policy
```

Create a new policy with the following settings:

| Setting            | Value     |
| ------------------ | --------- |
| Name               | Block-FTP |
| Incoming Interface | LAN       |
| Outgoing Interface | WAN       |
| Source             | all       |
| Destination        | all       |
| Service            | FTP       |
| Action             | DENY      |
| Log Traffic        | Enable    |

Save the policy.

---

### Step 3: Arrange Policy Order

Move the deny policy above the general Internet access policy.

Example:

```text
1. Block-FTP (DENY)
2. LAN-to-WAN (ALLOW)
```

FortiGate processes policies from top to bottom and applies the first matching rule.

---

### Step 4: Generate FTP Traffic

From Kali Linux:

```bash
ftp ftp.gnu.org
```

Expected Result:

```text
Connection timed out
FTP connection failed
```

This confirms that FTP traffic is being blocked.

---

### Step 5: Verify Logs

Navigate to:

```text
Log & Report → Forward Traffic
```

Verify the following:

* Action = DENY
* Service = FTP
* Source IP = Kali Linux IP
* Policy = Block-FTP

---

## Screenshots

### Screenshot 1

Firewall Policy List

### Screenshot 2

Block-FTP Policy Configuration

### Screenshot 3

FTP Connection Attempt from Kali Linux

### Screenshot 4

FortiGate Traffic Log Showing FTP Denied

---

## Key Concepts Learned

### Deny Policy

A deny policy blocks traffic that matches the configured criteria.

### Policy Order

FortiGate evaluates policies from top to bottom. The first matching rule is applied.

### Logging

Traffic logs help administrators verify whether traffic was allowed or denied.

### FTP Security Risks

FTP transmits usernames and passwords in plain text, making it insecure for modern enterprise environments.

---

## Verification

| Test                  | Result     |
| --------------------- | ---------- |
| Internet Connectivity | Successful |
| FTP Access            | Blocked    |
| Log Generation        | Successful |
| Policy Enforcement    | Successful |

---

## Result

Successfully configured a FortiGate firewall deny policy to block FTP traffic from the LAN network to the Internet. Verified the policy using FTP connection tests and FortiGate traffic logs. This lab demonstrated policy evaluation order, service-based traffic control, and log analysis in FortiGate firewalls.

## GitHub Repository

[FortiGate Labs Repository](https://github.com/Loke31033/Fortigate-Labs?utm_source=chatgpt.com)

---

**Skills Practiced:** FortiGate Firewall Policies, Service Control, Traffic Filtering, Log Analysis, Network Security, FortiGate Administration.
