# Lab 13: FortiGate VIP (Virtual IP) and Port Forwarding

## Objective

The objective of this lab is to understand how FortiGate Virtual IPs (VIPs) are used to publish internal services to external users through Port Forwarding. This lab demonstrates how Internet traffic can be forwarded securely to an internal web server.

---

## Lab Topology

| Device                | Interface     | IP Address      |
| --------------------- | ------------- | --------------- |
| FortiGate             | WAN (Port1)   | 192.168.121.129 |
| FortiGate             | LAN (Port2)   | 192.168.223.1   |
| Kali Linux Web Server | eth0          | 192.168.223.100 |
| Internet Client       | External User | WAN Network     |

---

## Theory

### Problem

Internal servers use private IP addresses.

Example:

```text
192.168.223.100
```

Private IP addresses cannot be accessed directly from the Internet.

### Solution

Use a FortiGate VIP (Virtual IP).

VIP maps:

```text
Public IP
192.168.121.129
        ↓
Private IP
192.168.223.100
```

This allows Internet users to access services hosted inside the network.

---

## SNAT vs DNAT

### Source NAT (SNAT)

Used when internal users access the Internet.

```text
LAN User
      ↓
FortiGate
      ↓
Internet
```

Source IP is translated.

---

### Destination NAT (DNAT)

Used when Internet users access internal servers.

```text
Internet User
      ↓
FortiGate VIP
      ↓
Internal Server
```

Destination IP is translated.

---

## Configuration Steps

### Step 1: Configure Web Server

Start a simple web server on Kali Linux.

```bash
python3 -m http.server 80
```

Expected Output:

```text
Serving HTTP on 0.0.0.0 port 80
```

---

### Step 2: Create Virtual IP (VIP)

Navigate to:

```text
Policy & Objects → Virtual IPs
```

Create a new VIP.

| Parameter       | Value           |
| --------------- | --------------- |
| Name            | Kali-WebServer  |
| External IP     | 192.168.121.129 |
| Mapped IP       | 192.168.223.100 |
| Port Forwarding | Enabled         |
| External Port   | 80              |
| Mapped Port     | 80              |

---

### Step 3: Create Firewall Policy

Navigate to:

```text
Policy & Objects → Firewall Policy
```

Create a WAN-to-LAN policy.

| Parameter          | Value                |
| ------------------ | -------------------- |
| Incoming Interface | WAN (Port1)          |
| Outgoing Interface | LAN (Port2)          |
| Source             | all                  |
| Destination        | Kali-WebServer (VIP) |
| Service            | HTTP                 |
| Action             | ACCEPT               |

Save the policy.

---

## Verification

### Verify Web Server

On Kali Linux:

```bash
python3 -m http.server 80
```

Verify that the service is running.

---

### Verify Browser Access

Open a browser and browse to:

```text
http://192.168.121.129
```

Expected Result:

```text
Python HTTP Server Page
```

---

### Verify Traffic Logs

Navigate to:

```text
Log & Report → Forward Traffic
```

Verify:

* Action = Accept
* Service = HTTP
* VIP Object Used

---

## Traffic Flow

```text
Internet User
        |
        |
192.168.121.129
        |
        |
FortiGate VIP
        |
        |
192.168.223.100
        |
        |
Kali Web Server
```

---

## Screenshots

### Screenshot 1

Kali Web Server Running

```bash
python3 -m http.server 80
```

### Screenshot 2

VIP Configuration

### Screenshot 3

WAN-to-LAN Firewall Policy

### Screenshot 4

Browser Access to VIP Address

### Screenshot 5

FortiGate Traffic Logs

---

## Key Concepts Learned

### Virtual IP (VIP)

A VIP maps a public IP address to a private internal IP address.

### Port Forwarding

Port forwarding allows external users to access internal services through the firewall.

### Destination NAT (DNAT)

Destination NAT changes the destination IP address of incoming traffic before forwarding it to an internal server.

### Publishing Internal Services

VIPs are commonly used to publish:

* Web Servers
* SSH Servers
* Mail Servers
* Application Servers

---

## Interview Questions

### What is a VIP in FortiGate?

A VIP is a Virtual IP object that maps an external IP address to an internal private IP address.

### What is Port Forwarding?

Port Forwarding allows Internet users to access internal services by forwarding traffic from a public IP address to a private IP address.

### Difference Between SNAT and DNAT?

| SNAT                     | DNAT                         |
| ------------------------ | ---------------------------- |
| Changes Source IP        | Changes Destination IP       |
| LAN → Internet           | Internet → Internal Server   |
| Used for Internet Access | Used for Publishing Services |

---

## Result

Successfully configured a FortiGate Virtual IP (VIP) and Port Forwarding rule to publish an internal web server to external users. Verified connectivity through browser testing and traffic logs. This lab demonstrated the concepts of VIPs, Destination NAT (DNAT), and secure service publishing using FortiGate firewalls.

## GitHub Repository

[FortiGate Labs Repository](https://github.com/Loke31033/Fortigate-Labs?utm_source=chatgpt.com)

### Skills Practiced

* FortiGate VIP Configuration
* Port Forwarding
* Destination NAT (DNAT)
* Firewall Policies
* Web Server Publishing
* Traffic Analysis
* Network Security Administration
