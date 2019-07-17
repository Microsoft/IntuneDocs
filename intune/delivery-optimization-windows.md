---
# required metadata

title: Delivery optimization settings for Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Configure how Windows 10 devices you manage with Intune use delivery optimization. In Intune, create a device configuration profile to install updates from the internet. Also see how to replace existing update rings with a delivery optimization profile.
keywords:
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
---

# Delivery optimization settings in Microsoft Intune

With Intune, you can use Delivery optimization settings for your Windows 10 devices to reduce bandwidth consumption when those devices download applications and updates. Delivery optimization is configured as part of your device configuration profiles.  

This article describes how to configure delivery optimization settings as part of a device configuration profile. After you create a profile, you then assign or deploy that profile to your Windows 10 devices. 

For a list of the delivery optimization settings that Intune supports, see [Delivery optimization settings for Intune](delivery-optimization-settings.md).  

To learn about Delivery Optimization on Windows 10, see [Delivery Optimization updates](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) in the Windows documentation.  

> [!NOTE]
> **Software updates – Windows 10 Update Rings** are replaced by the **Delivery optimization** settings. Your existing update rings can be changed to use the **Delivery optimization** settings. [Move existing update rings to delivery optimization](#move-existing-update-rings-to-delivery-optimization) (in this article) 
## Create the profile

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. Select **Device configuration** > **Profiles** > **Create Profile**.

3. Enter the following properties:

    - **Name**: Enter a descriptive name for the new profile.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
    - **Platform**: Select the platform:  

        - **Windows 10 and later**

    - **Profile type**: Select **Delivery optimization**.
    - **Settings**: Configure settings that define how you want updates and apps to download. For information about available settings, see [Delivery optimization settings for Intune](delivery-optimization-settings.md).

4. When finished, select **OK** > **Create** to save your changes.

The profile is created and is shown in the list. Next, [assign the profile](device-profile-assign.md) and then [monitor its status](device-profile-monitor.md).

## Move existing update rings to delivery optimization

**Delivery optimization** settings replace **Software updates – Windows 10 Update Rings**. Your existing update rings can be easily changed to use the **Delivery optimization** settings. To maintain the same settings when you create a delivery optimization profile, use the same *Delivery optimization download mode* and then set the same settings as you already use. However, you can choose to reconfigure delivery optimization settings to take advantage of the full range of addition settings that the Delivery Optimization profile can manage.

1. Create a delivery optimization configuration profile:

    1. In Intune, select **Device configuration** > **Profiles** > **Create profile**.
    2. Enter the following properties:

        - **Name**: Enter a descriptive name for the new profile.
        - **Description**: Enter a description for the profile. This setting is optional, but recommended.
        - **Platform**: Select **Windows 10 and later**.
        - **Profile type**: Select **Delivery optimization**.
        - **Settings**: For **Delivery optimization download mode**, choose the same mode that's used by the existing software update ring unless you want to change the settings you apply to your devices. Your options:
            - **Not configured​**
            - **HTTP only, no peering​**
            - **HTTP blended with peering behind the same NAT**
            - **HTTP blended with peering across a private group​**
            - **HTTP blended with Internet peering​**
            - **Simple download mode with no peering​**
            - **Bypass mode**
    3. Configure any additional settings you might want to manage.
1. Assign this new profile to the same devices and users as the existing software update ring. [Assign the profile](device-profile-assign.md) lists the steps.

3. Unconfigure the existing software ring:
    1. In Intune, go to **Software updates** > Windows 10 Update Rings.
    2. In the list, select your update ring.
    3. In the settings, set **Delivery optimization download mode** to **Not configured**.
    4. **OK** > **Save** your changes.

## Next steps

[Assign the profile](device-profile-assign.md) and [monitor its status](device-profile-monitor.md) its status.  
View the [delivery optimization settings](delivery-optimization-settings.md) for Intune.
