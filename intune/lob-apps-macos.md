---
# required metadata

title: How to add macOS line-of-business apps to Microsoft Intune
titleSuffix:
description: Learn about how to add macOS line-of-business (LOB) apps to Microsoft Intune.
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76

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

# How to add macOS line-of-business (LOB) apps to Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Use the information in this article to help you add macOS line-of-business apps to Microsoft Intune. You must download an external tool to pre-process your *.pkg* files before you can upload your line-of-business file to Microsoft Intune. The pre-processing of your *.pkg* files must take place on a macOS device.

> [!NOTE]
> While users of macOS devices can remove some of the built-in macOS apps like Stocks, and Maps, you cannot use Intune to redeploy those apps. If end users delete these apps, they must go to the app store, and manually re install them.

## Before your start

You must download an external tool to pre-process your *.pkg* files before you can upload your line-of-business file to Microsoft Intune. The pre-processing of your *.pkg* files must take place on a macOS device. Use the Intune App Wrapping Tool for Mac to enable Mac apps to be managed by Microsoft Intune.

> [!IMPORTANT]
> The *.pkg* file must be signed using “Developer ID Installer” certificate, obtained from an Apple Developer account. Only *.pkg* files may be used to upload macOS LOB apps to Microsoft Intune. Conversion of other formats, such as *.dmg* to *.pkg* is not supported.
>

1. Download and run the [Intune App Wrapping Tool for Mac](https://github.com/msintuneappsdk/intune-app-wrapping-tool-mac).

    > [!NOTE]
    > The **Intune App Wrapping Tool for Mac** must be run on a macOS machine.

2. Use the `IntuneAppUtil` command within the **Intune App Wrapping Tool for Mac** to wrap *.pkg* LOB app file from a *.intunemac* file.<br>

    Sample commands to use for the Microsoft Intune App Wrapping Tool for macOS:
    
    - `IntuneAppUtil -h`<br>
    This command will show usage information for the tool.
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    This command will wrap *.pkg* LOB app file to a *.intunemac* file.
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    This command will extract the detected parameters and version for the created *.intunemac* file.

## Step 1 - Specify the software setup file

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. On the **Intune** pane, choose **Client apps**.
4. In the **Client apps** workload, choose **Manage** > **Apps**.
5. Above the list of apps, choose **Add**.
6. In the **Add App** pane, choose **Line-of-business app**.

## Step 2 - Configure the app package file

1. On the **Add app** pane, choose **App package file**.
2. On the **App package file** pane, choose the browse button, and select an macOS installation file with the extension *.intunemac*.
3. When you are finished, choose **OK**.

## Step 3 - Configure app information

1. On the **Add app** pane, choose **App information**.
2. On the **App information** pane, add the details for your app. Depending on the app you have chosen, some of the values in this pane might have been automatically filled-in:
    - **Name** - Enter the name of the app to be displayed in the company portal. Make sure all app names that you use are unique. If the same app name exists twice, only one of the apps will be displayed to users in the company portal.
    - **Description** - Enter a description for the app to be displayed to users in the company portal.
    - **Publisher** - Enter the name of the publisher of the app.
    - **Minimum Operating System** - From the list, choose the minimum operating system version on which the app can be installed. If you assign the app to a device with an earlier operating system, it will not be installed.
    - **Category** - Select one or more of the built-in app categories, or a category you created. This makes it easier for users to find the app when they browse the company portal.
    - **Display this as a featured app in the Company Portal** - Display the app prominently on the main page of the company portal when users browse for apps.
    - **Information URL** - Optionally, enter the URL of a website that contains information about this app. The URL is displayed to users in the company portal.
    - **Privacy URL** - Optionally, enter the URL of a website that contains privacy information for this app. The URL is displayed to users in the company portal.
    - **Developer** - Optionally, enter the name of the app developer.
    - **Owner** - Optionally, enter a name for the owner of this app, for example, **HR department**.
    - **Notes** - Enter any notes you would like to associate with this app.
    - **Logo** - Upload an icon that is associated with the app. This is the icon that is displayed with the app when users browse the company portal.
3. When you are finished, choose **OK**.

## Step 4 - Finish up

1. On the **Add app** pane, verify that the details for your app is correct.
2. Choose **Add**, to upload the app to Intune.

The app you have created appears in the apps list where you can assign it to the groups you choose. For help, see [How to assign apps to groups](apps-deploy.md).

> [!NOTE]
> If the *.pkg* file contains multiple apps or app installers, then Microsoft Intune will only report that the *app* is successfully installed when all installed apps are detected on the device.

## Step 5 - Update a line-of-business app

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> For the Intune service to successfully deploy a new *.pkg* file to the device you must increment the package `version` and `CFBundleVersion` string in the *packageinfo* file in your *.pkg* package.

## Next steps

- The app you have created is displayed in the apps list. You can now assign it to the groups you choose. For help, see [How to assign apps to groups](apps-deploy.md).

- Learn more about the ways in which you can monitor the properties and assignment of your app. For more information, see [How to monitor app information and assignments](apps-monitor.md).

- Learn more about the context of your app in Intune. For more information, see [Overview of device and app lifecycles](introduction-device-app-lifecycles.md)
