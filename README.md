# Yenepoya University Network Topology

### Multi-Campus Network Design and Configuration Using Cisco Packet Tracer

## Project Overview

This project presents a simulated multi-campus network for **Yenepoya University**, designed and configured using Cisco Packet Tracer. The topology connects departmental networks, student laboratories, internal servers, and an external email service across two campuses.

The design demonstrates practical networking concepts including VLAN-based segmentation, inter-VLAN routing, IPv4 addressing, RIPv2 dynamic routing, router-based DHCP, and connectivity between campus networks.

> \*\*Project scope:\*\* This repository documents a Cisco Packet Tracer learning project. Network features described below should be considered implemented only where they are configured and verified in the supplied `.pkt` file.

## Network Topology

The network is organized into a main campus and an Arts campus, with a simulated external network for email services.

!\[Yenepoya University Network Topology](screenshots/yenepoya-university-network-topology.png)

## Campus Layout

### Main Campus

The main campus contains three buildings connected to the main campus router through the university's central Layer 3 switch.

#### Building A — Administration and Business

Building A contains the following departments:

* Administration (ADMIN) — VLAN 10
* Human Resources (HR) — VLAN 20
* Finance — VLAN 30
* Business — VLAN 40

Each department is assigned a separate VLAN and IPv4 subnet. The administrative PCs are intended to obtain their IP configuration from a router-based DHCP service.

#### Building B — Health Sciences

Building B contains two departmental network segments:

* **MLT — Medical Laboratory Technology:** VLAN 50
* **MIT — Medical Imaging Technology:** VLAN 60

Each department uses a separate VLAN and IP subnet while sharing the main campus network infrastructure.

#### Building C — Student Laboratories and IT

Building C contains:

* Student Laboratory (ST LAB) — VLAN 70
* IT Department (IT DEP) — VLAN 80
* University Web Server
* FTP Server

The web and FTP servers represent internal university services hosted by the IT department.

### Arts Campus

The separate Arts campus connects to the main campus through campus routers and includes:

* Arts \& Science Staff — VLAN 90
* Student Laboratory (LAB) — VLAN 100

The two network segments use separate VLANs and IPv4 subnets.

### External Email Service

A simulated cloud network connects to an external email server. This represents a service hosted outside the university's internal network. External access depends on the appropriate routing and server configuration.

## VLAN and IPv4 Addressing Plan

The following table is based on the labels visible in the topology and the main campus router's routing-table output.

|VLAN|Department / Network Segment|IPv4 Network|Subnet Mask|
|-:|-|-|-|
|10|Administration (ADMIN)|`192.168.1.0/24`|`255.255.255.0`|
|20|Human Resources (HR)|`192.168.2.0/24`|`255.255.255.0`|
|30|Finance|`192.168.3.0/24`|`255.255.255.0`|
|40|Business|`192.168.4.0/24`|`255.255.255.0`|
|50|Medical Laboratory Technology (MLT)|`192.168.5.0/24`|`255.255.255.0`|
|60|Medical Imaging Technology (MIT)|`192.168.6.0/24`|`255.255.255.0`|
|70|Student Laboratory (ST LAB)|`192.168.7.0/24`|`255.255.255.0`|
|80|IT Department (IT DEP)|`192.168.8.0/24`|`255.255.255.0`|
|90|Arts \& Science Staff|`192.168.9.0/24`|`255.255.255.0`|
|100|Student Laboratory (LAB)|`192.168.10.0/24`|`255.255.255.0`|

The main campus router's displayed configuration uses subinterfaces with gateway addresses `192.168.1.1` through `192.168.8.1` for VLANs 10–80. The routing-table screenshot also shows routes to `192.168.9.0/24` and `192.168.10.0/24` learned through RIPv2.

## Networking Technologies

The project covers the following concepts, as represented in the topology and configuration:

* Cisco Packet Tracer network simulation
* Multi-campus network design
* VLANs for departmental segmentation
* IPv4 addressing and subnetting
* Router subinterfaces for inter-VLAN routing
* IEEE 802.1Q VLAN trunking
* RIPv2 dynamic routing between internal routers
* Router-based DHCP for Building A (as required by the design)
* Serial links between campus routers
* Internal web and FTP servers
* Simulated external email service
* Network troubleshooting and connectivity verification

## Routing and Connectivity

### Inter-VLAN Routing

The main campus router has subinterfaces on its `GigabitEthernet0/0` interface for VLANs 10 through 80. The subinterfaces provide Layer 3 gateway addresses for their corresponding IP networks, enabling inter-VLAN communication when permitted by the network configuration.

### RIPv2 Dynamic Routing

RIPv2 is used to exchange routes between internal routers. The displayed main campus routing table includes RIPv2-learned routes to the Arts campus networks `192.168.9.0/24` and `192.168.10.0/24`.

### External Network Routing

The topology includes a simulated cloud and external email server. The coursework brief specifies static routing for the external server. Verify the static route, return route, and end-to-end connectivity in Packet Tracer before claiming that external email access is fully functional.

The captured main campus routing table displays **“Gateway of last resort is not set.”** This indicates that no default route is shown in that output; external connectivity may require additional route configuration.

## DHCP

The coursework requirements specify a router-based DHCP service for devices in Building A. DHCP should provide the appropriate IP address, subnet mask, default gateway, and other required settings to client devices.

Verify DHCP operation by checking that the relevant PCs receive valid addresses and can reach their configured gateway.

## Servers and Services

* **University Web Server:** Represents the university's internal web service.
* **FTP Server:** Represents an internal file-transfer service.
* **External Email Server:** Represents an email service hosted outside the university network.

Service availability depends on the server settings, client configuration, and routing between the source and destination networks.

## Security and Segmentation

VLANs separate departmental broadcast domains and help organize network traffic. VLANs alone do not prevent all unauthorized communication between networks.

Possible additional security measures include:

* Configuring switch port security.
* Disabling unused switch ports.
* Restricting inter-VLAN traffic with access control lists (ACLs).
* Securing device management access.
* Applying appropriate access controls to internal servers.
* Reviewing trunk ports and allowing only required VLANs.

## Testing and Verification

The following checks can be used to validate the project:

* Confirm VLAN assignments and trunk configuration on switches.
* Check router interface and subinterface status using `show ip interface brief`.
* Inspect routing entries using `show ip route`.
* Verify RIPv2 route learning between campus routers.
* Confirm that Building A clients receive DHCP addresses.
* Test connectivity between devices in the same VLAN.
* Test inter-VLAN connectivity where intended.
* Test connectivity between the main and Arts campuses.
* Verify access to the university web and FTP servers.
* Test external email-server reachability and service configuration.

Record successful test results with screenshots or command output before describing them as verified outcomes.

## Tools Used

* Cisco Packet Tracer
* Cisco IOS CLI
* IPv4 addressing and subnetting
* VLANs and IEEE 802.1Q
* RIPv2
* DHCP
* Web and FTP server simulation

## Repository Contents

```text
yenepoya-university-network-topology/
├── README.md
├── University Network.pkt
└── screenshots/
    └── yenepoya-university-network-topology.png
```

Add your actual topology screenshot to the `screenshots/` directory using the filename shown above, or update the image path in this README to match your chosen filename.

## How to Open the Project

1. Install Cisco Packet Tracer.
2. Clone or download this repository.
3. Open `Yenepoya University network-topology.pkt` in Cisco Packet Tracer.
4. Inspect the topology, device configurations, and routing tables.
5. Use Packet Tracer's simulation tools and CLI to test connectivity.

## Learning Outcomes

This project provides practical experience in:

* Designing a multi-campus network topology.
* Segmenting departments using VLANs and IPv4 subnets.
* Configuring router subinterfaces for inter-VLAN routing.
* Understanding dynamic routing with RIPv2.
* Working with router-based DHCP.
* Connecting internal servers and simulated external services.
* Verifying routes and troubleshooting network connectivity.
* Considering network scalability, reliability, and security.

## Acknowledgment


This project is intended for educational and portfolio demonstration purposes.

