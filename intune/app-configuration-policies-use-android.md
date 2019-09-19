---
# required metadata

title: Add app configuration policies for managed Android Enterprise devices
titleSuffix: Microsoft Intune
description: Use app configuration policies in Microsoft Intune to supply settings when users run a Managed Google Play app.
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0


# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Add app configuration policies for managed Android Enterprise devices

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

App configuration policies in Microsoft Intune supply settings to Managed Google Play apps on managed Android Enterprise devices. The app developer exposes Android-managed app configuration settings. Intune uses these exposed setting to let the admin configure features for the app. The app configuration policy is assigned to your user groups. The policy settings are used when the app checks for them, typically the first time the app runs.

> [!NOTE]  
> Not every app supports app configuration. Check with the app developer to see if their app supports app configuration policies.

1. In [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), select **Client apps** > **App configuration policies** >  **Add**.
2. Enter the following properties:

    - **Name**: Enter a descriptive name for the policy. Name your policies so you can easily identify them later. For example, a good policy name is **Android Enterprise Nine Work app policy for entire company**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
    - **Device enrollment type**: Select **Managed devices**.
    - **Platform**: Select **Android**.

3. Select **Associated App**. Choose the app you want to define an app configuration policy. Select from the list of Managed Google Play apps that you've approved and synchronized with Intune.
4. Select **Permissions**. You can set configurations by using:

    - [Configuration designer](#use-the-configuration-designer)
    - [JSON editor](#enter-the-json-editor)

5. Select **OK** > **Add**.

## Use the configuration designer

You can use the configuration designer for Managed Google Play apps when the app is designed to support configuration settings. Configuration applies to devices enrolled in Intune. The designer lets you configure specific configuration values for the settings exposed by the app.

1. Select **Add**. Choose the list of configuration settings that you want to enter for the app.

    If you're using GMail or Nine Work for your email app, see [Android Enterprise device settings to configure email](email-settings-android-enterprise.md) for more information on these settings.

2. For each key and value in the configuration, set:

    - **Value type**: The data type of the configuration value. For String value types, you can optionally choose a variable or certificate profile as the value type.
    - **Configuration value**: The value for the configuration. If you select variable or certificate for the **Value type**, choose from a list of variables or certificate profiles. If you choose a certificate, then the certificate alias of the certificate deployed to the device is populated at runtime.

### Supported variables for configuration values

You can choose the following options if you choose variable as the value type:

| Option | Example |
|----|----|
| Mail | john@contoso.com |
| User Principal Name | john@contoso.com |
| Partial UPN | john |
| Domain | contoso.com |
| User name | John Doe |
| Account ID | fc0dc142-71d8-4b12-bbea-bae2a8514c81 |
| User ID | 3ec2c00f-b125-4519-acf0-302ac3761822 |
| Device ID | b9841cd9-9843-405f-be28-b2265c59ef97 |

### Allow only configured organization accounts in multi-identity apps 

For Android devices, use the following key/value pairs:

| **Key** | com.microsoft.intune.mam.AllowedAccountUPNs |
|---|---|
| **Values** | <ul><li>One or more <code>;</code> delimited UPNs.</li><li>Only account(s) allowed are the managed user account(s) defined by this key.</li><li> For Intune enrolled devices, the <code>{{userprincipalname}}</code> token may be used to represent the enrolled user account.</li></ul> |

   > [!NOTE]
   > You must use Outlook for Android 2.2.222 or later when allowing only configured organization accounts with multi-identity.<p></p>
   > As the Microsoft Intune administrator, you can control which user accounts are added to Microsoft Office applications on managed devices. You can limit access to only allowed organization user accounts and block personal accounts on enrolled devices. The supporting applications process the app configuration and remove and block unapproved accounts.<p></p>
   > For Microsoft Word, Microsoft Excel, Microsoft PowerPoint, you must use app version 16.0.9327.1000 and later. 

## Enter the JSON editor

Some configuration settings on apps (such as apps with Bundle types) can't be configured with the configuration designer. Use the JSON editor for those values. Settings are supplied to apps automatically when the app is installed.

1. For **Configuration settings format**, select **Enter JSON editor**.
2. In the editor, you can define JSON values for configuration settings. You can choose **Download JSON template** to download a sample file that you can then configure.
3. Choose **OK**, and then choose **Add**.

The policy is created and shown in the list.

When the assigned app is run on a device, it runs with the settings that you configured in the app configuration policy.

## Preconfigure the permissions grant state for apps

You can also preconfigure app permissions to access Android device features. By default, Android apps that require device permissions, such as access to location or the device camera, prompt users to accept or deny permissions.

For example, an app uses the device's microphone. The user is prompted to grant the app permission to use the microphone.

1. In [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), select **Client apps** > **App configuration policies** >  **Add**.
2. Enter the following properties:

    - **Name**: Enter a descriptive name for the policy. Name your policies so you can easily identify them later. For example, a good policy name is **Android Enterprise prompt permissions app policy for entire company**.
    - **Description**. Enter a description for the profile. This setting is optional, but recommended.
    - **Device enrollment type**: Select **Managed devices**.
    - **Platform**: Select **Android**.

3. Select **Associated App**. Choose the app you want to define a configuration policy. Select from the list of Android work profile apps that you've approved and synchronized with Intune.
4. Select **Permissions** > **Add**. From the list, select the available app permissions > **OK**.
5. Select an option for each permission to grant with this policy:
    - **Prompt**. Prompt the user to accept or deny.
    - **Auto grant**. Automatically approve without notifying the user.
    - **Auto deny**. Automatically deny without notifying the user.
6. To assign the app configuration policy, select the app configuration policy > **Assignment** > **Select groups**. Choose the user groups to assign > **Select**.
7. Choose **Save** to assign the policy.

## Additional information

- [Assigning a Managed Google Play app to Android Enterprise devices](apps-add-android-for-work.md#assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices)
- [Deploying Outlook for iOS and Android app configuration settings](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## Next steps

Continue to [assign](apps-deploy.md) and [monitor](apps-monitor.md) the app.
