---
# required metadata

title: How your Android users get their apps 
description: Methods for making Android apps available to end users
keywords:
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/21/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-classic
ms.collection: M365-identity-device-management
---

# How your Android users get their apps

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Use this information to understand how and where your Android end users get the apps that you distribute through Microsoft Intune. The information can vary by device type (native Android devices or Samsung Knox Standard devices).

## Native (non-Samsung Knox Standard) Android devices

| App type | Line-of-business (LOB) apps | Play Store apps  |
| ------------- |-------------| -----|
| Available apps      | Users tap **install** in the Company Portal. A notification appears, which users then tap to start the installation. After the installation is successful, the notification disappears. | Users tap the app in the Company Portal and are taken to an app page in the Play Store, where they can start the installation.|
| Required apps      | Users are shown a notification, which they cannot dismiss, indicating that they need to install an app. Users tap the notification to start the installation. After the installation is successful, the notification disappears.    | Users are shown a notification, which they cannot dismiss, indicating that they need to install an app. Users tap the notification and are taken to an app page in the Play Store, where they can start the installation. After the installation is successful, the notification disappears. |

Your end users need to allow installation from unknown sources in order to install [LOB apps](lob-apps-android.md). These are normally found in two different places:

* **Android 7.1.2 and lower**: **Settings** > **Security** > **Unknown sources**
* **Android 8.0 and above**: **Settings** > **Apps & notifications** > **Special app access** > **Install unknown apps** > **Company Portal** > **Allow from this source**

If this occurs, the Company Portal app will inform and directly guide the end user to the appropriate setting. 

## Samsung Knox Standard Android devices

| App type | Line-of-business (LOB) apps | Play Store apps  |
| ------------- |-------------| -----|
| Available apps      | Users tap **install** in the Company Portal. The app installs without further user intervention. | Users tap the app in the Company Portal and are taken to an app page in the Play Store, where they can start the installation.|
| Required apps      | The app is installed without any user intervention.    | Users are shown a notification, which they cannot dismiss, indicating that they need to install an app. Users tap the notification and are taken to an app page in the Play Store, where they can start the installation. After the installation is successful, the notification disappears. |

Apps can be managed or unmanaged, as described below. The process of making apps managed is the same for all types of Android devices.

**Managed apps** - These are apps that can be managed through policies. They have been "wrapped" by Intune or built with the Intune App SDK. These apps can be managed by Intune, and application policies can be applied to them.

**Unmanaged apps** - These are apps that cannot be managed through policies. They have not been wrapped by Intune or do not incorporate the Intune App SDK. Application policies cannot be applied to these apps.

### See also
[Add apps with Microsoft Intune](apps-add.md)

[How your iOS users get their apps](end-user-apps-ios.md)

[How your Windows users get their apps](end-user-apps-windows.md)
