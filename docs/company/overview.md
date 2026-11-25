# Company Vision and Operating Model

**Status:** Planned enterprise model.

LionraForge is the enterprise IT environment I'm designing and building in my home lab. Its business model is a growing technology company that develops and hosts SaaS applications for business customers. The model gives me realistic requirements for network services, identity management, support operations and cybersecurity.

## Sites and workforce

| Site | Role | Modelled employees |
|---|---|---:|
| Dublin | Headquarters | 60 |
| Limerick | Branch | 40 |
| **Total** | | **100** |

These are **modelled office locations**. The employee counts define the account, permission and support scenarios I intend to reproduce; they do not require 100 running virtual machines.

## Department distribution

| Department | Dublin | Limerick | Total |
|---|---:|---:|---:|
| Management | 4 | 2 | 6 |
| Software Development | 18 | 14 | 32 |
| Quality Assurance | 7 | 5 | 12 |
| IT Support & Infrastructure | 6 | 4 | 10 |
| DevOps | 5 | 3 | 8 |
| Human Resources | 3 | 2 | 5 |
| Finance & Accounting | 4 | 2 | 6 |
| Sales & Marketing | 5 | 3 | 8 |
| Customer Support | 5 | 3 | 8 |
| Cybersecurity / SOC | 3 | 2 | 5 |
| **Total** | **60** | **40** | **100** |

## Business and IT needs

I am designing the environment to support staff identities, Windows and Linux workstations, segmented office networks, internal servers, file sharing, access permissions, remote administration, IT support tickets, inventory, backup, monitoring and security investigations.

The SaaS product's exact functionality has deliberately been left open. I plan to develop and deploy a real application at a later stage, once the underlying infrastructure is established.

## How this model will be used

The company model will shape the organisational units, employee accounts, groups, VLANs, server roles and simulated service requests. When I work through a support ticket or a SOC case, I'll make clear that the scenario is simulated and distinguish it from real implementation results.

For the implementation sequence, see the [roadmap](../roadmap.md). For the network and system plan, see [architecture](../architecture/README.md).