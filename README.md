Secure Network Lab

Overview

A hands-on networking and security lab built in Cisco Packet Tracer. This project explores VLAN segmentation, 802.1Q trunking, inter-VLAN routing, Access Control Lists (ACLs), connectivity testing and Spanning Tree Protocol (STP).

Objectives

Configure VLANs to separate network departments.

Configure an 802.1Q trunk.

Implement router-on-a-stick inter-VLAN routing.

Apply an extended ACL to restrict traffic between VLANs.

Test permitted and blocked connectivity.

Examine STP root bridge information.

Troubleshoot network connectivity.

Network Topology

The lab contains one Cisco 2911 router, one Cisco 2960 switch and three PCs.



IP Addressing

Device

VLAN

IP address

Default gateway

PC0 — Admin

10

192.168.10.10/24

192.168.10.1

PC1 — Staff

20

192.168.20.10/24

192.168.20.1

PC2 — Servers

30

192.168.30.10/24

192.168.30.1

All devices use the subnet mask 255.255.255.0.

VLAN Configuration

VLAN ID

Name

Switch port

10

ADMIN

Fa0/1

20

STAFF

Fa0/2

30

SERVERS

Fa0/3

The switch-to-router connection uses an 802.1Q trunk. Router subinterfaces provide the default gateway for each VLAN.

Access Control List

The extended ACL BLOCK-STAFF-TO-SERVERS is applied outbound on router subinterface GigabitEthernet0/0.30.

It denies IP traffic from the Staff subnet to the Servers subnet, with an ICMP echo-reply exception that allows the tested Servers-to-Staff ping to succeed.

Security limitation: ACLs are stateless. This ICMP exception does not provide stateful inspection or automatically permit return traffic for TCP and UDP sessions.

Connectivity Test Results

Test

Result

Staff → Servers

Blocked; 100% packet loss

Staff → Admin

Successful; 0% packet loss

Admin → Servers

Successful; 0% packet loss

Servers → Staff

Successful; 0% packet loss

Spanning Tree Protocol

The switch's show spanning-tree output was examined. The switch identifies itself as the root bridge in the VLAN output captured.

This single-switch topology demonstrates STP operation on the switch but does not demonstrate root bridge election between multiple switches.

Evidence

Configuration screenshots, IP addressing and connectivity test evidence are stored in the screenshots/ directory.

Tools and Technologies

Cisco Packet Tracer

Cisco IOS CLI

VLANs and 802.1Q trunking

Router-on-a-stick routing

Extended IP ACLs

ICMP connectivity testing

Spanning Tree Protocol (STP)
