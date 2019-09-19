---
# required metadata

title: Discovered apps
titleSuffix: Microsoft Intune
description: Understand details about the detected apps that Intune found on a device.
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 07dd262f-13e7-4cb2-9cc2-b755d1c276cf

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: 
ms.collection: M365-identity-device-management
---

# Intune discovered apps

Intune **discovered apps** is a list of detected apps on the Intune enrolled devices in your tenant. It acts as a software inventory for your tenant. **Discovered apps** is a separate report from the [app installation](apps-monitor.md) reports. For personal devices, Intune never collects information on applications that are unmanaged. On corporate devices, any app whether it is a managed app or not is collected for this report. Below is the table mapping the expected behavior. In general, the report refreshes every 7 days from the time of enrollment (not a weekly refresh for the entire tenant). The only exception to this refresh period is application information collected through the Intune Management Extension for Win32 Apps, which is collected every 24 hours.

## Monitor discovered apps with Intune

Intune provides an aggregated list of detected apps on the Intune enrolled devices in your tenant.

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. In the **Intune** pane, select **Client apps** > **Discovered apps**.

>[!NOTE]
>You can export the list of discovered apps to a .csv file by selecting **Export** from the **Discovered apps** blade.
>
>For discovered Win32 apps, there currently is no aggregate count. This type of data can only be viewed on a per-device basis.

Intune also provides the list of discovered apps for the individual device in your tenant. 

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. In the Intune pane, select **Devices** > **All Devices**.
3. Select a device.
4. To view detected apps for this device, select **Discovered Apps** in the **Monitor** section. 

## Details of discovered apps

The following list provides the app platform type, the apps that are monitored for personal devices, the apps that are monitored for company-owned devices, and the refresh cycle. For more information about app types supported by Intune, see [App types in Microsoft Intune](apps-add.md#app-types-in-microsoft-intune).

| Platform | For personally-owned devices | For company-owned devices | Refresh cycle |
|------------------------------------------------------------------------|----------------------------------|--------------------------------------------------|---------------------------------------|
| Windows 10 (Win32 Apps) NOTE: [Requires Intune Management Extension](intune-management-extension.md) on device | Not Applicable | All Win32 Apps found in Add Remove Programs list | Every 24 hours from device enrollment |
| Windows 10 (Modern Apps) | Only managed modern apps | All modern apps installed on the device | Every 7 days from device enrollment |
| Windows 8.1 | Only managed apps | Only managed apps | Every 7 days from device enrollment |
| Windows Phone 8 | Only managed apps | Only managed apps | Every 7 days from device enrollment |
| Windows RT | Only managed apps | Only managed apps | Every 7 days from device enrollment |
| iOS | Only managed apps | All apps installed on the device | Every 7 days from device enrollment |
| macOS | All apps installed on the device | All apps installed on the device | Every 7 days from device enrollment |
| Android | Only managed apps | All apps installed on the device | Every 7 days from device enrollment |
| Android Enterprise | Only managed apps | Only apps installed in the Work Profile | Every 7 days from device enrollment |

> [!NOTE]
>Windows 10 Hybrid Azure AD Joined devices with the Intune Management Extension do not currently collect app inventory as per the above schedule. This is a known issue. Any changes or updates on this behavior are announced in [in development](in-development.md) and/or [what's new](whats-new.md).

The number of discovered apps may not match the app install status count. Possibilities for inconsistencies include:
- A targeting change of an installed managed app can cause the install count in the status blade to decrement, but remain reported in the detected apps.
- Targeting multiple instances of the same app in a tenant will result in different counts due to potential overlap of users or devices. Each instance of the app will count overlapping users, but discovered apps will have duplicated counts.
- Discovered apps and app status are collected at different time intervals, which could cause a discrepancy in the app counts.

## Next steps

- [App types in Microsoft Intune](apps-add.md#app-types-in-microsoft-intune)
- [Monitor app information and assignments with Microsoft Intune](apps-monitor.md)
