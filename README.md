<img width="827" height="485" alt="Screenshot 2026-11-05 181932" src="https://github.com/user-attachments/assets/9ce9c079-416b-473c-ac1e-4594675b5163" />

# CCNA Capstone Project: Global Logistics Network (GLN)

A 5-site enterprise network designed and configured in **Cisco Packet Tracer**. The project covers VLANs, trunking, Router-on-a-Stick, EIGRP, DHCP, DNS, ACLs and device hardening.

> Full project documentation: [CCNA-Project.pdf](CCNA-Project.pdf)

## Scenario
Global Logistics Network (GLN) is a fictional company with 5 locations. The goal was to design the topology, configure all devices and give full connectivity between all sites using dynamic routing.

## Topology
- 5 sites connected in a ring, joined by serial WAN links
- 5 routers, 5 Cisco 2960 switches
- 20+ end devices (2 PCs, 1 printer and 1 server per site)

| Site | Router | VLANs |
|------|--------|-------|
| HQ | R1-HQ | 10 Admin, 20 Finance |
| Branch A | R2-BrA | 30 Sales, 40 Support |
| Branch B | R3-BrB | 50 Marketing, 60 Dev |
| Warehouse | R4-Whse | 70 Inventory, 80 Shipping |
| Data Center | R5-DC | 90 Servers, 99 Management |

Each VLAN uses the subnet `192.168.<VLAN ID>.0/24`. WAN links use `10.0.0.0/30` subnets.

## What I configured
- **Basic setup:** hostnames, MOTD banner, enable secret, console and VTY passwords, password encryption, clock
- **Layer 2:** VLANs, access ports and trunk ports on all switches
- **Layer 3:** Router-on-a-Stick sub-interfaces for inter-VLAN routing, serial WAN interfaces with clock rate
- **Routing:** EIGRP (AS 100) with auto-summary disabled
- **Services:** DHCP pools on each router, DNS server in the data center hosting `www.gln.com`
- **Security:** standard ACL on R5-DC that blocks the Inventory VLAN from the data center servers

## Verification
- Ping between PCs at different sites
- `www.gln.com` opens from a browser on another site
- The Inventory VLAN cannot reach the data center servers, while all other VLANs can
- `show ip route` shows EIGRP routes
- `show vlan brief` shows the correct port assignments

## Tools
Cisco Packet Tracer

## Author
**Mariam Benyamin Gabriel**, Business Information Systems graduate, Suez Canal University
[LinkedIn](https://linkedin.com/in/mariambenyamin)
