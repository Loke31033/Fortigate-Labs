Lab 01 - FortiGate VM Deployment

Objective

The objective of this lab is to deploy a FortiGate Virtual Machine (VM) in VMware Workstation, configure the initial setup, activate the evaluation license, and access both the Command Line Interface (CLI) and Graphical User Interface (GUI).

⸻

Lab Environment

Component	Details
Host OS	Windows 11
Hypervisor	VMware Workstation Pro
Firewall	FortiGate VM
Firmware Version	FortiOS v7.4.12
CPU	1 vCPU
RAM	2 GB
Network Mode	NAT
License Type	Evaluation License

⸻

Architecture

Windows 11 Host
       │
VMware Workstation
       │
┌─────────────────┐
│   FortiGate VM  │
└─────────────────┘
       │
   NAT Network
       │
    Internet

⸻

Deployment Steps

Step 1: Download FortiGate VM

Downloaded the FortiGate VMware OVF image from the Fortinet Support Portal.

Files extracted:

* FortiGate-VM64.ovf
* fortios.vmdk
* datadrive.vmdk

⸻

Step 2: Import into VMware

1. Open VMware Workstation.
2. Select Open Virtual Machine.
3. Import the FortiGate OVF package.
4. Complete the deployment wizard.

⸻

Step 3: Configure VM Resources

Configured the VM with:

* CPU: 1 vCPU
* Memory: 2048 MB
* Disk: 30 GB

These settings comply with FortiGate Evaluation License requirements.

⸻

Step 4: Boot the VM

Powered on the FortiGate VM.

The FortiGate operating system successfully booted and presented the CLI login prompt.

⸻

Step 5: Initial Login

Default administrator account:

* Username: admin
* Password: blank

After first login, FortiGate required an administrator password change.

⸻

Step 6: Evaluation License Activation

Activated the FortiGate Evaluation License using the FortiCare account.

Evaluation License Limits:

* 1 CPU
* 2 GB RAM
* 3 Interfaces
* 3 Firewall Policies
* 3 Routes

⸻

Step 7: GUI Access

Accessed the FortiGate management interface using HTTPS.

Example:

https://192.168.185.129

Successfully logged into the FortiGate Dashboard.

⸻

Verification

CLI command used:

get system status

Verified:

* Hostname
* Firmware Version
* Serial Number
* Operation Mode
* License Status

⸻

Screenshots

Screenshot 1

Extracted FortiGate VM files

Screenshot 2

VMware Import Process

Screenshot 3

VM Configuration Settings

Screenshot 4

FortiGate CLI Login

Screenshot 5

Administrator Password Setup

Screenshot 6

Evaluation License Information

Screenshot 7

FortiGate Dashboard

Screenshot 8

System Status Verification

⸻

Key Concepts Learned

FortiGate VM

A virtualized Next Generation Firewall (NGFW) that provides:

* Firewall Protection
* Routing
* NAT
* VPN
* IPS
* Web Filtering
* Application Control

VMware Workstation

A desktop hypervisor used to run virtual machines without requiring physical hardware.

OVF

Open Virtualization Format (OVF) is a standard packaging format used for deploying virtual appliances.

Evaluation License

A free FortiGate VM license intended for learning and testing purposes with limited resources.

⸻

Challenges Faced

* Initial VirtualBox deployment issues.
* QCOW2 image conversion problems.
* License activation troubleshooting.
* VM serial number mismatch.
* DNS and connectivity verification.

⸻

Outcome

Successfully deployed FortiGate VM v7.4.12 on VMware Workstation, activated the evaluation license, accessed the GUI dashboard, and prepared the environment for future FortiGate administration and security labs.

⸻

Skills Acquired

* FortiGate VM Deployment
* VMware Virtualization
* Initial FortiGate Configuration
* License Management
* CLI Administration
* GUI Navigation
* Basic Troubleshooting

⸻

Author

Lokeshwar V

Cybersecurity Student | SOC Analyst Aspirant
