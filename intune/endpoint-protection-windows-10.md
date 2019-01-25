---
# required metadata
title: Protection settings for Windows 10 devices in Microsoft Intune - Azure | Microsoft Docs
description: On Windows 10 devices, use or configure endpoint protection settings to enable Windows Defender feature includes, Application Guard, Firewall, SmartScreen, encryption and bitlocker, Exploit Guard, Application Control, Security Center, and security on local devices in Microsoft Intune.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/26/2018
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
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure; seodec18

---

# Windows 10 (and later) settings to protect devices using Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune includes many settings to help protect your devices. This article describes all the settings you can enable and configure in Windows 10 and newer devices. These settings are created in an endpoint protection configuration profile in Intune to control security, including BitLocker and Windows Defender.

To configure Windows Defender Antivirus, see [Windows 10 device restrictions](device-restrictions-windows-10.md#windows-defender-antivirus).

## Before you begin

[Create an endpoint protection device configuration profile](endpoint-protection-configure.md).

## Windows Defender Application Guard

Supported on the following Windows 10 editions:

- Enterprise
- Professional

While using Microsoft Edge, Windows Defender Application Guard protects your environment from sites that aren't trusted by your organization. When users visit sites that aren’t listed in your isolated network boundary, the sites open in a Hyper-V virtual browsing session. Trusted sites are defined by a network boundary, which are configured in Device Configuration.

Application Guard is only available for Windows 10 (64-bit) devices. Using this profile installs a Win32 component to activate Application Guard.

- **Application Guard**: **Enable** to turn on this feature, which opens unapproved sites in a Hyper-V virtualized browsing container. **Not configured** (default) means that any site (approved and unapproved) opens on the device.
- **Clipboard behavior**: Choose what copy/paste actions are allowed between the local PC and the Application Guard virtual browser.
- **External content on enterprise sites**: **Block** content from unapproved websites from loading. **Not configured** (default) means that non-enterprise sites can open on the device.
- **Print from virtual browser**: Choose **Allow** so PDF, XPS, local, and network printers can print content from the virtual browser. **Not configured** (default) disables all print features.
- **Collect logs**: **Allow** to collect logs for events that occur within an Application Guard browsing session. **Not configured** (default) doesn't collect any logs within the browsing session.
- **Retain user-generated browser data**: **Allow** saves user data (such as passwords, favorites, and cookies) that's created during an Application Guard virtual browsing session. **Not configured** (default) discards user-downloaded files and data when the device restarts, or when a user signs out.
- **Graphics acceleration**: Choose **Enable** to load graphic-intensive websites and video faster by getting access to a virtual graphics processing unit. **Not configured** (default) uses the device's CPU for graphics; it doesn't use the virtual graphics processing unit.
- **Download files to host file system**: **Enable** so users download files from the virtualized browser onto the host operating system. **Not configured** (default) keeps the files local on the device, and doesn't download files to the host file system.

## Windows Defender Firewall

Supported on the following Windows 10 editions:
- Home
- Professional
- Business
- Enterprise
- Education
- Mobile
- Mobile Enterprise

### Global settings

These settings are applicable to all network types.

- **File Transfer Protocol**: **Block** to disable stateful FTP. When **Not configured** (default), the firewall does stateful FTP filtering to allow secondary connections.
- **Security association idle time before deletion**: Security associations are deleted after no network traffic is detected for *n* seconds. Enter an idle time in seconds.
- **Pre-shared key encoding**: Choose **Enable** to use preshared key encoding using UTF-8. **Not configured** (default) uses the local store value.
- **IPsec exemptions**: Configure specific traffic to be exempt from IPsec, including:
  - **Neighbor discover IPv6 ICMP type-codes**
  - **ICMP**
  - **Router discover IPv6 ICMP type-codes**
  - **Both IPv4 and IPv6 DHCP network traffic**
- **Certificate revocation list verification**: Choose how the device verifies the certificate revocation list. Options include **Disable CRL verification**, **Fail CRL verification on revoked certificate only**, and **Fail CRL verification on any error encountered**.
- **Opportunistically match authentication set per keying module**: **Enable** so keying modules MUST ignore only the authentication suites that they don’t support. When **Not configured**, keying modules MUST ignore the entire authentication set if they don't support all of the authentication suites specified in the set.
- **Packet queuing**: Enter how software scaling on the receive side is enabled for the encrypted receive and clear text forward for the IPsec tunnel gateway scenario. This setting confirms the packet order is preserved.

### Network settings

These settings are applicable to specific network types, including **Domain (workplace) network**, **Private (discoverable) network**, and **Public (non-discoverable) network**.

#### General settings

- **Windows Defender Firewall**: Choose **Enable** to turn on the firewall, and advanced security. **Not configured** (default) allows all network traffic, regardless of any other policy settings.
- **Stealth mode**: **Block** the firewall from operating in stealth mode. Blocking stealth mode allows you to also block **IPsec secured packet exemption**. **Not configured** (default) operates the firewall in stealth mode, which helps prevent responses to probing requests.
- **Shielded**: **Block** turns off this feature. **Not configured** (default) enables this setting. When this setting and the Windows Defender Firewall are turned on, then all incoming traffic is blocked, regardless of any other policy settings.
- **Unicast responses to multicast broadcasts**: When set to **Block**, it disables unicast responses to multicast broadcasts. Typically, you don't want to receive unicast responses to multicast or broadcast messages. These responses can indicate a denial of service (DOS) attack, or an attacker trying to probe a known live computer. **Not configured** (default) enables this setting.
- **Inbound notifications**: When set to **Block**, it hides notifications to users when an app is blocked from listening on a port. **Not configured** (default) enables this setting, and may show a notification to users when an app is blocked from listening on a port.
- **Default action for inbound connections**: When set to **Block**, the default firewall action isn't run on inbound connections. When set to **Not configured** (default), the default firewall action is run on inbound connections.

#### Rule merging

- **Authorized application Windows Defender Firewall rules from the local store**: Choose **Enable** to apply firewall rules in the local store so they're recognized and enforced. When **Not configured** (default), the authorized application firewall rules in the local store are ignored and not enforced.
- **Global port Windows Defender Firewall rules from the local store**: Choose **Enable** to apply global port firewall rules in the local store to be recognized and enforced. When **Not configured** (default), the global port firewall rules in the local store are ignored and not enforced.
- **Windows Defender Firewall rules from the local store**: Choose **Enable** to apply firewall rules in the local store to be recognized and enforced. When **Not configured** (default), the firewall rules from the local store are ignored and not enforced.
- **IPsec rules from the local store**: Choose **Enable** to apply connection security rules from the local store, regardless of schema or connection security rule versions. When **Not configured** (default), the connection security rules from the local store are ignored and not enforced, regardless of the schema version and connection security rule version.

## Windows Defender SmartScreen settings

Supported on the following Windows 10 editions with Microsoft Edge installed:
- Home
- Professional
- Business
- Enterprise
- Education
- Mobile
- Mobile Enterprise

**Settings**:

- **SmartScreen for apps and files**: **Enable** Windows SmartScreen for file execution, and running apps. SmartScreen is a cloud-based anti-phishing and anti-malware component. **Not configured** (default) disables SmartScreen.
- **Unverified files execution**: **Block** end users from running files that haven't been verified by Windows SmartScreen. **Not configured** (default) disables this feature, and allows end users to run files that haven't been verified.

## Windows Encryption

### Windows Settings

Supported on the following Windows 10 editions:

- Professional (starting in 1809)
- Business
- Enterprise
- Education
- Mobile
- Mobile Enterprise

**Settings**:

- **Encrypt devices**: **Require** to prompt users to enable device encryption. Depending on the Windows edition and system configuration, users may be asked:  
  - To confirm that encryption from another provider isn't enabled
  - Be required to turn off Bitlocker Drive Encryption, and then turn Bitlocker back on
    
    If Windows encryption is turned on while another encryption method is active, the device might become unstable. 
- **Encrypt storage card (mobile only)**: **Require** to encrypt any removable storage cards used by the device. **Not configured** (default) doesn't require storage card encryption, and doesn't prompt the user to turn it on. This setting only applies to Windows 10 mobile devices.

### BitLocker base settings

Supported on the following Windows 10 editions:

- Enterprise
- Education
- Mobile
- Mobile Enterprise
- Professional

Base settings are universal BitLocker settings for all types of data drives. These settings manage what drive encryption tasks or configuration options the end user can modify across all types of data drives.

- **Warning for other disk encryption**: Select **Block** to disable the warning prompt if another disk encryption service is on the device. **Not configured** (default) allows the warning to be shown.
- **Configure encryption methods**: **Enable** this setting to configure encryption algorithms for operating system, data, and removable drives. When **Not configured** (default), BitLocker uses XTS-AES 128 bit as the default encryption method, or uses the encryption method specified by any setup script.
  - **Encryption for operating system drives**: Choose the encryption method for operating system drives. We recommend you use the XTS-AES algorithm.
  - **Encryption for fixed data-drives**: Choose the encryption method for fixed (built-in) data drives. We recommend you use the XTS-AES algorithm.
  - **Encryption for removable data-drives**: Choose the encryption method for removable data drives. If the removable drive is used with devices that aren't running Windows 10, then we recommend you use the AES-CBC algorithm.

### BitLocker OS drive settings
Supported on the following Windows 10 editions:

- Enterprise
- Education
- Mobile
- Mobile Enterprise
- Professional

These settings apply specifically to operating system data drives.

- **Additional authentication at startup**: Select **Require** to configure the authentication requirements for computer startup, including the use of Trusted Platform Module (TPM). Select **Not configured** (default) to configure only basic options on devices with a TPM.
  - **BitLocker with non-compatible TPM chip**: **Block** (disable) using BitLocker when a device doesn't have a compatible TPM chip. When **Not configured**, users can use BitLocker without a compatible TPM chip. BitLocker may require a password or a startup key.
  - **Compatible TPM startup**: Choose to allow, not allow, or require the TPM chip.
  - **Compatible TPM startup PIN**: Choose to allow, not allow, or require using a startup PIN with the TPM chip. Enabling a startup PIN requires interaction from the end user. 
  - **Compatible TPM startup key**: Choose to allow, not allow, or require using a startup key with the TPM chip. Enabling a startup key requires interaction from the end user. 
  - **Compatible TPM startup key and PIN**: Choose to allow, not allow, or require using a startup key and PIN with the TPM chip. Enabling startup key and PIN requires interaction from the end user.
- **Minimum PIN Length**: **Enable** this setting to configure a minimum length for the TPM startup PIN. When **Not configured** (default), users can configure a startup PIN of any length between 6 and 20 digits.
  - **Minimum characters**: Enter the number of characters required for the startup PIN from **4**-**20**.
- **OS drive recovery**: **Enable** this setting to control how BitLocker-protected operating system drives recover when the required start-up information isn't available. When **Not configured** (default), the default recovery options are supported for BitLocker recovery. By default, a DRA is allowed, the recovery options are chosen by the user, including the recovery password and recovery key, and recovery information isn't backed up to AD DS.
  - **Certificate-based data recovery agent**: When set to **Block**, you can't use data recovery agent with BitLocker-protected OS drives. Set to **Not configured** (default) to enable this setting, which allows data recovery agents to be used with BitLocker-protected operating system drives.
  - **User creation of recovery password**: Choose if users are allowed, required, or not allowed to generate a 48-digit recovery password.
  - **User creation of recovery key**: Choose if users are allowed, required, or not allowed to generate a 256-bit recovery key.
  - **Recovery options in the BitLocker setup wizard**: Set to **Block** so users can't see and change the recovery options. When set to **Not configured** (default), users can see and change the recovery options when they turn on BitLocker.
  - **Save BitLocker recovery information to AD DS**: Choose **Enable** to store the BitLocker recovery information to Azure Active Directory (AAD). When **Not configured** (default), the recovery information isn't stored in AAD.
  - **BitLocker recovery Information stored to AD DS**: Configure what parts of BitLocker recovery information are stored in Azure AD. Choose from:
    - **Backup recovery passwords and key packages**
    - **Backup recovery passwords only**
  - **Store recovery information in AD DS before enabling BitLocker**: **Require** this setting to stop users from turning on BitLocker unless the BitLocker recovery information is successfully stored in Azure Active Directory (AD). **Not configured** (default) allows users to turn on BitLocker, even if recovery information isn't successfully stored in Azure AD.
- **Pre-boot recovery message and URL**: **Enable** this setting to configure the message and URL that are displayed on the pre-boot key recovery screen. **Not configured** (default) disables this feature.
  - **Pre-boot recovery message**: Configure how the pre-boot recovery message displays to users. Choose from:
    - **Use default recovery message and URL**
    - **Use empty recovery message and URL**
    - **Use custom recovery message**
    - **Use custom recovery URL**

### BitLocker fixed data-drive settings

Supported on the following Windows 10 editions:

- Enterprise
- Education
- Mobile
- Mobile Enterprise
- Professional

**Settings**:

- **Write access to fixed data-drive not protected by BitLocker**: Set to **Block** to give read-only access to data drives that aren't BitLocker-protected. When **Not configured** (default), there's read and write access to data drives that aren't BitLocker-protected.
- **Fixed drive recovery**: **Enable** this setting to control how BitLocker-protected fixed drives recover when the required start-up information isn't available. **Not configured** (default) disables this feature.
  - **Data recovery agent**: **Block** the use of data recovery agent with BitLocker-protected fixed drives Policy Editor. **Not configured** (default) enables using data recovery agents with BitLocker-protected fixed drives.
  - **User creation of recovery password**: Configure whether users are allowed, required, or not allowed to generate a 48-digit recovery password.  
  - **User creation of recovery key**: Configure whether users are allowed, required, or not allowed to generate a 256-bit recovery key.
  - **Recovery options in the BitLocker setup wizard**: Set to **Block** so users can't see and change the recovery options. When set to **Not configured** (default), users can see and change the recovery options when they turn on BitLocker.
  - **Save BitLocker recovery information to AD DS**: Choose **Enable** to store the BitLocker recovery information in Azure Active Directory (Azure AD). When **Not configured** (default), the recovery information isn't stored in Azure AD.
  - **BitLocker recovery Information to AD DS**: Configure what parts of BitLocker recovery information are stored in Azure AD. Your options:
    - **Backup recovery passwords and key packages**
    - **Backup recovery passwords only**
  - **Store recovery information in AD DS before enabling BitLocker**: **Require** this setting to stop users from turning on BitLocker unless the BitLocker recovery information is successfully stored in Azure AD. **Not configured** (default) allows users to turn on BitLocker, even if recovery information is not successfully stored in Azure AD.

### BitLocker removable data-drive settings

Supported on the following Windows 10 editions:

- Enterprise
- Education
- Mobile
- Mobile Enterprise
- Professional

**Settings**:

- **Write access to removable data-drive not protected by BitLocker**: Set to **Block** to give read-only access to data drives that aren't BitLocker-protected. When **Not configured** (default), there's read and write access to data drives that aren't BitLocker-protected.
  - **Write access to devices configured in another organization**: **Block** allows write access to devices configured in another organization. **Not configured** (default) denies write access.

## Windows Defender Exploit Guard

Supported on the following Windows 10 editions:

- Home
- Professional
- Business
- Enterprise
- Education
- Mobile
- Mobile Enterprise

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

#### Rules to protect against Ransomware
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

To use exploit protection, create an XML file that includes the system and application mitigation settings you want. There are two methods:

 1. PowerShell: Use one or more of the Get-ProcessMitigation, Set-ProcessMitigation, and ConvertTo-ProcessMitigationPolicy PowerShell cmdlets. The cmdlets configure mitigation settings, and export an XML representation of them.

 2. Windows Defender Security Center UI: In the Windows Defender Security Center, click on App & browser control and then scroll to the bottom of the resulting screen to find Exploit Protection. First, use the System settings and Program settings tabs to configure mitigation settings. Then, find the Export settings link at the bottom of the screen to export an XML representation of them.

Block **User editing of the exploit protection interface** by uploading an XML file that allows you to configure memory, control flow, and policy restrictions. The settings in the XML file can be used to block an application from exploits. **Not configured** (default) doesn't push out a custom configuration. 

## Windows Defender Application Control

Supported on the following Windows 10 editions:

**Mobile Device Management (MDM)**: 
- Professional
- Business
- Enterprise
- Education
- Mobile
- Mobile Enterprise

**Group policy management**: 
- Enterprise

Use **Application control code integrity policies** to choose additional apps that are audited, or are trusted to run by Windows Defender Application Control. Windows components and all apps from the Windows store are automatically trusted to run.

Applications aren't blocked when running in **audit only** mode. **Audit only** mode logs all events in local client logs.

Once enabled, Application Control can only be disabled by changing the mode from **Enforce** to **Audit only**. Changing the mode from **Enforce** to **Not Configured** results in Application Control continuing to be enforced on assigned devices.

## Windows Defender Credential Guard

Supported on the following Windows 10 editions:

- Enterprise

Windows Defender Credential Guard protects against credential theft attacks. It isolates secrets so that only privileged system software can access them.

The **Credential Guard** settings include:

- **Disable**: Turns off Credential Guard remotely, if it was previously turned on with the **Enabled without UEFI lock** option.​

- **Enable with UEFI lock**: Credential Guard can't be disabled remotely by using a registry key or group policy.

    > [!NOTE]
    > If you use this setting, and then later want to disable Credential Guard, you must set the Group Policy to **Disabled**. And, physically clear the UEFI configuration information from each computer. As long as the UEFI configuration persists, Credential Guard is enabled.​

- **Enable without UEFI lock**: Allows Credential Guard to be disabled remotely by using Group Policy. The devices that use this setting must be running Windows 10 version 1511 and newer.​

When you enable Credential Guard, the following required features are also enabled:

- **Virtualization-based Security** (VBS): Turns on during the next reboot. Virtualization-based security uses the Windows Hypervisor to provide support for security services.
- **Secure Boot with Directory Memory Access**: Turns on VBS with Secure Boot and direct memory access (DMA) protections. DMA protections require hardware support, and are only enabled on correctly configured devices.

## Windows Defender Security Center

Supported on the following Windows 10 editions:

- Home
- Professional
- Business
- Enterprise
- Education
- Mobile
- Mobile Enterprise

Windows Defender Security Center operates as a separate app or process from each of the individual features. It displays notifications through the Action Center. It acts as a collector or single place to see the status and run some configuration for each of the features. Find out more in the [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) docs.

#### Windows Defender Security Center app and notifications

Block end-user access to the various areas of the Windows Defender Security Center app. Hiding a section also blocks related notifications.

- **Virus and threat protection**
- **Device performance and health**
- **Firewall and network protection**
- **App and browser control**
- **Family options**
- **Notifications from the displayed areas of app**: Choose which notifications to display to end users. Non-critical notifications include summaries of Windows Defender Antivirus activity, including notifications when scans have completed. All other notifications are considered critical.

#### IT contact Information

Provide IT contact information to appear in the Windows Defender Security Center app and the app notifications. You can choose to **Display in app and in notifications**, **Display only in app**, **Display only in notifications**, or **Don't display**. Enter the **IT organization name**, and at least one of the following contact options:

- **IT department phone number or Skype ID**
- **IT department email address**
- **IT support website URL**

## Local device security options

Supported on the following Windows 10 editions:
 
- Home
- Professional
- Business
- Enterprise
- Education

Use these options to configure the local security settings on Windows 10 devices.

### Accounts

- **Add new Microsoft accounts**: Set to **Block** to prevent users from adding new Microsoft accounts to the device. When set to **Not configured** (default), users can use Microsoft accounts on the device.
- **Remote log on without password**: **Enable** allows local accounts with blank passwords to sign in using the device's keyboard. **Not configured** (default) allows local accounts with blank passwords to sign in from locations other than the physical device.

#### Admin

- **Local admin account**: Set to **Enabled** to allow the local administrator account. Set to **Not configured** (default) to disable the local administrator account.
- **Rename admin account**: Define a different account name to be associated with the security identifier (SID) for the Administrator account.

#### Guest

- **Guest account**: Set to **Enabled** to allow the local guest account. Set to **Not configured** (default) to disable the local guest account.
- **Rename guest account**: Define a different account name to be associated with the security identifier (SID) for the Guest account.

### Devices

- **Undock device without logon**: Set to **Block** so users can press a docked portable device's physical eject button to safely undock the device. **Not configured** (default) requires the user to sign in to the device, and receive permission to undock the device.
- **Install printer drivers for shared printers**: When **Enabled**, any user can install a printer driver as part of connecting to a shared printer. When **Not configured** (default), only Administrators can install a printer driver as part of connecting to a shared printer.
- **Restrict CD-ROM access to local active user**: When **Enabled**, only the interactively logged-on user can use the CD-ROM media. If this policy is enabled, and no one is logged on interactively, then the CD-ROM is accessed over the network. When **Not configured** (default), anyone has access to the CD-ROM.
- **Format and eject removable media**: Define who is allowed to format and eject removable NTFS media:
  - **Not configured**
  - **Administrators**
  - **Administrators and Power Users**
  - **Administrators and Interactive Users**

### Interactive Logon

- **Minutes of lock screen inactivity until screen saver activates**: Enter the maximum minutes of inactivity on the interactive desktop’s sign in screen until the screen saver starts.
- **Require CTRL+ALT+DEL to log on**: Set to **Enable** so pressing CTRL+ALT+DEL isn't required for users to sign in. Set to **Not configured** (default) to require users to press CTRL+ALT+DEL before logging on to Windows.
- **Smart card removal behavior**: Determines what happens when the smart card for a logged-on user is removed from the smart card reader. Your options:

  - **Lock Workstation**: The workstation is locked when the smart card is removed. This option allows users to leave the area, take their smart card with them, and still maintain a protected session.​
  - **Force Logoff**: The user is automatically logged off when the smart card is removed.
  - **Disconnect if a Remote Desktop Services session**: Removal of the smart card disconnects the session without logging off the user. This option allows the user to insert the smart card and resume the session later, or at another smart card reader-equipped computer, without having to sign in again. If the session is local, this policy functions identically to Lock Workstation.

    [LocalPoliciesSecurity options](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-smartcardremovalbehavior) provides more details.

#### Display

- **User information on lock screen**: Configure the user information that is displayed when the session is locked. If not configured, user display name, domain, and username are shown.
  - **Not configured**
  - **User display name, domain, and user name**
  - **User display name only**
  - **Do not display user information**
- **Hide last signed-in user**: **Enable** hides the username. **Not configured** (default) shows the username.
- **Hide username at sign-in**: **Enable** hides the username. **Not configured** (default) shows the username.
- **Logon message title**: Set the message title for users signing in.
- **Logon message text**: Set the message text for users signing in.

### Network access and security

- **Anonymous access to Named Pipes and Shares**: **Not configured** (default) restricts anonymous access to share and Named Pipe settings. Applies to the settings that can be accessed anonymously.
- **Anonymous enumeration of SAM accounts**: **Allow** anonymous users to enumerate the SAM accounts. Windows allows anonymous users to enumerate the names of domain accounts and network shares.
- **Anonymous enumeration of SAM accounts and shares**: **Not configured** (default) means anonymous users can enumerate the names of domain accounts and network shares. To prevent anonymous enumeration of SAM accounts and shares, set to **Block**.
- **LAN Manager hash value stored on password change**: At the next password change, choose to **Allow** the LAN Manager (LM) to store the hash value for the new password. When set to **Not configured** (default), the hash value isn't stored.
- **PKU2U authentication requests**: **Block** PKU2U authentication requests to the device to use online identities. **Not configured** (default) allows these requests.
- **Restrict remote RPC connections to SAM**: **Allow** the default Security Descriptor Definition Language string to deny users and groups to make remote calls to the SAM. **Not configured** (default) the default Security Descriptor Definition Language string to allow users and groups to make remote calls to the SAM.
  - **Security descriptor**

### Recovery console and shutdown

- **Clear virtual memory pagefile when shutting down**: Set to **Enable** to clear the virtual memory pagefile when the device is powered down. **Not configured** doesn't clear the virtual memory.
- **Shut down without log on**: **Block** hides the shutdown option on the Windows sign in screen. Users must sign in to the device, and then shut down. **Not configured** (default) allows users to shut down the device from the Windows sign in screen.

### User account control

- **UIA integrity without secure location**: When set to **Enable**, apps in a secure location in the file system run only with UIAccess integrity. **Not configured** (default) enables apps to run with UIAccess integrity, even if the apps aren't in a secure location in the file system.
- **Virtualize file and registry write failures to per-user locations**: When set to **Block**, application write failures redirect at run time to defined user locations for the file system and registry. When set to **Not configured** (default), applications that write data to protected locations fail.
- **Only elevate executable files that are signed and validated**: Set to **Enabled** to enforce the PKI certification path validation for an executable file before it can run. Set to **Not configured** (default) to not enforce PKI certification path validation before an executable file can run.

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
- **Route elevation prompts to user’s interactive desktop**: **Enable** so all elevation requests go to the interactive user's desktop, not the secure desktop. Any prompt behavior policy settings for administrators and standard users are used. **Not configured** (default) forces all elevation requests go to the secure desktop, regardless of any prompt behavior policy settings for administrators and standard users.
- **Elevated prompt for app installations**: When set to **Block**, application installation packages aren't detected or prompted for elevation. When set to **Not configured** (default) and an application installation package requires elevated privileges, the user is prompted for an administrative user name and password.
- **UIA elevation prompt without secure desktop**: **Enable** allows UIAccess apps to prompt for elevation, without using the secure desktop. When **Not configured** (default), the elevation prompts use a secure desktop.

#### Admin Approval Mode settings

- **Admin approval Mode for Built-in Administrator**: **Enabled** allows the built-in Administrator account to use Admin Approval Mode. Any operation that requires elevation of privilege prompts the user to approve the operation. **Not configured** (default) runs all apps with full admin privileges.
- **Run all admins in Admin Approval Mode**: Set to **Block** to disable Admin Approval Mode and all related UAC policy settings. **Not configured** (default) enables Admin Approval Mode.

### Microsoft Network Client

- **Digitally sign communications (if server agrees)**: Determines if the SMB client negotiates SMB packet signing. When **Not configured** or enabled (default), the Microsoft network client asks the server to run SMB packet signing upon session setup. If packet signing is enabled on the server, packet signing is negotiated. If set to **Disable**, the SMB client never negotiates SMB packet signing.
- **Send unencrypted password to third-party SMB servers**: When set to **Enable**, the Server Message Block (SMB) redirector can send plaintext passwords to non-Microsoft SMB servers that don't support password encryption during authentication. When **Not configured** (default), the passwords are encrypted.

### Microsoft Network Server

- **Digitally sign communications (if client agrees)**: Determines if the SMB server negotiates SMB packet signing with clients that request it. When set to **Enable**, the Microsoft network server negotiates SMB packet signing as requested by the client. That is, if packet signing is enabled on the client, packet signing is negotiated. When **Not configured** or disabled (default), the SMB client never negotiates SMB packet signing.
- **Digitally sign communications (always)**: Determines if packet signing is required by the SMB server component. When set to **Enable**, the Microsoft network server doesn't communicate with a Microsoft network client unless that client agrees to SMB packet signing. When **Not configured** or disabled (default), SMB packet signing is negotiated between the client and server.

## Next steps

The profile is created, but it's not doing anything yet. Next, [assign the profile](device-profile-assign.md), and [monitor its status](device-profile-monitor.md).

Configure endpoint protections settings on [macOS](endpoint-protection-macos.md) devices.
