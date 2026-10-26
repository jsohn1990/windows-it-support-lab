# Troubleshooting: Finance Share Access Denied

## Problem

A simulated user, Alice, received an "Access is denied" error when attempting to open the Finance shared folder on the Windows Server domain controller.

## Environment

- Windows Server 2025 domain controller (`DC01`)
- Windows 11 domain-joined workstation
- Active Directory domain: `corp.example.test`
- SMB share: `\\DC01.corp.example.test\Finance`

## Investigation

1. Verified that the Windows 11 workstation could connect to the file server and enumerate its shared folders.
2. Confirmed that opening the Finance share returned "Access is denied."
3. Checked the share permissions, which granted Everyone Full Control.
4. Examined the NTFS permissions on `C:\Finance` and identified that the `Finance-Share-Access` security group had Modify permissions.
5. Checked Alice's Active Directory group membership and found that she belonged only to Domain Users.

## Resolution

1. Added Alice to the `Finance-Share-Access` security group in Active Directory.
2. Signed out and back in to refresh her Windows session.
3. When access remained denied, checked the user's security groups using `whoami /groups`.
4. Refreshed Kerberos tickets using `klist purge`.
5. Obtained a fresh file-server service ticket using `klist get cifs/DC01.corp.example.test`.
6. Retested access using `\\DC01.corp.example.test\Finance`.

The Finance share opened successfully after refreshing the Kerberos tickets.

## Outcome

Restored the user's access without weakening the folder's NTFS permissions. Documented the investigation and resolution in Jira Service Management as a simulated help desk ticket.
