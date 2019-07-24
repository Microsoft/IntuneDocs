---
title: include file
description: include file
author: ErikjeMS  
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
---

These notices provide important information that can help you prepare for future Intune changes and features. 

### Update your Android Company Portal app to the latest version <!--4536963-->
Intune periodically releases updates to the Android Company Portal App. In November 2018 we released a company portal update, which included a back-end switch to prepare for Google’s change from their existing notification platform to Google’s Firebase Cloud Messaging (FCM). When Google retires their existing notification platform and moves to FCM, end users will need to have updated their company portal app to at least November 2018 release to continue communicating with the Google play store.

#### How does this affect me?
Our telemetry indicates you have devices with a Company Portal version earlier than 5.0.4269.0. If this version or later of the company portal app is not installed, IT pro initiated device actions like wipe, reset password, available and required app installs, and certificate enrollment may not work as expected. If your devices are MDM enrolled in Intune, then you can see the company portal versions and users by going to Client apps – Discovered apps. Selecting earlier versions of the Company Portal will allow you to see what end users have the devices that haven’t updated the company portal.

#### What do I need to do to prepare for this change?
Ask end users of Android devices that have not updated to update the company portal through Google play. Notify your help desk in case a user has not kept auto-updating of the company portal app. See the link in Additional Information for more on Google’s FCM platform and change.

#### Additional information
https://firebase.google.com/docs/cloud-messaging/


### New Fullscreen experience coming to Intune <!--4593669-->
We’re rolling out updated create and edit UI experiences to Intune in the Azure portal. This new experience will simplify the existing workflows by using a wizard style format condensed within one blade. This update will do away with “blade sprawl” or any create and edit flows that require you to drill down into deep blade journeys. The create workflows will also be updated to include Assignments (except for App assignment).

#### How does this affect me?
The full screen experience will be rolled out to Intune both at portal.azure.com and devicemanagement.microsoft.com over the next few months. This update to the UI will not impact functionality of your existing policies and profiles, but you will see a slightly modified workflow. When you create new policies, for example, you will be able to set some assignments as part of this flow instead of doing so after creating the policy. See the blog post at Additional information for screenshots of what the new experience will look like in the console.

#### What can I do to prepare for this change?
You do not need to take any action but can consider updating your IT pro guidance if necessary. We’ll update our documentation as this experience rolls out to various blades in the Intune on Azure portal.

#### Additional information 
https://aka.ms/intune_fullscreen

### Plan for Change: Intune moving to support iOS 11 and higher in September <!-- 4665342-->
In September, we expect iOS 13 to be released by Apple. Intune enrollment, the Company Portal, and the Managed Browser will move to support iOS 11 and higher shortly after the iOS 13 release.

#### How does this affect me?
Provided that O365 mobile apps are supported on iOS 11.0 and higher, this may not affect you; you’ve likely already upgraded your OS or devices. However, if you have any of the devices listed below, or decide to enroll any of the devices listed below, know that the devices below do not support an OS greater than iOS 10. These devices will need to be upgraded to a device that supports iOS 11 or higher:

- iPhone 5
- iPhone 5c
- iPad (4th Generation)

Starting in July, MDM enrolled devices with iOS 10 and the Company Portal will receive a prompt to upgrade their OS or device. If you use Application Protection Policies (APP) you can also set the “Require minimum iOS operating system (Warning only)” access setting.

#### What do I need to do to prepare for this change?
Check your Intune reporting to see what devices or users may be affected. Go to **Devices** > **All devices** and filter by OS. You can add in additional columns to help identify who in your organization has devices running iOS 10. Request that your end users upgrade their devices to a supported OS version before September.

### Plan for Change: Support for version 8.1.1 and higher of Intune App SDK for iOS <!-- 3586942-->
Starting in September 2019, Intune will move to support iOS apps with Intune App SDK 8.1.1 and higher. Apps built with SDK versions less than 8.1.1 will no longer be supported. This change will go into effect with Apple’s release of iOS 13 which is expected to come around September and also been announced in MC181399.

#### How does this affect me?
With Intune App SDK or App Wrapping integration, you can protect corporate data from unapproved applications and users via data encryption. The Intune App SDK for iOS will use 256-bit encryption keys by default when encryption is enabled by Intune App Protection Policies (APP). After this change, any iOS apps on SDK versions prior to 8.1.1, which use 128-bit encryption keys, will no longer be able to share data with applications integrated with SDK 8.1.1 or using the 256-bit keys. All iOS apps will need to have an SDK version 8.1.1 or higher to allow protected data sharing.

#### What can I do to prepare for this change?
Check your Microsoft, third-party, and line-of-business (LOB) apps. You should ensure all that all your applications protected with Intune APP are using SDK version 8.1.1 or later.

- For LOB apps: You may need to republish your apps integrated with SDK version 8.1.1 or later. We recommend the latest SDK version. For information on how to prepare your LOB apps for App protection policies, see [Prepare line-of-business apps for app protection policies](../apps-prepare-mobile-application-management.md).
- For Microsoft/Third Party apps: Ensure that you are deploying the latest version of these apps to your users.

You should also update your documentation or developer guidance if applicable to include this change in support for the SDK.

#### Additional information
https://docs.microsoft.com/intune/apps-prepare-mobile-application-management

### Plan for change: New Windows updates settings in Intune <!-- 4464404 -->
Starting with the August release to the Intune service or 1908, we’re adding in new “Deadline settings” which you can configure instead of the “Allow user to restart (engaged restart)” settings. We plan to disable the engaged restart settings in the UI in 1909 or the September update and then completely remove them from the console towards the end of October. 

#### How does this affect me?
If you manage Windows 10 devices in your environment: 
- With the August Intune update or 1908, you will see new deadline settings in the console in addition to the old engaged restart settings.
- When both these old and new settings are configured, the deadline settings values will override the engaged restart setting values.
- Deadline settings will replace the “Allow user to restart (engaged restart) option in the console in the 1910 update.

#### What can I do to prepare for this change?
Start using the deadline settings in 1908 by configuring them with your desired values. Once you have that in place, you can set the engaged restart setting to “Not configured” to prepare for these being removed from the console in October.

Update your documentation and any automation scripts if needed. 

We’ll keep you updated and post a reminder to the Message center before we remove the engaged restart settings.
