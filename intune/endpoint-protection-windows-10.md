---
# required metadata

title: Add endpoint protection on Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: On Windows 10 devices, use or configure endpoint protection settings to enable Windows Defender feature includes, Application Guard, Firewall, SmartScreen, encryption and bitlocker, Exploit Guard, Application Control, Security Center, and security on local devices in Microsoft Intune.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/21/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: ilwu
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Endpoint protection settings for Windows 10 (and later) in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

The endpoint protection profile lets you control security features on Windows 10 devices, like BitLocker and Windows Defender.

Use the information in this article to create endpoint protection profiles. To configure Windows Defender Antivirus, see [Windows 10 Device Restrictions](device-restrictions-windows-10.md#windows-defender-antivirus). 

> [!NOTE]
> These settings are not supported on the Home edition of Windows 10.

## Windows Defender Application Guard

While using Microsoft Edge, Windows Defender Application Guard protects your environment from sites that haven’t been defined as trusted by your organization. When users visit sites that aren’t listed in your isolated network boundary, the sites are opened in a virtual browsing session in Hyper-V. Trusted sites are defined by a network boundary, which can be configured in Device Configuration. 

Application Guard is only available for Windows 10 (64-bit) devices. Using this profile installs a Win32 component to activate Application Guard.

- **Application Guard**: Open unapproved sites in a Hyper-V virtualized browsing container.
- **Clipboard behavior**: Choose what copy/paste actions are allowed between the local PC and the Application Guard virtual browser.
- **External content on enterprise sites**: Block content from unapproved websites from loading.
- **Print from virtual browser**: Allow PDF, XPS, local, and/or network printers to print content from the virtual browser.
- **Collect logs**: Collect logs for events that occur within an Application Guard browsing session.
- **Retain user-generated browser data**: Save user data (such as passwords, favorites, and cookies) that is created during an Application Guard virtual browsing session.
- **Graphics acceleration**: Load graphics-intensive websites faster when working within the Application Guard virtual browsing session. Websites load faster by enabling access to a virtual graphics processing unit.
- **Download files to host file system**: Allow users to download files from the virtualized browser onto the host operating system.

## Windows Defender Firewall

### Global settings

These settings are applicable to all network types.

- **File Transfer Protocol**: Block stateful FTP.
- **Security association idle time before deletion**: Security associations are deleted after no network traffic is detected for *n* seconds.
- **Pre-shared key encoding**: Encode preshared keys using UTF-8.
- **IPsec exemptions**: Configure specific traffic to be exempt from IPsec, including **Neighbor discover IPv6 ICMP type-codes**, **ICMP**, **Router discover IPv6 ICMP type-codes**, and **Both IPv4 and IPv6 DHCP network traffic**.
- **Certificate revocation list verification**: Set a value for how certificate revocation list verification is enforced, including **Disable CRL verification**, **Fail CRL verification on revoked certificate only**, and **Fail CRL verification on any error encountered**.
- **Opportunistically match authentication set per keying module**: Set keying modules to ignore the entire authentication set if they do not support all authentication suites in that set.
- **Packet queuing**: Enter how software scaling on the receive side is enabled for the encrypted receive and clear text forward for the IPsec tunnel gateway scenario. This setting ensures that packet order is preserved.

### Network settings

These settings are applicable to specific network types, including **Domain (workplace) network**, **Private (discoverable) network**, and **Public (non-discoverable) network**.

#### General settings

- **Windows Defender Firewall**: Enable this setting to block network traffic.
- **Stealth mode**: Block Firewall from operating in stealth mode. Blocking stealth mode allows you to also block **IPsec secured packet exemption**.
- **Shielded**: Enabling this setting and the firewall setting will block all incoming traffic.
- **Unicast responses to multicast broadcasts**: Block unicast responses to multicast broadcasts. Typically, you don't want to receive unicast responses to multicast or broadcast messages. These responses can indicate a denial of service (DOS) attack, or an attacker attempting to probe a known live computer.
- **Inbound notifications**: Block notifications from displaying to users when an application is blocked from listening on a port.
- **Default action for inbound connections**: Block the default action that firewall performs on inbound connections.

#### Rule merging

- **Authorized application Windows Defender Firewall rules from the local store**: Apply authorized firewall rules in the local store to be recognized and enforced.
- **Global port Windows Defender Firewall rules from the local store**: Apply global port firewall rules in the local store to be recognized and enforced.
- **Windows Defender Firewall rules from the local store**: Apply global firewall rules in the local store to be recognized and enforced.
- **IPsec rules from the local store**: Apply connection security rules from the local store, regardless of schema or connection security rule versions.

## Windows Defender SmartScreen settings

- **SmartScreen for apps and files**: Enable Windows SmartScreen for file execution, and running apps.
- **Unverified files execution**: Block the end user from running files that have not been verified by Windows SmartScreen.

## Windows Encryption

### Windows Settings

The following two settings apply to all versions of Windows 10:

- **Encrypt devices**: If enabled, users are prompted to enable device encryption. Additionally, they are asked to confirm that encryption from another provider has not been enabled. If Windows encryption is turned on while another encryption method is active, the device might become unstable.
- **Encrypt storage card**: Enable this setting to encrypt any removable storage cards used by the device.


### BitLocker base settings

Base settings are universal BitLocker settings for all types of data drives. BitLocker Group Policy settings manage what drive encryption tasks or configuration options the end user can modify across all types of data drives.

- **Warning for other disk encryption**: Disable the warning prompt for other disk encryption on end users' machines.
- **Configure encryption methods**: Enable this setting to configure encryption algorithms for operating system, data, and removable drives.
  - **Encryption for operating system drives**: Choose the encryption method for operating system drives. We recommend you use the XTS-AES algorithm.
  - **Encryption for fixed data-drives**: Choose the encryption method for fixed (built-in) data drives. We recommend you use the XTS-AES algorithm.
  - **Encryption for removable data-drives**: Choose the encryption method for removable data drives. If the removable drive is used with devices that are not running Windows 10, we recommend you use the AES-CBC algorithm.

### BitLocker OS drive settings

These settings apply specifically to operating system data drives.

- **Additional authentication at startup**: Configure authentication requirements for computer startup, including the use of Trusted Platform Module (TPM).
  - **BitLocker with non-compatible TPM chip**
  - **Compatible TPM startup**: Choose to allow, not allow, or require the TPM chip.
  - **Compatible TPM startup PIN**: Choose to allow, not allow, or require using a startup PIN with the TPM chip.
  - **Compatible TPM startup key**: Choose to allow, not allow, or require using a startup key with the TPM chip.
  - **Compatible TPM startup key and PIN**: Choose to allow, not allow, or require using a startup key and PIN with the TPM chip.
- **Minimum PIN Length**: Enable this setting to configure a minimum length for the TPM startup PIN.
  - **Minimum characters**: Enter the number of characters required for the startup PIN from **4**-**20**.
- **OS drive recovery**: Enable this setting to control how BitLocker-protected operating system drives are recovered when the required start-up information is not available.
  - **Certificate-based data recovery agent**: Enable this setting if you want data recovery agents to be able to be used with BitLocker-protected operating system drives.
  - **User creation of recovery password**: Choose if users are allowed, required, or not allowed to generate a 48-digit recovery password.
  - **User creation of recovery key**: Choose if users are allowed, required, or not allowed to generate a 256-bit recovery key.
  - **Recovery options in the BitLocker setup wizard**: Enable this setting to prevent users from seeing, or changing recovery options when they turn on BitLocker.
  - **Save BitLocker recovery information to AD DS**: Enables the storage of BitLocker recovery information in Active Directory.
  - **BitLocker recovery Information stored to AD DS**: Configure what parts of BitLocker recovery information are stored in Active Directory. Choose from:
    - **Backup recovery passwords and key packages**
    - **Backup recovery passwords only**
  - **Store recovery information in AD DS before enabling BitLocker**: Enable this setting to stop users from turning on BitLocker unless the device is domain-joined, and BitLocker recovery information is successfully stored in Active Directory.
- **Pre-boot recovery message and URL**: Enable this setting to configure the message and URL that are displayed on the pre-boot key recovery screen.
  - **Pre-boot recovery message**: Configure how the pre-boot recovery message displays to users. Choose from:
    - **Use default recovery message and URL**
    - **Use empty recovery message and URL**
    - **Use custom recovery message**
    - **Use custom recovery URL**

### BitLocker fixed data-drive settings

- **Write access to fixed data-drive not protected by BitLocker**: If enabled, BitLocker protection must be enabled on all fixed, or built-in data drives to be able to write to them.
- **Fixed drive recovery**: Enable this setting to control how BitLocker-protected fixed drives are recovered when the required start-up information is not available.
  - **Data recovery agent**: Enable this setting if you want data recovery agents to be used with BitLocker-protected fixed drives.
  - **User creation of recovery password**: Configure whether users are allowed, required, or not allowed to generate a 48-digit recovery password.  
  - **User creation of recovery key**: Configure whether users are allowed, required, or not allowed to generate a 256-bit recovery key.
  - **Recovery options in the BitLocker setup wizard**: Enable this setting to prevent users from seeing, or changing recovery options when they turn on BitLocker.
  - **Save BitLocker recovery information to AD DS**: Enables the storage of BitLocker recovery information in Active Directory.
  - **BitLocker recovery Information to AD DS**: Configure what parts of BitLocker recovery information are stored in Active Directory. Choose from:
    - **Backup recovery passwords and key packages**
    - **Backup recovery passwords only**
  - **Store recovery information in AD DS before enabling BitLocker**: Enable this setting to stop users from turning on BitLocker unless the device is domain-joined, and BitLocker recovery information has been successfully stored in Active Directory.

### BitLocker removable data-drive settings

- **Write access to removable data-drive not protected by BitLocker**: Specify whether BitLocker encryption is required for removable storage drives.
  - **Write access to devices configured in another organization**: Specify whether removable data drives that belong to another organization can be written to.

## Windows Defender Exploit Guard

Use [Windows Defender Exploit Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard) to manage and reduce the attack surface of apps used by your employees.

### Attack Surface Reduction

- **Flag credential stealing from the Windows local security authority subsystem**

Help [prevent actions and apps](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) that are typically used by exploit-seeking malware to infect machines.

#### Rules to prevent Office Macro threats

Block Office apps from taking the following actions:

- **Office apps injecting into other processes (no exceptions)**
- **Office apps/macros creating executable content**
- **Office apps launching child processes**
- **Win32 imports from Office macro code**

#### Rules to prevent script threats

Block the following to help prevent against script threats:

- **Obfuscated js/vbs/ps/macro code**
- **js/vbs executing payload downloaded from Internet (no exceptions)**
- **Process creation from PSExec and WMI commands**
- **Untrusted and unsigned processes that run from USB**
- **Executables that don’t meet a prevalence, age, or trusted list criteria**

#### Rules to prevent email threats

Block the following to help prevent email threats:

- **Execution of executable content (exe, dll, ps, js, vbs, etc.) dropped from email (webmail/mail client) (no exceptions)**

#### Rules to protect against ransomware
- **Advanced ransomware protection**

> [!TIP]
> [Reduce attack surfaces with Windows Defender Exploit Guard](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) provides more details on these rules.

#### Attack Surface Reduction exceptions

- **Files and folder to exclude from attack surface reduction rules**: Import/add a list of locations to exclude from the configured rules.

### Controlled folder access

Help protect valuable data from malicious apps and threats, such as ransomware.

- **Folder protection**: Protect files and folders from unwanted changes by malicious apps. You can import a **List of apps that have access to protected folders** or add them manually. You can also add a **List of additional folders that need to be protected** with an upload or adding them manually.

### Network filtering

Block outbound connections from any app to low reputation IP/domains.

### Exploit protection

Block **User editing of the exploit protection interface** by uploading an XML file that allows you to configure memory, control flow, and policy restrictions. The settings in the XML file can be used to block an application from exploits.

To enable exploit protection, create an XML file representing the system and application mitigation settings of your choice. You can do so using one of two methods:

 1. PowerShell: Use one or more of the Get-ProcessMitigation, Set-ProcessMitigation, and ConvertTo-ProcessMitigationPolicy PowerShell cmdlets. The cmdlets configure mitigation settings, and export an XML representation of them.

 2. Windows Defender Security Center UI: In the Windows Defender Security Center, click on App & browser control and then scroll to the bottom of the resulting screen to find Exploit Protection. First, use the System settings and Program settings tabs to configure mitigation settings. Then, find the Export settings link at the bottom of the screen to export an XML representation of them.

## Windows Defender Application Control

Use **Application control code integrity policies** to choose additional apps that must be audited by, or can be trusted to run by Windows Defender Application Control. Windows components and all apps from Windows store are automatically trusted to run.

Applications are not blocked when running in **audit only** mode. **Audit only** mode logs all events in local client logs.

Once enabled, Application Control can only be disabled by changing the mode from **Enforce** to **Audit only**. Changing the mode from **Enforce** to **Not Configured** results in Application Control continuing to be enforced on assigned devices.

## Windows Defender Credential Guard
Windows Defender Credential Guard protects against credential theft attacks. It isolates secrets so that only privileged system software can access them.

The **Credential Guard** settings include:

- **Disabled**: Turns off Credential Guard remotely, if it was previously turned on with the **Enabled without UEFI lock** option.​
- **Enabled with UEFI lock**: Ensures that Credential Guard can't be disabled remotely by using a registry key or Group Policy.

    > [!NOTE]
    > If you use this setting, and then later want to disable Credential Guard, you must set the Group Policy to **Disabled**. And, physically clear the UEFI configuration information from each computer. As long as the UEFI configuration persists, Credential Guard is enabled.​

- **Enabled without UEFI lock**: Allows Credential Guard to be disabled remotely by using Group Policy. The devices that use this setting must be running Windows 10 version 1511 and newer.​

When you enable Credential Guard, the following required features are also enabled:

- **Virtualization-based Security** (VBS): Turns on during the next reboot. Virtualization-based security uses the Windows Hypervisor to provide support for security services.
- **Secure Boot with Directory Memory Access**: Turns on VBS with Secure Boot and direct memory access (DMA) protections. DMA protections require hardware support, and are only enabled on correctly configured devices.

## Windows Defender Security Center

The Windows Defender Security Center app operates as a separate app or process from each of the individual features. It displays notifications through the Action Center. It acts as a collector or single place to see the status and perform some configuration for each of the features. Find out more in the [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) docs.

#### Windows Defender Security Center app and notifications

Block end-user access to the various areas of the Windows Defender Security Center app. Hiding a section will also block related notifications.

- **Virus and threat protection**
- **Device performance and health**
- **Firewall and network protection**
- **App and browser control**
- **Family options**
- **Notifications from the displayed areas of app**: Choose which notifications to display to end users. Non-critical notifications include summaries of Windows Defender Antivirus activity, including notifications when scans have completed. All other notifications are considered critical.

#### IT contact Information

Provide IT contact information to appear in the Windows Defender Security Center app and the app notifications. You can choose to **Display in app and in notifications**, **Display only in app**, **Display only in notifications**, or **Don't display**. You must enter the **IT organization name**, and at least one of the following contact options:

- **IT department phone number or Skype ID**
- **IT department email address**
- **IT support website URL**

## Local device security options

Use these options to configure the local security settings on Windows 10 devices.

### Accounts

- **Add new Microsoft accounts**: Prevent users from adding new Microsoft accounts to this computer.
- **Remote log on without password**: Enable local accounts that are not password-protected to log on from locations other than the physical device.

#### Admin

- **Local admin account**: Determine whether the local Administrator account is enabled or disabled.
- **Rename admin account**: Define a different account name to be associated with the security identifier (SID) for the Administrator account.

#### Guest

- **Guest account**: Determine if the Guest account is enabled or disabled.
- **Rename guest account**: Define a different account name to be associated with the security identifier (SID) for the Guest account.

### Devices

- **Undock device without logon**: Prevent a portable computer from being undocked without having to log in.
- **Install printer drivers for shared printers**: Restrict installing printer drivers as part of connecting to a shared printer to admins only.
- **Restrict CD-ROM access to local active user**: Enabling this setting allows only interactively logged on user to access CD-ROM media
- **Format and eject removable media**: Define who is allowed to format and eject removable NTFS media:
  - **Not configured**
  - **Administrators and Power Users**
  - **Administrators and Interactive Users**

### Interactive Logon

- **Minutes of lock screen inactivity until screen saver activates**: Define maximum minutes of inactivity on the interactive desktop’s login screen until the screen saver runs.
- **Require CTRL+ALT+DEL to log on**: Require CTRL+ALT+DEL to be pressed before a user can log on.
- **Smart card removal behavior**: Determines what happens when the smart card for a logged-on user is removed from the smart card reader. Your options:

  - **Lock Workstation​**: The workstation is locked when the smart card is removed. This option allows users to leave the area, take their smart card with them, and still maintain a protected session.​
  - **Force Logoff​**: The user is automatically logged off when the smart card is removed.​
  - **Disconnect if a Remote Desktop Services session**: Removal of the smart card disconnects the session without logging the user off. This option allows the user to insert the smart card and resume the session later, or at another smart card reader-equipped computer, without having to sign in again. If the session is local, this policy functions identically to Lock Workstation.

    [LocalPoliciesSecurity options](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-smartcardremovalbehavior) provides more details.

#### Display

- **User information on lock screen**: Configure the user information that is displayed when the session is locked. If not configured, user display name, domain, and username are shown.
  - **Not configured**: User display name, domain, and user name
  - **User display name, domain and user name**
  - **User display name only**
  - **Do not display user information**
- **Hide last signed-in user**: Don't display the username of the last person who signed in on this device.
- **Hide username at sign-in**: Don't display the username of the person signing in to this device after credentials are entered, and before the device’s desktop is shown.
- **Logon message title**: Set message title for users attempting to log in.
- **Logon message text**: Set message text for users attempting to log in.

### Network access and security

- **Anonymous access to Named Pipes and Shares**: **Not configured** (default) restricts anonymous access to share and Named Pipe settings. Applies to the settings that can be accessed anonymously.
- **Anonymous enumeration of SAM accounts**: **Allow** anonymous users to enumerate the SAM accounts. Windows allows anonymous users enumerate the names of domain accounts and network shares.
- **Anonymous enumeration of SAM accounts and shares**: **Not configured** (default) means anonymous users can enumerate the names of domain accounts and network shares. To prevent anonymous enumeration of SAM accounts and shares, set to **Block**.
- **LAN Manager hash value stored on password change**: At the next password change, choose to **Allow** the LAN Manager (LM) to store the hash value for the new password. When set to **Not configured** (default), the hash value is not stored.
- **PKU2U authentication requests**: **Block** PKU2U authentication requests to the device to use online identities. **Not configured** (default) allows these requests.
- **Restrict remote RPC connections to SAM**: **Allow** the default Security Descriptor Definition Language string to deny users and groups to make remote calls to the SAM. **Not configured** (default) the default Security Descriptor Definition Language string to allow users and groups to make remote calls to the SAM.
  - **Security descriptor**

### Recovery console and shutdown

- **Clear virtual memory pagefile when shutting down**: Clear the virtual memory pagefile when the device is powered down.
- **Shutdown without logon**: Block the option to shut down the computer from the Windows logon screen. In this case, users must be able to log on to the computer successfully and before they can perform a system shutdown.

### User account control

- **UIA integrity without secure location**: Enable apps from unsecure locations in the file system to run with UIAccess integrity level.
- **Virtualize file and registry write failures to per-user locations**: Determine if app write failures are redirected to defined registry and file system locations. Or, cause the app to fail.
- **Only elevate executable files that are signed and validated**: Enforce PKI certification path validation for a given executable file before it is permitted to run.

#### UIA elevation prompt behavior settings

- **Elevation prompt for admins**: Define the behavior of the elevation prompt for admins in Admin Approval Mode:
  - **Elevate without prompting**
  - **Prompt for credentials on the secure desktop**
  - **Prompt for consent on the secure desktop**
  - **Prompt for credentials**
  - **Prompt for consent**
  - **Not configured**: Prompt for consent for non-Windows binaries
- **Elevation prompt for standard users**: Define the behavior of the elevation prompt for standard users:
  - **Automatically deny elevation requests**
  - **Prompt for credentials on the secure desktop**
  - **Not configured**: Prompt for credentials
- **Route elevation prompts to user’s interactive desktop**: Enable all elevation requests to go to the interactive user's desktop rather than the secure desktop. Prompt behavior policy settings for admins and standard users are used.
- **Elevated prompt for app installations**: App installations requiring elevated privileges will prompt for admin credentials.
- **UIA elevation prompt without secure desktop**: Allow UIAccess apps to prompt for elevation without using the secure desktop.

#### Admin Approval Mode settings

- **Admin approval Mode for Built-in Administrator**: Defines whether the built-in admin account uses Admin Approval Mode or runs all apps with full admin privileges.
- **Run all admins in Admin Approval Mode**: Define whether Admin Approval Mode and all UAC policy settings are enabled.

### Microsoft Network Client

- **Digitally sign communications (if server agrees)**: Determines if the SMB client attempts to negotiate SMB packet signing. When enabled (Not configured), the Microsoft network client asks the server to perform SMB packet signing upon session setup. If packet signing is enabled on the server, packet signing is negotiated. If this policy is disabled, the SMB client never negotiates SMB packet signing.
- **Send unencrypted password to third-party SMB servers**: When enabled, the Server Message Block (SMB) redirector is allowed to send plaintext passwords to non-Microsoft SMB servers that don't support password encryption during authentication.

### Microsoft Network Server

- **Digitally sign communications (if client agrees)**: Determines if the SMB server negotiates SMB packet signing with clients that request it. When enabled, the Microsoft network server negotiates SMB packet signing as requested by the client. That is, if packet signing is enabled on the client, packet signing is negotiated. When **Not configured** or disabled (default), the SMB client never negotiates SMB packet signing.
- **Digitally sign communications (always)**: Determines if packet signing is required by the SMB server component. When enabled, the Microsoft network server doesn't communicate with a Microsoft network client unless that client agrees to perform SMB packet signing. When **Not configured** disabled (Default), SMB packet signing is negotiated between the client and server.

## Next steps

To assign this profile to groups, see [How to assign device profiles](device-profile-assign.md).