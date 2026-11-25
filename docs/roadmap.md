# Implementation Roadmap

**Current state:** All implementation phases are **Planned**. This roadmap establishes dependencies and learning goals; it is not a claim that any services are running.

| Phase | Area | Planned outcome | Status |
|---|---|---|---|
| 01 | Lab Foundation | VMware, GNS3, VMs and initial lab networking | Planned |
| 02 | Enterprise Networking | Dublin/Limerick VLANs, switching, inter-VLAN and inter-site routing | Planned |
| 03 | Active Directory & DNS | Two domain controllers, domain, sites, DNS, OUs, users and groups | Planned |
| 04 | Workstation Management | Windows/Linux workstations, domain management and Group Policy | Planned |
| 05 | Core IT Services | DHCP, file services, remote administration and tested backup/restore | Planned |
| 06 | IT Helpdesk & Asset Management | GLPI, workflows, ticketing and inventory | Planned |
| 07 | IT Support Scenarios | Investigated and documented simulated employee issues | Planned |
| 08 | Linux Administration & Automation | Linux management, Bash, PowerShell and repeatable automation | Planned |
| 09 | Network Security | Firewalls, access policies, VPN and advanced routing | Planned |
| 10 | Infrastructure Monitoring | Zabbix, monitoring and alert investigation | Planned |
| 11 | Centralized Security Monitoring | Wazuh, Sysmon and centralised security events | Planned |
| 12 | Network Detection | Suricata, Zeek, telemetry and network detections | Planned |
| 13 | SOC & Incident Response | Simulated investigations, analysis and response | Planned |
| 14 | Purple Team Exercises | Controlled tests, detection evaluation and improvements | Planned |
| 15 | Cloud, DevOps & SaaS Expansion | Selected cloud services, deployment pipelines and custom SaaS application | Planned |

## Status meanings

- **Planned:** Designed but implementation has not started.
- **In Progress:** Actively configuring, testing or troubleshooting.
- **Implemented:** Configuration is finished; verification or documentation is pending.
- **Verified:** Required tests passed and supporting results are documented.

## How the roadmap will evolve

I plan to break each phase into smaller labs with clear prerequisites and acceptance tests. Only tested work will be marked Verified. Basic security practices should be applied from the beginning even though advanced security phases come later. I will adjust the sequence when actual resource constraints or dependencies require it and record significant changes through Git history and decision records.

[Lab guide conventions](../labs/README.md) · [Architecture plan](architecture/README.md)