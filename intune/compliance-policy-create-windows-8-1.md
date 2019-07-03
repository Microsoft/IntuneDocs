---
# required metadata

title: Windows 8.1 compliance settings in Microsoft Intune - Azure | Microsoft Docs
description: See a list of all the settings you can use when setting compliance for your Windows 8.1 and Windows Phone 8.1 devices in Microsoft Intune. Check for compliance on the minimum and maximum operating system, set password restrictions and length, enable encryption on data storage, and more.
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
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Windows 8.1 settings to mark devices as compliant or not compliant using Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

This article lists and describes the different compliance settings you can configure on Windows 8.1 devices in Intune. As part of your mobile device management (MDM) solution, use these settings to block simple passwords, set a minimum and maximum OS version, and more.

This feature applies to:

- Windows Phone 8.1
- Windows 8.1 and later

As an Intune administrator, use these compliance settings to help protect your organizational resources. To learn more about compliance policies, and what they do, see [get started with device compliance](device-compliance-get-started.md).

## Before you begin

[Create a compliance policy](create-compliance-policy.md#create-the-policy). For **Platform**, select **Windows Phone 8.1** or **Windows 8.1 and later**.

## Device properties

- **Minimum OS required**: Enter the minimum allowed version. When a device doesn't meet the minimum OS version requirement, it's reported as non-compliant. A link with information on how to upgrade is displayed. The end user can choose to upgrade their device, and then get access to company resources.
- **Maximum OS version allowed**: Enter the maximum allowed version. When a device is using an OS version later than the version entered in the rule, access to company resources is blocked. The user is asked to contact their IT admin. The device can't access organizational resources until you change the rule to allow the OS version.

Windows 8.1 PCs return a version of **3**. If the OS version rule is set to Windows 8.1 for Windows, then the device is reported as non-compliant even if the device has Windows 8.1.

## System security

### Password

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

    Setting a higher number requires the user to create a password that is more complex. For devices that are accessed with a Microsoft account, the compliance policy fails to evaluate correctly:

    - If minimum password length is greater than eight characters
    - Or if minimum number of character sets is more than two

- **Maximum minutes of inactivity before password is required**: Enter the idle time before the user must reenter their password.
- **Password expiration (days)**: Select the number of days before the password expires, and they must create a new one.
- **Number of previous passwords to prevent reuse**: Enter the number of previously used passwords that can't be used.

### Encryption

- **Require encryption on mobile device**: **Require** the device to be encrypted to connect to data storage resources.

Select **OK** > **Create** to save your changes.

## Next steps

- [Add actions for noncompliant devices](actions-for-noncompliance.md) and [use scope tags to filter policies](scope-tags.md).
- [Monitor your compliance policies](compliance-policy-monitor.md).
- See the [compliance policy settings for Windows 10 and later](compliance-policy-create-windows.md) devices.
