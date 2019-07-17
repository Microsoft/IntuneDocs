---
# required metadata

title: Install Office 365 to macOS devices using Microsoft Intune
titleSuffix: 
description: Learn how you can use Microsoft Intune to install Office 365 apps on macOS devices.
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Assign Office 365 to macOS devices with Microsoft Intune

This app type makes it easy for you to assign Office 365 2016 apps to macOS devices. By using this app type, you can install Word, Excel, PowerPoint, Outlook, and OneNote. To help keep the apps more secure and up to date, the apps come with Microsoft AutoUpdate (MAU). The apps that you want are displayed as one app in the list of apps in the Intune console.

## Before you start

Before you begin adding Office 365 to macOS devices, understand the following details:

- Devices to which you deploy these apps must be running macOS 10.10 or later.
- Intune supports adding the Office apps that are included with Office 2016 for Mac suite only.
- If any Office apps are open when Intune installs the app suite, users might lose data from unsaved files.

## Create and configure the app suite

Add Office 365 from the **Apps** pane.
1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. In the **Intune** pane, select **Client apps**.
4. In the **Client apps** workload pane, under **Manage**, select **Apps**. 
5. Select **Add**.
6. In the **App type** list, in the **Office 365 Suite** group, select **macOS**.
7. To get information about the app suite, select **App Suite Information**.  
    This information helps you to identify the app suite in Intune, and it helps users to find the app suite in the company portal.
8. Enter the following information:
    - **Suite Name**: Enter the name of the app suite as it is displayed in the company portal. Make sure that all suite names that you use are unique. If the same app suite name exists twice, only one of the apps is displayed to users in the company portal.
    - **Suite Description**: Enter a description for the app suite.
    - **Publisher**: Microsoft appears as the publisher.
    - **Category**: Select one or more of the built-in app categories, or a category you created. This setting makes it easier for users to find the app suite when they browse the company portal.
    - **Display this as a featured app in the Company Portal**: Select this option to display the app suite prominently on the main page of the company portal when users browse for apps.
    - **Information URL**: Optionally, enter the URL of a website that contains information about this app. The URL is displayed to users in the company portal.
    - **Privacy URL**: Optionally, enter the URL of a website that contains privacy information for this app. The URL is displayed to users in the company portal.
    - **Developer**: Microsoft appears as the developer.
    - **Owner**: Microsoft appears as the owner.
    - **Notes**: Optionally, enter any notes that you want to associate with this app.
    - **Logo**: The Office 365 logo is displayed with the app when users browse the company portal.
9. Select **OK**.
10. On the **Add app** pane, select **Add**.  
    The suite appears in the list of apps as a single entry.

## Configure app assignments

In this step, configure the assignments for the app suite. 

1. In the list of apps, select the **Office 365** app suite to display the **Office 365** overview pane.
2. In the **Office 365** pane, select **Assignments**.
3. To add a group that will use the app suite, select **Add group**.  
    The **Add group** pane is displayed.
4. Set the **Assignment type** to **Required** or **Available**.
5. Assign the suite to the groups that you select. For more information, see [Assign apps to groups with Microsoft Intune](apps-deploy.md).

    >[!Note]
    > You cannot uninstall the Office 365 app suite through Intune.

5. In the **Assign** pane, select **OK**.
6. In the **Add group** pane, select **OK**.
7. To commit your assignments, select **Save**.

## Next steps

- To learn about adding Office 365 apps to Windows 10 devices, see [Assign Office 365 ProPlus 2016 apps to Windows 10 devices with Microsoft Intune](apps-add-office365.md).
- To learn about including and excluding app assignments from groups of users, see [Include and exclude app assignments](apps-inc-exl-assignments.md).
