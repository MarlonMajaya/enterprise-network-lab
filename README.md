# Enterprise-network-lab
CCNA enterprise network lab using Cisco Packet Tracer, VLANs, EtherChannel, OSPF, DHCP, ACLs and network security.


# Enterprise Network Lab

## Overview

This project demonstrates a small enterprise network built using Cisco Packet Tracer. It was created after completing the Cisco CCNA certification to gain practical experience with enterprise networking and network security.

## Technologies

- Cisco IOS
- VLANs and 802.1Q trunking
- LACP EtherChannel
- Router-on-a-stick
- OSPF
- DHCP
- Extended ACLs
- SSH
- Port security
- DHCP snooping
- Dynamic ARP Inspection

## Network Architecture

The lab contains two routers, two switches, four PCs and one server.

The network uses four department VLANs:

| VLAN | Department | Network |
|---|---|---|
| 10 | Management | 192.168.10.0/24 |
| 20 | Users | 192.168.20.0/24 |
| 30 | Servers | 192.168.30.0/24 |
| 40 | Guest | 192.168.40.0/24 |
| 99 | Native | No client addressing |

R1 and R2 use OSPF area 0. R2 provides inter-VLAN routing and DHCP services. SW1 and SW2 are connected using a two-link LACP EtherChannel.

## Security

- Guest traffic is restricted from reaching the Servers VLAN.
- SSH is used for secure remote management.
- Port security limits MAC addresses on access ports.
- DHCP snooping and Dynamic ARP Inspection are configured where supported.

## Testing

The following tests are documented in the screenshots folder:

- Intra-VLAN and inter-VLAN connectivity
- OSPF neighbor and routing table verification
- DHCP address assignment
- Guest ACL enforcement
- SSH connectivity
- EtherChannel link failure testing
- Layer 2 security verification

## Repository Contents

- `configurations/` contains device configurations.
- `screenshots/` contains verification evidence.
- `troubleshooting/` contains the troubleshooting log.
- `docs/` contains the IP addressing plan.

## Skills Demonstrated

Cisco IOS configuration, network segmentation, routing, switching, troubleshooting, network security and technical documentation.
