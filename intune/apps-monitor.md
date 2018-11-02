---
# required metadata

title: Monitor app information and assignments
titlesuffix: Microsoft Intune
description: After you've assigned an app to users or devices, use this information to help you monitor the app's status.
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/10/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mghadial
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure
---

# Monitor app information and assignments with Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune provides several ways to monitor the properties of apps that you manage and to manage app assignment status.

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Select **All services** > **Intune**. Intune is located in the **Monitoring + Management** section.
3. In the **Intune** menu, select **Client apps**.
4. In the **Manage** section of the menu, select **Apps**.
5. In the list of apps, select an app to monitor. You'll then see the app pane, which includes an overview of the device status and the user status.

> [!NOTE]
> Android Store apps that are deployed as **Available** do not report their installation status.

## App overview pane

In the app pane, you can review details about the status of an app in your environment.

### Essentials
The **Essentials** section contains the following information about the app:

 | **App details**            | **Description**                                                      |
|------------------------|------------------------------------------------------------------|
| **Publisher**          | The publisher of the app.                                            |
| **Operating system**   | The app operating system (Windows, iOS, Android, and so on). |
| **Created**             | The date and time when this revision was created.                         |
| **Assigned**           | Whether the app has been assigned (**Yes** or **No**).                  |

### Device and user status graphs
The graphs show the number of apps for the following status:

| **Device status**       | **Description**                                       |
|-----------------------|-------------------------------------------------------|
| **Installed**         | The number of apps installed.                         |
| **Not Installed**     | The number of apps not installed.                     |
| **Failed**            | The number of failed installations.                   |
| **Install Pending**   | The number of apps that are in the process of being installed. |
| **Not Applicable**           | The number of apps for which status is not applicable.            |

> [!NOTE]
> The number of discovered apps may not match the app install status count. Possibilities for inconsistencies include:
>    - A targeting change of an installed managed app can cause the install count in the status blade to decrement, but remain reported in the detected apps.
>    - Targeting multiple instances of the same app in a tenant will result in different counts due to potential overlap of users or devices. Each instance of the app will count overlapping users, but discovered apps will have duplicated counts.
>    - Discovered apps and app status are collected at different time intervals, which could cause a discrepancy in the app counts.
>
> Also be aware that Android line of business (LOB) apps deployed as **Available with or without enrollment** only report app installation status for enrolled devices. This information will not be available for devices not enrolled in Intune.
 
### Device install status

A device status list is shown when you select **Device install status** in the **Monitor** section of the menu. The details table includes the following columns:

| **Device column**      | **Description**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Device name**      | The name of the device on platforms that allow naming a device. On other platforms, Intune creates a name from other properties. This attribute isn't available to any other device.                                                                       |
| **User name**        | The name of the user.                                                                                                                                                                                                                                      |
| **Platform**         | The operating system of the device (Windows, iOS, Android, and so on).                                                                                                                                                                                           |
| **Version**          | The version number of the app. For line-of-business apps, the full version number of the app is shown. The full version number identifies a specific release of the app. The number appears as _Version_(_Build_). For example,  2.2(2.2.17560800). |
| **Status**           | The status of the app.                                                                                                                                                                                                                                     |
| **Status details**   | The details of the status.                                                                                                                                                                                                                                     |
| **Last check-in**    | The date of the device's last sync with Intune.                                                                                                                                                                                                                  |


### User install status

A user status list is shown when you select **User install status** in the **Monitor** section of the menu. The details table includes the following columns:

| **User column**     | **Description**                           |
|---------------------|-------------------------------------------|
| **Name**            | The name of the user in Azure Active Directory.         |
| **User name**       | The unique name of the user.              |
| **Installations**   | The number of apps installed by the user. |
| **Failures**        | The number of failed app installations for the user.     |
| **Not installed**   | The number of apps not installed by the user. |


## Next steps

- To learn more about working with your Intune data, see [Use the Intune Data Warehouse](reports-nav-create-intune-reports.md).
- To learn about app configuration policies, see [App configuration policies for Intune](app-configuration-policies-overview.md).
