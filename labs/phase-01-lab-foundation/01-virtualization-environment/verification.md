# Verification Results — Lab 01

**Lab:** Virtualization and Network Lab Foundation  
**Verification date:** 26 November 2026  
**Status:** Verified within the foundation acceptance scope

## 1. Acceptance Criteria

I defined the foundation lab as successful when:

- The physical host could support the virtualization environment.
- VMware Workstation could run a Linux virtual machine.
- The host and guest could communicate over a private virtual network.
- GNS3 could start and communicate with its virtual appliance.
- Nested virtualization was available.
- A simple GNS3 network could successfully exchange traffic.

## 2. Host Preparation

| Test | Expected result | Actual result | Status |
|---|---|---|---|
| Hardware virtualization | Enabled | Enabled | Pass |
| Physical memory | Sufficient for initial lab | 15.8 GB | Pass |
| Disk condition | Healthy | Both disks reported Healthy | Pass |
| Storage availability | Sufficient for initial VMs | 492.5 GB free on D: at inspection | Pass |
| Windows hypervisor inspection | Compatible starting environment | HypervisorPresent: False | Pass |
| Lab directories | Required folders exist | Four directories created | Pass |

## 3. VMware Workstation

| Test | Expected result | Actual result | Status |
|---|---|---|---|
| Application startup | Application opens | VMware Workstation Pro launched | Pass |
| Installed version | Version identifiable | 26H1u1 | Pass |
| Supporting services | Required services running | Authorization, DHCP, NAT and USB services running | Pass |
| Virtual adapters | VMnet1 and VMnet8 available | Both adapters Up | Pass |
| Virtual network configuration | Host-only and NAT networks present | Both configured | Pass |
| Default VM directory | Dedicated lab directory configured | D:\LionraForge\Virtual-Machines | Configured |

## 4. Ubuntu Virtual Machine

| Test | Expected result | Actual result | Status |
|---|---|---|---|
| VM startup | Guest operating system boots | Ubuntu booted successfully | Pass |
| User authentication | Successful console login | Successful | Pass |
| Hostname | test-vm01 | test-vm01 | Pass |
| Virtualization detection | VMware | vmware | Pass |
| Administrative access | sudo works | sudo whoami returned root | Pass |
| Virtual CPU allocation | 2 vCPUs | 2 detected | Pass |
| RAM allocation | 2 GB configured | 2 GB configured; 1.6 GiB usable | Pass |
| Virtual disk | 25 GB | 25 GB detected | Pass |
| LVM and filesystems | Configured and mounted | LVM and ext4 operational | Pass |

## 5. VMware Network Connectivity

| Test | Expected result | Actual result | Status |
|---|---|---|---|
| DHCP assignment | Valid VMnet1 address | 192.168.108.130/24 | Pass |
| Windows to Ubuntu | ICMP replies | Successful | Pass |
| Ubuntu to Windows — initial | ICMP replies | 100% packet loss | Fail |
| Ubuntu to Windows — after resolution | ICMP replies | 4/4 replies | Pass |
| Windows Firewall | Retained | Enabled with scoped ICMP rule | Pass |

The initial failed test was resolved. See the [troubleshooting journal](troubleshooting.md) for the investigation.

## 6. GNS3 Integration

| Test | Expected result | Actual result | Status |
|---|---|---|---|
| GNS3 application | Installed and accessible | Version 2.2.61 | Pass |
| GNS3 VM | Imported and operational | VM version 0.21.0 | Pass |
| VMware command execution | vmrun executes successfully | Successful direct execution | Pass |
| Automatic VM startup | GNS3 starts VMware appliance | Successful | Pass |
| Nested virtualization | KVM available | True | Pass |
| Local controller | Online | Green indicator | Pass |
| GNS3 VM server | Online | Green indicator | Pass |
| Permanent executable discovery | Normal application launch works | Both servers online after normal launch | Pass |
| Project directory | Dedicated D: directory configured | D:\LionraForge\GNS3-Projects | Configured |
| Project creation | New project opens | Successful | Pass |

## 7. GNS3 Network Test

### Topology

One Ethernet switch and two VPCS endpoints connected within an isolated test network.

| Device | IP address |
|---|---|
| PC1 | 10.255.1.10/24 |
| PC2 | 10.255.1.20/24 |

### Test Procedure

From PC1:

```text
ping 10.255.1.20
```

### Actual Results

| Sequence | Response time | TTL |
|---|---:|---:|
| 1 | 2.181 ms | 64 |
| 2 | 1.891 ms | 64 |
| 3 | 1.969 ms | 64 |
| 4 | 1.956 ms | 64 |
| 5 | 1.908 ms | 64 |

| Metric | Result |
|---|---|
| Requests | 5 |
| Successful replies | 5 |
| Packet loss | 0% |
| Mean round-trip time | 1.981 ms |
| Test status | Pass |

## 8. Evidence

I captured screenshots of the VMware installation, virtual network configuration, Ubuntu deployment, network troubleshooting, GNS3 VM information, server connectivity and the working test topology.

Consolidated text evidence:

- [Host preparation inventory](evidence/host-preparation/host-inventory.txt)
- [VMware verification](evidence/vmware/vmware-verification.txt)
- [GNS3 compatibility diagnostics](evidence/gns3/vmrun-diagnostics.txt)

Some command results and configuration confirmations were recorded as text during implementation rather than captured as screenshots. The ISO integrity check was completed, but the exact checksum output was not retained in this record. Selected screenshots are prepared for a separate upload.

## 9. Deferred Tests

The following tests are outside the required acceptance scope for this initial foundation milestone:

- VMware NAT and external internet connectivity.
- Snapshot creation and restoration.
- Independent backup and recovery.
- Detailed firmware inspection.
- KVM-based router and firewall appliance execution.
- Verification of physical VM file locations.
- Enterprise VLAN isolation and routing.
- Cross-host virtualization networking.

These will be introduced when required by subsequent labs.

KVM availability has been confirmed, but execution of a nested KVM-based network appliance has not yet been tested.

## 10. Final Result

The required foundation acceptance tests passed.

I have a working VMware and GNS3 environment capable of running a Linux virtual machine and a basic simulated network.

The environment is ready for the next stage: enterprise network implementation.
