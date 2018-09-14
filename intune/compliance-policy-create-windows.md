---
# required metadata

title: Create Windows device compliance policy in Microsoft Intune - Azure | Microsoft Docs
description: Create or configure a Microsoft Intune device compliance policy for Windows Phone 8.1, Windows 8.1 and later, and Windows 10 and later devices. Check for compliance on the the minimum and maximum operating system, set password restrictions and length, require bitlocker, check for third (3rd) party AV solutions, set the acceptable threat level, and enable encypryption on data storage, including Surface Hub and Windows Holographic for Business.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/13/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---
# Add a device compliance policy for Windows devices in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

An Intune device compliance policy for Windows specifies the rules and settings that Windows devices must meet to be considered compliant. You can use these policies with conditional access to allow or block access to company resources. You can also get device reports and take actions for non-compliance. You create device compliance policies for each platform in the Intune Azure portal. To learn more about compliance policies, and any prerequisites, see [Get started with device compliance](device-compliance-get-started.md).

The following table describes how noncompliant settings are managed when a compliance policy is used with a conditional access policy.

---------------------------

| **Policy setting** | **Windows 8.1 and later** | **Windows Phone 8.1 and later** |
|----| ----| --- |
| **PIN or password configuration** | Remediated | Remediated |   
| **Device encryption** | Not applicable | Remediated |   
| **Jailbroken or rooted device** | Not applicable | Not applicable |  
| **Email profile** | Not applicable | Not applicable |   
| **Minimum OS version** | Quarantined | Quarantined |   
| **Maximum OS version** | Quarantined | Quarantined |   
| **Windows health attestation** | Quarantined: Windows 10 and Windows 10 Mobile|Not applicable: Windows 8.1 |

-------------------------------

**Remediated** = The device operating system enforces compliance. (For example, the user is forced to set a PIN.)

**Quarantined** = The device operating system does not enforce compliance. (For example, Android devices do not force the user to encrypt the device.) When the device is not compliant, the following actions take place:

- The device is blocked if a conditional access policy applies to the user.
- The company portal notifies the user about any compliance problems.

## Create a device compliance policy

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. For **Platform**, select **Windows Phone 8.1**, **Windows 8.1 and later**, or **Windows 10 and later**.
6. Choose **Settings Configure**, and enter the **Device Health**, **Device Properties**, and **System Security** settings. When you're done, select **OK**, and **Create**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## Windows 8.1 devices policy settings

These policy settings apply to devices running the following platforms:

- Windows Phone 8.1
- Windows 8.1 and later

### Device properties

- **Minimum OS required**: When a device doesn't meet the minimum OS version requirement, it's reported as noncompliant. A link with information on how to upgrade is displayed. The end user can choose to upgrade their device, and then get access to company resources.
- **Maximum OS version allowed**: When a device is using an OS version later than the version specified in the rule, access to company resources is blocked. The user is asked to contact their IT admin. Until there is a rule change to allow the OS version, this device can't access company resources.

Windows 8.1 PCs return a version of **3**. If the OS version rule is set to Windows 8.1 for Windows, then the device is reported as noncompliant even if the device has Windows 8.1.

### System security

#### Password

- **Require a password to unlock mobile devices**: **Require** users to enter a password before they can access their device.
- **Simple passwords**: Set to **Block** so users can't create simple passwords, such as **1234** or **1111**. Set to **Not configured** to let users create passwords like **1234** or **1111**.
- **Minimum password length**: Enter the minimum number of digits or characters that the password must have.

  For devices that run Windows and are accessed with a Microsoft account, the compliance policy fails to evaluate correctly:
  - If minimum password length is greater than eight characters
  - Or, if minimum number of character sets is more than two

- **Password type**: Choose if a password should have only **Numeric** characters, or if there should be a mix of numbers and other characters (**Alphanumeric**).
  
  - **Number of non-alphanumeric characters in password**: If **Required password type** is set to **Alphanumeric**, this setting specifies the minimum number of character sets that the password must contain. The four character sets are:
    - Lowercase letters
    - Uppercase letters
    - Symbols
    - Numbers

    Setting a higher number requires the user to create a password that is more complex. For devices that run Windows, and are accessed with a Microsoft account, the compliance policy fails to evaluate correctly if minimum password length is greater than eight characters, or if minimum number of character sets is more than two.

- **Maximum minutes of inactivity before password is required**: Enter the idle time before the user must reenter their password.
- **Password expiration (days)**: Select the number of days before the password expires, and they must create a new one.
- **Number of previous passwords to prevent reuse**: Enter the number of previously used passwords that cannot be used.

#### Encryption

- **Require encryption on mobile device**: **Require** the device to be encrypted to connect to data storage resources.

## Windows 10 and later policy settings

### Device health

- **Require BitLocker**: When BitLocker is on, the device can protect data stored on the drive from unauthorized access when the system is turned off, or goes to hibernation. Windows BitLocker Drive Encryption encrypts all data stored on the Windows operating system volume. BitLocker uses the TPM to help protect the Windows operating system and user data. It also helps to ensure that a computer is not tampered with, even if it's left unattended, lost, or stolen. If the computer is equipped with a compatible TPM, BitLocker uses the TPM to lock the encryption keys that protect the data. As a result, the keys cannot be accessed until the TPM has verified the state of the computer.
- **Require Secure Boot to be enabled on the device**: When Secure Boot is enabled, the system is forced to boot to a factory trusted state. Also, when Secure Boot is enabled, the core components used to boot the machine must have correct cryptographic signatures that are trusted by the organization that manufactured the device. The UEFI firmware verifies the signature before it lets the machine start. If any files have been tampered with, breaking their signature, the system does not boot.

  > [!NOTE]
  > The **Require Secure Boot to be enabled on the device** setting is supported on TPM 1.2 and 2.0 devices. For devices that don't support TPM 2.0 or later, the policy status in Intune shows as **Not Compliant**. This is a limitation of the [Device Health Attestation](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation) service in Windows 10

- **Require code integrity**: Code integrity is a feature that validates the integrity of a driver or system file each time it's loaded into memory. Code integrity detects whether an unsigned driver or system file is being loaded into the kernel. Or whether a system file has been modified by malicious software run by a user account with administrator privileges.

See [Health Attestation CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp) for details about how the HAS service works.

To set up Windows Defender ATP (Advanced Threat Protection) as your defense threat service, see [Enable Windows Defender ATP with conditional access](advanced-threat-protection.md).

### Device properties

- **Minimum OS version**: Enter the minimum allowed version in the **major.minor.build.CU number** format. To get the correct value, open a command prompt, and type `ver`. The `ver` command returns the version in the following format:

  `Microsoft Windows [Version 10.0.17134.1]`

  When a device has an earlier version that the specified OS version, it is reported as noncompliant. A link with information on how to upgrade is displayed. The end user can choose to upgrade their device after which they can access company resources.

- **Maximum OS version**: Enter the maximum allowed version, in the **major.minor.build.revision number** format. To get the correct value, open a command prompt, and type `ver`. The `ver` command returns the version in the following format:

  `Microsoft Windows [Version 10.0.17134.1]`

  When a device is using an OS version later than the one specified in the rule, access to company resources is blocked and the user is asked to contact their IT admin. Until there is a change in rule to allow the OS version, this device cannot be used to access company resources.

- **Minimum OS required for mobile devices**: Enter the minimum allowed version, in the major.minor.build number format.

  When a device has an earlier version that the specified OS version, it is reported as noncompliant. A link with information on how to upgrade is displayed. The end user can choose to upgrade their device after which they can access company resources.

- **Maximum OS required for mobile devices**: Enter the maximum allowed version, in the major.minor.build number.

  When a device is using an OS version later than the one specified in the rule, access to company resources is blocked and the user is asked to contact their IT admin. Until there is a change in rule to allow the OS version, this device cannot be used to access company resources.

- **Valid operating system builds**: Enter a range for the acceptable operating systems versions, including a minimum and maximum. You can also **Export** a comma-separated values (CSV) file list of these acceptable OS build numbers.

### System security settings

#### Password

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
- **Number of previous passwords to prevent reuse**: Enter the number of previously used passwords that cannot be used.
- **Require password when device returns from idle state (Mobile and Holographic)**: Force users to enter the password every time the device returns from an idle state.

#### Encryption

- **Encryption of data storage on a device**: Choose **Require** to encrypt data storage on your devices.

#### Device Security

- **Antivirus**: When set to **Require**, you can check compliance using antivirus solutions that are registered with Windows Security Center, such as Symantec and Windows Defender. When **Not configured**, Intune doesn't check for any AV solutions installed on the device.
- **AntiSpyware**: When set to **Require**, you can check compliance using antispyware solutions that are registered with Windows Security Center, such as Symantec and Windows Defender. When **Not configured**, Intune doesn't check for any antispyware solutions installed on the device.

### Windows Defender ATP

- **Require the device to be at or under the machine risk score**: Use this setting to take the risk assessment from your defense threat services as a condition for compliance. Choose the maximum allowed threat level:
  - **Clear**: This option is the most secure, as the device can't have any threats. If the device is detected as having any level of threats, it is evaluated as noncompliant.
  - **Low**: The device is evaluated as compliant if only low-level threats are present. Anything higher puts the device in a noncompliant status.
  - **Medium**: The device is evaluated as compliant if existing threats on the device are low or medium level. If the device is detected to have high-level threats, it is determined to be noncompliant.
  - **High**: This option is the least secure, and allows all threat levels. It may be useful if you're using this solution only for reporting purposes.

## Windows Holographic for Business

Windows Holographic for Business uses the **Windows 10 and later** platform. Windows Holographic for Business supports the following setting:

- **System Security** > **Encryption** > **Encryption of data storage on device**.

To verify device encryption on the Microsoft HoloLens, see [Verify device encryption](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## Surface Hub
Surface Hub uses the **Windows 10 and later** platform. Surface Hubs are supported for both compliance and conditional access. To enable these features on Surface Hubs, we recommend you [enable Windows 10 automatic enrollment](windows-enroll.md) in Intune (also requires Azure Active Directory (AAD)) and target the Surface Hub devices as device groups. Surface Hubs are required to be Azure Active Directory joined for compliance and conditional access to function.

See [set up enrollment for Windows devices](windows-enroll.md) for guidance.

## Assign user or device groups

1. Choose a policy that you've configured. Existing policies are in **Device compliance** > **Policies**.
2. Choose the policy, and choose **Assignments**. You can include or exclude Azure AD security groups.
3. Choose **Selected groups** to see your Azure AD security groups. Select the user or device groups you want this policy to apply, and choose **Save** to deploy the policy.

You have applied the policy. The devices used by the users who are targeted by the policy are evaluated for compliance.

## Next steps
[Automate email and add actions for noncompliant devices](actions-for-noncompliance.md)  
[Monitor Intune Device compliance policies](compliance-policy-monitor.md)
