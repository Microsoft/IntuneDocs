---
# required metadata

title: App configuration policies for Microsoft Intune
titleSuffix: 
description: Learn how to use app configuration policies on an iOS or Android device in Microsoft Intune.
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708

# optional metadata 

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# App configuration policies for Microsoft Intune

Use app configuration policies in Microsoft Intune to provide configuration settings for an iOS or Android app. These configuration settings allow an app to be customized by using an industry standard approach to app configuration and management. The configuration policy settings are used when the app checks for them, typically the first time it is run.

You can assign an app configuration policy to a group of users and devices by using a combination of include and exclude assignments. Once you add an app configuration policy, you can set the assignments for the app configuration policy. When you set the assignments for the policy, you can choose to include and exclude the groups of users for which the policy applies. When you choose to include one or more groups, you can choose to select specific groups to include or select built-in groups. Built-in groups include **All Users**, **All Devices**, and **All Users + All Devices**.

An app configuration setting, for example, might require you to specify any of the following details:

- A custom port number
- Language settings
- Security settings
- Branding settings such as a company logo

If users were to enter these settings instead, they could do this incorrectly, which could increase the burden on your help desk and slow the adoption of new apps.

App configuration policies can help you eliminate app setup up problems by letting you assign configation settings to a policy that is assigned to users before they run the app. The settings are then supplied automatically, and users need to take no action.

The configuration settings are used whenever the app checks for them. Typically, an app checks for configuration settings the first time the app is run by the user.

You have two options for how to use app configurations with Intune:
- **Managed devices** - The device is managed by Intune as the mobile device management (MDM) provider.
- **Managed apps** - An app is managed without device enrollment.

> [!NOTE]
> As the Microsoft Intune admin, you can control which user accounts are added to Microsoft Office applications on managed devices. You can limit access to only allowed organization user accounts and block personal accounts on enrolled devices. The supporting applications process the app configuration and remove and block unapproved accounts.

## Apps that support app configuration

### Managed devices
You can use app configuration polices for apps that support it. To support app configuration in Intune, apps must have been written to support the use of app configurations as defined by the [Appconfig Community](https://www.appconfig.org/members). Consult your app vendor for details.

### Managed apps
You can prepare your line-of-business apps by either incorporating the Intune App SDK into the app, or wrapping the app after it is developed. The Intune App SDK, available for both iOS and Android, enables your app for Intune app protection configuration policies. It strives to minimize the amount of code changes required from the app developer. For more information, see the [Intune App SDK overview](app-sdk.md).

## Graph API support for app configuration

Additionally, you can use Graph API to accomplish app configuration tasks. For details, see [Graph API Reference MAM Targeted Config](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## Next steps

### Managed devices

- Learn how to use app configuration with your iOS devices.  See [Add app configuration policies for managed iOS devices](app-configuration-policies-use-ios.md).
- Learn how to use app configuration with your Android devices.  See [Add app configuration policies for managed Android devices](app-configuration-policies-use-android.md).

### Managed apps

- Learn how to use app configuration with managed apps. See [Add app configuration policies for managed apps without device enrollment](app-configuration-policies-managed-app.md).
