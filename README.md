# LionraForge

### Enterprise IT Infrastructure & Cybersecurity Home Lab

LionraForge is my hands-on project where I'm building and managing the IT infrastructure of an enterprise SaaS company environment, designed around two locations in Dublin and Limerick.

I'm starting from the ground up, designing the network, configuring Windows and Linux servers, setting up Active Directory, and practising everyday IT support through realistic tickets and troubleshooting scenarios.

As the project develops, I'll introduce firewalls, intrusion detection and prevention, SIEM monitoring, and controlled attack simulations to understand how these technologies work together in an enterprise environment.

I'm documenting the process step by step, explaining what I'm doing, why I've chosen a particular approach, how I configure and test it, and what I learn along the way. My aim is to build practical experience, demonstrate my skills, and provide a resource that others can follow to build a similar environment.

## The Company

LionraForge is built around the vision of a growing technology company that develops and hosts SaaS applications for business customers.

I'm designing its IT infrastructure to support two locations in Ireland: a headquarters in Dublin and a branch in Limerick. The enterprise model covers 100 employees across 10 departments, including Software Development, IT Support, DevOps, Finance, Human Resources and Cybersecurity.

My goal is to build and manage the infrastructure such an organisation needs to operate. This includes enterprise networking, Windows and Linux systems, Active Directory, shared resources, IT support, monitoring and security.

Both locations will have their own network infrastructure while operating as part of the same centrally managed environment.

As the project grows, I'll expand the infrastructure to include more advanced networking, cloud services, security monitoring and eventually a SaaS application developed and deployed as part of LionraForge.

I'm building and testing this environment in my own lab, using virtualisation and network simulation to reproduce enterprise systems and real-world technical challenges.

[Company model and department breakdown](docs/company/overview.md)

## Infrastructure Overview

I'm designing LionraForge as a multi-site enterprise network connecting the company's Dublin headquarters and Limerick branch.

Both offices will have their own network segments, Windows and Linux systems, and a local Active Directory domain controller. They'll share the same Active Directory domain (`ad.lionraforge.test`), allowing employees to use centrally managed accounts and access the company resources they're authorized to use.

I'll use VMware Workstation to run the virtual machines and GNS3 to build and configure the network infrastructure, including routers, switches, VLANs and inter-site connectivity.

The network will initially use static routing between the two offices. Later, I'll introduce OSPF, firewalls and a site-to-site VPN to practise more advanced networking and security configurations.

For day-to-day IT operations, I plan to use GLPI to manage support tickets and IT assets, along with Windows and Linux administration tools for troubleshooting, remote support and system maintenance.

As the infrastructure grows, I'll add centralized monitoring, IDS/IPS, a SIEM and an isolated attacker environment. This will allow me to simulate security incidents, investigate alerts and test how the company's security controls respond.

The project will start on two physical laptops, with virtual machines and network workloads distributed between them as resources allow. I'll expand the environment gradually, testing and documenting each part before introducing the next.

**Architecture status: Planned.** The Dublin and Limerick sites are modelled network locations within my lab, not claims of operational offices. A layered high-level diagram is part of the approved design but has not yet been committed as an editable diagram or image. The [architecture document](docs/architecture/README.md) records the current plan; diagrams will be added with their editable sources.

## Project Objectives

My main goal with LionraForge is to gain practical experience by building and managing an enterprise IT environment from scratch, rather than learning each technology separately.

I want to understand how different systems work together, what happens when something goes wrong, and how IT teams troubleshoot, maintain and secure those systems in real working environments.

Through this project, I aim to:

- **Build and manage enterprise infrastructure:** Design networks, configure routers and switches, deploy Windows and Linux servers, manage Active Directory, and connect two office locations.
- **Practise real IT support:** Simulate employee problems through GLPI tickets, investigate issues, provide remote support, manage devices and software, and document how problems are resolved.
- **Develop systems and network administration skills:** Work with DNS, DHCP, Group Policy, permissions, routing, backups, monitoring and automation.
- **Understand enterprise security:** Configure firewalls, IDS/IPS, endpoint monitoring and SIEM tools, then investigate security events across the infrastructure.
- **Practise offensive and defensive security:** Use an isolated attacker environment to simulate controlled attacks, study the resulting activity, evaluate detections and improve security controls.
- **Connect my programming experience with IT operations:** Develop scripts and automation tools, and eventually build and deploy a SaaS application within the environment.
- **Document and share what I learn:** Explain the design decisions, configurations, tests and troubleshooting steps so others can reproduce the labs and learn from them.

I'm approaching LionraForge from different roles as the environment grows, starting with IT Support and moving into Systems Administration, Networking and Security Operations.

I also want this project to serve as a portfolio of my practical work. Rather than simply listing the technologies I know, I want to demonstrate what I've configured, how I've tested it, the problems I've solved and what I've learned along the way.

## Project Roadmap & Progress

I'm building LionraForge in phases, starting with the core network and IT infrastructure before moving into everyday IT support, system administration and cybersecurity.

Each phase builds on the previous work. For example, I need a functioning network and Active Directory environment before I can realistically troubleshoot employee login problems, manage domain-joined workstations or investigate security events.

I'll document each stage as I work through it, including the configuration steps, tests, problems encountered and their solutions.

### Implementation Roadmap

| Phase | What I'll Build and Practise | Status |
|---|---|---|
| 01 — Lab Foundation | Prepare VMware Workstation, GNS3, virtual machines and the initial lab networking environment | Planned |
| 02 — Enterprise Networking | Build the Dublin and Limerick networks, configure VLANs, IP addressing, switching, inter-VLAN routing and initial inter-site connectivity | Planned |
| 03 — Active Directory & DNS | Deploy two domain controllers, configure `ad.lionraforge.test`, AD Sites, organizational units, users, groups and DNS | Planned |
| 04 — Workstation Management | Deploy Windows and Linux workstations, join supported systems to the domain, configure Group Policy and access permissions | Planned |
| 05 — Core IT Services | Configure DHCP, file sharing, Windows and Linux services, remote administration and basic backup and restore procedures | Planned |
| 06 — IT Helpdesk & Asset Management | Deploy GLPI, create support workflows, configure ticket categories and priorities, record assets and resolve simulated employee issues | Planned |
| 07 — IT Support Scenarios | Work through realistic tickets involving authentication, networking, permissions, software, printers and system failures | Planned |
| 08 — Linux Administration & Automation | Administer Linux systems, manage services and permissions, develop Bash and PowerShell scripts, and automate repetitive tasks | Planned |
| 09 — Network Security | Introduce firewalls, access-control rules, site-to-site VPN connectivity and more advanced routing | Planned |
| 10 — Infrastructure Monitoring | Deploy Zabbix, monitor servers and network devices, configure alerts and investigate performance or availability problems | Planned |
| 11 — Centralized Security Monitoring | Deploy Wazuh, collect Windows and Linux security events, configure Sysmon and begin investigating alerts | Planned |
| 12 — Network Detection | Introduce Suricata and Zeek, collect network telemetry, investigate suspicious traffic and develop detection rules | Planned |
| 13 — SOC & Incident Response | Simulate security incidents, investigate alerts, correlate evidence, document findings and practise response procedures | Planned |
| 14 — Purple Team Exercises | Use an isolated attacker environment to run controlled attack simulations, evaluate detections and improve security controls | Planned |
| 15 — Cloud, DevOps & SaaS Expansion | Extend selected services into the cloud, explore deployment pipelines, and develop, deploy and secure a business management SaaS application | Planned |

### Progress Tracking

I'll use four statuses to distinguish between work that's planned, being built, configured or fully tested:

- **Planned:** The phase has been designed but implementation hasn't started.
- **In Progress:** I'm actively working on the configuration, testing or troubleshooting.
- **Implemented:** The planned configuration has been completed but full verification or documentation is still pending.
- **Verified:** The implementation has been tested successfully and the results are documented.

Each phase will have its own documentation, including practical configuration guides, troubleshooting notes, evidence and links to relevant scripts or configuration files.

I'll also use GitHub Issues and GitHub Projects to track individual tasks, outstanding problems and progress throughout the project.

The roadmap is a working plan, not a fixed schedule. I'll update it as I gain experience, discover technical constraints or identify better ways to build the environment.

[Detailed roadmap](docs/roadmap.md)

## Technical Documentation

I'm documenting LionraForge as I build it, with the goal of making the project useful both as a record of my practical work and as a learning resource for anyone who wants to build a similar environment.

The documentation is organised in two ways: **chronologically**, so you can follow the infrastructure from the beginning, and **by technical subject**, so you can find the technologies or skills you're interested in.

### Follow the Labs Step by Step

Each implementation phase will contain practical labs explaining:

- **What I'm building:** The purpose of the lab and the problem it addresses.
- **Why I've chosen this approach:** The design decisions and alternatives considered.
- **How to reproduce it:** The configuration steps, commands and explanations.
- **How to verify it:** Tests to confirm that the configuration works as expected.
- **How to troubleshoot it:** Problems encountered, investigations and solutions.
- **Supporting evidence:** Relevant screenshots, configuration files, scripts and test results.

Labs will be organised in implementation order, starting with the environment setup and enterprise networking before progressing to systems administration, IT support and cybersecurity.

**Lab Guides:** [Lab documentation approach](labs/README.md) — individual lab guides will become available as labs are implemented and verified.

### Browse by Technical Subject

For readers interested in a particular technology or skill, I'll also maintain a technical index covering:

| Technical Area | Topics |
|---|---|
| Networking | VLANs, switching, routing, DNS, DHCP, VPN and network troubleshooting |
| Windows Server & Active Directory | Domain controllers, users, groups, Group Policy, permissions and replication |
| IT Support | GLPI, helpdesk tickets, remote support, endpoint troubleshooting and asset management |
| Linux Administration | Linux servers, services, permissions, file sharing and troubleshooting |
| Automation & Scripting | PowerShell, Bash, Python and administrative automation |
| Infrastructure Monitoring | System monitoring, alerts, availability and performance troubleshooting |
| Cybersecurity & SOC | Firewalls, IDS/IPS, SIEM, log analysis, detection and incident response |
| Cloud & DevOps | Cloud infrastructure, application deployment, CI/CD and SaaS development |

**Technical Subject Index:** Planned — links will be added as relevant documentation becomes available.

### Additional Documentation

Alongside the practical guides, I'll maintain several supporting resources:

| Resource | Purpose |
|---|---|
| [Architecture & Design](docs/architecture/README.md) | Network diagrams, IP addressing plans, infrastructure components and system relationships |
| [Architecture Decision Records (ADRs)](docs/decisions/README.md) | Important technical decisions, alternatives, trade-offs and reasons for each choice |
| Troubleshooting Journal | Actual problems encountered during implementation, their investigation and resolution |
| Skills & Evidence Index | A central reference connecting practical skills to completed labs, configurations and verified results |
| Scripts & Configurations | Reusable scripts, configuration examples and supporting technical files |
| References & Learning Resources | Official documentation and other resources used during the project |
| Changelog | Significant changes, improvements and completed milestones |

### Documentation Principles

I want the documentation to reflect what I've actually done, not just describe how a technology is supposed to work.

I'll distinguish between planned work, completed configurations and verified results. When something doesn't work, I'll document the actual troubleshooting process rather than presenting everything as if it worked perfectly the first time.

The guides will be updated as I improve the environment, while Git history will preserve earlier versions and the troubleshooting journals will record genuine problems and their solutions.

As the project grows, I'll add links from this section to the relevant guides, indexes and supporting documents.