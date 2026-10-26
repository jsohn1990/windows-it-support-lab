# Home Lab Architecture

## Overview

This lab uses Oracle VirtualBox to simulate a small business Windows network connected to Microsoft cloud services.

## Infrastructure

| Component | Purpose |
|---|---|
| Windows 11 host | Physical computer running Oracle VirtualBox |
| Windows Server 2025 VM (`DC01`) | Active Directory domain controller, DNS, Group Policy, and SMB file sharing |
| Windows 11 VM (`DESKTOP-PFE59GR`) | Domain-joined workstation for IT support exercises |
| Microsoft Entra ID | Cloud identity and hybrid device registration |
| Microsoft Entra Cloud Sync | Synchronization of on-premises Active Directory identities and devices |
| Microsoft Intune | Cloud-based Windows device management |
| Microsoft 365 | Cloud user and group administration |
| Jira Service Management | Simulated help desk ticket management |

## Network Architecture

```text
Windows 11 Physical Host
│
└── Oracle VirtualBox
    │
    ├── Windows Server 2025 VM (DC01)
    │   ├── Active Directory Domain Services
    │   ├── DNS
    │   ├── Group Policy
    │   ├── SMB file shares
    │   └── Microsoft Entra provisioning agent
    │
    └── Windows 11 VM (DESKTOP-PFE59GR)
        ├── Joined to corp.example.test
        ├── Microsoft Entra hybrid joined
        └── Enrolled in Microsoft Intune

Microsoft Cloud
├── Microsoft Entra ID
├── Microsoft Intune
└── Microsoft 365

Jira Service Management
└── Simulated help desk tickets
```

## Identity and Device Management

Active Directory provides local domain authentication, group membership, and Group Policy. Microsoft Entra Cloud Sync synchronizes selected on-premises identities and devices to Microsoft Entra ID.

The Windows 11 workstation is joined to the local Active Directory domain and registered with Microsoft Entra ID through hybrid join. Group Policy initiates automatic Intune enrollment.

Intune manages Windows configuration policies, while Microsoft 365 provides cloud user and group administration.

## Network Details

- **Active Directory domain:** `corp.example.test`
- **Domain controller:** `DC01`
- **Domain controller IP:** `192.168.50.10`
- **Virtual network:** `192.168.50.0/24`
- **File share:** `\\DC01.corp.example.test\Finance`
