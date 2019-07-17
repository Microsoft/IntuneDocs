---
# required metadata

title: Add a Windows line-of-business app to Microsoft Intune
titleSuffix:
description: Learn how to add a Windows line-of-business (LOB) app using Microsoft Intune.
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/10/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896

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

# Add a Windows line-of-business app to Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A line-of-business (LOB) app is one that you add from an app installation file. This kind of app is typically written in-house. The following steps provide guidance to help you add a Windows LOB app to Microsoft Intune.

## Step 1: Specify the software setup file

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. In the **Intune** pane, select **Client apps**.
4. In the **Client apps** workload, select **Manage** > **Apps**.
5. Above the list of apps, select **Add**.
6. In the **Add app** pane, select **Line-of-business app**.

## Step 2: Configure the app package file

1. In the **Add app** pane, select **App package file**.
2. In the **App package file** pane, select the browse button. Then select a Windows installation file with the extension **.msi**, **.appx**, or **.appxbundle**.

    > [!NOTE]
    > The file extensions for Windows apps include **.msi**, **.appx**, **.appxbundle**, **.msix**, and **.msixbundle**.  

1. When you're finished, select **OK**.

## Step 3: Configure app information

1. In the **Add app** pane, select **App information**.
2. In the **App information** pane, configure the following information. Some of the values in this pane might be automatically filled in.
    - **Name**: Enter the name of the app as it appears in the company portal. Make sure all app names that you use are unique. If the same app name exists twice, only one of the apps appears in the company portal.
    - **Description**: Enter a description for the app. The description appears in the company portal.
    - **Publisher**: Enter the name of the publisher of the app.
    - **Ignore app version**: Set to **Yes** if the app developer automatically updates the app. This option applies to mobile .msi apps only.
    - **Category**: Select one or more of the built-in app categories, or select a category that you created. Categories make it easier for users to find the app when they browse through the company portal.
    - **Display this as a featured app in the Company Portal**: Display the app prominently on the main page of the company portal when users browse for apps.
    - **Information URL**: Optionally, enter the URL of a website that contains information about the app. The URL appears in the company portal.
    - **Privacy URL**: Optionally, enter the URL of a website that contains privacy information for the app. The URL appears in the company portal.
    - **Command-line arguments**: Optionally, enter any command-line arguments that you want to apply to the .msi file when it runs.  An example is **/q**. Do not include the msiexec command or arguments, such as **/i** or **/x**, as they are automatically used. For more information, see [Command-Line Options](https://docs.microsoft.com/windows/desktop/Msi/command-line-options). If the .MSI file needs additional command-line options consider using [Win32 app management](apps-win32-app-management.md).
    - **Developer**: Optionally, enter the name of the app developer.
    - **Owner**: Optionally, enter a name for the owner of this app. An example is **HR department**.
    - **Notes**: Enter any notes that you want to associate with this app.
    - **Logo**: Upload an icon that is associated with the app. The icon is displayed with the app when users browse through the company portal.
3. When you're finished, select **OK**.

## Step 4: Finish up

1. In the **Add app** pane, verify that you configured the app information correctly.
2. Select **Add** to upload the app to Intune.

## Step 5: Update a line-of-business app

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

    > [!NOTE]
    > For the Intune service to successfully deploy a new APPX file to the device, you must increment the `Version` string in the AppxManifest.xml file in your APPX package.
    
## Configure a self-updating mobile MSI app to ignore the version check process

You can configure a known self-updating mobile MSI app to ignore the version check process. 

Some MSI installer-based apps are automatically updated by the app developer. For these automatically updated MSI apps, you can configure the **Ignore app version** setting in the **App information** pane. When you switch this setting to **Yes**, Microsoft Intune will not enforce the app version that's installed on the Windows client. 

This capability is useful to avoid getting into a race condition. For instance, a race condition can occur when the app is automatically updated by the app developer and is updated by Intune. Both might try to enforce a version of the app on a Windows client, which creates a conflict.

## Next steps

- The app that you created appears in the list of apps. You can now assign it to groups that you choose. For help, see [How to assign apps to groups](apps-deploy.md).

- Learn more about the ways in which you can monitor the properties and assignment of your app. See [How to monitor app information and assignments](apps-monitor.md).

- Learn more about the context of your app in Intune. See [Overview of the app lifecycle in Microsoft Intune](app-lifecycle.md).
