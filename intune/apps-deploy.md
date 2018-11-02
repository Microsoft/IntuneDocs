---
# required metadata

title: Assign apps to groups in Microsoft Intune
titlesuffix:
description: Learn how to assign an Intune app to groups of users or devices.
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mghadial
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure
---

# Assign apps to groups with Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

After you've [added an app](apps-add.md) to Microsoft Intune, you can assign the app to users and devices. It is important to note that you can assign an app to a device whether or not the device is managed by Intune. 

The following table lists the various options for assigning apps to users and devices:

||||
|-|-|-|-|
|&nbsp;|**Devices enrolled with Intune**|**Devices not enrolled with Intune**|
|Assign to users|Yes|Yes|
|Assign to devices|Yes|No|
|Assign wrapped apps or apps that incorporate the Intune SDK (for app protection policies)|Yes|Yes|
|Assign apps as Available|Yes|Yes|
|Assign apps as Required|Yes|No|
|Uninstall apps|Yes|No|
|Receive app updates from Intune|Yes|No|
|End users install available apps from the Company Portal app|Yes|No|
|End users install available apps from the web-based Company Portal|Yes|Yes|

> [!NOTE]
> Currently, you can assign iOS and Android apps (line-of-business and store-purchased apps) to devices that aren't enrolled with Intune.
>
> To receive app updates on devices that aren't enrolled with Intune, device users must go to their organization's Company Portal and manually install app updates.

## To assign an app

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Select **All services** > **Intune**. Intune is located in the **Monitoring + Management** section.
3. In the **Intune** menu, select **Client apps**.
4. In the **Manage** section of the menu, select **Apps**.
5. In the **Apps** pane, select the app you want to assign.
6. In the **Manage** section of the menu, select **Assignments**.
7. Select **Add Group** to open the **Add group** pane that is related to the app.
8. For the specific app, select an **assignment type**:
   - **Available for enrolled devices**: Users install the app from the Company Portal app or website.
   - **Available with or without enrollment**: Assign this app to groups of users whose devices are not enrolled with Intune. Apps from Managed Google Play don't support this option. 
   - **Required**: The app is installed on devices in the selected groups.
   - **Uninstall**: The app is uninstalled from devices in the selected groups.

     > [!NOTE]
     > **For iOS apps only**: If you have created an iOS VPN profile that contains per-app VPN settings, you can select the VPN profile under **VPN**. When the app is run, the VPN connection is opened. For more information, see [VPN settings for iOS devices](vpn-settings-ios.md).
     > **For Android apps only**: If you deploy an Android line of business (LOB) app as **Available with or without enrollment**, reporting status will only be available on enrolled devices. This information will not be available for devices not enrolled in Intune.

9. To select the groups of users that are affected by this app assignment, select **Included Groups**.
10. After you have selected one or more groups to include, select **Select**.
11. In the **Assign** pane, select **OK** to complete the included groups selection.
12. If you want to exclude any groups of users from being affected by this app assignment, select **Exclude Groups**.
13. If you have chosen to exclude any groups, in **Select groups**, select **Select**.
14. In the **Add group** pane, select **OK**.
15. In the app **Assignments** pane, select **Save**.

The app is now assigned to the groups that you selected. For more information about including and excluding app assignments, see [Include and exclude app assignments](apps-inc-exl-assignments.md).

## How conflicts between app intents are resolved

Sometimes, the same app is assigned to multiple groups but with different intents. The information in the following table can help you understand the resulting intent when this occurs:

||||
|-|-|-|
|**Group 1 intent**|**Group 2 intent**|**Resulting intent**|
|User Required|User Available|Required and Available|
|User Required|User Not Available|Required|
|User Required|User Uninstall|Required|
|User Available|User Not Available|Not Available|
|User Available|User Uninstall|Uninstall|
|User Not Available|User Uninstall|Uninstall
|User Required|Device Required|Both exist, Intune treats Required
|User Required|Device Uninstall|Both exist, Intune resolves Required
|User Available|Device Required|Both exist, Intune resolves Required (Required and Available)
|User Available|Device Uninstall|Both exist, Intune resolves Available.<br><br>App shows up in the Company Portal.<br><br>If the app is already installed (as a required app with previous intent), the app is uninstalled.<br><br>If the user selects **Install from the Company Portal**, the app is installed, and the uninstall intent is not honored.|
|User Not Available|Device Required|Required|
|User Not Available|Device Uninstall|Uninstall|
|User Uninstall|Device Required|Both exist, Intune resolves Required|
|User Uninstall|Device Uninstall|Both exist, Intune resolves Uninstall|
|Device Required|Device Uninstall|Required|
|User Required and Available|User Available|Required and Available|
|User Required and Available|User Uninstall|Required and Available|
|User Required and Available|User Not Available|Required and Available|
|User Required and Available|Device Required|Both exist, Required and Available
|User Required and Available|Device Not Available|Required and Available|
|User Required and Available|Device Uninstall|Both exist, Intune resolves Required (Required and Available)
|User Not Available|Device Not Available|Not Available|
|User Available|Device Not Available|Available|
|User Required|Device Not Available|Required|
|User Available without enrollment|User Required and Available|Required and Available
|User Available without enrollment|User Required|Required
|User Available without enrollment|User Not Available|Not Available
|User Available without enrollment|User Available|Available|
|User Available without enrollment|Device Required|Required and Available without enrollment|
|User Available without enrollment|Device Not Available|Available without enrollment|
|User Available without enrollment|Device Uninstall|Uninstall and Available without enrollment.<br><br>If the user didn’t install the app from the Company Portal, the uninstall is honored.<br><br>If the user installs the app from the Company Portal, the install is prioritized over the uninstall.|

> [!NOTE]
> For managed iOS store apps only, when you add these apps to Microsoft Intune and assign them as **Required**, the apps are automatically created with both **Required** and **Available** intents.<br><br>
> iOS Store apps (not iOS VPP apps) that are targeted with required intent will be enforced on the device at the time of the device check-in and will also show in the Company Portal app.

## Next steps

To learn more about monitoring app assignments, see [How to monitor apps](apps-monitor.md).
