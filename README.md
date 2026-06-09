Campus Network Design and Implementation

Project Overview

The main goal of this project is to design and implement a functional campus network that separates departments into different VLANs while allowing controlled communication between required network segments.

The network consists of two campuses:

Main Campus / Sümer Campus
Branch Campus / Mimar Sinan Campus

The campuses are connected through a WAN link and routed dynamically using OSPFv2.

Network Features
Hierarchical campus network topology
VLAN-based department segmentation
Router-on-a-stick inter-VLAN routing
OSPFv2 dynamic routing
Multi-area OSPF design
Area 0 for Main Campus
Area 1 for Branch Campus
Centralized DHCP server located in VLAN 60
DHCP relay using ip helper-address
DNS, Web, Email, and DHCP server configuration
Wireless access points for each department
SSHv2 secure remote management
Telnet disabled on managed devices
Extended ACLs for Teknopark security policies
Port Security on access ports
Native VLAN changed from VLAN 1 to unused VLAN 999
VLAN Design
VLAN ID	Department / Area	Network
VLAN 10	Faculty of Engineering	195.148.10.0/24
VLAN 20	Administrative Offices	195.148.20.0/24
VLAN 30	Faculty of Art & Design	195.148.30.0/24
VLAN 40	Faculty of Business	195.148.40.0/24
VLAN 50	Student Computer Labs	195.148.50.0/24
VLAN 60	IT Department / Servers	195.148.60.0/24
VLAN 70	Teknopark Administration	195.148.70.0/24
VLAN 80	Company Offices	195.148.80.0/24
VLAN 999	Native Unused VLAN	Used only as native VLAN on trunk links
Routing Design

OSPFv2 is used as the dynamic routing protocol.

Main Campus networks are advertised in OSPF Area 0.
Branch Campus networks are advertised in OSPF Area 1.
The WAN link between routers is part of Area 0.
End-device-facing interfaces are configured as passive interfaces.
Security Policies

The project includes ACL rules to enforce security boundaries:

VLAN 80 Company Offices is blocked from accessing internal academic and IT VLANs.
VLAN 70 Teknopark Administration is allowed to access only the Web Server in VLAN 60.
VLAN 70 is blocked from accessing other internal VLANs.
VLAN 60 IT Department is allowed full management access.
SSHv2 is enabled for secure remote device management.
Telnet access is disabled.
Port Security is configured to protect access ports from unauthorized devices.
DHCP and Server Services

A centralized DHCP server is located in VLAN 60. Separate DHCP pools are configured for each VLAN. Branch Campus clients receive IP addresses from the Main Campus DHCP server through DHCP relay.

Server room devices use static IP addresses, while end devices receive dynamic addresses from their corresponding DHCP pools.

Testing and Verification

The project was tested using the following methods:

Intra-VLAN ping tests
Inter-VLAN ping tests
Cross-campus connectivity tests
OSPF neighbor verification
OSPF routing table verification
DHCP release and renew tests
DHCP relay verification for Branch Campus VLANs
ACL enforcement tests
Web server access test
SSH remote access test
Telnet blocked test
Port Security violation test
Wireless client IP assignment test
