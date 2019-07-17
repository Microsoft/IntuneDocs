---
# required metadata

title: Add an Android line-of-business app to Microsoft Intune
description: Learn about how to add a Android line-of-business (LOB) app to Microsoft Intune.
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661

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

# Add an Android line-of-business app to Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A line-of-business (LOB) app is an app that you add to Intune from an app installation file. This kind of app is typically written in-house. Intune installs the LOB app on the user's device. 

> [!Note]
> For more information about LOB apps from the Managed Google Play store, see [Working with a line-of-business app from the Managed Google Play store](apps-add-android-for-work.md?#working-with-a-line-of-business-app-from-the-managed-google-play-store). 

> [!Note]
> For Android for Work devices, follow [this article](https://docs.microsoft.com/intune/apps-add-android-for-work). 

## Step 1: Specify the software setup file

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. In the **Intune** pane, select **Client apps**.
4. In the **Client apps** workload, select **Manage** > **Apps**.
5. Above the list of apps, select **Add**.
6. In the **Add app** pane, select **Line-of-business app**.

## Step 2: Configure the app package file

1. In the **Add app** pane, select **App package file**.
2. In the **App package file** pane, select the browse button. Then select an Android installation file with the extension **.apk**.
3. When you're finished, select **OK**.

## Step 3: Configure app information

1. In the **Add app** pane, select **App information**.
2. In the **App information** pane, add the details for your app. Depending on the app that you chose, some of the values in this pane might be automatically filled in.
    - **Name**: Enter the name of the app as it appears in the company portal. Make sure all app names that you use are unique. If the same app name exists twice, only one of the apps appears in the company portal.
    - **Description**: Enter the description of the app. The description appears in the company portal.
    - **Publisher**: Enter the name of the publisher of the app.
    - **Minimum Operating System**: From the list, choose the minimum operating system version on which the app can be installed. If you assign the app to a device with an earlier operating system, it will not be installed.
    - **Category**: Select one or more of the built-in app categories, or select a category that you created. Categories make it easier for users to find the app when they browse through the company portal.
    - **Display this as a featured app in the Company Portal**: Display the app prominently on the main page of the company portal when users browse for apps.
    - **Information URL**: Optionally, enter the URL of a website that contains information about this app. The URL appears in the company portal.
    - **Privacy URL**: Optionally, enter the URL of a website that contains privacy information for this app. The URL appears in the company portal.
    - **Developer**: Optionally, enter the name of the app developer.
    - **Owner**: Optionally, enter a name for the owner of this app. An example is **HR department**.
    - **Notes**: Enter any notes that you want to associate with this app.
    - **Logo**: Upload an icon that is associated with the app. This icon is displayed with the app when users browse through the company portal.
3. When you're finished, select **OK**.

## Step 4: Finish up

1. In the **Add app** pane, verify that the details of your app are correct.
2. Select **Add** to upload the app to Intune.

The app that you created now appears in the list of apps. From the list, you can assign the app to groups that you choose. For help, see [How to assign apps to groups](apps-deploy.md).

## Step 5: Update a line-of-business app

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

If **Check apps from external sources** is enabled on the Android device, the user will be prompted before installing the update. Otherwise the update will be installed automatically.

> [!Note]
> For the Intune service to successfully deploy a new APK file to the device, you must increment the `android:versionCode` string in the AndroidManifest.xml file in your APK package.

## Next steps

- The app that you created appears in the list of apps. You can now assign it to groups that you choose. For help, see [How to assign apps to groups](apps-deploy.md).

- Learn more about the ways in which you can monitor the properties and assignment of your app. See [How to monitor app information and assignments](apps-monitor.md).

- Learn more about the context of your app in Intune. See [Overview of device and app lifecycles](introduction-device-app-lifecycles.md).
