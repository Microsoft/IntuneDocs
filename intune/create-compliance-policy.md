---
# required metadata

title: Device compliance policies in Microsoft Intune - Azure | Microsoft Docs
description: Get started with use device compliance policies, overview of status and severity levels, using the InGracePeriod status, working with Conditional Access, handling devices without an assigned policy, and the differences in compliance in the Azure portal and classic portal in Microsoft Intune
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.reviewer: joglocke

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

# Create a compliance policy in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Device compliance policies are a key feature when using Intune to protect your organization's resources. In Intune, you can create rules and settings that devices must meet to be considered compliant, such as a minimum OS version. If the device isn't compliant, you can then block access to data and resources using [Conditional Access](conditional-access.md).

You can also take actions for non-compliance, such as sending a notification email to the user. For an overview of what compliance policies do, and how they're used, see [get started with device compliance](device-compliance-get-started.md).

This article:

- Lists the prerequisites and steps to create a compliancy policy.
- Shows you how to assign the policy to your user and device groups.
- Describes additional features, including scope tags to "filter" your policies, and steps you can take on devices that aren't compliant.
- Lists the check-in refresh cycle times when devices receive policy updates.

## Before you begin

To use device compliance policies, be sure you:

- Use the following subscriptions:

  - Intune
  - If you use Conditional Access, then you need Azure Active Directory (AD) Premium edition. [Azure Active Directory pricing](https://azure.microsoft.com/pricing/details/active-directory/) lists what you get with the different editions. Intune compliance doesn't require Azure AD.

- Use a supported platform:

  - Android
  - Android Enterprise
  - iOS
  - macOS (preview)
  - Windows 10
  - Windows 8.1
  - Windows Phone 8.1

- Enroll devices in Intune (required to see the compliance status)

- Enroll devices to one user, or enroll without a primary user. Devices enrolled to multiple users aren't supported.

## Create the policy

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Select **Device compliance**. You have the following options:

    - **Overview**: Shows a summary and number of devices that are compliant, not evaluated, and so on. It also lists the policies and individual settings in your policies. [Monitor Intune device compliance policies](compliance-policy-monitor.md) provides some good information.
    - **Manage**: Create device policies, send [notifications](quickstart-send-notification.md) to non-compliant devices, and enable [network fencing](use-network-locations.md).
    - **Monitor**: Check the compliance status of your devices, and at the setting and policy level. [Monitor Intune device compliance policies](compliance-policy-monitor.md) is a good resource. Also view logs and check the threat agent status of your devices.
    - **Setup**: Use the [built-in compliance policies](device-compliance-get-started.md#ways-to-deploy-device-compliance-policies), enable [Windows Defender advanced threat protection (ATP)](advanced-threat-protection.md), add a [mobile threat defense connector](mobile-threat-defense.md), and use [Jamf](conditional-access-integrate-jamf.md).

3. Select **Policies** > **Create Policy**. Enter the following properties:

    - **Name**: Enter a descriptive name for the policy. Name your policies so you can easily identify them later. For example, a good policy name is **Mark iOS jailbroken devices as not compliant**.
    - **Description**: Enter a description for the policy. This setting is optional, but recommended.
    - **Platform**: Choose the platform of your devices. Your options:  

       - **Android**
       - **Android enterprise**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 and later**
       - **Windows 10 and later**

    - **Settings**: The following articles list and describe the settings for each platform:

        - [Android](compliance-policy-create-android.md)
        - [Android Enterprise](compliance-policy-create-android-for-work.md)
        - [iOS](compliance-policy-create-ios.md)
        - [macOS](compliance-policy-create-mac-os.md)
        - [Windows Phone 8.1, Windows 8.1 and later](compliance-policy-create-windows-8-1.md)
        - [Windows 10 and later](compliance-policy-create-windows.md)

4. When finished, select **OK** > **Create** to save your changes. The policy is created, and shown in the list. Next, assign the policy to your groups.

## Assign user groups

Once a policy is created, the next step is to assign the policy to your groups:

1. Choose a policy you created. Existing policies are in **Device compliance** > **Policies**.
2. Select the policy > **Assignments**. You can include or exclude Azure Active Directory (AD) security groups.
3. Choose **Selected groups** to see your Azure AD security groups. Select the user groups you want this policy to apply > Choose **Save** to deploy the policy to users.

You applied the policy to users. The devices used by the users targeted by the policy are evaluated for compliance.

### Evaluate how many users are targeted

When you assign the policy, you can also **Evaluate** how many users are affected. This feature calculates users; it doesn't calculate devices.

1. In Intune, select **Device compliance** > **Policies**.
2. Select a policy > **Assignments** > **Evaluate**. A message shows you how many users are targeted by this policy.

If the **Evaluate** button is grayed out, make sure the policy is assigned to one or more groups.

## Actions for noncompliance

For devices that don't meet your compliance policies, you can add a sequence of actions to apply automatically. You can change the schedule when the device is marked non-compliant, such as after one day. You can also configure a second action that sends an email to the user when the device isn't compliant.

[Add actions for noncompliant devices](actions-for-noncompliance.md) provides more information, including creating a notification email to your users.

For example, you're using the Locations feature, and add a location in a compliance policy. The default action for noncompliance applies when you select at least one location. If the device isn't connected to the selected locations, it's immediately considered not compliant. You can give your users a grace period, such as one day.

## Scope tags

Scope tags are a great way to assign and filter policies to specific groups, such as Sales, HR, All US-NC employees, and so on. After you add the settings, you can also add a scope tag to your compliance policies. [Use scope tags to filter policies](scope-tags.md) is a good resource.

## Refresh cycle times

Intune uses different refresh cycles to check for updates to compliance policies. If the device recently enrolled, the check-in runs more frequently. [Policy and profile refresh cycles](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) lists the estimated refresh times.

At any time, users can open the Company Portal app, and sync the device to immediately check for policy updates.

### Assign an InGracePeriod status

The InGracePeriod status for a compliance policy is a value. This value is determined by the combination of a device’s grace period, and a device’s actual status for that compliance policy.

Specifically, if a device has a NonCompliant status for an assigned compliance policy, and:

- The device has no grace period assigned to it, then the assigned value for the compliance policy is NonCompliant
- The device has a grace period that's expired, then the assigned value for the compliance policy is NonCompliant
- The device has a grace period that's in the future, then the assigned value for the compliance policy is InGracePeriod

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

For example, a device has three compliance policies assigned to it: one Unknown status (severity = 1), one Compliant status (severity = 3), and one InGracePeriod status (severity = 4). The InGracePeriod status has the highest severity level. So, all three policies have the InGracePeriod compliance status.

## Next steps

[Monitor your policies](compliance-policy-monitor.md).
