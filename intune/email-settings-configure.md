---
# required metadata

title: Configure email settings in Microsoft Intune - Azure | Microsoft Docs
titleSuffix:
description: Create an email profile in Microsoft Intune, and deploy this profile to Android Enterprise, iOS, and Windows devices. Use an email profile to configure common email settings, including an email server and authentication method to connect to corporate email on devices you manage.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/22/2018
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

# Add email settings to devices using Intune

Microsoft Intune includes different email settings you can deploy to devices in your organization. An IT administrator can create email profiles with specific settings to connect to a mail server, such as Office 365 and Gmail. Users then connect, authenticate, and synchronize their organizational email accounts on their mobile devices. By creating and deploying an email profile, you can confirm that settings are standard across many devices. And, help reduce support calls from end users who don't know the correct email settings.

You can use email profiles to configure the built-in email settings for the following devices:

- Android Samsung Knox Standard 4.0 and later
- Android work profile devices
- iOS 8.0 and later
- Windows Phone 8.1 and later
- Windows 10 (desktop) and Windows 10 Mobile

This article shows you how to create an email profile in Microsoft Intune. It also includes links to the different platforms for more specific settings.

## Create a device profile

1. In the [Azure portal](https://portal.azure.com), select **All services**, filter on **Intune**, and select **Microsoft Intune**.
2. Select **Device configuration** > **Profiles** > **Create profile**.
3. Enter a **Name** and **Description** for the email profile.
4. Choose your **Platform** from the drop-down list. Your options:

	- **Android** (Samsung Android Knox Standard only)
	- **Android enterprise**
	- **iOS**
	- **macOS**
	- **Windows Phone 8.1**
	- **Windows 8.1 and later**
	- **Windows 10 and later**

5. In the **Profile** type drop-down list, choose **Email**.
6. The settings you can configure may be different for each platform. For specific settings, choose your platform:

	- [Android work profile and Samsung Knox Standard settings](email-settings-android.md)
	- [iOS settings](email-settings-ios.md)
	- [Windows Phone 8.1 settings](email-settings-windows-phone-8-1.md)
	- [Windows 10 settings](email-settings-windows-10.md)

After you enter your settings, and create the profile, your profile is shown in the profiles list. Next, [assign this profile to some groups](device-profile-assign.md).

## Remove an email profile

Email profiles are assigned to device groups, not user groups. There are different ways to remove an email profile from a device, even when there's only one email profile on the device:

- **Option 1**: Open the email profile (**Device configuration** > **Profiles**), and choose **Assignments**. The **Include** tab shows the groups that are assigned the profile. Right-click the group > **Remove**. Be sure to **Save** your changes.

- **Option 2**: [Wipe or retire the device](devices-wipe.md). You can use these actions to selectively or fully remove data and settings.

## Secure email access

You can help secure email profiles using the following options:

- **Certificates**: When you create the email profile, you choose a certificate profile previously created in Intune. This certificate is known as the identity certificate. It authenticates against a trusted certificate profile or a root certificate to confirm a user’s device is allowed to connect. The trusted certificate is assigned to the computer that authenticates the email connection. Typically, this computer is the native mail server.

  For more information about how to create and use certificate profiles in Intune, see [How to configure certificates with Intune](certificates-configure.md).

- **User name and password**: The user authenticates to the native mail server by entering a user name and password. The password doesn't exist in the email profile. So, the user needs to enter the password when connecting to email.

## How Intune handles existing email accounts

If the user already configured an email account, then the email profile is assigned differently, depending on the platform.

- **iOS**: An existing, duplicate email profile is detected based on host name and email address. The duplicate email profile blocks the assignment of an Intune profile. In this case, the Company Portal app notifies the user that they aren't compliant, and prompts the user to manually remove the configured profile. To help prevent this scenario, tell your users to enroll *before* installing an email profile, which allows Intune to set up the profile.

- **Windows:** An existing, duplicate email profile is detected based on host name and email address. Intune overwrites the existing email profile created by the user.

- **Android Samsung Knox Standard**: An existing, duplicate email profile is detected based on the email address, and overwrites it with the Intune profile. Android doesn't use host name to identify the profile. Don't create multiple email profiles using the same email address on different hosts. The profiles will overwrite each other.

- **Android work profiles**: Intune provides two Android work email profiles: one for the Gmail app and one for the Nine Work app. These apps are available in the Google Play Store, and install in the device work profile. These apps won't create duplicate profiles. Both apps support connections to Exchange. To use email connectivity, deploy one of these email apps to your users' devices. Then create and deploy the appropriate email profile. Email apps such as Nine Work may not be free. Review the app’s licensing details, or contact the app company with any questions.

## Changes to assigned email profiles

If you make changes to an email profile you previously assigned, end users may see a message asking them to approve the reconfiguration of their email settings.

## Next steps
Once the profile is created, it isn't doing anything yet. Next, [assign the profile to somce devices](device-profile-assign.md). We recommend deploying the email profile to user groups.
