---
# required metadata

title: Windows 10 app deployment using Microsoft Intune
titleSuffix: 
description: Learn about Windows 10 app deployment scenarios available with Microsoft Intune.
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Windows 10 app deployment using Microsoft Intune 

Microsoft Intune currently support a variety of apps types and deployment scenarios on Windows 10 devices. After you've added an app to Intune, you can assign the app to users and devices. The following information provides more details related to the supported Windows 10 scenarios. Additionally, the following information provides key details to note when deploying apps to Windows. 

Line-of-business (LOB) apps and Microsoft Store for Business apps are the app types supported on Windows 10 devices. The file extensions for Windows apps include **.msi**, **.appx**, and **.appxbundle**.  

> [!Note]
> The minimum needed Windows 10 updates to deploy modern apps are as follows:
> - For Windows 10 1803, [May 23, 2018—KB4100403 (OS Build 17134.81)](https://support.microsoft.com/help/4100403/windows-10-update-kb4100403).
> - For Windows 10 1709, [June 21, 2018—KB4284822 (OS Build 16299.522)](https://support.microsoft.com/help/4284822).

## Windows 10 Line-of-business apps

Windows 10 LOB apps are signed and uploaded to the Intune admin console and can include both modern apps, such as Universal Windows Platform (UWP) apps and Windows App Packages (AppX), as well as Win 32 apps, such as simple Microsoft Installer package files (MSI). Updates of LOB apps must be manually uploaded and deployed each time by the admin. Updates that are deployed are automatically installed on end-user devices that have installed the app with no user intervention. The user has no control over the updates. 

## Microsoft Store for Business apps

Microsoft Store for Business apps that are modern apps purchased from the Microsoft Store for Business admin portal and are then synced over to Microsoft Intune for management. The apps can either be **online licensed** or **offline licensed**. Updates of Microsoft Store for Business apps are managed directly by the Microsoft Store, with no additional action required by the admin. The admin can also prevent updates to specific apps using custom Uniform Resource Identifier (URI). For more information, see [Enterprise app management - Prevent app from automatic updates](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates). On the device, the end user can also disable updates for all Microsoft Store for Business apps on the device. 

## Installing apps on Windows 10 devices
Depending on the app type, the app can be installed on a Windows 10 device in one of two ways:

- **User Context**: When an app is deployed in user context, the managed app will be installed for that user on the device when the user signs-in to the device. Note that the app installation will not succeed until the user signs-in to the device. 
  - Modern line-of-business apps and Microsoft store for business apps (both online and offline) can be deployed in user context and will support both the Required and Available intent.
  - Win32 apps built as **User Mode** or **Dual Mode** can be deployed in user context and will support both **Required** and **Available** intent. 
- **Device Context**: When an app is deployed in device context, the managed app will be installed directly to the device by Intune.
  - Only modern line-of-business apps and offline licensed Microsoft Store for Business apps can be deployed in device context and will only support the Required intent.
  - Win32 apps built as **Machine Mode** or **Dual Mode** can be deployed in user context and will support only the **Required** intent.

> [!NOTE]
> For Win32 apps built as **Dual Mode** apps, you (the admin) will need to pick if the app will function as a **User Mode** or **Machine Mode** app for all assignments associated with that instance. The deployment context cannot be changed per assignment.  

When an app is deployed in device context, the installation will only succeed when targeted to a device that supports device context. In addition, deploying in device context supports the following conditions:
- If an app is deployed in device context and targeted to a user, the installation will fail with the following status and error displayed in the admin console:
  - Status: Failed.
  - Error: A user can’t be targeted with a Device context install.
- If an app is deployed in device context but targeted to a device that does not support device context, the installation will fail with the following status and error in the admin console:
  - Status: Failed.
  - Error: This platform does not support device context installs. 

> [!Note]
> Once an app assignment is saved with a specific deployment, the context cannot be changed for that assignment, except for modern apps. For the modern app case, context can be changed from user context to device context. 

In the event that there is a conflict in policies on a single user/device, the following are the policy priorities that will be used to determine the final policy:
- A device context policy is a higher priority than a user context policy. 
- An install policy is a higher priority than an uninstall policy.

For more information about assigning apps using Microsoft Intune, see [Assign apps to groups with Microsoft Intune](apps-deploy.md) and [Include and exclude app assignments in Microsoft Intune](apps-inc-exl-assignments.md). For more information about app types in Intune, see [Add apps to Microsoft Intune](apps-add.md).

## Next steps

- To learn more about assigning apps to groups, see [Assign apps to groups with Microsoft Intune](apps-deploy.md).
- To learn more about monitoring app assignments, see [How to monitor apps](apps-monitor.md).
