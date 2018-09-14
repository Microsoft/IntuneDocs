---
# required metadata

title: Kiosk settings for Android in Microsoft Intune - Azure | Microsoft Docs
description: Configure your Android kios devices as single-app and multi-app kiosks. 
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 9/13/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Kiosk settings for Android devices in Intune

You can configure a device into single or multi-app kiosk mode by using device configuration settings. When a device is in kiosk mode, use of the device is limited to the app(s) or web links defined by the restriction profile. 

## Restrict an Android kiosk device to a single app

If a kiosk device's restriction profile is set to **Kiosk mode** = **single app kiosk**, users can only access a single app. When a device configured in this mode starts up, the specific app starts. Users are restricted from opening new apps or from changing the running app.

1. Make sure the app you want on the kiosk device is [deployed to the device](apps-deploy.md), and that you assigned the app to the device group you created for your kiosk devices.
2. Go to the [Intune portal](https://portal.azure.com) and choose **Device configuration** > **Profiles** > **Create profile**.
3. In the **Create profile** blade, set the following fields:
     - **Name**
     - **Platform**: Android enterprise
     - **Profile type**: Device Owner only > Device restrictions
4. Choose **Settings** > **Kiosk**.
5. For **Kiosk mode**, choose **Single app kiosk**.
6. Choose **Select a managed app** and then select the managed Google Play app that you want to be the only app available for devices using this profile.
7. Choose **OK** > **OK** > **OK** > **Create**.
8. Choose the profile you just created > **Assignments**.
9. Under **Assign to**, choose **Selected groups**.
10. Choose **Select groups to include** > choose the device group that you created for your kiosk devices > **Select**.

## Restrict a kiosk device to a set of apps or web links

If a kiosk device's restriction profile is set to **Kiosk mode** = **multi-app kiosk**, users can only access the limited number of apps that you configure. You can also define a set of web links that users can visit. When the policy is applied, users see icons for the permissible apps on the home screen.

To set an Android kiosk device for multiple apps, follow these main steps:

1. [Import and deploy the Managed Home Screen app from managed Google Play](#import-and -deploy-the-managed-home-screen-app)
2. [Add and assign apps that can be used in kiosk mode](#add-and-assign-apps-that-can-be-used-in-kiosk-mode)
3. (Optional) [Add web links that can be used in kiosk mode](#add-web-links-that-can-be-used-in-kiosk-mode)

### Import and deploy the Managed Home Screen app

1. Browse to the [Managed Home Screen page on Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) and sign in with the same account you use for other managed Google Play apps.
2. Choose **Approve**.
3. Go to the [Intune portal](https://portal.azure.com) and choose **Client apps** > **Managed Google Play** > **Sync**.
4. Choose **Apps** > **Managed Home Screen** > **Assignments** > **Add group**.
5. Under **Assignment type**, choose **Required**.
6. Choose **Included groups** > **Select groups to include** > choose the device group that you created for your kiosk devices > **Select** > **OK** > **OK** > **Save**.

> [!NOTE]
> When you add the Managed Home Screen app to the multi-app kiosk profile, an icon is added. But, nothing happens when you select the icon. As a result, you don't have to add the Managed Home Screen app to the multi-app kiosk profile.

### Add and assign apps that can be used in kiosk mode

For each app that you want to be available on the kiosk devices, follow these steps:

1. [Add the app to Intune](store-apps-android.md).
2. Choose **Client apps** > **Apps** > choose the app > **Assignments** > **Add group**.
3. Under **Assignment type**, choose **Required**.
4. Choose **Included groups** > **Select groups to include** > choose the device group that you created for your kiosk devices > **Select** > **OK** > **OK** > **Save**.

### Add web links that can be used in kiosk mode

1. Go to the [Intune portal](https://portal.azure.com) and choose **Client apps** > **Apps** > **Add**.
2. Under **App type**, choose **Web link**.
3. Choose **Configure** and provide the required information. You don't need to add a Logo image because it will be automatically retrieved from the web site's favicon.ico.
4. Choose **OK** > **Add**.

Be sure you deployed a web app to the kiosk devices. For more informtaion, see [Add web apps to Microsoft Intune](web-app.md).

### Create a multi-app kiosk profile

1. Go to the [Intune portal](https://portal.azure.com) and choose **Device configuration** > **Profiles** > **Create profile**.
3. In the **Create profile** blade, set the following fields:
     - **Name**: type an intuitive name
     - **Platform**: Android enterprise
     - **Profile type**: Device Owner only > Device restrictions
4. Choose **Settings** > **Kiosk**.
5. For **Kiosk mode**, choose **Multi-app kiosk**.
6. Choose **Add** and then select the apps or web links that you want available for devices using this profile.
7. Choose **OK** > **OK** > **OK** > **Create**.
8. Choose the profile you just created > **Assignments**.
9. Under **Assign to** choose **Selected groups**.
10. Choose **Select groups to include** > choose the device group that you created for your kiosk devices > **Select** > **Save**.

## Next steps
[Assign the profile](device-profile-assign.md) and [monitor its status](device-profile-monitor.md).
