# Enterprise Office Network Design Project


**OVERVIEW**

This project demonstrates the design and configuration of a small enterprise office network using a multilayer switching architecture. The goal was to build a scalable, secure, and fully routed environment supporting multiple VLANs, centralized DHCP services, dynamic routing with OSPF, and internet access through PAT. The topology reflects real-world enterprise design principles, integrating Layer 2 and Layer 3 switching, routing, and service delivery.

**PROJECT OBJECTIVES**

- Implement inter-VLAN routing using a Layer 3 multilayer switch
- Configure OSPF for dynamic routing between internal devices and the edge router
- Deploy DHCP Relay (IP Helper) to support centralized DHCP services across VLANs
- Enable PAT (NAT Overload) for secure internet access through a single public IP
- Validate end-to-end connectivity, routing convergence, and host address assignment

**NETWORK TOPOLOGY SUMMARY**

The network consists of:

Core Layer
- Layer 3 Multilayer Switch (MLS)
- Performs inter-VLAN routing
- Runs OSPF with the edge router
- Acts as the default gateway for all VLANs

Distribution/Access Layer
- Layer 2 Switch
- Hosts the DHCP server and end-user devices
- Provides VLAN segmentation for HR, Finance, and Sales departments

Edge Layer
- Enterprise Router
- Connects the internal network to the ISP
- Performs PAT for outbound internet traffic
- Participates in OSPF with the MLS

Services
- DHCP Server
- Provides IP addressing for VLAN10, VLAN20, and VLAN30
- Centralized on the L2 switch, requiring DHCP relay on the MLS

**TECHNICAL IMPLEMENTATION**

<ins> VLAN Segmentation & Inter-VLAN Routing </ins>

+ Three VLANs were created to separate departmental traffic:

   VLAN 10-IT

   VLAN 20-Sales

   VLAN 30-HR

+ SVIs were configured on the MLS, and ip routing was enabled to allow inter-VLAN communication.

<ins> OSPF Dynamic Routing </ins>

+ OSPF was implemented between the MLS and the edge router to ensure:
   
   Automatic route exchange
   Fast convergence
   Scalability for future network expansion
   
+ The ISP router advertised a default route, which was redistributed into OSPF to provide internet reachability for all internal networks.

<ins> DHCP Relay Agent </ins>

+ Since the DHCP server resides on the L2 switch, the MLS was configured with DHCP relay (IP helper) on each SVI. This allowed DHCP broadcasts from VLAN hosts to be forwarded to the centralized DHCP server, ensuring consistent address assignment across all VLANs.

<ins> PAT (NAT Overload) </ins>

+ The edge router was configured to translate all internal private IP addresses to a single public IP using PAT. This provided:

   Secure outbound internet access
   Efficient use of public IP space
   Simplified firewall and ISP integration

**TESTING & VALIDATION**

A structured verification process was performed:

Connectivity

-  Hosts successfully obtained IP addresses from the DHCP server
- Inter-VLAN communication verified via ping
- Internet access validated through PAT translations

Routing

- OSPF neighbor adjacency confirmed
- Routing tables validated for internal and default routes

NAT

- NAT translations observed using show ip nat translations
- Traffic statistics confirmed active PAT sessions

**KEY OUTCOMES**

- Successfully built a functional, scalable enterprise network
- Demonstrated strong understanding of Layer 2/Layer 3 integration
- Implemented industry-standard protocols (OSPF, DHCP Relay, NAT)
- Showcased practical troubleshooting and verification skills
- Produced a topology that mirrors real-world enterprise environments
