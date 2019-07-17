---
# required metadata

title: Add built-in apps to mobile devices using Microsoft Intune
titleSuffix: 
description: Learn how you can use Intune to make it easier to install built-in apps mobile devices.
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec

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

# Add built-in apps to Microsoft Intune

The *built-in* app type makes it easy for you to assign curated managed apps, such as Office 365 apps, to iOS and Android devices. You can assign specific apps for this app type, such as Excel, OneDrive, Outlook, Skype, and others. After you add an app, the app type is displayed as either *Built-in iOS app* or *Built-in Android app*. By using the built-in app type, you can choose which of these apps to publish to device users.

In earlier versions of the Intune console, Intune provided several default managed Office 365 apps, such as Outlook and OneDrive. The app types for these managed apps were tagged as *Managed iOS Store App* or *Managed Android App*. Instead of using these app types, we recommend that you use the built-in app type. By using the built-in app type, you have the additional flexibility to edit and delete Office 365 apps.

>[!NOTE]
>Default Office 365 apps that are tagged as *Managed iOS Store* and *Managed Android App* are removed from the app list when all assignments are deleted.

## Add a built-in app

To add a built-in app to your available apps in Microsoft Intune, do the following:
1. Sign in to the Azure portal.
2. To display the Microsoft Intune pane, select **More Services** > **Monitoring + Management** > **Intune**.
3. In the **Intune** pane, select **Client apps**.
4. In the **Client apps** pane, under **Manage**, select **Apps**.
5. Select **Add**.
6. In the **Add** app pane, in the **App type** list, select **Built-In app**.
7. Select **Select app**.
8. In the **Built-In app** pane, select the apps that you want to include.
9. In the **Add app** pane, select **Add**.

## Configure app information

You can modify information about the built-in app. This information helps you to identify the app in Intune and helps users find the app in the company portal.
1. In the **Client apps - Apps** pane, select the built-in app that you want to modify.  
    A pane for the built-in app is displayed.
2. Under **Manage**, select the **Properties** option.
3. To modify the built-in app information, select the **Configure** option.
4. In the **App information** pane, you can modify the following information:
    - **Name**: Enter the name of the built-in app as it is displayed in the company portal. Make sure all names that you use are unique. If the same app name exists twice, only one of the apps is displayed to users in the company portal.
    - **Description**: Enter a description for the app. 
    - **Publisher**: Enter the name of the publisher of the app.
    - **Category**: Optionally, select one or more of the built-in app categories. Setting this option makes it easier for users to find the app when they browse the company portal.
    - **Display this as a featured app in the company portal**: Display the app prominently on the main page of the company portal when users browse for apps.
    - **Information URL**: Optionally, enter the URL of a website that contains information about this app. The URL is displayed to users in the company portal.
    - **Privacy URL**: Optionally, enter the URL of a website that contains privacy information for this app. The URL is displayed to users in the company portal.
    - **Developer**: Optionally, enter the name of the app developer.
    - **Owner**: Optionally, enter a name for the owner of this app (for example, *HR department*).
    - **Notes**: Enter any notes that you want to associate with this app.
    - **Upload Icon**: Upload an icon that is displayed with the app when users browse the company portal.
4. Select **OK**.
5. In the **Properties** pane, select **Save**.

## Next steps

- You can now assign the apps to the groups that you choose. For more information, see [Assign apps to groups](apps-deploy.md).
