---
# required metadata

title: Reset device passcodes with Microsoft Intune - Azure | Microsoft Docs
description: Remove or reset the passcode by using the remove passcode action on devices you manage or monitor with Intune.
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: ilwu
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Reset or remove a device passcode in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

To create a new passcode for a device, use the **Remove passcode** action.

## Supported platforms

- Android devices enrolled with a Work profile, version 8.0 and later
- Android devices on version 6.0 or earlier
- iOS 
 	 
## Unsupported platforms

- Android devices enrolled with a Work profile, version 7.0 and earlier
- Android devices on version 7.0 or later
- macOS
- Windows

## Reset a passcode

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Select **All services**, filter on **Intune**, and then select **Microsoft Intune**.
3. Select **Devices**, and then select **All devices**.
4. From the list of devices you manage, select a device, and choose **...More**. Then choose the **Remove passcode** device remote action.

## Resetting Android for Work passcodes

Supported Android for Work devices receive a new managed profile unlock password or a managed profile challenge for the end user. For devices on Android 8.0 or later with Work profiles, end users receive notifications to activate their reset passcode token immediately after enrollment is completed. The notification is displayed if a Work profile password is required and set. Once their passcode is entered, the notification is dismissed.

## Resetting iOS passcodes

Passcodes are removed from iOS devices. If there is a passcode compliance policy is set, then the device will prompt the user to set a new passcode in Settings. 

## Next steps

To see the status of the action you just took, in **Devices**, select **Device actions**.
