---
# required metadata

title: Microsoft Intune policy to allow/block apps for Samsung Knox
titleSuffix:
description: Create a custom profile to allow and block apps for Samsung Knox Standard devices.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology:

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure

ms.collection: M365-identity-device-management
---
# Use custom policies in Microsoft Intune to allow and block apps for Samsung Knox Standard devices 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Use the procedure in this article to create a Microsoft Intune custom policy that creates one of the following:

- A list of apps that are blocked from running on the device. Apps in this list are blocked from being run, even if they were already installed when the policy was applied.
- A list of apps that users of the device are allowed to install from the Google Play store. Only the apps you list can be installed. No other apps can be installed from the store.

These settings can only be used by devices that run Samsung Knox Standard.

## Create an allowed or blocked app list

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. On the **Intune** pane, choose **Device configuration**.
2. On the **Device configuration** pane, choose **Manage** > **Profiles**.
2. In the list of profiles pane, choose **Create profile**.
3. On the **Create profile** pane, enter a **Name** and optional **Description** for this device profile.
2. Choose a **Platform** of **Android**, and a **Profile type** of **Custom**.
3. Click **Settings**.
3. On the **Custom OMA-URI Settings** pane, choose **Add**.
4. In the **Add or Edit OMA-URI Setting** dialog box, specify the following settings:

   For a list of apps that are blocked from running on the device:

   - **Name** - Enter **PreventStartPackages**.
   - **Description** - Enter an optional description like 'List of apps that are blocked from running.'
   - **Data type** - From the drop-down list, choose **String**.
   - **OMA-URI** - Enter **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
   - **Value** - Enter a list of the app package names you want to allow. You can use **; : ,** or **|** as a delimiter. (Example: package1;package2;)

   For a list of apps that users are allowed to install from the Google Play store while excluding all other apps:
   - **Name** - Enter **AllowInstallPackages**.
   - **Description** - Enter an optional description like 'List of apps that users can install from Google Play.'
   - **Data type** - From the drop-down list, choose **String**.
   - **OMA-URI** - Enter **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
   - **Value** - Enter a list of the app package names you want to allow. You can use **; : ,** or **|** as a delimiter. (Example: package1;package2;)

4. Click **OK**, and then, on the **Create Profile** pane, choose **Create**.

>[!TIP]
> You can find the package ID of an app by browsing to the app on the Google Play store. The package ID is contained in the URL of the app's page. For example, the package ID of the Microsoft Word app is **com.microsoft.office.word**.

The next time each targeted device checks in, the app settings will be applied.

<!---## Assign the custom profile--->
