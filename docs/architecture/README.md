# Architecture and Design

**Status: Planned.** This document records design decisions, not an implemented or verified environment.

I'm building a two-site enterprise IT lab using VMware Workstation for virtual machines and GNS3 for the simulated network. Dublin and Limerick are logical office sites in the company model. Hardware workloads can be distributed across the two physical laptops according to capacity rather than assigning one laptop permanently to each site.

## High-level layout

- **Dublin HQ:** local VLANs, user systems, Windows and Linux services, and domain controller `DC01-DUB`.
- **Limerick branch:** corresponding VLANs, user systems, services, and domain controller `DC02-LIM`.
- **Between sites:** initially a routed private connection using static routes; later OSPF, firewalls and a site-to-site VPN.
- **Shared identity:** one Active Directory forest/domain, `ad.lionraforge.test`, with both writable domain controllers providing AD DS and DNS.
- **Operations:** GLPI for service desk and asset management, with monitoring and security tooling added progressively.
- **Security:** isolated testing networks, later Wazuh, Sysmon, Suricata, Zeek and controlled SOC/purple-team exercises.

## VLAN and subnet plan

The same VLAN IDs are used at both sites, but each site has its own IP ranges.

| VLAN | Purpose | Dublin | Limerick |
|---:|---|---|---|
| 10 | IT Management | `10.10.10.0/24` | `10.20.10.0/24` |
| 20 | Employee Workstations | `10.10.20.0/24` | `10.20.20.0/24` |
| 30 | Development & QA | `10.10.30.0/24` | `10.20.30.0/24` |
| 40 | Internal Servers | `10.10.40.0/24` | `10.20.40.0/24` |
| 50 | SOC Monitoring | `10.10.50.0/24` | `10.20.50.0/24` |
| 60 | Guest / Untrusted | `10.10.60.0/24` | `10.20.60.0/24` |
| 70 | Security Testing | `10.10.70.0/24` | `10.20.70.0/24` |

## Planned design progression

1. Build initial virtual networks, VLANs and router-on-a-stick connectivity.
2. Connect the site networks with static routing; verify reachability and isolation.
3. Add two AD DS/DNS domain controllers and establish sites and replication.
4. Develop workstation, file services, DHCP and IT support operations.
5. Progress to OSPF, Layer 3 switching and firewall-managed traffic controls.
6. Add monitoring, network detection and isolated security testing.
7. Expand selected workloads toward cloud and SaaS hosting.

## Physical hosts and constraints

| Host | Known hardware | Proposed role |
|---|---|---|
| AMD laptop | Ryzen 7 5700U, 16 GB RAM | Initial VMware/GNS3 workloads |
| Gigabyte Aero 15 | Intel i7-9750H, 16 GB RAM | Additional VM/network workloads |

The final cross-host lab connectivity and isolation method has **not** been selected or tested. I will document the installed software versions, available storage and real resource use during Phase 01.

## Diagrams and verification

The architecture will use layered, editable diagrams: a simple project overview, detailed network topology and focused AD/security diagrams. Mermaid or diagrams.net source files and readable exports will be added when prepared and reviewed. A proposed diagram is not evidence of a functioning network.

Real configuration files, command outputs, connectivity tests, replication checks and troubleshooting notes will be linked to their labs only after implementation.

See the [implementation roadmap](../roadmap.md) and [ADR conventions](../decisions/README.md).