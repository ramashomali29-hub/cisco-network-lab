# Cisco Enterprise Network Lab

A multi-VLAN enterprise network designed and configured in Cisco Packet Tracer, covering routing, switching, and Layer 2 security based on the CCNA curriculum.

## Topology Overview
- **2 Routers (ISR4331):** R1 and R2 connected via a point-to-point link
- **2 Switches (Catalyst 2960):** connected with an EtherChannel trunk
- **4 PCs** distributed across two VLANs
- **1 Server** providing DHCP services

## Configurations
- Basic device configuration on routers and switches
- VLANs with access ports on switches
- EtherChannel between switches for trunk redundancy and bandwidth
- Trunk link between S1 and R2
- Inter-VLAN routing using Router-on-a-Stick
- Switch management interfaces on VLAN 99
- DHCP server for automatic IP addressing
- OSPF routing between R1 and R2
- Port security on PC-facing interfaces
- DHCP snooping on switches

## IP Addressing

| VLAN / Link | Network | Gateway |
|---|---|---|
| VLAN 10 | 192.168.10.0/24 | 192.168.10.1 |
| VLAN 20 | 192.168.20.0/24 | 192.168.20.1 |
| VLAN 99 (Native, Management) | 192.168.99.0/24 | 192.168.99.1 |
| R1 – R2 Link | 10.10.10.0/30 | — |
| Server Network | 172.16.1.0/24 | 172.16.1.1 |

## VLAN Assignment

| Device | VLAN |
|---|---|
| PC0, PC2 | VLAN 10 |
| PC1, PC3 | VLAN 20 |

## Port Security Demonstration
The link between Switch0 and PC0 appears **down (red)** intentionally.
Port security was configured on PC-facing interfaces to allow only authorized MAC addresses.
A violation was triggered on PC0's port, so the switch automatically shut it down (err-disabled state), which shows how port security blocks unauthorized devices.

To verify, run on Switch0:
```
show port-security interface [interface]
show interfaces status err-disabled
```

To recover the port after removing the unauthorized device:
```
interface [interface]
 shutdown
 no shutdown
```<img width="1532" height="592" alt="topology" src="https://github.com/user-attachments/assets/cf31b133-7ec6-4807-a5a7-d435dad1f4e1" />


## How to Open
1. Download and install [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer)
2. Download the `.pkt` file from this repository
3. Open it in Packet Tracer
