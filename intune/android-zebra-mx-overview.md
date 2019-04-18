---
# required metadata

title: Use Zebra Mobility Extensions on Android devices in Microsoft Intune - Azure | Microsoft Docs
description: Use Microsoft Intune to manage and use Zebra devices running Android with Zebra Mobility Extensions (MX). See all the steps, including install the Company Portal app, sideload the app, assign device administrator role, create a StageNow profile, and more.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod:
ms.service: microsoft-intune
ms.localizationpriority:
ms.technology:
ms.assetid: 

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Use and manage Zebra devices with Zebra Mobility Extensions in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune includes a rich set of features, including managing apps and configuring device settings. These built-in features and settings are used to manage Android devices manufactured by Zebra Technologies, also known as "Zebra devices".

If you want to customize or add more Zebra-specific settings, you can also use Zebra **Mobility Extensions (MX)** on these devices. 

This feature applies to:

- Android

Your company may use Zebra devices for retail, on the factory floor, and more. For example, you're a retailer and your environment includes thousands of Zebra mobile devices used by sales associates. Intune can help manage these devices as part of your mobile device management (MDM) solution.

Using Intune, you can enroll Zebra devices to deploy your line-of-business apps to the devices. "Device configuration" profiles let you create MX profiles to manage your Zebra-specific settings.

This article shows you how to use Zebra Mobility Extensions (MX) on Zebra devices in Microsoft Intune.

## Before you begin

- Be sure you have the latest version of the StageNow desktop app from Zebra Technologies.
- Be sure to check [Zebra's full MX feature matrix](http://techdocs.zebra.com/mx/compatibility) (opens Zebra's web site) to confirm the profiles you create are compatible with the device's MX version, OS version, and model.
- Certain devices, such as TC20/25 devices, don't support all of the available MX features in StageNow. Be sure to check [Zebra's feature matrix](http://techdocs.zebra.com/mx/tc2x/) (opens Zebra's web site) for updated support info.

## Step 1: Install the latest Company Portal app

On the device, go to the Google Play store, and download and install the Intune Company Portal app from Microsoft. When installed from Google Play, the Company Portal app gets updates and fixes automatically.

If Google Play isn't available, download the [Microsoft Intune Company Portal for Android](https://www.microsoft.com/download/details.aspx?id=49140) (opens another Microsoft website), and [sideload it](#sideload-the-company-portal-app) (in this article). When installed this way, the app doesn't receive updates or fixes automatically. You should regularly update and patch the app manually.

### Sideload the Company Portal app

"Sideloading" is when you don't use Google Play to install an app. To sideload the Company Portal app, use StageNow. 

The following steps provide an overview. For specific details, see Zebra's documentation. [Enroll in an MDM using StageNow](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/) (opens Zebra's web site) may be a good resource.

1. In StageNow, create a profile for **Enroll in an MDM**.
2. In **Deployment**, choose to download the MDM agent file.
3. Set the **Support App** and **Download Configuration** steps to **No**.
4. In **Download MDM**, select **Transfer/Copy File**. Add the source and destination of the Company Portal Android package (APK).
5. In **Launch MDM**, leave the default values as-is. Add the following details:

    - **Package Name**: `com.microsoft.windowsintune.companyportal`
    - **Class Name**: `com.microsoft.windowsintune.companyportal.views.SplashActivity`

Continue to publish the profile, and consume it with the StageNow app on the device. The Company Portal app is installed and opened on the device.

> [!TIP]
> For more information on StageNow, and what it does, see [StageNow Android device staging](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html) (opens Zebra's web site).

## Step 2: Confirm the Company Portal app has device administrator role

The Company Portal app requires Device Administrator to manage Android devices. To activate the Device Administrator role, some Zebra devices include a user interface (UI) on the device. If the device includes a UI, the Company Portal app prompts the end user to grant Device Administrator during [enrollment](#step-3-enroll-the-device-in-to-intune) (in this article).

If a UI isn't available, use the **DevAdmin Manager** in StageNow to create a profile that manually grants Device Administrator to the Company Portal app.

The following steps provide an overview. For specific details, see Zebra's documentation. 
[Set battery swap mode as device administrator](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool) (opens Zebra's website) may be a good resource.

1. In StageNow, create a profile and select **Xpert Mode**.
2. Add **DevAdmin Manager** to the profile.
3. Set **Device Administration Action** to **Turn On as Device Administrator**.
4. Set **Device Admin Package Name** to `com.microsoft.windowsintune.companyportal`.
5. Set **Device Admin Class Name** to `com.microsoft.omadm.client.PolicyManagerReceiver`.

Continue to publish the profile, and consume it with the StageNow app on the device. The Company Portal app is granted the Device Administrator role.

## Step 3: Enroll the device in to Intune

After completing the first two steps, the Company Portal app is installed on the device. The device is ready to be enrolled in to Intune.

[Enroll Android devices](android-enroll.md) lists the steps. If you have many Zebra devices, you may want to use a [device enrollment manager (DEM) account](device-enrollment-manager-enroll.md). Using a DEM account also prevents end users from unenrolling the devices.

## Step 4: Create a device management profile in StageNow

Use StageNow to create a profile that configures the settings you want to manage on the device. For specific details, see Zebra's documentation. [Profiles](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/) (opens Zebra's website) may be a good resource.

When you create the profile in StageNow, on the last step, select **Export to MDM**. This generates an XML file. Save this file. You need it in a later step.

> [!TIP]
> It's recommended to test the profile before you deploy it to devices in your organization. To test, in the last step when creating profiles with StageNow on your computer, use the **Test** options. Then, consume the StageNow-generated file with the StageNow app on the device. 
> 
> The StageNow app on the device shows logs generated when you test the profile. [Use StageNow logs on Zebra devices running Android in Intune](android-zebra-mx-logs-troubleshoot.md) has information on using StageNow logs to understand errors.

> [!NOTE]
> If you reference apps, update packages, or update other files in your StageNow profile, you want the device to get these updates. To get the updates, the device must connect to the StageNow deployment server when the profile is applied. 
> 
> Or, you can use built-in features in Intune to get these changes, including: 
> - App management features to [add](apps-add.md), [deploy](apps-deploy.md), update, and [monitor](apps-monitor.md) apps.
> - Manage [system and app updates](device-restrictions-android-for-work.md#device-owner-only) on devices running Android Enterprise

After you test the file, the next step is to deploy the profile to devices using Intune.

> [!NOTE]
> Deploy one profile to each device. If there are multiple StageNow profiles you want to deploy on the devices, then export the StageNow profiles, and combine the settings into a single XML file before you add it to Intune. 
> 
> You don’t want two settings that configure the same property in the same XML file. The goal is to prevent conflicts between settings on the device.

## Step 5: Create a profile in Intune

In Intune, create a device configuration profile:

1. In the [Azure portal](https://portal.azure.com), select **All Services** > filter on **Intune** > select **Intune**.
2. Select **Device Configuration** > **Profiles** > **Create profile**.
3. Enter the following properties:

    - **Name**: Enter a descriptive name for the new profile.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
    - **Platform**: Select **Android**.
    - **Profile type**: Select **MX profile (Zebra only)**.

4. In **MX profile in .xml format**, add the XML profile file [you exported from StageNow](#step-4-create-a-device-management-profile-in-stagenow) (in this article).
5. Select **OK** > **Create** to save your changes. The policy is created and shown in the list.

The profile is created, but it's not doing anything yet. Next, [assign the profile](device-profile-assign.md) and [monitor its status](device-profile-monitor.md).

The next time the device checks for configuration updates, the MX profile is deployed to the device. Devices sync with Intune when devices enroll, and then approximately every 8 hours. You can also [force a sync in Intune](device-sync.md). Or, on the device, open the **Company Portal app** > **Settings** > **Sync**. 

> [!TIP]
> - For security reasons, you won’t see the profile XML text after you save it. The text is encrypted, and you only see asterisks (`****`). For your reference, it's recommended to save copies of the MX profiles before you add them to Intune.
> 
> - To update a profile after it's assigned to Zebra devices, create an updated StageNow XML file, edit the existing Intune profile, and add the new StageNow XML file. This new file overwrites the previous StageNow policy in the profile.

## Next steps

[Assign the profile](device-profile-assign.md) and [monitor its status](device-profile-monitor.md).

[Use StageNow logs to troubleshoot Zebra devices](android-zebra-mx-logs-troubleshoot.md).
