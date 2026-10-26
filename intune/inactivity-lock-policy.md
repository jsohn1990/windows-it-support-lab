# Microsoft Intune: Five-Minute Inactivity Lock Policy

## Objective

Configure a Windows 11 workstation to lock automatically after five minutes of inactivity using Microsoft Intune.

## Environment

- Windows 11 virtual machine running in Oracle VirtualBox
- Windows Server 2025 Active Directory domain
- Microsoft Entra hybrid-joined workstation
- Microsoft Intune enrollment
- Microsoft 365 Business Premium trial

## Configuration

1. Opened Microsoft Intune admin center.
2. Navigated to **Devices → Configuration**.
3. Created a Windows Settings Catalog policy named `Lab - Inactivity Lock - 5 Minutes`.
4. Configured **Interactive Logon Machine Inactivity Limit** to `300` seconds.
5. Assigned the policy to **All devices**.
6. Created the policy and initiated a device sync.

## Verification

1. Confirmed that Intune reported the configuration policy as **Succeeded** for the Windows 11 VM.
2. Used PowerShell to check the Windows registry:

   `Get-ItemPropertyValue -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System' -Name InactivityTimeoutSecs`

3. Confirmed that Windows returned `300`.
4. Left the Windows 11 VM idle and verified that it locked automatically after five minutes.

## Outcome

Successfully deployed and verified a Windows configuration policy through Microsoft Intune, including confirmation in the admin center, registry verification, and functional testing.
