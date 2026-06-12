# Lab 02 - FortiGate Dashboard Navigation

## Objective

The objective of this lab is to explore the FortiGate Dashboard, understand the purpose of each dashboard widget, monitor system health, and become familiar with the FortiGate graphical user interface (GUI).

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

The FortiGate Dashboard is the central monitoring interface used by administrators to view system health, resource utilization, network activity, interface status, and security information.

Understanding the dashboard is essential because it provides real-time visibility into the firewall's operational status and helps identify potential performance or security issues.

---

## Accessing the Dashboard

### Step 1: Login

Open a web browser and connect to the FortiGate management interface.

Example:

```text
https://<FortiGate-IP>
```

Login using the administrator account.

---

## Dashboard Overview

Navigate to:

```text
Dashboard → Status
```

The dashboard contains multiple widgets that provide system information and monitoring capabilities.

---

## System Information Widget

The System Information widget provides important details about the FortiGate device.

### Information Observed

* Hostname
* Firmware Version
* Serial Number
* Operation Mode
* System Uptime
* Administrative Domain (VDOM)

### Purpose

This widget helps administrators quickly identify the firewall configuration and operational status.

---

## CPU and Memory Monitoring

### CPU Usage

CPU utilization indicates the processing load on the firewall.

High CPU usage may be caused by:

* Heavy network traffic
* Intrusion Prevention System (IPS) activity
* Malware scanning
* Large numbers of active sessions

### Memory Usage

Memory utilization represents RAM consumption.

High memory usage may result from:

* Excessive logging
* High session counts
* Security profile processing

### Importance

Monitoring CPU and memory helps administrators identify performance bottlenecks and resource exhaustion.

---

## Session Monitoring

The Sessions widget displays active network sessions passing through the firewall.

### Examples of Sessions

* Web browsing
* SSH connections
* VPN tunnels
* Email communication

### Purpose

Session monitoring helps administrators understand current network activity and troubleshoot connectivity issues.

---

## Interface Monitoring

The Interface widget displays:

* Interface names
* IP addresses
* Link status
* Traffic statistics

### Common Interfaces

* port1 (WAN)
* port2 (LAN)

### Importance

Administrators use interface monitoring to verify connectivity and identify network issues.

---

## Navigation Menu Exploration

The left navigation panel contains all major FortiGate management sections.

### Dashboard

Used for monitoring system status and performance.

### Network

Used to configure:

* Interfaces
* Routing
* DNS
* SD-WAN

### Policy & Objects

Used to create:

* Firewall Policies
* Address Objects
* Service Objects

### Security Profiles

Used to configure:

* Antivirus
* Intrusion Prevention System (IPS)
* Web Filtering
* Application Control

### VPN

Used to configure:

* SSL VPN
* IPsec VPN

### User & Authentication

Used to manage:

* Local Users
* User Groups
* Authentication Methods

### Log & Report

Used to analyze:

* Traffic Logs
* Event Logs
* Security Logs

---

## Verification

CLI command executed:

```bash
get system status
```

Verified:

* Hostname
* Firmware Version
* Serial Number
* License Status
* Operation Mode

---

## Screenshots

### Screenshot 1

Dashboard Status Page

### Screenshot 2

System Information Widget

### Screenshot 3

CPU and Memory Widget

### Screenshot 4

Session Monitoring Widget

### Screenshot 5

Interface Monitoring Widget

### Screenshot 6

Navigation Menu

### Screenshot 7

CLI Verification Output

---

## Key Concepts Learned

### Dashboard

Provides centralized monitoring of firewall health and activity.

### Sessions

Represents active communication flows between devices and services.

### System Information

Displays essential device identification and operational details.

### Resource Monitoring

Tracks CPU and memory utilization to ensure stable firewall performance.

### Interface Monitoring

Allows administrators to verify network connectivity and traffic flow.

---

## Challenges Faced

* Understanding the purpose of each dashboard widget.
* Identifying key system health indicators.
* Interpreting session and interface statistics.

---

## Outcome

Successfully explored the FortiGate Dashboard, understood the functionality of key widgets, verified system information, monitored resource utilization, and became familiar with the FortiGate management interface.

---

## Skills Acquired

* FortiGate Dashboard Navigation
* System Health Monitoring
* Resource Monitoring
* Session Monitoring
* Interface Monitoring
* FortiGate GUI Familiarity
* Basic FortiGate Administration

---

## Interview Questions

### What information is available in the FortiGate Dashboard?

The dashboard displays system information, CPU usage, memory usage, active sessions, interface status, and security monitoring information.

### Why is CPU and memory monitoring important?

It helps administrators identify performance issues, resource bottlenecks, and abnormal activity.

### What is a network session?

A session is a tracked communication flow between a source and destination device through the firewall.

### Which FortiGate menu is used to create firewall policies?

Policy & Objects.

---

## Author

Lokeshwar V

Cybersecurity Student | SOC Analyst Aspirant
