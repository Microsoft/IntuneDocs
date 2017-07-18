---
# required metadata

title: Android apps with app protection policies
description: This topic describes what to expect when your app is managed by app protection policies.
keywords:
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: andcerat
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-classic

---

# What to expect when your Android app is managed by app protection policies

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

This topic describes the user experience for apps with app protection policies. App protection policies are applied only when apps are used in a work context: for example, when the user is accessing apps with a work account or accessing files that are stored in a company OneDrive business location.
##  Access apps

The Company Portal app is required for all apps that are associated with app protection policies on Android devices.

For devices that are not enrolled in Intune, the Company Portal app must be installed on the device. However, the user does not have to launch  or sign into the Company Portal app before they can use apps that are managed by app protection policies.

The Company Portal app is a way for Intune to share data in a secure location. Therefore, the Company Portal app is a requirement for all apps that are associated with app protection policies, even if the device is not enrolled in Intune.


##  Use apps with multi-identity support

App protection polices are only applied in the work context. Therefore, the app might behave differently depending on whether the context is work or personal.

For example, the user gets a PIN prompt when accessing work data. For the **Outlook app**, the user is prompted for a PIN when they launch the app. For the **OneDrive app**, the user is prompted for the pin when they type in the work account. For Microsoft **Word**, **PowerPoint**, and **Excel**, the user is prompted for the pin when they access documents that are stored in the company OneDrive for Business location.

##  Manage user accounts on the device

Intune  supports the deployment of app protection policies to one user account per device only.

* Depending on the app that you're using, the second user might be blocked on the device. However, in all cases, only the first user who gets the app protection policies is affected by the policy.

  * **Microsoft Word**, **Excel**, and **PowerPoint** don't block a second user account, but the second user account is not affected by the app protection policies.

  * For **OneDrive** and **Outlook apps**, you can only use one work account.  You can't add multiple work accounts for these apps.  You can however, remove a user and add a different user on the device.


* If a device has existing multiple user accounts before the app protection policies are deployed, the account that the app protection policies are deployed to first is managed by Intune app protection policies.


Read the following example scenario to get a deeper understanding of how multiple user accounts are treated.

User A works for two companies—**Company X** and **Company Y**. User A has a work account for each company, and both use Intune to deploy app protection policies. **Company X** deploys app protection policies **before** **Company Y**. The account that's associated with **Company X** gets the app protection policy, but not the account that's associated with Company Y. If you want the user account that's associated with Company Y to be managed by the app protection policies, you must remove the user account that's associated with Company X.
### Add a second account
####  Android
If you are using an Android device, you might see a blocking message with instructions to remove the existing account and add a new one.  To remove the existing account, go to **Settings  &gt;General &gt; Application Manager &gt;Company Portal.** Then choose **Clear Data**.

![Screenshot of the error message and instructions to remove the account](./media/Android_SwitchUser.png)

##  View media files with the Azure Information Protection app
To view company AV, PDF, and image files on Android devices, use the [Azure Information Protection app](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer) (previously known as the Rights Management sharing app).

Download this app from the Google Play store.  

The following file types are supported:

* **Audio:** AAC LC, HE-AACv1 (AAC+), HE-AACv2 (enhanced AAC+), AAC ELD (enhanced low delay AAC), AMR-NB, AMR-WB, FLAC, MP3, MIDI, Ogg Vorbis, PCM/WAVE
* **Video:** H.263, H.264 AVC, MPEG-4 SP, VP8
* **Image:** .jpg, .pjpg, .png, .ppng, .bmp, .pbmp, .gif, .pgif, .jpeg, .pjpeg
* **Documents:** PDF, PPDF


|**pfile**|**text**|
|----|----|
|Pfile is a generic “wrapper” format for protected files that encapsulates the encrypted content and the Azure Information Protection licenses. It can be used to protect any file type.|Text files, including XML, CSV, and so on, can be opened for viewing in the app even when they are protected. File types: .txt, .ptxt, .csv, .pcsv, .log, .plog, .xml, .pxml.|

Note: Microsoft GSM WAV files are not supported in the Azure Information Protection app. 

## Next steps
[What to expect when your iOS app is managed by app protection policies](end-user-mam-apps-ios.md)
