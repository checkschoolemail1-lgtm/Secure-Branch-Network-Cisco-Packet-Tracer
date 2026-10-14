# Secure-Branch-Network-Cisco-Packet-Tracer
Secure Branch Network — Cisco Packet Tracer
Project Overview

Lab type: CCNA Layer 2 security and inter-VLAN routing
Time spent: Approximately 35–40 minutes
Platform: Cisco Packet Tracer

Built and secured a small enterprise branch network using VLAN segmentation, router-on-a-stick, DHCP, spanning-tree protections, Port Security, and an extended ACL.

Topology

                     +------------+
                     |     R1     |
                     | DHCP + ACL |
                     | Inter-VLAN |
                     |   Routing  |
                     +------+-----+
                            |
                       802.1Q trunk
                            |
                     +------+-----+
                     |    SW1     |
                     | Root Bridge|
                     +--+------+--+
                        |      |
                 PC1    |      | Admin PC
                VLAN 10 |      | VLAN 99
                        |      |
                  Inter-switch trunk
                            |
                     +------+-----+
                     |    SW2     |
                     | Access SW  |
                     +--+------+--+
                        |      |
                       PC2    PC3
                     VLAN 10 VLAN 20
                     USERS   GUEST

See topology.png for the Packet Tracer topology.

Technologies Implemented

VLANs 10, 20, 99, and 999

IEEE 802.1Q trunking and native VLAN configuration

Router-on-a-stick using R1 subinterfaces

DHCP pools for user and guest clients

Rapid PVST+ root-bridge selection

PortFast and BPDU Guard on end-device ports

Port Security with sticky MAC learning and violation mode restrict

Management SVIs on SW1 and SW2

Extended ACL restricting Guest VLAN access to the Management VLAN

VLAN and IP Addressing Plan

VLAN

Purpose

Network

Default Gateway

10

Users

192.168.10.0/24

192.168.10.1

20

Guests

192.168.20.0/24

192.168.20.1

99

Management

192.168.99.0/24

192.168.99.1

999

Native / unused-port VLAN

No IP addressing

None

Infrastructure Addresses

Device

IP Address

R1 VLAN 10 gateway

192.168.10.1

R1 VLAN 20 gateway

192.168.20.1

R1 VLAN 99 gateway

192.168.99.1

SW1 management SVI

192.168.99.2

SW2 management SVI

192.168.99.3

Admin PC

192.168.99.10

PC1 and PC2 use VLAN 10, while PC3 uses VLAN 20. Client addresses are assigned through DHCP.

Security Requirements

Layer 2

Configure trunks with an explicit allowed-VLAN list.

Use VLAN 999 as the native VLAN on both ends of trunk links.

Make SW1 the STP root bridge for VLANs 10, 20, and 99.

Enable PortFast and BPDU Guard on host-facing ports.

Enable Port Security with a maximum of one secure MAC address per access port.

Layer 3

The extended ACL on R1 blocks traffic from Guest VLAN 20 to Management VLAN 99 while permitting other traffic required by the lab.

The ACL is applied inbound on R1's VLAN 20 subinterface so guest traffic is filtered as it enters the router.
