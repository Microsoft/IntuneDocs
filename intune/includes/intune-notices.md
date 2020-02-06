---
title: include file
description: include file
author: ErikjeMS  
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
---

These notices provide important information that can help you prepare for future Intune changes and features.

### Updated support statement for 'Adobe Acrobat Reader for Intune' mobile app<!--5746776-->
We shared in MC188653 at the end of August, that the Adobe Acrobat Reader for Intune mobile app was reaching end-of-life on December 1, 2019 and that Adobe was planning on supporting Intune’s app protection policies within their main Acrobat Reader app. Since then, we received customer feedback that we needed to provide more time to continue allowing IT admins to target, and end users to begin using Adobe Acrobat Reader for Intune. Given the high usage of Adobe Acrobat Reader for Intune on end user devices and its importance in enterprise scenarios, we want to make sure any experience meets your organization's app protection needs. 

While we still recommend targeting the general Acrobat Reader mobile app in your policies since the Acrobat Reader mobile app supports App Protection Policies and has integrated the Intune SDK, the Adobe Acrobat Reader for Intune app will continue to be supported until March 31, 2020. 

#### How does this affect me?
You are receiving this message because our reporting indicates one or more policies in your organization are targeting the Adobe Acrobat Reader for Intune application and/or you may have received our previous EOL communication. 

#### What do I need to do to prepare for this change?
Let your end users and helpdesk know of this change. You can use the [Company Portal's support information functionality](../apps/company-portal-app.md#support-information) to establish a channel for Intune-related questions.

#### Additional Information
https://helpx.adobe.com/acrobat/kb/intune-app-end-of-life.html


### End Support for Windows Phone 8.1<!--3544909-->
Microsoft mainstream support for Windows Phone 8.1 ended in July 2017, and extended support ended in June 2019. The Company Portal app for Windows Phone 8.1 has been in sustain mode since October 2017. Microsoft Intune will now end support on February 20, 2020 for Windows Phone 8.1.

#### How does this affect me?
After February 20, 2020 these devices  won't receive any security updates, and you  won't be able to enroll any new devices. Existing Windows Phone 8.1 devices will stay enrolled (policy, apps, reporting) but note any troubleshooting of an existing enrollment  won't be supported after this date, as many components, such as third-party certificates, have already ended support for the platform. Intune will stop compatibility testing with Intune and Windows Phone 8.1.

#### What do I need to do to prepare for this change?
You can check your Intune reporting to see what devices or users may be affected. Go to Devices > All devices and filter by OS. You can add in additional columns to help identify who in your organization has devices running Windows Phone 8.1. Request that your end users upgrade their devices to a supported OS version.


### Take Action: Use Microsoft Edge for your Protected Intune Browser Experience<!--5728447-->
As we have been sharing over the past year, Microsoft Edge mobile supports the same set of management features as the Managed Browser, while providing a much-improved end user experience. To make way for the robust experiences provided in Microsoft Edge, we will be retiring the Intune Managed Browser. Starting on January, 27, 2020, Intune will no longer support the Intune Managed Browser.  

#### How does this affect me? 
Starting on February 1, 2020, the Intune Managed Browser will no longer be available in the Google Play Store or the iOS App Store. At this point, you will still be able to target new app protection policies to the Intune Managed Browser, though new users won't be able to download the Intune Managed Browser app. In addition, on iOS, new web clips that are pushed down to MDM-enrolled device will open in Microsoft Edge instead of the Intune Managed Browser.  

On March, 31 2020, the Intune Managed Browser will be removed from the Azure console. This means you will no longer be able to create new policies for the Intune Managed Browser. If you have existing Intune Managed Browser policies in place, they won't be affected. The Intune Managed Browser will show up in the console as an LOB app with no icon, and existing policies will show as targeted to the app still. At this point, we will also remove the option to redirect web content to the Intune Managed Browser within the Data Protection section of App protection policies.  

#### What do I need to do to prepare for this change? 
To ensure a smooth transition from the Intune Managed Browser to Microsoft Edge, we recommend you take the following steps proactively: 

1. Target Microsoft Edge for iOS and Android with app protection policy (also referred to as MAM)  and app config settings. You can reuse your Intune Managed Browser policies for Microsoft Edge by targeting those existing policies to Microsoft Edge as well.  
2. Ensure all MAM-protected apps in your environment have the app protection policy setting "Restrict web content transfer with other apps" set to "Policy managed browsers". 
3. Target all the MAM-protected with the managed app configuration setting "com.microsoft.intune.useEdge" set to true. Starting next month with the release of 1911, you will be able to accomplish steps 2 and 3 simply by configuring the setting "Restrict web content transfer with other apps" to have "Microsoft Edge" selected in the Data Protection section of your app protection policies. 

Support for web clips on iOS and Android is coming. When this support is released, you will need to retarget pre-existing web clips to ensure they open in Microsoft Edge instead of the Managed Browser. 

#### Additional information
Visit our docs on [using Microsoft Edge with app protection policies](../apps/manage-microsoft-edge.md) for more info, or view our [support blog post](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269).


### End of support for legacy PC management

Legacy PC management is going out of support on October 15, 2020. Upgrade devices to Windows 10 and reenroll them as Mobile Device Management (MDM) devices to keep them managed by Intune.

[Learn more](https://go.microsoft.com/fwlink/?linkid=2107122)

### Decreasing support for Android device administrator 
Android device administrator (sometimes referred to "legacy" Android management and released with Android 2.2) is a way to manage Android devices. However, improved management functionality is now available with [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (released with Android 5.0). In an effort to move to modern, richer, and more secure device management, Google is decreasing device administrator support in new Android releases.

#### How does this affect me?
Because of these changes by Google, Intune users will be impacted in the following ways:  
- Intune will only be able to provide full support for device administrator-managed Android devices running Android 10 and later through Q2 CY2020. Device administrator-managed devices that are running Android 10 or later after this time won't be able to be entirely managed. In particular, impacted devices won’t receive new password requirements.
    - Samsung Knox devices won't be impacted in this timeframe because extended support is provided through Intune’s integration with the Knox platform. This gives you more time to plan the transition off device admin management.    
- Device administrator-managed Android devices that remain on Android versions below Android 10 won't be impacted and can continue to be entirely managed with device administrator.    
- For all devices running Android 10 and later, Google has restricted the ability for device administrator management agents like Company Portal to access device identifier information. This restriction impacts the following Intune features after a device is updated to Android 10 or later:  
    - Network access control for VPN will no longer work.   
    - Identifying devices as corporate-owned with an IMEI or serial number won't automatically mark devices as corporate-owned.  
    - The IMEI and serial number will no longer be visible to IT admins in Intune. 
        > [!NOTE]
        > This only impacts device administrator-managed devices on Android 10 and later and does not affect devices being managed as Android Enterprise. 

#### What do I need to do to prepare for this change?
To avoid the reduction in functionality coming in Q3 CY2020, we recommend the following:
- Don't onboard new devices into device administrator management.
- If a device is expected to receive an update to Android 10, migrate it off of device administrator management to Android Enterprise management and/or app protection policies.

#### Additional information
- [Google's guidance for migration from device administrator to Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Google's documentation on the plan to deprecate the device administrator API](https://developers.google.com/android/work/device-admin-deprecation)

### Plan for change: Intune App SDK and app protection policies for Android moving to support Android 5.0 and higher in an upcoming release <!--4911065 -->
Intune will be moving to support Android 5.x (Lollipop) and higher in an upcoming release. Update any wrapped apps with the latest Intune App SDK and update your devices.

#### How does this affect me?
If you're not using or plan to use either the SDK or APP for Android, this change won't affect you. If you are using the Intune App SDK, be sure to update to the latest version and also update your devices to Android 5.x and higher. If you don't update, apps won't receive updates, and the quality of their experience will diminish over time.

Below find a list of common devices enrolled in Intune that run Android version 4.x. If you have one of these devices, take the appropriate steps to make sure that this device will support Android version 5.0 or higher or that it will be replaced with a device that supports Android version 5.0 or higher. This list isn't exhaustive of all devices that may need to be evaluated:

- Samsung SM-T561  
- Samsung SM-T365
- Samsung GT-I9195
- Samsung SM-G800F
- Samsung SM-G357FZ
- Motorola XT1080
- Samsung GT-I9305
- Samsung SM-T231

#### What do I need to do to prepare for this change?
Wrap your apps with the latest Intune App SDK. You may also set the "Require minimum OS version (Warning only)" conditional launch setting to notify end users on personal devices to upgrade.

### Intune plan for change: Nearing end of support for Windows 7<!-- 3042987 -->
As we messaged in MC148476, posted last September 2018, and again in MC176794 back in March 2019, Windows 7 reaches its end of extended support on January 14, 2020. At that time, Intune will retire support for devices running Windows 7 so we can focus our investment on supporting newer technologies and providing great new end-user experiences. After that date, technical assistance and automatic updates that help protect your Windows 7 PC will no longer be available through Intune. Microsoft strongly recommends that you move to Windows 10 before January 2020 to avoid a scenario where you need service or support that is no longer available. Read more about the Windows support lifecycle [here](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

#### How does this affect me?
You are receiving this message because you are currently managing Windows 7 PCs using the legacy Intune PC software agent. Because less than a year remains before the end of Windows 7 extended support, we strongly encourage your organization to begin upgrading to Windows 10 as soon as possible.  

PC management capabilities are built directly into the Windows 10 operating system, and you no longer need to install a client agent such as the Intune software client for Windows 7. Starting with Windows 8.1, Microsoft uses the Mobile Device Management (MDM) architecture to provision, configure, update, and manage Windows PCs. When you have set up Intune, you can simplify Windows enrollment by [enrolling Windows 10 PCs into Intune](..\windows-enroll.md) through the MDM channel. We recommend that you use this "agentless" MDM management solution to manage your Windows 10 PCs.

#### What do I need to do to prepare for this change?
We encourage your organization to immediately consider this action plan:

- Plan and upgrade the Windows 7 fleet to Windows 10 before January 14, 2020.
- Explore [Windows 10 deployment support](https://docs.microsoft.com/windows/deployment/) to learn more about how to upgrade your existing fleet of Windows 7 PCs to Windows 10.
- Review the [Desktop App Assure](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1) offer through FastTrack, which will assist with the Microsoft application compatibility promise.
- Transition existing legacy Intune software client-managed devices to the Microsoft-recommended solution to manage Windows 10 using MDM management. Enroll all new Windows 10 PCs using MDM management for Intune in the Azure portal.

For more information, see the [blog post here](https://aka.ms/Windows7_Intune).


