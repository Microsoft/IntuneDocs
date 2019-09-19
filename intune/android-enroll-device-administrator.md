---
# required metadata

title: Android device administrator enrollment in Microsoft Intune
titleSuffix: 
description: Enroll Android devices into Intune by using device administrator enrollment.
keywords:
author: ErikjeMS 
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Android device administrator enrollment

Android device administrator (sometimes referred to “legacy” Android management and released with Android 2.2) is a way to manage Android devices. However, improved management functionality is now available with [Android Enterprise](https://www.android.com/enterprise/management/) (released with Android 5.0). In an effort to move to modern, richer, and more secure device management, Google is decreasing device administrator support in new Android releases.

Therefore, to avoid such reduced functionality, we advise against enrolling new devices using the device administrator process described below.

For the same reasons, we also recommend that you migrate devices off of device administrator management if the devices are going to update to Android 10. 

For more information about Intune support for Android device administrator support, see the [Notices section](whats-new.md#decreasing-support-for-android-device-administrator).

If you still decide to have users enroll their Android devices with device administrator management, continue to the next section.  


> [!Note]  
> Android 10 and higher won't be supported in hybrid mobile device management (hybrid MDM; Intune managed with the System Center Configuration Manager console) because hybrid MDM is going out of service on September 1, 2019. If you're still using hybrid MDM, you should migrate to Intune standalone as soon as possible. Contact to support if you need help migrating. For more information, see [Move from Hybrid Mobile Device Management to Intune on Azure](https://aka.ms/hybrid_notification).

For more information about Google's Android Enterprise features, see these articles:
- [Google’s guidance for migration from device administrator to Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Google’s documentation on the plan to deprecate the device administrator API](https://developers.google.com/android/work/device-admin-deprecation)


## Set up device administrator enrollment

Intune by default allows enrollment of Android devices with device administrator capabilities.

1. To prepare to manage mobile devices, you must set the mobile device management (MDM) authority to **Microsoft Intune**. See [Set the MDM authority](mdm-authority-set.md) for instructions. You set this item only once, when you are first setting up Intune for mobile device management
2. [Tell your users how to enroll their devices](/intune-user-help/enroll-your-device-in-intune-android).  

After a user has enrolled, you can begin managing their devices in Intune, including [assigning compliance policies](compliance-policy-create-android.md), [managing apps](app-management.md), and more.

For information about other user tasks, see these articles:
- [Resources about the end-user experience with Microsoft Intune](end-user-educate.md)
- [Using your Android device with Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)


## Block device administrator enrollment
To block Android device administrator devices, or to block only personally owned Android device administrator devices from enrollment, see [Set device type restrictions](enrollment-restrictions-set.md).



## Next steps
- [Assign compliance policies](compliance-policy-create-android.md)
- [Managing apps](app-management.md)