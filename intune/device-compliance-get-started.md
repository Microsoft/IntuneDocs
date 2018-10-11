---
# required metadata

title: Device compliance policies in Microsoft Intune - Azure | Microsoft Docs
description: Requirements to use device compliance policies, overview of status and severity levels, using the InGracePeriod status, working with conditional access, handling devices without an assigned policy, and the differences in compliance in the Azure portal and classic portal in Microsoft Intune
keywords:

author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/28/2018

ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.reviewer: joglocke

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Get started with device compliance policies in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Compliance requirements are essentially rules, such as requiring a device PIN, or requiring encryption. Device compliance policies define these rules and settings that a device must follow to be considered compliant. These rules include:

- Use a password to access devices

- Encryption

- Whether the device is jail-broken or rooted

- Minimum OS version required

- Maximum OS version allowed

- Require the device to be at, or under the Mobile Threat Defense level

You can also use device compliance policies to monitor the compliance status in your devices.

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

-   3 days after initial noncompliance state, a follow up reminder is sent to the user.

-   5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

-   7 days after initial noncompliance state, access to company resources is blocked. This requires that you have conditional access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement conditional access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## Prerequisites
To use device compliance policies, the following are required:

- Use the following subscriptions:

  - Intune
  - Azure Active Directory (AD) Premium

- Use a supported platform:

  - Android
  - iOS
  - macOS (preview)
  - Windows 8.1
  - Windows Phone 8.1
  - Windows 10

- To report their compliance status, devices must be enrolled in Intune

- Devices enrolled to one user or devices with no primary user are supported. Multiple user contexts are not supported.

## How Intune device compliance policies work with Azure AD

When a device is enrolled in Intune, the Azure AD registration process starts, and updates the device attributes into Azure AD. One key piece of information is the device compliance status. This compliance status is used by conditional access policies to block or allow access to e-mail and other corporate resources.

[Azure AD registration process](https://docs.microsoft.com/azure/active-directory/device-management-introduction) provides more information.

### Assign a resulting device configuration profile status

If a device has multiple configuration profiles, and the device has different compliance statuses for two or more of the assigned configuration profiles, then a single resulting compliance status is assigned. This assignment is based on a conceptual severity level assigned to each compliance status. Each compliance status has the following severity level:

|Status  |Severity  |
|---------|---------|
|Pending     |1|
|Succeeded     |2|
|Failed     |3|
|Error     |4|

When a device has multiple configuration profiles, then the highest severity level of all the profiles is assigned to that device.

For example, say a device has three profiles assigned to it: one Pending status (severity = 1), one Succeeded status (severity = 2), and one Error status (severity = 4). The Error status has the highest severity level, so all three profiles have the Error compliance status.

### Assign an InGracePeriod status

The InGracePeriod status for a compliance policy is a value. This value is determined by the combination of a device’s grace period, and a device’s actual status for that compliance policy.

Specifically, if a device has a NonCompliant status for an assigned compliance policy, and:

- the device has no grace period assigned to it, then the assigned value for the compliance policy is NonCompliant
- the device has a grace period that is expired, then the assigned value for the compliance policy is NonCompliant
- the device has a grace period that is in the future, then the assigned value for the compliance policy is InGracePeriod

The following table summarizes these points:

|Actual compliance status|Value of assigned grace period|Effective compliance status|
|---------|---------|---------|
|NonCompliant |No grace period assigned |NonCompliant |
|NonCompliant |Yesterday’s date|NonCompliant|
|NonCompliant |Tomorrow’s date|InGracePeriod|

For more information about monitoring device compliance policies, see [Monitor Intune Device compliance policies](compliance-policy-monitor.md).

### Assign a resulting compliance policy status

If a device has multiple compliance policies, and the device has different compliance statuses for two or more of the assigned compliance policies, then a single resulting compliance status is assigned. This assignment is based on a conceptual severity level assigned to each compliance status. Each compliance status has the following severity level:

|Status  |Severity  |
|---------|---------|
|Unknown     |1|
|NotApplicable     |2|
|Compliant|3|
|InGracePeriod|4|
|NonCompliant|5|
|Error|6|

When a device has multiple compliance policies, then the highest severity level of all the policies is assigned to that device.

For example, say a device has three compliance policies assigned to it: one Unknown status (severity = 1), one Compliant status (severity = 3), and one InGracePeriod status (severity = 4). The InGracePeriod status has the highest severity level, so all three policies have the InGracePeriod compliance status.

## Ways to use device compliance policies

#### With conditional access
For devices that comply to policy rules, you can give those devices access to email and other corporate resources. If the devices don't comply to policy rules, then they don't get access to corporate resources. This is conditional access.

#### Without conditional access
You can also use device compliance policies without any conditional access. When you use compliance policies independently, the targeted devices are evaluated and reported with their compliance status. For example, you can get a report on how many devices are not encrypted, or which devices are jail-broken or rooted. When you use compliance policies without conditional access, there are no access restrictions to company resources.

## Ways to deploy device compliance policies
You can deploy compliance policy to users in user groups or devices in device groups. When a compliance policy is deployed to a user, all of the user's devices are checked for compliance. For WIndows 10 1803+ devices that are automatically MDM enrolled we recommend deploying to device groups if the primary user didn't enroll the device to aid in Compliance reporting

The default **Compliance policy settings** (Azure portal > Device compliance) include:

- **Mark devices with no compliance policy assigned as**: This property has two values:

  - **Compliant**: security feature off
  - **Not compliant** (default): security feature on

  If a device doesn't have a compliance policy assigned, then this device is considered not compliant. By default, devices are marked as **Compliant**. If you use conditional access, we recommended you change the  setting to **Not compliant**. If an end user is not compliant because a policy isn't assigned, then Company Portal lists `No compliance policies have been assigned`.

- **Enhanced jailbreak detection**: When enabled, this setting causes iOS devices to check-in with Intune more frequently. Enabling this property uses the device’s location services, and impacts battery usage. The user location data is not stored by Intune.

  Enabling this setting requires devices to:
  - Enable location services at the OS level
  - Allow the company portal to use location services
  - Evaluate and report its jailbreak status to Intune at least once every 72 hours. Otherwise, the device is marked not compliant. Evaluation is triggered by either opening the Company Portal app or physically moving the device 500 meters or more.

- **Compliance status validity period (days)**: Enter the time period that devices report the status for all received compliance policies. Devices that don't return the status within this time period are treated as noncompliant. The default value is 30 days.

All devices have a **Default Device Compliance Policy** (Azure portal > Device compliance > Policy compliance). Use this default policy to monitor these settings.

To learn the time it takes for mobile devices to get a policy after the policy is deployed, see [Troubleshooting device profiles](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

Compliance reports are a great way to check the status of devices. See [Monitor compliance policies](compliance-policy-monitor.md) for guidance.

### Actions for noncompliance
You can configure a time-ordered sequence of actions that apply to devices that don't meet the compliance policy criteria. These actions for noncompliance can be automated, as described in [Automate actions for noncompliance](actions-for-noncompliance.md).

## Azure classic portal vs. Azure portal

The main difference when using device compliance policies in the Azure portal:

- In the Azure portal, the compliance policies are created separately for each supported platform
- In the Azure classic portal, one device compliance policy is common to all supported platforms

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

## Device compliance policies in the classic portal and Azure portal

Device compliance policies created in the [classic portal](https://manage.microsoft.com) don't appear in the [Azure portal](https://portal.azure.com). However, they’re still targeted to users and manageable using the classic portal.

To use the device compliance-related features in the Azure portal, you must create new device compliance policies in the Azure portal. If you assign a device compliance policy in the Azure portal to a user who is also assigned a device compliance policy from the classic portal, then the device compliance policies from the Azure portal take precedence over the policies created in the classic portal.

## Next steps

- Create a device compliance policy for the following platforms:

  - [Android](compliance-policy-create-android.md)
  - [Android work profile](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- For information about the Intune Data Warehouse policy entities, see [Reference for policy entities](reports-ref-policy.md).
