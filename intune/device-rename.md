---
# required metadata

title: Rename a device with Microsoft Intune - Azure | Microsoft Docs
description: Rename a device by using Microsoft Intune.
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Rename a device in Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

The **Rename device** action lets you rename a device that is enrolled in Intune. The device's name is changed in Intune and on the device.

You can rename the following types of devices:
- corporate-owned Windows 
- iOS supervised
- corporate-owned MacOS 10

This feature doesn't currently support renaming hybrid Azure AD Windows devices.

## Rename a device

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Choose **Devices** > **All devices** > choose a device > **More** > **Rename device**.
4. In the **Rename device** blade, type the new name in the text box. You can use letters, numbers, and hyphens. The name must contain at least one letter or hyphen.
5. If you want to restart the device after renaming it, choose **Yes** next to **Restart after rename**.
6. Choose **Rename**.



## Next steps

To see the status of the **Rename** device action, check the **Overview** page for the device.
