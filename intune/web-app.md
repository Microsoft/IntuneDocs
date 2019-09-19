---
# required metadata

title: Add web apps to Microsoft Intune
titleSuffix: 
description: Learn about adding web apps (client-server applications) to Microsoft Intune.
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775

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

# Add web apps to Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune supports a variety of app types, including web apps. A web app is a client-server application. The server provides the web app, which includes the UI, content, and functionality. Additionally, modern web-hosting platforms commonly offer security, load balancing, and other benefits. A web app is separately maintained on the web. You use Microsoft Intune to point to this app type. You also assign the groups of users that can access this app. 

Before you can manage and assign an app for your users, add the app to Intune. Intune creates a shortcut to the web app on the user's device home screen.

> [!Note]
> Web apps are not supported on Android work profile devices.

## Add a web app to Intune
To add an app to Intune as a shortcut to an app on the web, do the following:

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. In the **Intune** pane, select **Client apps**.
4. In the **Client apps** workload pane, under **Manage**, select **Apps**.
5. In the **Apps** pane, select **Add**.
6. In the **Add app** pane, in the **App type** drop-down list, select the **Web link** type.
7. Select **Configure**.
8. In the **App information** pane, add the following information:
    - **Name**:  Enter the name of the app as it is to be displayed in the company portal. 

        > [!NOTE]
        > If you change the name of the app through the Intune azure portal after you have deployed and installed the app, the app will no longer be able to be targeted using commands.

    - **Description**: Enter a description for the app. This description is displayed to users in the company portal.
    - **Publisher**: Enter the name of the publisher of this app.
    - **App URL**: Enter the URL of the website that hosts the app that you want to assign.
    - **Category**: Optionally, select one or more of the built-in app categories, or a category that you created. Doing so makes it easier for users to find the app when they browse the company portal.
    - **Display this as a featured app in the Company Portal**: Select this option to display the app suite prominently on the main page of the company portal when users browse for apps.
    - **Require a managed browser to open this link**: Select this option to assign to your users a link to a website or web app that they can open in the Intune managed browser. This browser must be installed on their device.
    - **Logo**: Upload an icon that will be associated with the app. This icon is displayed with the app when users browse the company portal.
9. Select **OK**.
10. In the **Add app** pane, select **Add**.

> [!Note]
> Users must add the Intune widget to their home screen to display web apps that have been assigned to Android devices.
>
> Currently, deployment of Intune web apps to iOS devices is associated with the management profile and cannot be removed manually. You can change the deployment type to **Uninstall** in the Intune portal, at which point the web app can be removed automatically. However, if you remove the deployment before changing the app assignment intent to **Uninstall**, the web app will be permanently in place on the device until the device is un-enrolled from Intune.

## Next steps

The app that you've created is displayed in the apps list, where you can assign it to the groups that you select. For help, see [Assign apps to groups](apps-deploy.md). 
