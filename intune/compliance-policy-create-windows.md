---
# required metadata

title: Windows 10 compliance settings in Microsoft Intune - Azure | Microsoft Docs
description: See a list of all the settings you can use when setting compliance for your Windows 10, Windows Holographic, and Surface Hub devices in Microsoft Intune. Check for compliance on the minimum and maximum operating system, set password restrictions and length, check for partner anti-virus (AV) solutions, enable encryption on data storage, and more.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology:

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Windows 10 and later settings to mark devices as compliant or not compliant using Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

This article lists and describes the different compliance settings you can configure on Windows 10 and later devices in Intune. As part of your mobile device management (MDM) solution, use these settings to require BitLocker, set a minimum and maximum operating system, set a risk level using Microsoft Defender Advanced Threat Protection (ATP), and more.

This feature applies to:

- Windows 10 and later
- Windows Holographic for Business
- Surface Hub

As an Intune administrator, use these compliance settings to help protect your organizational resources. To learn more about compliance policies, and what they do, see [get started with device compliance](device-compliance-get-started.md).

## Before you begin

[Create a compliance policy](create-compliance-policy.md#create-the-policy). For **Platform**, select **Windows 10 and later**.

## Device health

- **Require BitLocker**: When set to **Require**, the device can protect data stored on the drive from unauthorized access when the system is off, or hibernates. Windows BitLocker Drive Encryption encrypts all data stored on the Windows operating system volume. BitLocker uses the TPM to help protect the Windows operating system and user data. It also helps confirm that a computer isn't tampered with, even if its left unattended, lost, or stolen. If the computer is equipped with a compatible TPM, BitLocker uses the TPM to lock the encryption keys that protect the data. As a result, the keys can't be accessed until the TPM verifies the state of the computer.

  When set to **Not configured** (default), this setting isn't evaluated for compliance or non-compliance.

- **Require Secure Boot to be enabled on the device**: When set to **Require**, the system is forced to boot to a factory trusted state. When enabled, the core components used to boot the machine must have correct cryptographic signatures that are trusted by the organization that manufactured the device. The UEFI firmware verifies the signature before it lets the machine start. If any files are tampered with, which breaks their signature, the system doesn't boot.

  When set to **Not configured** (default), this setting isn't evaluated for compliance or non-compliance.

  > [!NOTE]
  > The **Require Secure Boot to be enabled on the device** setting is supported on some TPM 1.2 and 2.0 devices. For devices that don't support TPM 2.0 or later, the policy status in Intune shows as **Not Compliant**. For more information on supported versions, see  [Device Health Attestation](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation).

- **Require code integrity**: Code integrity is a feature that validates the integrity of a driver or system file each time it's loaded into memory. When set to **Require**, code integrity detects if an unsigned driver or system file is being loaded into the kernel. It also detects if a system file is changes by malicious software run by a user account with administrator privileges.

  When set to **Not configured** (default), this setting isn't evaluated for compliance or non-compliance.

More resources:

- [Health Attestation CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp) has details about how the HAS service works.
- [Support Tip: Using Device Health Attestation Settings as Part of Your Intune Compliance Policy](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643)

## Device properties

- **Minimum OS version**: Enter the minimum allowed version in the **major.minor.build.CU number** format. To get the correct value, open a command prompt, and type `ver`. The `ver` command returns the version in the following format:

  `Microsoft Windows [Version 10.0.17134.1]`

  When a device has an earlier version than the OS version you enter, it's reported as noncompliant. A link with information on how to upgrade is shown. The end user can choose to upgrade their device. After they upgrade, they can access company resources.

- **Maximum OS version**: Enter the maximum allowed version, in the **major.minor.build.revision number** format. To get the correct value, open a command prompt, and type `ver`. The `ver` command returns the version in the following format:

  `Microsoft Windows [Version 10.0.17134.1]`

  When a device is using an OS version later than the version entered, access to organization resources is blocked. The end user is asked to contact their IT administrator. The device can't access organization resources until the rule is changed to allow the OS version.

- **Minimum OS required for mobile devices**: Enter the minimum allowed version, in the major.minor.build number format.

  When a device has an earlier version that the OS version you enter, it's reported as noncompliant. A link with information on how to upgrade is shown. The end user can choose to upgrade their device. After they upgrade, they can access company resources.

- **Maximum OS required for mobile devices**: Enter the maximum allowed version, in the major.minor.build number.

  When a device is using an OS version later than the version entered, access to organization resources is blocked. The end user is asked to contact their IT administrator. The device can't access organization resources until the rule is changed to allow the OS version.

- **Valid operating system builds**: Enter a range for the acceptable operating systems versions, including a minimum and maximum. You can also **Export** a comma-separated values (CSV) file list of these acceptable OS build numbers.

## Configuration Manager Compliance

Applies only to co-managed devices running Windows 10 and later. Intune-only devices return a not available status.

- **Require device compliance from System Center Configuration Manager**: Choose **Require** to force all settings (configuration items) in System Center Configuration Manager to be compliant. 

  For example, you require all software updates to be installed on devices. In Configuration Manager, this requirement has the “Installed” state. If any programs on the device are in an unknown state, then the device is non-compliant in Intune.
  
  When **Not configured**, Intune doesn't check for any of the Configuration Manager settings for compliance.

## System security

### Password

- **Require a password to unlock mobile devices**: **Require** users to enter a password before they can access their device.
- **Simple passwords**: Set to **Block** so users can't create simple passwords, such as **1234** or **1111**. Set to **Not configured** to let users create passwords like **1234** or **1111**.
- **Password type**: Choose if a password should have only **Numeric** characters, or if there should be a mix of numbers and other characters (**Alphanumeric**).

  - **Number of non-alphanumeric characters in password**: If **Required password type** is set to **Alphanumeric**, this setting specifies the minimum number of character sets that the password must contain. The four character sets are:
    - Lowercase letters
    - Uppercase letters
    - Symbols
    - Numbers

    Setting a higher number requires the user to create a password that is more complex.

- **Minimum password length**: Enter the minimum number of digits or characters that the password must have.
- **Maximum minutes of inactivity before password is required**: Enter the idle time before the user must reenter their password.
- **Password expiration (days)**: Select the number of days before the password expires, and they must create a new one.
- **Number of previous passwords to prevent reuse**: Enter the number of previously used passwords that can't be used.
- **Require password when device returns from idle state (Mobile and Holographic)**: Force users to enter the password every time the device returns from an idle state.

  > [!IMPORTANT]
  > When the password requirement is changed on a Windows desktop, users are impacted the next time they sign in, as that’s when the device goes from idle to active. Users with passwords that meet the requirement are still prompted to change their passwords.

### Encryption

- **Encryption of data storage on a device**: Choose **Require** to encrypt data storage on your devices.

  > [!NOTE]
  > The **Encryption of data storage on a device** setting generically checks for the presence of encryption on the device. For a more robust encryption setting, consider using **Require BitLocker**, which leverages Windows Device Health Attestation to validate Bitlocker status at the TPM level.

### Device Security

- **Trusted Platform Module (TPM)**: When set to **Require**, Intune checks the version for compliance. The device is compliant if the TPM chip version is greater than 0 (zero). The device is not compliant if there isn't a TPM version on the device. When **Not configured**, Intune doesn't check the device for a TPM chip version.

  [DeviceStatus CSP - DeviceStatus/TPM/SpecificationVersion node](https://docs.microsoft.com/windows/client-management/mdm/devicestatus-csp)
  
- **Antivirus**: When set to **Require**, you can check compliance using antivirus solutions that are registered with [Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), such as Symantec and Microsoft Defender. When **Not configured**, Intune doesn't check for any AV solutions installed on the device.
- **Antispyware**: When set to **Require**, you can check compliance using antispyware solutions that are registered with [Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), such as Symantec and Microsoft Defender. When **Not configured**, Intune doesn't check for any antispyware solutions installed on the device.

## Microsoft Defender ATP

- **Require the device to be at or under the machine risk score**: Use this setting to take the risk assessment from your defense threat services as a condition for compliance. Choose the maximum allowed threat level:

  - **Clear**: This option is the most secure, as the device can't have any threats. If the device is detected as having any level of threats, it's evaluated as non-compliant.
  - **Low**: The device is evaluated as compliant if only low-level threats are present. Anything higher puts the device in a non-compliant status.
  - **Medium**: The device is evaluated as compliant if existing threats on the device are low or medium level. If the device is detected to have high-level threats, it's determined to be non-compliant.
  - **High**: This option is the least secure, and allows all threat levels. It may be useful if you're using this solution only for reporting purposes.
  
  To set up Microsoft Defender ATP (Advanced Threat Protection) as your defense threat service, see [Enable Microsoft Defender ATP with Conditional Access](advanced-threat-protection.md).

Select **OK** > **Create** to save your changes.

## Windows Holographic for Business

Windows Holographic for Business uses the **Windows 10 and later** platform. Windows Holographic for Business supports the following setting:

- **System Security** > **Encryption** > **Encryption of data storage on device**.

To verify device encryption on the Microsoft HoloLens, see [Verify device encryption](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## Surface Hub

Surface Hub uses the **Windows 10 and later** platform. Surface Hubs are supported for both compliance and Conditional Access. To enable these features on Surface Hubs, we recommend you [enable Windows 10 automatic enrollment](windows-enroll.md) in Intune (requires Azure Active Directory (Azure AD)), and target the Surface Hub devices as device groups. Surface Hubs are required to be Azure AD joined for compliance and Conditional Access to work.

See [set up enrollment for Windows devices](windows-enroll.md) for guidance.

## Next steps

- [Add actions for noncompliant devices](actions-for-noncompliance.md) and [use scope tags to filter policies](scope-tags.md).
- [Monitor your compliance policies](compliance-policy-monitor.md).
- See the [compliance policy settings for Windows 8.1](compliance-policy-create-windows-8-1.md) devices.
