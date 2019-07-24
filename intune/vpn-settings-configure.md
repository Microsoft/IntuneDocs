---
# required metadata

title: Create VPN device profile in Microsoft Intune - Azure | Microsoft Docs
description: For iOS devices, view the virtual private network (VPN) connection types, create a VPN device profile in the Azure portal,and see your options to secure the VPN profile with certificates, or username and password in Microsoft Intune.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
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

# Create VPN profiles in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Virtual private networks (VPNs) give your users secure remote access to your company network. Devices use a VPN connection profile to initiate a connection with the VPN server. Use **VPN profiles** in Microsoft Intune to assign VPN settings to users and devices in your organization, so they can easily and securely connect to the network.

For example, assume that you want to provision all iOS devices with the settings required to connect to a file share on the corporate network. You create a VPN profile that contains the settings to connect to the corporate network. Then you assign this profile to all users who have iOS devices. The users see the VPN connection in the list of available networks, and can connect with minimal effort.

You can use Intune custom configuration policies to create VPN profiles for the following platforms:

* Android 4 and later
* Enrolled devices that run Windows 8.1 and later
* Windows Phone 8.1 and later
* Enrolled devices that run Windows 10 desktop
* Windows 10 Mobile
* Windows Holographic for Business

## VPN connection types

You can create VPN profiles using the following connection types:

|Connection type|Android<br>Android work profiles|iOS|macOS|Windows Phone 8.1|Windows 8.1|Windows 10|
|-|-|-|-|-|-|-|
|Automatic|No|No|No|No|No|Yes|
|Check Point Capsule VPN|Yes|Yes|Yes|Yes|Yes|Yes|
|Cisco AnyConnect|Yes|Yes|Yes|No|No|No|
|SonicWall Mobile Connect|Yes|Yes|Yes|Yes|Yes|Yes|
|F5 Edge Client|Yes|Yes|Yes|Yes|Yes|Yes|
|Palo Alto Networks GlobalProtect|No<sup>1</sup>|Yes|No|No|No|Yes|
|Pulse Secure|Yes|Yes|Yes|Yes|Yes|Yes|
|Cisco (IPSec)|No|Yes|No|No|No|No|
|Citrix|Yes (Android only)<sup>1</sup>|Yes|No|No|No|Yes|
|IKEv2|No|No|No|No|No|Yes|
|L2TP|No|No|No|No|No|Yes|
|PPTP|No|No|No|No|No|Yes|
|Zscaler|No|Yes|No|No|No|No|
|Custom VPN|No|Yes|Yes|No|No|No|

<sup>1</sup> These VPN client apps can be configured using app configuration policy for Android Enterprise. See [Add app configuration policies for managed Android Enterprise devices](app-configuration-policies-use-android.md).

> [!IMPORTANT]
> Before you can use VPN profiles assigned to a device, you must install the applicable VPN app for the profile. You can use the information in the [What is app management in Microsoft Intune?](app-management.md) article to help you assign the app by using Intune.  

Learn how to  create custom VPN profiles by using URI settings in [Create a profile with custom settings](custom-settings-configure.md).

## Create a device profile containing VPN settings

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Select **Device configuration** > **Profiles** > **Create profile**.
4. Enter a **Name** and **Description** for the VPN profile.
5. From the **Platform** drop-down list, select the device platform to which you want to apply VPN settings. Currently, you can choose one of the following platforms for VPN device settings:
   - **Android**
   - **Android enterprise**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 and later**
   - **Windows 10 and later**
6. From the **Profile** type drop-down list, choose **VPN**.
7. Depending on the platform you chose, the settings you can configure are different. Go to one of the following topics for detailed settings for each platform:
   - [Android and Android work profile settings](vpn-settings-android.md)
   - [iOS settings](vpn-settings-ios.md)
   - [macOS settings](vpn-settings-macos.md)
   - [Windows Phone 8.1 settings](vpn-settings-windows-phone-8-1.md)
   - [Windows 8.1 settings](vpn-settings-windows-8-1.md)
   - [Windows 10 settings](vpn-settings-windows-10.md) (including Windows Holographic for Business)
8. When you're done, **Create** your profile

The profile is created and appears on the profiles list. To assign this profile to groups, see [assign device profiles](device-profile-assign.md).

## Methods of securing VPN profiles

VPN profiles can use a number of different connection types and protocols from different manufacturers. These connections are typically secured through one of two methods.

### Certificates

When you create the VPN profile, you choose a SCEP or PKCS certificate profile that you previously created in Intune. This profile is known as the identity certificate. It's used to authenticate against a trusted certificate profile (or *root certificate*) that you create to allow the user’s device to connect. The trusted certificate is assigned to the computer that authenticates the VPN connection, typically, the VPN server.

For more information about how to create and use certificate profiles in Intune, see [How to configure certificates with Microsoft Intune](certificates-configure.md).

### User name and password

The user authenticates to the VPN server by providing a user name and password.
