---
# required metadata

title: In development - Microsoft Intune
titleSuffix: 
description: Microsoft Intune features in development
keywords:
author: ErikjeMS 
ms.author: erikje
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology:
ms.assetid: 

# optional metadata

#audience:
#ms.devlang:
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: seodec18
ms.collection: M365-identity-device-management
---

# In development for Microsoft Intune - July 2019

To assist in your readiness and planning, this page lists Intune UI updates and features that are in development but not yet released. In addition:

- If we anticipate that you'll need to take action prior to a change, we’ll publish a complementary Office Message Center post.
- When a feature is launched in production, either as a preview or generally available, the feature description will move off this page and onto the [What's New page](whats-new.md).
- This page and the [What's New page](whats-new.md) are updated periodically. Check back for additional updates.
- Refer to the [M365 roadmap](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) for strategic deliverables and timelines.

> [!Note]
> These items reflect Microsoft’s current expectations about Intune capabilities coming in a future release. Dates and individual features may change. Not all items in development have a feature description on this page.

**RSS feed**: Get notified when this page is updated by copying and pasting the following URL into your feed reader: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## App management

### Customized notifications for users and groups    <!-- 16766574   -->
You'll soon be able to send custom ad-hoc push notifications from the Company Portal application to users on iOS and Android devices you manage with Intune. These custom notifications are not tied to particular Intune features and can be used for any purpose you require, including general notifications you want to send to some or all your employees.  

### Configure app notification content for organization accounts <!-- 2576686 -->
Intune app protection policies (APP) on Android and iOS devices will allow you to control app notification content for Org accounts. This feature will require support from applications and may not be available for all APP enabled applications. For more about APP, see [What are app protection policies?](app-protection-policy.md).

### Available Google Play app reporting for Android work profiles <!-- 3041956  -->
For available app installs on Android work profile devices, you can view app installation status as well as the installed version of managed Google Play apps. For more information, see [How to monitor app protection policies](app-protection-policies-monitor.md), [Manage Android work profile devices with Intune](android-enterprise-overview.md) and [Managed Google Play app type](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## Device configuration

### Support for IKEv2 VPN profiles for iOS <!-- 1943438 -->
You'll be able to create VPN profiles for the iOS native VPN client using the IKEv2 protocol. IKEv2 is a new connection type in **Device configuration** > **Profiles** > **Create profile** > **iOS** for platform > **VPN** for profile type > **Settings**.

These VPN profiles configure the native VPN client. So, no VPN client apps are installed or pushed to managed devices. This feature requires devices be enrolled in Intune (MDM enrollment).

To see the current VPN settings you can configure, go to [Configure VPN settings on iOS devices in Microsoft Intune](vpn-settings-ios.md).

Applies to: iOS

### Use "applicability rules" when creating Windows 10 device configuration profiles <!-- 2549910 -->
You create Windows 10 device configuration profiles (**Device configuration** > **Profiles** > **Create profile** > **Windows 10** for platform). You'll be able to create an **applicability rule** so the profile only applies to a specific edition or specific version. For example, you create a profile that enables some BitLocker settings. Once you add the profile, use an applicability rule so the profile only applies to devices running Windows 10 Enterprise.

Applies to: 
- Windows 10 and later

### Manage FileVault for macOS   <!--  3858502 + 1210104   -->
You’ll be able to use an Intune endpoint protection device configuration profile to manage FileVault key encryption for macOS devices. This includes escrow of, viewing of and rotating the encryption keys of your corporate devices. End users will be able to retrieve those keys through the Company Portal website.

### Advanced settings for Windows Defender Firewall   <!--  1311949     -->
As a public preview, you'll soon be able to use Intune to manage the custom firewall rules on clients for Windows Defender.  

### New configuration designer when creating an OEMConfig profile for Android Enterprise <!-- 3712769  -->
In Intune, you can create a device configuration profile that uses an OEMConfig app (Device Configuration > Profiles > Create profile > Android enterprise for platform > OEMConfig for profile type). When you do this, a JSON editor opens with a template and values for you to change. This update includes a Configuration Designer with an improved user experience that shows details embedded in the app, including titles, descriptions, and more. The JSON editor is still available, and shows any changes you make in the Configuration Designer.

To see the current settings, go to [Use and manage Android Enterprise devices with OEMConfig](android-oem-configuration-overview.md).

Applies to: Android Enterprise

<!-- ***********************************************-->
## Device management

### Improve device location<!-- 3855417 -->
You'll be able to zoom in to the exact coordinates of a device using the **Locate device** action. For more information about locating lost iOS devices, see [Find lost iOS devices](device-locate.md).

### Configure automatic device clean-up time limit down to 30 days <!--4231059  -->
You'll be able to set the automatic device clean-up time limit as short as 30 days (instead of current limit of 90 days) after the last sign-in. To do so, go to **Intune** > **Devices** > **Setup** > **Device Clean Up Rules**.

<!-- ***********************************************-->
## Security

### Import and export security baselines    <!--3408610          -->  
We’re adding the capability to export and import security baselines so you can take your customizations with you and share them between Intune environments.

<!-- ***********************************************-->
## Notices

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## See also
See [What’s New in Microsoft Intune](whats-new.md) for details on recent developments.
