# Troubleshooting Journal — Lab 01

This journal documents the technical problems I encountered while preparing the LionraForge virtualization and networking environment.

## LF-P01-L01-001 — Virtual Machine Cannot Ping Windows Host

**Category:** Networking / Windows Firewall  
**Affected systems:** Aero Windows host and TEST-VM01  
**Status:** Resolved

### Problem

After installing Ubuntu Server, the virtual machine successfully obtained an IPv4 address from VMware DHCP but could not ping the Windows host.

Both systems were connected through VMware's VMnet1 host-only network.

| System | IP address |
|---|---|
| Windows host | 192.168.108.1/24 |
| Ubuntu Server | 192.168.108.130/24 |

### Initial Test

From Ubuntu:

```bash
ping -c 4 192.168.108.1
```

Result:

```text
4 packets transmitted, 0 received, 100% packet loss
```

### Investigation

I first checked the Ubuntu network interface:

```bash
ip -br a
```

The interface was operational and had received a valid IPv4 address.

I then tested communication in the opposite direction from Windows:

```powershell
ping 192.168.108.130
```

The Windows host successfully received replies from Ubuntu.

This indicated that the virtual network was functioning and suggested that Windows Firewall was blocking incoming ICMP Echo Requests.

### Resolution

Rather than disabling Windows Firewall, I created a restricted inbound firewall rule through PowerShell:

```powershell
New-NetFirewallRule `
    -DisplayName "LionraForge - Allow ICMPv4 on VMnet1" `
    -Direction Inbound `
    -Protocol ICMPv4 `
    -IcmpType 8 `
    -Action Allow `
    -InterfaceAlias "VMware Network Adapter VMnet1" `
    -RemoteAddress 192.168.108.0/24 `
    -LocalAddress 192.168.108.1 `
    -Profile Any
```

This rule allows incoming ICMPv4 Echo Requests through VMnet1 from the local virtual subnet without disabling firewall protection.

### Verification

I repeated the original test from Ubuntu:

```bash
ping -c 4 192.168.108.1
```

Result:

```text
4 packets transmitted, 4 received, 0% packet loss
```

Communication between the host and the virtual machine was successful in both directions.

### Rollback

If the rule is no longer required, it can be removed using:

```powershell
Remove-NetFirewallRule `
    -DisplayName "LionraForge - Allow ICMPv4 on VMnet1"
```

### What I Learned

A failed ping does not necessarily mean that the network is unavailable. Testing communication in both directions helped me identify the firewall as the likely cause and resolve the issue without disabling a security control.

---

## LF-P01-L01-002 — GNS3 Cannot Locate VMware vmrun

**Category:** Application Support / Software Compatibility  
**Status:** Resolved

### Environment

| Component | Version |
|---|---|
| Windows | Windows 11 Home |
| VMware Workstation Pro | 26H1u1 |
| GNS3 | 2.2.61 |

### Problem

While configuring GNS3 to use the imported GNS3 VM, I encountered the following error:

```text
Error while executing VMware command:
Could not find VMware vmrun, please make sure it is installed
```

### Investigation

I checked whether Windows could locate the VMware executable:

```powershell
where.exe vmrun
```

Result:

```text
INFO: Could not find files for the given pattern(s).
```

However, the executable was present in the VMware installation directory.

I tested it directly:

```powershell
& "C:\Program Files\VMware\VMware Workstation\vmrun.exe" list
```

Result:

```text
Total running VMs: 0
```

This confirmed that the executable was installed and working correctly.

VMware Workstation 26H1 introduced a native 64-bit installation path, which can cause compatibility issues with older GNS3 executable detection logic.

| Previous installation path | Current installation path |
|---|---|
| C:\Program Files (x86)\VMware\VMware Workstation | C:\Program Files\VMware\VMware Workstation |

### Resolution

I added the VMware installation directory to the Windows user PATH environment variable while preserving the existing entries.

```powershell
$p = "C:\Program Files\VMware\VMware Workstation"
$old = [Environment]::GetEnvironmentVariable("Path","User")

if (($old -split ";") -notcontains $p) {
    [Environment]::SetEnvironmentVariable(
        "Path",
        ("$old;$p").Trim(";"),
        "User"
    )
}
```

I restarted Windows and launched GNS3 normally.

### Verification

- GNS3 successfully detected the imported virtual machine.
- The GNS3 VM started automatically.
- Both GNS3 servers appeared online.
- KVM support was available.
- The initial network topology operated successfully.

### What I Learned

An application may fail to locate a dependency even when it is installed correctly. Understanding executable paths, environment variables and software compatibility helped me identify and resolve the problem without reinstalling either application.

### References

- [GNS3 VMware compatibility issue #3845](https://github.com/GNS3/gns3-gui/issues/3845)
- [GNS3 compatibility fix — Pull Request #3846](https://github.com/GNS3/gns3-gui/pull/3846)
