---
# required metadata

title: Configure endpoint protection settings in Microsoft Intune - Azure | Microsoft Docs
description: Create endpoint protection settings when you create a macOS or Windows 10 device profile in Microsoft Intune.
keywords:
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 5/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
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
mr.reviewer: karthib
---
# Add endpoint protection settings in Intune

With Intune, you can use device configuration profiles to manage common endpoint protection security features on devices, including:
- Firewall 
- BitLocker
- Allowing and blocking apps  
- Windows Defender and encryption

For example, you can create an endpoint protection profile that only allows macOS users to install apps from the Mac App Store. Or, enable Windows SmartScreen when running apps on Windows 10 devices.

Before you create a profile, review the following articles that detail the endpoint protection settings Intune can manage for each supported platform: 
- [macOS settings](endpoint-protection-macos.md)
- [Windows 10 settings](endpoint-protection-windows-10.md)

## Create a device profile containing endpoint protection settings

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Select **Device configuration** > **Profiles** > **Create profile**.
4. Enter a **Name** and **Description** for the endpoint protection profile.
5. From the **Platform** drop-down list, select the device platform to which you want to apply custom settings. Currently, you can choose one of the following platforms for device restriction settings:
   - **macOS**
   - **Windows 10 and later**
6. From the **Profile type** drop-down list, choose **Endpoint protection**. 
7. Depending on the platform you chose, the settings you can configure are different. See:
   - [macOS settings](endpoint-protection-macos.md)
   - [Windows 10 settings](endpoint-protection-windows-10.md)  

8. After you configure applicable settings, select **Create** on the **Create profile** page.

   The profile is created and appears on the profiles list page. To assign this profile to groups, see [assign device profiles](device-profile-assign.md).

## Next steps  

To assign a profile to groups, see [assign device profiles](device-profile-assign.md).
