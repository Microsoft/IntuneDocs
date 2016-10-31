---
# required metadata

title: What's new | Microsoft Intune
description: Find out what’s new in this month’s, and past releases of Microsoft Intune
keywords:
author: barlanmsftms.author: barlan
manager: angrobe
ms.date: 10/13/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mamoriss
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
# What's new in Microsoft Intune -- October 2016
Learn what’s new in this release of Microsoft Intune. You can also find out about upcoming changes that you should be planning for, as well as information about past releases.  

All of these features will eventually be supported for hybrid customers' deployments (Configuration Manager with Intune). For more information about new hybrid features, check out our [hybrid What’s New page](https://technet.microsoft.com/library/mt718155.aspx).
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

## What's new

### Conditional access for mobile application management
You will be able to restrict access to Exchange Online so that access can come only from apps that support Intune mobile application management policies such as Outlook. [This new feature](/intune/deploy-use/allow-policy-managed-apps-access-to-o365) pairs up perfectly with Intune mobile app management (MAM) policies as you can block access to built-in mail clients or other apps that have not been configured with the Intune MAM policies. This ensures your users are accessing your organization’s data with apps that can be protected using Intune MAM. You can get started in Intune mobile app management via the Azure portal. Look for the new Conditional Access section in the “Settings” blade.

### Conditional access for Windows PCs
You can now create conditional access policies through the Intune admin console to block Windows PCs from accessing [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) and [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune). You can also create conditional access policies to block access to Office desktop and universal applications.

### Android for Work support
Intune is now part of the Android for Work program. We will begin rolling out support for Android for Work features to Intune starting this month.
[Read Microsoft’s announcement about Intune support for Android for Work](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/).

The following Intune topics are new, or updated with Android for Work information:

For IT professionals:
- [Set up Android for Work](/intune/deploy-use/set-up-android-for-work)
<!--- [Nathan Bigman's resource access topics]()-->
- [Restrict email access to Exchange Online and new Exchange Online Dedicated with Intune](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
- [Restrict email access to Exchange on-premises and legacy Exchange Online Dedicated with Intune](/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
- [Android for Work compliance policy settings](/intune/deploy-use/afw-compliance-policy-settings-in-microsoft-intune)
- [How to deploy Android for Work apps](/intune/deploy-use/android-for-work-apps)
- [Configure Android for Work apps with mobile app configuration policies](/intune/deploy-use/afw-app-configuration-policy)
- [Android for Work policy settings](/intune/deploy-use/android-for-work-policy-settings-in-microsoft-intune)

For end users:
- [What happens when you create a work profile](/intune/enduser/what-happens-when-you-create-a-work-profile-android)
- [Create a work profile and enroll your device in Intune](/intune/enduser/create-a-work-profile-and-enroll-your-device-in-intune-android)

### Lookout integration to protect iOS devices
In October, Microsoft is integrating with Lookout’s mobile threat protection solution to protect iOS mobile devices by detecting malware, risky apps, and more, on devices. Lookout’s solution helps you determine the threat level, which is configurable. You can create a compliance policy rule in Intune to determine device compliance based on the risk assessment by Lookout. Using conditional access policies, you can allow or block access to company resources based on the device compliance status.

End users of noncompliant iOS devices will be prompted to enroll, and will be required to install the Lookout for Work app on their devices, activate the app, and remediate threats reported in the Lookout for Work application to gain access to company data. Learn how to [Configure and deploy Lookout for Work apps](/intune/deploy-use/configure-and-deploy-lookout-for-work-apps).
<!--TFS 1319493-->

<!--### New Microsoft Intune Company Portal available for Windows 10 devices
Microsoft is releasing a new [Microsoft Intune Company Portal for Windows 10 devices](https://go.microsoft.com/fwlink/?linkid=830663). This app, which leverages the new Windows 10 Universal format, will provide the user with an updated user experience within the app and identical experiences across all Windows 10 devices, PC and Mobile alike, while still enabling all the same functionality that they are using today.

The new app will also allow users to leverage additional platform features like single sign-on (SSO) and certificate-based authentication on Windows 10 devices. The app will be made available as an upgrade to the existing Windows 8.1 Company Portal and Windows Phone 8.1 Company Portal installs from the Windows Store.-->

### Intune App Wrapping Tool for Android
You can enable your apps to use Intune mobile application management (MAM) policies by using the Intune App Wrapping Tool. Support for Intune MAM policies without requiring device enrollment is now available.

### Manage printing from apps managed using MAM policies
You can now prevent printing company data from apps that have MAM policies. This setting is available on the [Azure portal](/Intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) and is supported on both [iOS](/Intune/deploy-use/ios-mam-policy-settings) and [Android](/Intune/deploy-use/android-mam-policy-settings) devices.
<!--TFS 1014328-->

## Notices

### Android Samsung KNOX compatibility with Intune
Certain models of the Samsung Galaxy Ace phone cannot be managed by Intune as Samsung KNOX devices. When you enroll these devices with Intune, they will instead be managed as standard Android devices.

The model numbers affected are:

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

You and your end users need take no further action. For more information, visit the [Samsung KNOX](https://www.samsungknox.com) website.

### Company Portal app for Windows 8 is deprecated; support for Windows Phone 8 and Windows RT platforms are being deprecated
Starting in October 2016, Microsoft Intune will deprecate support for the Windows 8 Company Portal. Microsoft Intune will also deprecate support for the Windows Phone 8 and Windows RT platforms. As a consequence, you will not be able to enroll or update any Windows Phone 8 or Windows RT devices.

You can continue to manage Windows Phone 8, Windows RT  and Windows 8 devices that are already enrolled. Update Windows Phone 8 and Windows 8 devices to Windows 8.1 and Windows Phone 8.1, and use the corresponding Windows 8.1 and Windows Phone 8.1 Company Portal apps to continue distributing apps to these devices without disruptions.

Starting in November 2016, we will deprecate support for the Windows Phone 8 Company Portal.
<!--TFS 1255391-->

## What's coming

### New Microsoft Intune Company Portal available for Windows 10 devices
Microsoft is releasing a new Microsoft Intune Company Portal for Windows 10 devices. This app, which leverages the new Windows 10 Universal format, will provide the user with an updated user experience within the app and identical experiences across all Windows 10 devices, PC and Mobile alike, while still enabling all the same functionality that they are using today.

The new app will also allow users to leverage additional platform features like single sign-on (SSO) and certificate-based authentication on Windows 10 devices. The app will be made available as an upgrade to the existing Windows 8.1 Company Portal and Windows Phone 8.1 Company Portal installs from the Windows Store. For more details, go to [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp).
<!--TFS 1016502-->

### See also
* [Microsoft Intune Blog](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Cloud Platform roadmap](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Previous Intune releases](previous-intune-releases.md)
