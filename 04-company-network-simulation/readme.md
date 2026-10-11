# Project 4: Company Network Simulation

## Overview

This project simulates a small company's network using Cisco Packet Tracer. The company has three departments: Human Resources (HR), Information Technology (IT), and Finance.

Each department has its own LAN, switch, and two PCs. A Cisco 2911 router connects the three networks and enables communication between departments.

## Objectives

- Design a multi-department company network.
- Configure IPv4 addresses and subnet masks.
- Configure router interfaces and default gateways.
- Understand communication within the same LAN and between different networks.
- Test connectivity using the `ping` command.
- Troubleshoot basic network connectivity issues.

## Tools and Devices

- Cisco Packet Tracer
- 1 Cisco 2911 router
- 3 Cisco 2960 switches
- 6 PCs
- Copper straight-through Ethernet cables

## Network Topology

The network consists of three department LANs connected through one router.

- HR-SW connects HR-PC1 and HR-PC2.
- IT-SW connects IT-PC1 and IT-PC2.
- FIN-SW connects FN-PC1 and FN-PC2.
- Router0 connects all three departmental networks.

## IP Addressing Plan

| Department | Device | IPv4 Address | Default Gateway |
|---|---|---|---|
| HR | Router0 G0/0 | 192.168.10.1 | — |
| HR | HR-PC1 | 192.168.10.10 | 192.168.10.1 |
| HR | HR-PC2 | 192.168.10.11 | 192.168.10.1 |
| IT | Router0 G0/1 | 192.168.20.1 | — |
| IT | IT-PC1 | 192.168.20.10 | 192.168.20.1 |
| IT | IT-PC2 | 192.168.20.11 | 192.168.20.1 |
| Finance | Router0 G0/2 | 192.168.30.1 | — |
| Finance | FN-PC1 | 192.168.30.10 | 192.168.30.1 |
| Finance | FN-PC2 | 192.168.30.11 | 192.168.30.1 |

**Subnet mask for all devices:** `255.255.255.0`

**DNS server:** Not configured; DNS was not required for these IP connectivity tests.

## Router Configuration

The following configuration was applied to Router0:

```text
enable
configure terminal

interface GigabitEthernet0/0
ip address 192.168.10.1 255.255.255.0
no shutdown
exit

interface GigabitEthernet0/1
ip address 192.168.20.1 255.255.255.0
no shutdown
exit

interface GigabitEthernet0/2
ip address 192.168.30.1 255.255.255.0
no shutdown
exit
```

The router interfaces became active. Because all three networks are directly connected to the router, it can route traffic between them without manually configured static routes.

## Connectivity Testing

Connectivity was tested using the Windows Command Prompt on the Packet Tracer PCs.

Examples of tests performed:

```text
ping 192.168.10.11
ping 192.168.20.10
ping 192.168.20.11
ping 192.168.30.10
ping 192.168.30.11
```

The tests confirmed communication between HR and IT, HR and Finance, and PCs within the same department. Reverse-direction communication was also tested from IT-PC1 to HR-PC1.

Some initial ping requests timed out, but subsequent requests received replies. This can occur while ARP resolves a destination's MAC address, although a timeout alone does not prove ARP was the cause.

## Key Concepts Learned

- IPv4 addressing and subnet masks
- Default gateways
- Ethernet switches and router interfaces
- Directly connected networks and inter-network routing
- ICMP Echo Requests and Echo Replies
- Basic connectivity troubleshooting

## Project File

`company-network-simulation.pkt` contains the Cisco Packet Tracer topology and configuration.

## Future Improvements

- Configure DHCP for automatic IP assignment.
- Create VLANs to logically separate departments.
- Apply Access Control Lists (ACLs) to restrict inter-department traffic.
- Add a server and test network services.
- Expand the network with additional departments.

## Author

Created as part of my hands-on cybersecurity and networking learning journey.
