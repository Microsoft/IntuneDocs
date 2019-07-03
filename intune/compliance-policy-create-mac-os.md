---
# required metadata

title: macOS device compliance settings in Microsoft Intune - Azure | Microsoft Docs
description: See a list of all the settings you can use when setting compliance for your macOS devices in Microsoft Intune. Require Apple's system integrity protection, set password restrictions, require a firewall, allow gatekeeper, and more.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology:

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# macOS settings to mark devices as compliant or not compliant using Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

This article lists and describes the different compliance settings you can configure on macOS devices in Intune. As part of your mobile device management (MDM) solution, use these settings to set a minimum or maximum OS version, set passwords to expire, and more.

This feature applies to:

- macOS

As an Intune administrator, use these compliance settings to help protect your organizational resources. To learn more about compliance policies, and what they do, see [get started with device compliance](device-compliance-get-started.md).

## Before you begin

[Create a compliance policy](create-compliance-policy.md#create-the-policy). For **Platform**, select **macOS**.

## Device Health

- **Require a system integrity protection**: **Require** your macOS devices to have [System Integrity Protection](https://support.apple.com/HT204899) (opens Apple's web site) enabled. When set to **Not configured** (default), this setting isn't evaluated for compliance or non-compliance.

## Device properties

- **Minimum OS version**: When a device doesn't meet the minimum OS version requirement, it's reported as noncompliant. A link with information on how to upgrade appears. The end user can choose to upgrade their device, and then get access to company resources.
- **Maximum OS version**: When a device is using an OS version later than the version specified in the rule, access to company resources is blocked. The user is asked to contact their IT admin. Until there is a rule change to allow the OS version, this device can't access company resources.
- **Minimum OS build version**: When Apple publishes security updates, the build number is typically updated, not the OS version. Use this feature to enter a minimum allowed build number on the device.
- **Maximum OS build version**: When Apple publishes security updates, the build number is typically updated, not the OS version. Use this feature to enter a maximum allowed build number on the device.

## System security settings

### Password

- **Require a password to unlock mobile devices**: **Require** users to enter a password before they can access their device.
- **Simple passwords**: Set to **Block** so users can't create simple passwords, such as **1234** or **1111**. Set to **Not configured** to let users create passwords like **1234** or **1111**.
- **Minimum password length**: Enter the minimum number of digits or characters that the password must have.
- **Password type**: Choose if a password should have only **Numeric** characters, or if there should be a mix of numbers and other characters (**Alphanumeric**).
- **Number of non-alphanumeric characters in password**: Enter the minimum number of special characters, such as `&`, `#`, `%`, `!`, and so on, that must be in the password.

    Setting a higher number requires the user to create a password that is more complex.

- **Maximum minutes of inactivity before password is required**: Enter the idle time before the user must reenter their password.
- **Password expiration (days)**: Select the number of days before the password expires, and they must create a new one.
- **Number of previous passwords to prevent reuse**: Enter the number of previously used passwords that can't be used.

    > [!IMPORTANT]
    > When the password requirement is changed on a macOS device, it doesn’t take effect until the next time the user changes their password. For example, if you set the password length restriction to eight digits, and the macOS device currently has a six digits password, then the device remains compliant until the next time the user updates their password on the device.

### Encryption

- **Encryption of data storage on a device**: Choose **Require** to encrypt data storage on your devices.

### Device Security

Firewall protects devices from unauthorized network access. You can use Firewall to control connections on a per-application basis. 

- **Firewall**: Select **Enable** to help protect devices from unauthorized access. Enabling this feature allows you to handle incoming internet connections, and use stealth mode. **Not configured** (default) leaves the firewall turned off, and network traffic is allowed (not blocked).
- **Incoming connections**: **Block** all incoming network connections except the connections required for basic internet services, such as DHCP, Bonjour, and IPSec. This setting also blocks all sharing services, including screen sharing, remote access, iTunes music sharing, and more. **Not configured** (default) allows incoming connections and sharing services.
- **Stealth Mode**: **Enable** stealth mode to prevent devices from responding to probing requests, which can be made my malicious users. When enabled, the device continues to answer incoming requests for authorized apps. **Not configured** (default) leaves stealth mode turned off.

### Gatekeeper

For more information, see [Gatekeeper on macOS](https://support.apple.com/HT202491) (opens Apple's web site).

**Allow apps downloaded from these locations**: Allows supported applications to be installed on your devices from different locations. Your location options:

- **Not configured**: Default. The gatekeeper option has no impact on compliance or non-compliance. 
- **Mac App Store**: Only install apps for the Mac app store. Apps can't be installed from third parties nor identified developers. If a user selects Gatekeeper to install apps outside the Mac App Store, then the device is considered not compliant.
- **Mac App Store and identified developers**: Install apps for the Mac app store and from identified developers. macOS checks the identity of developers, and does some other checks to verify app integrity. If a user selects Gatekeeper to install apps outside these options, then the device is considered not compliant.
- **Anywhere**: Apps can be installed from anywhere, and by any developer. This option is the least secure.

Select **OK** > **Create** to save your changes.

## Next steps

- [Add actions for noncompliant devices](actions-for-noncompliance.md) and [use scope tags to filter policies](scope-tags.md).
- [Monitor your compliance policies](compliance-policy-monitor.md).
- See the [compliance policy settings for iOS](compliance-policy-create-ios.md) devices.
