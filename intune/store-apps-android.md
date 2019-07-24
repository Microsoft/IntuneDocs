---
# required metadata

title: Add Android store apps to Microsoft Intune
titleSuffix: 
description: Learn how to add Android store apps from the Google Play store to Microsoft Intune.
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5

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

# Add Android store apps to Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Before you assign an app to a device or a group of users, you must first add the app to Microsoft Intune. 

## Add an app

You can add an Android store app to Intune from the Azure portal by doing the following:

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. In the **Intune** pane, select **Client apps**.
4. In the **Client apps** workload pane, under **Manage**, select **Apps**.
5. Select **Add**.
6. In the **Add App** pane, under the available **Store apps** types, select **Android**.
7. To configure the app information, select **Configure**, and then provide the following information. For Android apps, navigate to the [Google Play store](https://play.google.com/store) and search for the app you want to deploy. Select the app and make a note app details. Depending on the app you've chosen, some values might have been automatically filled in.
    - **Name**: Enter the name of the app as it is to be displayed in the company portal. Make sure that any app name that you use is unique. If an app name is duplicated, only one name is displayed to users in the company portal.
    - **Description**: Enter a description for the app. This description is displayed to users in the company portal.
    - **Publisher**: Enter the name of the publisher of the app.
    - **Appstore URL**: Enter the app store URL of the app that you want to create.
    - **Minimum operating system**: In the list, select the earliest operating system version on which the app can be installed. If you assign the app to a device with an earlier operating system, it will not be installed.
    - **Category**: Optionally, select one or more of the built-in app categories, or a category that you created. Doing so makes it easier for users to find the app when they browse the company portal.
    - **Display this as a featured app in the Company Portal**: Select this option to display the app suite prominently on the main page of the company portal when users browse for apps. Applies to apps deployed with Available intent.
    - **Information URL**: Optionally, enter the URL of a website that contains information about this app. The URL is displayed to users in the company portal.
    - **Privacy URL**: Optionally, enter the URL of a website that contains privacy information for this app. The URL is displayed to users in the company portal.
    - **Developer**: Optionally, enter the name of the app developer.
    - **Owner**: Optionally, enter a name for the owner of this app, for example, *HR department*.
    - **Notes**: Optionally, enter any notes that you want to associate with this app.
    - **Logo**: Optionally, upload an icon that will be associated with the app. This icon is displayed with the app when users browse the company portal.
8. Select **OK**.
9. Select **Add**.

The app you've created is displayed in the apps list, where you can assign it to the groups that you select. 

## Next steps

- [Assign apps to groups](apps-deploy.md)
