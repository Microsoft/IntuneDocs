---
# required metadata

title: Intune enrollment method capabilities for Windows devices
titleSuffix: Microsoft Intune
description: Capabilities for each enrollment method for Windows devices.
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer:
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.custom: seodec18
ms.collection: M365-identity-device-management
---

# Intune enrollment method capabilities for Windows devices
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

There are several methods to enroll your workforce’s devices in Intune. Each method has different best practices and capabilities, as shown in the tables below.

## Best practices by enrollment method
| **Best practices** | **[Azure AD joined](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD joined with Autopilot (User driven mode)](enrollment-autopilot.md)** |**[Azure AD joined with Autopilot (Self deploying mode)](enrollment-autopilot.md)** |**[Bulk](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Co-management](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Commonly used in EDU|![X](media/xmark.png)|![Checkmark](media/checkmark.png)|![X](media/xmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Devices can be used as shared devices|![X](media/xmark.png)|![X](media/xmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Personal devices must access company resources|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Checkmark](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Self-servicing of apps|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|

## Capabilities by enrollment method

| **Capabilities** | **[Azure AD joined](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD joined with Autopilot (User driven mode)](enrollment-autopilot.md)** |**[Azure AD joined with Autopilot (Self deploying mode)](enrollment-autopilot.md)** |**[Bulk](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Co-management](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Conditional Access                                      |![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|
|User gets associated with the device                    |![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|
|Requires Azure AD Premium                               |![X](media/xmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|
|Device can assess resources protected by CA             |![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![X](media/xmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|
|Users must not be admins on their devices               |![X](media/xmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Ability to configure the device setup experience        |![X](media/xmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Ability to enroll devices without user interaction      |![X](media/xmark.png)|![X](media/xmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![X](media/xmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|
|Ability to run PowerShell scripts                       |![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)| 
|Supports automatic enrollment after AD domain join      |![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|
|Supports automatic enrollment after Hybrid Azure AD join|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|
|Supports automatic enrollment after Azure AD join       |![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![Checkmark](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|

## Next steps

[Set up enrollment for Windows](windows-enroll.md)
