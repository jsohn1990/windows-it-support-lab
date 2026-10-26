# Windows IT Support Home Lab

## Overview

This home lab simulates a small business IT environment for practicing Windows administration, Microsoft 365 administration, device management, and help desk troubleshooting.

The environment uses Oracle VirtualBox to run Windows Server and Windows 11 virtual machines.

## Technologies

- Windows Server 2025 and Active Directory Domain Services (AD DS)
- DNS, Group Policy, and SMB file sharing
- Microsoft Entra ID and Entra Cloud Sync
- Microsoft Intune
- Microsoft 365 administration
- Jira Service Management
- PowerShell and Windows administrative tools

## Lab Environment

- **Domain controller:** Windows Server 2025 (`DC01`)
- **Active Directory domain:** `corp.example.test`
- **Client:** Domain-joined Windows 11 virtual machine
- **Identity:** On-premises Active Directory synchronized with Microsoft Entra ID
- **Device management:** Microsoft Intune

## Completed Exercises

- Configured Active Directory users, organizational units, and security groups.
- Joined a Windows 11 workstation to the Active Directory domain.
- Configured Group Policy and shared-folder access permissions.
- Synchronized Active Directory identities with Microsoft Entra ID.
- Hybrid-joined a Windows 11 workstation to Microsoft Entra ID.
- Enrolled the workstation in Microsoft Intune.
- Deployed and verified a five-minute inactivity-lock policy using Intune.
- Created and administered Microsoft 365 user accounts and security groups.
- Practiced password resets and account access management.
- Investigated and resolved a shared-folder access issue involving NTFS permissions and Active Directory group membership.
- Documented simulated help desk requests and resolutions in Jira Service Management.

## Purpose

The project provides a practical environment for learning and documenting common entry-level IT support and Windows administration tasks.
