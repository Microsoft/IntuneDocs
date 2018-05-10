---
# required metadata

title: Create Android for Work compliance policy in Microsoft Intune - Azure | Microsoft Docs
description: Create or configure a Microsoft Intune device compliance policy for Android for Work devices. Choose to allow jailbroken devices, set the acceptable threat level, check for Google Play, enter the minimum and maximum operating system version, choose your password requirements, and allow Side-loading applications.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: muhosabe
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Add a device compliance policy for Android for Work devices in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

An Intune device compliance policy for Android for Work specifies the rules and settings that these devices must meet to be considered compliant. You can use these policies with conditional access to allow or block access to company resources. You can also get device reports, and take actions for non-compliance. You create device compliance policies for different platforms in the Intune Azure portal. To learn more about compliance policies, and any prerequisites, see [get started with device compliance](device-compliance-get-started.md).

The following table describes how noncompliant settings are managed when a compliance policy is used with a conditional access policy.

--------------------------

|**policy setting**| **Android for Work** |
| --- | --- |
| **PIN or password configuration** |  Quarantined |
| **Device encryption** |  Quarantined |
| **Jailbroken or rooted device** | Quarantined (not a setting) |
| **email profile** | Not applicable |
| **Minimum OS version** | Quarantined |
| **Maximum OS version** | Quarantined |
| **Windows health attestation** |Not applicable |

**Remediated** = The device operating system enforces compliance. (For example, the user is forced to set a PIN.)+

**Quarantined** = The device operating system does not enforce compliance. (For example, Android devices do not force the user to encrypt the device.) When the device is not compliant, the following actions take place:

- If a conditional access policy applies to the user, the device is blocked.
- The company portal notifies the user about any compliance problems.

## Create a device compliance policy

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. For **Platform**, select **Android for Work**. Choose **Settings Configure**, and enter the **Device Health**, **Device Properties**, and **System Security** settings. When done, select **OK**, and **Create**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## Device health

- **Rooted devices**: If you enable this setting, jailbroken devices are evaluated as noncompliant.
- **Require the device to be at or under the Device Threat Level**: Use this setting to take the risk assessment from the Lookout MTP solution as a condition for compliance. Choose the maximum allowed threat level:
  - **Secured**: This option is the most secure, and means that the device cannot have any threats. If the device is detected as having any level of threats, it is evaluated as noncompliant.
  - **Low**: The device is evaluated as compliant if only low-level threats are present. Anything higher puts the device in a noncompliant status.
  - **Medium**: The device is evaluated as compliant if the threats that are present on the device are low or medium level. If the device is detected to have high-level threats, it is determined to be noncompliant.
  - **High**: This option is the least secure, as it allows all threat levels. It may be useful if you're using this solution only for reporting purposes.
- **Google Play Services is configured**: Require that the Google Play services app is installed and enabled. Google Play services allows security updates, and is a base-level dependency for many security features on certified-Google devices.
- **Up-to-date security provider**: Require that an up-to-date security provider can protect a device from known vulnerabilities.
- **SafetyNet device attestation**: Enter the level of [SafetyNet attestation](https://developer.android.com/training/safetynet/attestation.html) that must be met. Your options:
  - **Not configured**
  - **Check basic integrity**
  - **Check basic integrity & certified devices**

#### Threat scan on apps

On devices with work profiles (Android for Work), the **Threat scan on apps** setting can be found as a configuration policy setting. Administrators can enable the setting for a device.

If your enterprise uses Android work profiles, you can enable **Threat scan on apps** for your enrolled devices. Establish a device profile and require the system security setting. For more information, see [Android for Work device restriction settings in Intune](device-restrictions-android-for-work.md).

## Device property settings

- **Minimum OS version**: When a device doesn't meet the minimum OS version requirement, it's reported as noncompliant. A link with information on how to upgrade is displayed. The end user can choose to upgrade their device, and then access company resources.
- **Maximum OS version**: When a device is using an OS version later than the version in the rule, access to company resources is blocked. And, the user is asked to contact their IT admin. Until there is a rule change to allow the OS version, the device cannot access company resources.

## System security settings

### Password

- **Require a password to unlock mobile devices**: **Require** users to enter a password before they can access their device.
- **Minimum password length**: Enter the minimum number of digits or characters that the user's password must have.
- **Required password type**: Choose whether a password should have only numeric characters there should be a mix of numbers and other characters. Choose from:
  - **Device Default**
  - **Low security biometric**
  - **At least numeric**
  - **Numeric complex**: Repeated or consecutive numerals (such as "1111" or "1234") are not allowed.
  - **At least alphabetic**
  - **At least alphanumeric**
  - **At least alphanumeric with symbols**
- **Maximum minutes of inactivity before password is required**: Enter the idle time before the user must reenter their password.
- **Password expiration (days)**: Select the number of days before the password expires and the user must create a new password.
- **Number of previous passwords to prevent reuse**: Enter the number of recent passwords that can't be reused. Use this setting to restrict the user from creating previously used passwords.

### Encryption

- **Require encryption on mobile device**: You don't have to configure this setting because Android for Work devices enforce encryption.

### Device Security

- **Block apps from unknown sources**: You don't have to configure this setting as Android for Work devices always restrict installation from unknown sources.
- **Company portal app runtime integrity**: Checks if the Company Portal app has the default runtime environment installed, is properly signed, is not in debug-mode, and is installed from a known source.
- **Block USB debugging on device**: You don't have to configure this setting because USB debugging is already disabled on Android for Work devices.
- **Minimum security patch level**: Select the oldest security patch level a device can have. Devices that are not at least at this patch level are noncompliant. The date must be entered in the `YYYY-MM-DD` format.

## Assign user groups

1. Choose a policy that you've configured. Existing policies are in **Device compliance** > **Policies**.
2. Choose the policy, and choose **Assignments**. You can include or exclude Azure Active Directory (AD) security groups.
3. Choose **Selected groups** to see your Azure AD security groups. Select the user groups you want this policy to apply, and choose **Save** to deploy the policy to users.

You have applied the policy to users. The devices used by the users who are targeted by the policy are evaluated for compliance.

## Next steps
[Automate email and add actions for noncompliant devices](actions-for-noncompliance.md)  
[Monitor Intune Device compliance policies](compliance-policy-monitor.md)
