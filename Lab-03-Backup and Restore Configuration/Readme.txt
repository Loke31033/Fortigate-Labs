# Lab 03 - FortiGate Configuration Backup and Restore

## Objective

The objective of this lab is to understand how to create a configuration backup, restore a saved configuration, and learn the importance of configuration management in FortiGate firewalls.

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

Configuration backup is one of the most important administrative tasks in FortiGate.

A backup file contains all firewall settings including:

* Interfaces
* Routing
* Firewall Policies
* NAT Configuration
* VPN Settings
* User Accounts
* Security Profiles

If the firewall fails or a configuration mistake occurs, the backup can be restored to recover the system quickly.

---

## Why Configuration Backup is Important

In production environments, administrators regularly create backups before:

* Firmware upgrades
* Policy modifications
* VPN deployment
* Security profile changes
* Major network changes

A recent backup helps minimize downtime and configuration loss.

---

## Step 1: Access Configuration Menu

Navigate to:

```text id="7ihib2"
Configuration
→ Backup & Restore
```

This page provides options for:

* Configuration Backup
* Configuration Restore

---

## Step 2: Backup Configuration

Selected:

```text id="zhy9i6"
Backup
```

Chose:

```text id="11pcja"
Local PC
```

Downloaded the FortiGate configuration file.

Example:

```text id="0ms8hz"
backup_20260612.conf
```

---

## Step 3: Store Backup Securely

Created a dedicated backup directory:

```text id="pc2mdo"
FortiGate-Backups
```

Stored the backup file for future recovery purposes.

---

## Step 4: Examine Configuration File

Opened the configuration file using Notepad.

Observed configuration sections such as:

```text id="3zy4eu"
config system interface
```

```text id="f11jfx"
config router static
```

```text id="afkhxg"
config firewall policy
```

```text id="xnl3h0"
config user local
```

This demonstrates that FortiGate stores configuration in a readable text format.

---

## Step 5: Explore Restore Function

Selected:

```text id="u2x5sh"
Restore
```

Observed the configuration upload interface.

No configuration was restored during this lab.

### Purpose

Restore is used when:

* Recovering from configuration corruption
* Replacing failed devices
* Reverting unwanted changes

---

## Step 6: Understand Factory Reset

Reviewed the CLI reset option.

Command:

```bash id="dyh2kl"
execute factoryreset
```

This command restores FortiGate to its default factory settings.

### Factory Reset Removes

* Firewall Policies
* Static Routes
* VPN Configuration
* Users and Groups
* Security Profiles
* Administrative Settings

After reset, the firewall behaves like a fresh installation.

---

## Verification

Verified firewall status using:

```bash id="7c6s0d"
get system status
```

Confirmed:

* Firewall operational status
* Firmware version
* Hostname
* Serial number
* License information

---

## Screenshots

### Screenshot 1

Configuration Backup and Restore Menu

### Screenshot 2

Backup Configuration Window

### Screenshot 3

Downloaded Configuration File

### Screenshot 4

Restore Configuration Window

### Screenshot 5

Factory Reset Reference

### Screenshot 6

System Status Verification

---

## Key Concepts Learned

### Configuration Backup

Creates a copy of the current FortiGate configuration.

### Configuration Restore

Restores a previously saved configuration file.

### Configuration File

A text-based file containing all firewall settings and policies.

### Factory Reset

Resets FortiGate to default settings by removing all custom configurations.

---

## Real-World Importance

Configuration backups are critical for:

* Disaster Recovery
* Change Management
* Compliance Requirements
* Business Continuity
* Incident Recovery

Organizations often automate backup schedules to ensure configuration availability during emergencies.

---

## Challenges Faced

* Locating the Backup and Restore menu in FortiOS 7.4.12.
* Understanding the structure of the configuration file.
* Learning the difference between restore and factory reset operations.

---

## Outcome

Successfully performed a FortiGate configuration backup, explored the restore process, examined the configuration file structure, and understood the role of backups in firewall administration and disaster recovery.

---

## Skills Acquired

* FortiGate Configuration Management
* Configuration Backup Procedures
* Configuration Restore Concepts
* Disaster Recovery Planning
* Firewall Administration
* FortiGate CLI Verification

---

## Interview Questions

### Why should a FortiGate configuration be backed up?

To recover firewall settings after accidental changes, hardware failure, firmware issues, or disaster recovery situations.

### What does a FortiGate backup file contain?

Interfaces, routing, firewall policies, VPN settings, users, security profiles, and system configurations.

### What happens during configuration restore?

The current configuration is replaced with the uploaded configuration and the firewall applies the restored settings.

### What is the difference between Restore and Factory Reset?

Restore loads a saved configuration, whereas Factory Reset removes all existing configurations and returns the device to default settings.

---

## Author

**Lokeshwar V**

Cybersecurity Student | SOC Analyst Aspirant | FortiGate Hands-on Lab Series
