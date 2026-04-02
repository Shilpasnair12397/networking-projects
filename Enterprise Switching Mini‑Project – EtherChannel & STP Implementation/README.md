### ENTERPRISE SWITCHING MINI-PROJECT - ETHERCHANNEL & STP IMPLEMENTATION

## PROJECT OVERVIEW ##

This project demonstrates the design and implementation of a small enterprise Layer 2/Layer 3 switching environment
using Cisco Catalyst switches. The focus is on two core technologies used in real production networks:

• 	EtherChannel (LACP) for link aggregation, redundancy, and increased bandwidth

• 	Spanning Tree Protocol (Rapid‑PVST+) for loop prevention and fast convergence

The topology includes multiple VLANs, a multilayer switch acting as the core, and several access switches hosting user devices and servers.

## NETWORK TOPOLOGY SUMMARY ##

• 	Core Switch:
    
    Performs inter‑VLAN routing

    Acts as STP root bridge

    Provides trunk uplinks to all access switches

•   Access Switches:

    Host VLANs 10, 20, 30, 40

    VLAN 100 contains two DHCP servers
  
•   EtherChannel:

    Used between core and access switches (LACP)
  
•   STP:

    Rapid‑PVST+ running across all VLANs
  
 Spanning Tree Protocol (Rapid‑PVST+)
STP ensures a loop‑free Layer 2 topology.

Cisco switches run STP by default, but the design explicitly sets:
- Core switch as the STP root bridge
- Rapid‑PVST+ for faster convergence
- PortFast + BPDU Guard on access ports

## TESTING VALIDATION ##

EtherChannel
- Verified logical bundling using show etherchannel summary
- Confirmed trunking and VLAN propagation across Port‑Channels

STP
- Confirmed core switch elected as root bridge
- Verified designated and blocking ports
- Ensured PortFast active on access ports

Connectivity
- Successful inter‑VLAN communication
- DHCP relay functioning for all VLANs
- End‑to‑end reachability validated

## KEY SKILLS DEMONSTRATED ##
- VLAN design and segmentation
- Inter‑VLAN routing on a multilayer switch
- EtherChannel (LACP) configuration and verification
- Rapid‑PVST+ STP tuning and root bridge placement
- DHCP relay and multi‑VLAN service delivery
- Enterprise‑style documentation and topology design
