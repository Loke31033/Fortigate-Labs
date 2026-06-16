Lab 9: FortiGate Firewall Configuration – LAN to WAN Internet Access Policy
Objective

To configure a FortiGate firewall to provide Internet access from a LAN network to a WAN network using firewall policies, routing, and NAT.

Network Topology
Device	Interface	IP Address
FortiGate	Port1 (LAN)	192.168.223.1/24
FortiGate	Port2 (WAN)	192.168.121.x/24
Kali Linux	eth0	192.168.223.x/24
WAN Gateway	VMnet8 Gateway	192.168.121.2

Configuration Steps
1. Configure Interfaces
Port1 configured as LAN interface.
Port2 configured as WAN interface.
Assigned IP addresses to both interfaces.

2. Configure Default Route
config router static
edit 1
set dst 0.0.0.0/0
set gateway 192.168.121.2
set device port2
next
end

3. Configure Firewall Policy

Source Interface: Port1 (LAN)

Destination Interface: Port2 (WAN)

Action: ACCEPT

NAT: ENABLED

Services:

HTTP
HTTPS
DNS
PING

4. Configure DNS
config system dns
set primary 8.8.8.8
set secondary 1.1.1.1
end
Verification
Verify Interface Configuration
show system interface
Verify Routing Table
get router info routing-table all
Verify Internet Connectivity

On Kali Linux:

ping 8.8.8.8
Verify DNS Resolution
ping google.com
Verify Web Browsing

Opened websites:

Google
YouTube

Successfully accessed through FortiGate firewall.

Screenshots Included
Interface Configuration
Routing Table
Firewall Policy
Kali IP Configuration (ip a)
Kali Routing Table (ip route)
Successful Ping to 8.8.8.8
Successful DNS Resolution
Successful Web Browser Access
Result

Successfully configured a FortiGate firewall to allow LAN-to-WAN Internet access using firewall policies, static routing, NAT, and DNS services. Internet connectivity and web access were verified from the Kali Linux client.