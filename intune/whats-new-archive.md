---
# required metadata
title: What's new in previous months in the Microsoft Intune - Azure | Microsoft Docs
titleSuffix: 
description: Review older announcements from the Intune what's new page
keywords:
author: ErikjeMS  
ms.author: erikje
manager: dougeby
ms.date: 7/8/2019
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology:
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c

# optional metadata

ROBOTS: NOINDEX,NOFOLLOW
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# What's new in the Microsoft Intune - previous months

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

<!-- ########################## -->
## December 2018

### App management

#### Updates for Application Transport Security <!-- 748318 -->

Microsoft Intune supports Transport Layer Security (TLS) 1.2+ to provide best-in-class encryption, to ensure Intune is more secure by default, and to align with other Microsoft services such as Microsoft Office 365. In order to meet this requirement, the iOS and macOS company portals will enforce Apple's updated Application Transport Security (ATS) requirements, which also require TLS 1.2+. ATS is used to enforce stricter security on all app communications over HTTPS. This change impacts Intune customers using the iOS and macOS Company Portal apps. For more information, see the [Intune support blog](https://aka.ms/compportalats).

#### The Intune App SDK will support 256-bit encryption keys <!-- 1832174 -->
The Intune App SDK for Android now uses 256-bit encryption keys when encryption is enabled by App Protection Policies. The SDK will continue to provide support of 128-bit keys for compatibility with content and apps that use older SDK versions.

#### Microsoft Auto Update version 4.5.0 required for macOS devices <!-- 3503442 -->
To continue receiving updates for the Company Portal and other Office applications, macOS devices managed by Intune must upgrade to Microsoft Auto Update 4.5.0. Users might already have this version for their Office apps.

### Device management

#### Intune requires macOS 10.12 or later <!-- 2827778 -->
Intune now requires macOS version 10.12 or later. Devices using prior macOS versions can't use the Company Portal to enroll into Intune. To receive support assistance and new features, users must upgrade their device to macOS 10.12 or later and upgrade the Company Portal to the latest version.

<!-- ########################## -->
## November 2018

### App management

#### Uninstalling apps on corporate-owned supervised iOS devices <!-- 1281677 -->
You can remove any app on corporate-owned supervised iOS devices. You can remove any app by targeting either user or device groups with an **Uninstall** assignment type. For personal or unsupervised iOS devices, you will continue to be able to remove only apps that were installed using Intune.

#### Downloading Intune Win32 app content <!-- 2617320 -->
Windows 10 RS3 and above clients will download Intune Win32 app content using a Delivery Optimization component on the Windows 10 client. Delivery optimization provides Peer-to-Peer functionality that it is turned on by default. Currently, delivery optimization can be configured by group policy. For more information, see [Delivery Optimization for Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

#### End user device and app content menu <!-- 2771453 -->
End users can now use context menu on device and apps to trigger common actions like renaming a device or checking compliance.

#### Set custom background in Managed Home Screen app  <!-- 3041945 -->
We're adding a setting that lets you customize the background appearance of the Managed Home Screen app on Android Enterprise, multi-app, kiosk mode devices.  To configure the **Custom URL background**, go to Intune in the Azure portal > Device configuration. Select a current device configuration profile or create a new one to edit its kiosk settings.
To see the kiosk settings, see [Android Enterprise device restrictions](device-restrictions-android-for-work.md).

#### App protection policy assignment save and apply <!-- 3104570 -->
You now have better control over your [app protection policy assignments](app-protection-policies.md#deploy-a-policy-to-users). When you select *Assignments* to set or edit the assignments of a policy, you must **Save** your configuration before the change applies. Use **Discard** to clear all changes you make without saving any changes to the Include or Exclude lists.  By requiring Save or Discard, only the users you intend are assigned an app protection policy.

#### New Microsoft Edge browser settings for Windows 10 and later <!-- 3174639 -->
This update includes new settings to help control and manage the Microsoft Edge browser on your devices. For a list of these settings, see [Device restriction for Windows 10 (and newer)](device-restrictions-windows-10.md#microsoft-edge-browser).

#### New apps support with app protection policies <!-- 3330037 -->
You can now manage the following apps with [Intune app protection policies](app-protection-policies.md):
- Stream (iOS)
- To DO (Android, iOS)
- PowerApps (Android, iOS)
- Flow (Android, iOS)

Use app protection policies to protect corporate data and control data transfer for these apps, like other Intune policy managed apps. 
Note: If Flow is not yet visible in the console, you add Flow when you create or edit and app protection policies. To do so, use the **+ More apps** option, and then specify the *App ID* for Flow in the input field. For Android use *com.microsoft.flow*,  and for iOS use *com.microsoft.procsimo*.

### Device configuration

#### Support for iOS 12 OAuth in iOS email profiles <!--2155106 -->
Intune's iOS email profiles support iOS 12 Open Authorization (OAuth). To see this feature, create a new profile (**Device Configuration** > **Profiles** > **Create profile** > **iOS** for platform > **Email** for profile type), or update an existing iOS email profile. If you enable OAuth in a profile that's already deployed to users, then users are prompted to reauthenticate, and download their email again.

[iOS email profiles](email-settings-ios.md) has more information on using OAuth in an email profile.

#### Network Access Control (NAC) support for Citrix SSO for iOS <!-- 3259404 -->
Citrix released an update to Citrix Gateway to allow Network Access Control (NAC) for Citrix SSO for iOS in Intune. You can opt in to include a device ID within a VPN profile in Intune, and then push this profile to your iOS devices. You will need to install the latest update to Citrix Gateway to use this functionality.

[Configure VPN settings on iOS devices](vpn-settings-ios.md#base-vpn-settings) provides more information on using NAC, including some additional requirements. 

#### iOS and macOS version numbers and build numbers are shown <!-- 1892471 -->
In **Device compliance** > **Device compliance**, the iOS and macOS operating system versions are shown, and available to use in compliance policies. This update includes, the build number, which is configurable for both platforms.
When security updates are released, Apple typically leaves the version number as-is, but updates the build number. By using the build number in a compliance policy, you can easily check if a vulnerability update is installed.
To use this feature, see [iOS](compliance-policy-create-ios.md#device-health) and [macOS](compliance-policy-create-mac-os.md#device-properties) compliance policies.

#### Update rings are being replaced with Delivery Optimization settings for Windows 10 and later <!-- 2753807 -->
Delivery optimization is a new configuration profile for Windows 10 and later. This feature provides a more streamlined experience to deliver software updates to devices in your organization. This update also helps you deliver the settings in new and existing update rings using a configuration profile.
To configure a delivery optimization configuration profile, see [Windows 10 (and newer) delivery optimization settings](delivery-optimization-windows.md).

#### New device restriction settings added to iOS and macOS devices <!-- 2827760 -->
This update includes new settings for your iOS and macOS devices that are released with iOS 12:

**iOS settings**: 
- General: Block app removal (supervised only)​
- General: Block USB Restricted mode (supervised only)​
- General: Force automatic date and time (supervised only)​​
- Password: Block password AutoFill (supervised only)​
- Password: Block password proximity requests (supervised only)​
- Password: Block password sharing (supervised only)

**macOS settings**: 
- Password: Block password AutoFill
- Password: Block password proximity requests
- Password: Block password sharing

To learn more about these settings, see [iOS](device-restrictions-ios.md) and [macOS](device-restrictions-macos.md) device restriction settings.

### Device enrollment

#### Autopilot support for hybrid Azure Active Directory joined devices (Preview) <!-- 1048100-->
You can now set up hybrid Azure Active Directory joined devices by using Autopilot. Devices must be joined to your organization's network to use the hybrid Autopilot feature. For more information, see [Deploy hybrid Azure AD joined devices using Intune and Windows Autopilot](windows-autopilot-hybrid.md).
This feature is rolling out across the user base over the next few days. Therefore, you might not be able to follow these steps until it rolls out to your account.

#### Select apps tracked on the Enrollment Status Page<!-- 2531007 -->
You can choose which apps are tracked on the enrollment status page. Until these apps are installed, the user can't use the device. For more information, see [Set up an enrollment status page](windows-enrollment-status.md).

#### Search for Autopilot device by serial number <!--2595788 -->
You can now search for Autopilot devices by serial number. To do so, choose **Device enrollment** > **Windows enrollment** > **Devices** > type a serial number in the **Search by serial number** box > press Enter.

#### Track installation of Office ProPlus <!--2620217 -->
Users can track the installation progress of [Office ProPlus](apps-add-office365.md) using the [Enrollment Status Page](windows-enrollment-status.md). For more information, see [Set up an enrollment status page](windows-enrollment-status.md).

#### Alerts for expiring VPP token or Company Portal license running low <!-- 2237572 -->
If you are using Volume Purchase Program (VPP) to pre-provision the Company Portal during DEP enrollment, Intune will alert you when the VPP token is about to expire and when the licenses for the Company Portal are running low.

#### macOS Device Enrollment Program support for Apple School Manager accounts <!--3006133 -->
Intune now supports using the Device Enrollment Program on macOS devices for Apple School Manager accounts.  For more information, see [Automatically enroll macOS devices with Apple School Manager or Device Enrollment Program](device-enrollment-program-enroll-macos.md).

#### New Intune device subscription SKU <!--3312071-->
To help lower the cost of managing devices in enterprises, a new device-based subscription SKU is now available. This Intune device SKU is licensed per device on a monthly basis. Price varies by the licensing program. It's available directly through the Microsoft 365 admin center, and through the [Enterprise Agreement](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2) (EA), [Microsoft Products and Services Agreement](https://www.microsoft.com/licensing/mpsa/default) (MPSA), [Microsoft Open Agreements](https://partner.microsoft.com/licensing/licensing-agreements), and [Cloud Solution Provider](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP).

### Device management

#### Temporarily pause kiosk mode on Android devices to make changes <!-- 3041935 -->
When using Android devices in multi-app kiosk mode, an IT administrator may need to make changes to the device. This update includes new multi-app kiosk settings that allows an IT Administrator to temporarily pause kiosk-mode using a PIN, and get access to the entire device.
To see the kiosk settings, see [Android Enterprise device restrictions](device-restrictions-android-for-work.md).

#### Enable virtual home button on Android Enterprise kiosk devices  <!-- 3042021 -->
A new setting will allow users to tap a soft-key button on their device to switch between the Managed Home Screen app and other assigned apps on their multi-app kiosk device. This setting is particularly helpful in scenarios where a user's kiosk app does not respond appropriately to the "back" button. You'll be able to configure this setting for corporate-owned, single use Android devices. To enable or disable the **Virtual home button**, go to Intune in the Azure portal > Device configuration. Select a current device configuration profile or create a new one to edit its kiosk settings.
To see the kiosk settings, see [Android Enterprise device restrictions](device-restrictions-android-for-work.md).

<!-- ########################## -->
## October 2018

### App management

#### Access to key profile properties using the company portal app <!-- 772203 -->
End users can now access key account properties and actions, such as password reset, from the Company portal app. 

#### 3rd-party keyboards can be blocked by APP settings on iOS <!-- 1248481 -->
On iOS devices, Intune admins can block the use of 3rd-party keyboards when accessing organization data in policy protected apps. When the Application Protection Policy (APP) is set to block 3rd-party keyboards, the device user receives a message the first time they interact with corporate data when using a 3rd-party keyboard. All options, other than the native keyboard, are blocked and device users will not see them. Device users will only see the dialog message once. 

#### User account access of Intune apps on managed Android and iOS devices <!-- 1248496 -->
As the Microsoft Intune admin, you can control which user accounts are added to Microsoft Office applications on managed devices. You can limit access to only allowed organization user accounts and block personal accounts on enrolled devices. 

#### Outlook iOS and Android app configuration policy <!--1828527 -->
You can now create an Outlook iOS and Android app configuration policy for iOS and Android for on-premises users that leverage Basic authentication with the ActiveSync protocol. Additional configuration settings will be added as they are enabled for the Outlook for iOS and Android.

#### Office 365 Pro Plus language packs <!-- 1833450 -->
As the Intune admin, you will be able to deploy additional languages for Office 365 Pro Plus apps managed through Intune. The list of available languages includes the **Type** of language pack (core, partial, and proofing). In the Azure portal, select **Microsoft Intune** > **Client apps** > **Apps** > **Add**. In the **App type** list of the **Add app** blade, select **Windows 10** under **Office 365 Suite**. Select **Languages** in the **App Suite Settings** blade.

#### Windows line-of-business (LOB) apps file extensions <!-- 1884873 -->
The file extensions for Windows LOB apps will now include *.msi*, *.appx*, *.appxbundle*, *.msix*, and *.msixbundle*. You can add an app in Microsoft Intune by selecting **Client apps** > **Apps** > **Add**. The **Add app** pane is displayed which allows you to select the **App type**. For Windows LOB apps, select **Line-of-business** app as the app type, select the **App package file**, and then enter an installation file with the appropriate extension.

#### Windows 10 app deployment using Intune <!-- 2309001 -->
Building upon the existing support for line-of-business (LOB) apps and Microsoft Store for Business apps, administrators can use Intune to deploy most of their organization’s existing applications to end users on Windows 10 devices. Administrators can add, install, and uninstall applications for Windows 10 users in a variety of formats, such as MSIs, Setup.exe, or MSP. Intune will evaluate requirement rules before downloading and installing, notifying end users of the status or reboot requirements using the Windows 10 Action Center. This functionality will effectively unblock organizations interested in shifting this workload to Intune and the cloud. This feature is currently in public preview and we expect to add significant new capabilities to the feature over the next few months. 

#### App Protection Policy (APP) settings for web data <!-- 2662995 -->
APP policy settings for web content on both Android and iOS devices will be updated to better handle both http and https web links, as well as data transfer via iOS Universal Links and Android App Links. 

#### End user device and app content menu <!-- 2771453 -->
End users can now use the context menu on device and apps to trigger common actions like renaming a device or checking compliance. 

#### Windows Company Portal keyboard shortcuts <!-- 2771518 -->
End users will now be able to trigger app and device actions in the Windows Company Portal using keyboard shortcuts (accelerators).

#### Require non-biometric PIN after a specified timeout <!-- 1506985 -->
By requiring a non-biometric PIN after an admin-specified timeout, Intune provides improved security for Mobile Application Management (MAM) enabled apps by restricting the use of biometric identification for access to corporate data. The settings affect users who rely on Touch ID (iOS), Face ID (iOS), Android Biometric, or other future biometric authentication methods to access their APP/MAM-enabled applications. These settings enable Intune admins to have more granular control over user access, eliminating cases where a device with multiple fingerprints or other biometric access methods can reveal corporate data to an incorrect user. In the Azure portal, open **Microsoft Intune**. Select **Client apps** > **App protection policies** > **Add a policy** > **Settings**. Locate the **Access** section for specific settings. For information about access settings, see [iOS settings](app-protection-policy-settings-ios.md#access-requirements) and [Android settings](app-protection-policy-settings-android.md#access-requirements).

#### Intune APP data transfer settings on iOS MDM enrolled devices <!-- 2244713 -->
You can separate the control of Intune APP data transfer settings on iOS MDM enrolled devices from specifying the enrolled user's identity, also known as the User Principal Name (UPN). Admins not using the IntuneMAMUPN will not observe a behavior change. When this functionality is available, admins using the IntuneMAMUPN to control data transfer behavior on enrolled devices should review the new settings and update their APP settings as needed.

#### Windows 10 Win32 apps <!-- 2617325 -->
You can configure your Win32 apps to be installed in user context for individual users, versus installing the app for all users of the device.

#### Windows Win32 apps and PowerShell scripts <!-- 2617330 -->
End users are no longer required to be logged in on the device to install Win32 apps or execute PowerShell scripts. 

#### Troubleshooting client app installation <!-- 1363711 -->
You can troubleshoot the installation success of client apps by reviewing the column labeled **App install** in the **Troubleshoot** blade. To view the **Troubleshoot** blade, in the Intune portal, select **Troubleshoot** under **Help and support**.

### Device configuration

#### Create DNS suffixes in VPN configuration profiles on devices running Windows 10<!-- 1333668 -->
When you create a VPN device configuration profile (**Device configuration** > **Profiles** > **Create profile** > **Windows 10 and later** platform > **VPN** profile type), you enter some DNS settings. With this update, you can also enter multiple **DNS suffixes** in Intune. When using DNS suffixes, you can search for a network resource using its short name, instead of the fully qualified domain name (FQDN). This update also lets you change the order of the DNS suffixes in Intune.
[Windows 10 VPN settings](vpn-settings-windows-10.md#dns-settings) lists the current DNS settings.
Applies to: Windows 10 devices

#### Support for always-on VPN for Android enterprise work profiles <!-- 1333705 -->
In this update, you can use Always-on VPN connections on Android enterprise devices with managed work profiles. Always-on VPN connections stay connected, or immediately reconnect when the user unlocks their device, when the device restarts, or when the wireless network changes. You can also put the connection in "lockdown" mode, which blocks all network traffic until the VPN connection is active.
You can enable Always-on VPN in **Device configuration** > **Profiles** > **Create profile** > **Android enterprise** for platform > **Device restrictions** > **Connectivity** settings.

#### Issue SCEP certificates to user-less devices <!-- 1744554 -->
Currently, certificates are issued to users. With this update, SCEP certificates can be issued to devices, including user-less devices such as kiosks (**Device configuration** > **Profiles** > **Create profile** > **Windows 10 and later** for platform > **SCEP certificate** for profile). 
Other updates include:
- The **Subject** property in an SCEP profile is now a custom textbox and can include new variables. 
- The **Subject alternative name (SAN)** property in an SCEP profile is now a table format and can include new variables. In the table, an admin can add an attribute and fill out the value in a custom textbox. The SAN will support the following attributes: 
  - DNS
  - Email address
  - UPN

  These new variables can be added with static text in a custom value textbox. For example, the DNS attribute can be added as `DNS = {{AzureADDeviceId}}.domain.com`.

  > [!NOTE]
  > Curly brackets, semicolons, and pipe symbols “ { } ; | ” will not work in the static text of the SAN. Curly brackets must only enclose one of the new device certificate variables to be accepted for either `Subject` or `Subject alternative name`. 

New device certificate variables:  

```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
> - `{{FullyQualifiedDomainName}}` only works for Windows and domain-joined devices. 
> - When specifying device properties such as IMEI, Serial Number, and Fully Qualified Domain Name in the subject or SAN for a device certificate, be aware that these properties could be spoofed by a person with access to the device. 

[Create a SCEP certificate profile](certificates-scep-configure.md#create-a-scep-certificate-profile) lists the current variables when creating an SCEP configuration profile. 

Applies to: Windows 10 and later and iOS, supported for Wi-Fi

#### Remotely lock uncompliant devices <!-- 2064495 -->
When a device is not compliant, you can create an action on the compliance policy that locks the device remotely. In Intune > **Device compliance**, create a new policy, or select an existing policy > **Properties**. Select **Actions for noncompliance** > **Add**, and choose to remotely lock the device.
Supported on: 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 and later 

#### Windows 10 and later Kiosk profile improvements in the Azure portal <!-- 2748224 -->
This update includes the following improvements to the Windows 10 Kiosk device configuration profile (**Device configuration** > **Profiles** > **Create profile** > **Windows 10 and later** for platform > **Kiosk preview** for profile type): 
- Currently, you can create multiple kiosk profiles on the same device. With this update, Intune will support only one kiosk profile per device. If you still need multiple kiosk profiles on a single device, you can use a Custom URI.
- In a **Multi-app kiosk** profile, you can select the application tile size and order for the **Start menu layout** in the application grid. If you prefer more customization, you can continue to upload an XML file.
- The Kiosk Browser settings are moving into the **Kiosk** settings. Currently, the **Kiosk web browser** settings have their own category in the Azure portal.
Applies to: Windows 10 and later

#### PIN prompt when you change fingerprints or face ID on an iOS device  <!-- 2637704  -->
Users are now prompted for a PIN after making biometric changes on their iOS device. This includes changes to registered fingerprints or face ID. The timing of the prompt depends on how the configuration of the *Recheck access requirements after (minutes)* timeout.  When no PIN is set, the user is prompted to set one. 
 
This feature is only available for iOS, and requires the participation of applications that integrate the Intune APP SDK for iOS, version 9.0.1 or later. Integration of the SDK is necessary so that the behavior can be enforced on the targeted applications. This integration happens on a rolling basis and is dependent on the specific application teams. Some apps that participate include WXP, Outlook, Managed Browser, and Yammer.

#### Network access control support on iOS VPN clients <!-- 1333693 -->
With this update, there's a new setting to enable Network Access Control (NAC) when your create a VPN configuration profile for Cisco AnyConnect, F5 Access, and Citrix SSO for iOS. This setting allows the NAC ID of the device to be included in the VPN profile. Currently, there aren't any VPN clients or NAC partner solutions that support this new NAC ID, but we will keep you informed through our [support blog post](ttps://aka.ms/iOS12_and_vpn) when they do.

To use NAC, you'll need to:
1. Opt in to allow Intune to include device IDs in VPN profiles
2. Update your NAC provider software/firmware, using guidance directly from your NAC provider

For information on this setting within an iOS VPN profile, see [Add VPN settings on iOS devices in Microsoft Intune](vpn-settings-ios.md). For more information on network access control, see [Network access control (NAC) integration with Intune](network-access-control-integrate.md). 

Applies to: iOS

#### Remove an email profile from a device, even when there's only one email profile <!-- 1818139 -->
Previously, you couldn't remove an email profile from a device *if* it's the only email profile. With this update, this behavior changes. Now, you can remove an email profile, even if it's the only email profile on the device. 
See [Add email settings to devices using Intune](email-settings-configure.md) for details.

#### PowerShell scripts and AAD <!-- 2309469 -->
PowerShell scripts in Intune can be targeted to AAD device security groups.

#### New "Required password type" default setting for Android, Android enterprise<!-- 2649963 -->
When you create a new compliance policy (**Intune** > **Device compliance** > **Policies** > **Create policy** > **Android** or **Android enterprise** for Platform > System Security), the default value for **Required password type** changes:

From: Device default
To: At least numeric

Applies to: Android, Android Enterprise

To see these settings, go to [Android](compliance-policy-create-android.md) and [Android Enterprise](compliance-policy-create-android-for-work.md).

#### Use a pre-shared key in a Windows 10 Wi-Fi profile <!-- 2662938 -->
With this update, you can use a pre-shared key (PSK) with the WPA/WPA2-Personal security protocol to authenticate a Wi-Fi configuration profile for Windows 10. You can also specify the cost configuration for a metered network for devices on Windows 10 October 2018 update.

Currently, you must import a Wi-Fi profile, or create a custom profile to use a pre-shared key. [Wi-Fi settings for Windows 10](wi-fi-settings-windows.md) lists the current settings. 

#### Remove PKCS and SCEP certificates from your devices <!-- 3218390 -->
In some scenarios, PKCS and SCEP certificates remained on devices, even when removing a policy from a group, deleting a configuration or compliance deployment, or an admin updating an existing SCEP or PKCS profile. 
This update changes the behavior. There are some scenarios where PKCS and SCEP certificates are removed from devices, and some scenarios where these certificates remain on the device. 
See [Remove SCEP and PKCS certificates in Microsoft Intune](remove-certificates.md) for these scenarios.

#### Use Gatekeeper on macOS devices for compliance <!-- 2504381 -->
This update includes the macOS Gatekeeper to evaluate devices for compliance. To set the Gatekeeper property, [Add a device compliance policy for macOS devices](compliance-policy-create-mac-os.md).

### Device enrollment

#### Apply Autopilot profile to enrolled Win 10 devices not already registered for Autopilot <!-- 1558983 -->
You can apply Autopilot profiles to enrolled Win 10 devices that have not already been registered for Autopilot. In the Autopilot profile, choose the **Convert all targeted devices to Autopilot** option to automatically register non-Autopilot devices with the Autopilot deployment service. Allow 48 hours for the registration to be processed. When the device is unenrolled and reset, Autopilot will provision it.

#### Create and assign multiple Enrollment Status  Page profiles to Azure AD groups <!-- 2526564 -->
You can now [create and assign](windows-enrollment-status.md) multiple Enrollment Status Page profiles to Azure ADD groups.

#### Migration from Device Enrollment Program to Apple Business Manager in Intune <!--2748613-->
Apple Business Manager (ABM) works in Intune and you can upgrade your account from Device Enrollment Program (DEP) to ABM. The process in Intune is the same. To upgrade your Apple account from DEP to ABM, go to [https://support.apple.com/HT208817]( https://support.apple.com/HT208817).

#### Alert and enrollment status tabs on the Device enrollment overview page <!--2748656-->
Alerts and enrollment failures now appear on separate tabs on the Device enrollment overview page.

#### Enrollment abandonment report <!-- 1382924 -->
A new report that provides details on abandoned enrollments is available under **Device enrollment** > **Monitor**. For more information, see [Company portal abandonment report](enrollment-report-company-portal-abandon.md).

#### New Azure Active Directory terms of use feature <!-- 2870393 -->
Azure Active Directory has a terms of use feature that you can use instead of existing Intune terms and conditions. The Azure AD terms of use feature provides more flexibility on which terms to show and when to show them, better localization support, more control in how terms are rendered and improved reporting. The Azure AD terms of use feature does require Azure Active Directory Premium P1 which is also part of the Enterprise Mobility + Security E3 suite. To learn more, see the [Manage your company's terms and conditions for user access article](terms-and-conditions-create.md).

#### Android Device Owner mode support <!--3188762-->
For Samsung Knox Mobile Enrollment, Intune now supports enrolling devices to the Android Device Owner mode of management. Users on WiFi or cellular networks can enroll with just a few taps when they turn on their devices for the first time. For more information, see [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md).

### Device management
#### New settings for Software Updates   <!-- 1907869 -->  
- You can now configure some notifications to alert end-users about restarts that are required to finish installation of the latest software updates.   
- You can now configure a restart warning prompt for restarts that happen outside of work hours, which supports BYOD scenarios.

#### Group Windows Autopilot-enrolled devices by correlator ID <!-- 2075110 -->
Intune now supports grouping Windows devices by a correlator ID when enrolled using [Autopilot for existing devices](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) through Configuration Manager. The correlator ID is a parameter of the Autopilot configuration file. Intune will automatically set the [Azure AD device attribute enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) to equal "OfflineAutopilotprofile-<correlator ID>". This allows arbitrary Azure AD dynamic groups to be created based off correlator ID via the enrollmentprofileName attribute for offline Autopilot enrollments. For more information, see [Windows Autopilot for existing devices](enrollment-autopilot.md#windows-autopilot-for-existing-devices).

#### Intune app protection policies <!-- 2984657 -->
Intune app protection policies allow you to configure various data protection settings for Intune protected apps, such as Microsoft Outlook and Microsoft Word. We’ve change the look and feel of these settings for both [iOS](app-protection-policy-settings-ios.md) and [Android](app-protection-policy-settings-android.md) to make it easier to find individual settings. There are three categories of policy settings:
- **Data relocation** - This group includes the data loss prevention (DLP) controls, like cut, copy, paste, and save-as restrictions. These settings determine how users interact with data in the apps.
- **Access requirements** - This group contains the per-app PIN options that determine how the end user accesses the apps in a work context.  
- **Conditional launch** - This group holds settings like the minimum OS settings, jailbreak and rooted device detection, and offline grace periods.  
  
The functionality of the settings doesn’t change, but it will be easier to find them when you work in the policy authoring flow.

#### Restricts apps, and block access to company resources on Android devices <!-- 2451462  -->  
In **Device compliance** > **Policies** > **Create policy** > **Android** > **System Security**, there is a new setting under the *Device Security* section, named **Restricted apps**. The **Restricted apps** setting uses a compliance policy to block access to company resources if certain apps are installed on the device. The device is considered non-compliant until the restricted apps are removed from the device.
Applies to: 
- Android

### Intune apps

#### Intune will support a maximum package size of 8 GB for LOB apps <!-- 1727158 -->
Intune increased the maximum package size to 8 GB for Line-of-business (LOB) apps. For more information, see [Add apps to Microsoft Intune](apps-add.md).

#### Add custom brand image for Company Portal app <!-- 1916266 -->
As the Microsoft Intune admin, you can upload a custom brand image which will be displayed as a background image on the user's profile page in the iOS Company Portal app. For more information about configuring the Company Portal app, see [How to configure the Microsoft Intune Company Portal app](company-portal-app.md).

#### Intune will maintain the Office localized language when updating Office on end users machines <!-- 2971030 -->
When Intune installs Office on your end user's machines, end users automatically get the same language packs that they had with previous .MSI Office installations. For more information, see [Assign Office 365 apps to Windows 10 devices with Microsoft Intune](apps-add-office365.md).

### Monitor and troubleshoot

#### New Intune Support Experience in the Microsoft 365 Device Management portal <!-- 3076965 -->
We are rolling out a new Help and Support experience for Intune in the [Microsoft 365 Device Management portal]( http://devicemanagement.microsoft.com). The new experience lets you describe your problem in your own words and receive troubleshooting insight and web-based remediation content. These solutions are offered via a rule-based machine learning algorithm, driven by user inquiries.  

In addition to issue-specific guidance, you can also use the new case creation workflow to open a support case by email or phone.  

For customers who are part of the rollout, this new experience replaces the current Help and Support experience of a static set of pre-selected options that are based on the area of the console you are in when you open Help and Support.  

*This new Help and Support experience is being rolled out to some but not all tenants and is available in the Device Management portal. Participants for this new experience are randomly selected from the available Intune tenants. New tenants will be added as we expand the rollout.*  

For more information, see [Help and Support experience](get-support.md#help-and-support-experience) in How to get support for Microsoft Intune.  

#### PowerShell module for Intune – Preview available <!-- 951068 -->
A new PowerShell module, which provides support for the Intune API through Microsoft Graph, is now available for preview on [GitHub]( https://aka.ms/intunepowershell). For details about how to use this module, see the README in that location. 

<!-- ########################## -->
## September 2018

### App management

#### Remove duplication of app protection status tiles <!-- 3083391 -->
The **User status for iOS** and the **User status for Android** tiles were present in both the **Client Apps - Overview** page, as well as the **Client Apps - App protection status** page. The status tiles have been removed from the **Client Apps - Overview** page to avoid duplication. 

### Device configuration

#### Support for more third-party certification authorities (CA) <!-- 3093107 -->
By using the Simple Certificate Enrollment Protocol (SCEP), you can now issue new certificates and renew certificates on mobile devices using Windows, iOS, Android, and macOS.

### Device enrollment

#### Intune moves to support iOS 10 and later <!-- 2454656 -->  
Intune enrollment, the Company Portal, and the managed browser now only support iOS devices running iOS 10 and later. To check for devices or users that are affected in your organization, go to Intune in the Azure portal > **Devices** > **All devices**. Filter by OS and then click **Columns** to surface OS version details. Ask these users to upgrade their devices to a supported OS version.  

If you have any of the devices listed below, or want to enroll any of the devices listed below, be aware that they only support iOS 9 and earlier.  To continue to access the Intune Company Portal, you must upgrade these devices to devices that support iOS 10 or later:  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (3rd Generation) 
* iPad Mini (1st Generation)  

### Device management

#### Microsoft 365 Device Management administration center <!-- 3078424 -->
One of the promises of Microsoft 365 is simplified administration, and over the years we’ve integrated the back-end Microsoft 365 services to deliver end-to-end scenarios such as Intune and Azure AD Conditional Access. The new [Microsoft 365 administration center](http://devicemanagement.microsoft.com) is the place to consolidate, simplify, and integrate the admin experience. The specialist workspace for Device Management provides easy access to all of the device and app management information and tasks that your organization needs. We expect this to become the primary cloud workspace for enterprise end user computing teams.

<!-- ########################## -->
## August 2018

### App management

#### Packet tunnel support for iOS per-app VPN profiles for custom and Pulse Secure connection types <!-- 1520957 -->
When using iOS per-app VPN profiles, you can choose to use app-layer tunneling (app-proxy) or packet-level tunneling (packet-tunnel). These options are available with the following connection types:
- Custom VPN
- Pulse Secure
If you are not sure which value to use, consult your VPN provider's documentation.

#### Delay when iOS software updates are shown on the device <!-- 1949583 -->
In Intune > **Software Updates** > **Update policies for iOS**, you can configure the days and times when you don't want devices to install any updates. In a future update, you'll be able to delay when a software update is visibly shown on the device, from 1-90 days. 
[Configure iOS update policies in Microsoft Intune](software-updates-ios.md) lists the current settings.

#### Office 365 ProPlus version <!-- 2213968 -->
When assigning the Office 365 ProPlus apps to Windows 10 devices using Intune, you will be able to select the version of Office. In the Azure portal, select **Microsoft Intune** > **Apps** > **Add App**. Then, select **Office 365 ProPlus Suite (Windows 10)** from the **Type** dropdown list. Select **App Suite Settings** to display the associated blade. Set the **Update Channel** to a value, such as **Monthly**. Optionally, remove other version of Office (msi) from end user devices by selecting **Yes**. Select **Specific** to install a specific version of Office for the selected channel on end user devices. At this point, you can select the **Specific version** of Office to use. The available versions will change over time. Therefore, when creating a new deployment, the versions available may be newer and not have certain older versions available. Current deployments will continue to deploy the older version, but the version list will be continually updated per channel. For more information, see [Overview of update channels for Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

#### Support for Register DNS setting for Windows 10 VPN <!-- 2282852 -->
With this update, you can configure Windows 10 VPN profiles to dynamically register the IP addresses assigned to the VPN interface with the internal DNS, without needing to use custom profiles.
For information about the current VPN profile settings available, see [Windows 10 VPN settings](vpn-settings-windows-10.md). 

#### The macOS Company Portal installer now includes the version number in the installer file name <!--2652728-->

#### iOS automatic app updates <!-- 2729759 -->
Automatic app updates work for both device and user licensed apps for iOS Version 11.0 and above.

### Device configuration

#### Windows Hello will target users and devices <!-- 1106609 -->
When you create a [Windows Hello for Business](windows-hello.md) policy, it applies to all users within the organization (tenant-wide). With this update, the policy can also be applied to specific users or specific devices using a device configuration policy (**Device Configuration** > **Profiles** > **Create profile** > **Identity Protection** > **Windows Hello for Business**).
In Intune in the Azure portal, the Windows Hello configuration and settings now exists in both **Device enrollment** and **Device configuration**. **Device enrollment** targets the entire organization (tenant-wide), and supports Windows AutoPilot (OOBE). **Device configuration** targets devices and users using a policy that's applied during check-in.
This feature applies to:  
- Windows 10 and later
- Windows Holographic for Business

#### Zscaler is an available connection for VPN profiles on iOS <!-- 1769858 -->
When you create an iOS VPN device configuration profile (**Device configuration** > **Profiles** > **Create profile** > **iOS** platform > **VPN** profile type), there are several connection types, including Cisco, Citrix, and more. This update adds Zscaler as a connection type. 
[VPN settings for devices running iOS](vpn-settings-ios.md) lists the available connection types.

#### FIPS mode for Enterprise Wi-Fi profiles for Windows 10 <!-- 1879077 -->
You can now enable Federal Information Processing Standards (FIPS) mode for Enterprise Wi-Fi profiles for Windows 10 in the Intune Azure portal. Be sure FIPS mode is enabled on your Wi-Fi infrastructure if you enable it in your Wi-Fi profiles.
[Wi-Fi settings for Windows 10 and later devices in Intune](wi-fi-settings-windows.md) shows you how to create a Wi-Fi profile.

#### Control S-mode on Windows 10 and later devices - public preview <!-- 1958649 -->
With this feature update, you can create a device configuration profile that switches a Windows 10 device out of S-mode, or prevent users from switching the device out of S-mode. This feature is in Intune > **Device configuration** > **Profiles** >  **Windows 10 and later** > **Edition upgrade and mode switch**.
[Introducing Windows 10 in S mode](https://www.microsoft.com/windows/s-mode) provides more information on S mode.
Applies to: the most recent [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) build (while in preview).

#### Windows Defender ATP configuration package automatically added to configuration profile <!-- 2144658 -->
When using [Advanced Threat Protection and onboarding](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) devices in Intune, you previously had to download a configuration package, and add it to your configuration profile. With this update, Intune automatically gets the package from Windows Defender Security Center, and adds it to your profile.
Applies to Windows 10 and later.

#### Require users to connect during device setup <!--2311457-->
You can now set device profiles to require that the device connects to a network before proceeding past the Network page during Windows 10 setup. While this feature is in preview, a Windows Insider build 1809 or later is required to use this setting.
Applies to: the most recent [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) build (while in preview).

#### Restricts apps, and block access to company resources on iOS and Android Enterprise devices <!-- 2451462 -->
In **Device compliance** > **Policies** > **Create policy** > **iOS** > **System Security**, there is a new **Restricted applications** setting. This new setting uses a compliance policy to block access to company resources if certain apps are installed on the device. The device is considered non-compliant until the restricted apps are removed from the device.
Applies to: iOS

#### Modern VPN support updates for iOS <!-- 2459928, 1819876, and 2650856 -->
This update adds support the following iOS VPN clients: 
- F5 Access (version 3.0.1 and higher)
- Citrix SSO
- Palo Alto Networks GlobalProtect version 5.0 and higher
Also in this update:
- Existing **F5 Access** connection type is renamed to **F5 Access Legacy** for iOS.
- Existing **Palo Alto Networks GlobalProtect** connection type is renamed to **Palo Alto Networks GlobalProtect (legacy)** for iOS.
Existing profiles with these connection types continue to work with their respective legacy VPN client. If you're using Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN, or Palo Alto Networks GlobalProtect version 4.1 and earlier with iOS, you should move to the new apps. Do this as soon as possible to ensure that VPN access is available for iOS devices as they update to iOS 12.
For more information about iOS 12 and VPN profiles, see the [Microsoft Intune Support Team Blog](https://go.microsoft.com/fwlink/?linkid=2013806).

#### Export Azure classic portal compliance policies to recreate these policies in the Intune Azure portal <!-- 2469637 -->
Compliance policies created in the Azure classic portal will be deprecated. You can review and delete any existing compliance policies, however you can't update them. If you need to migrate any compliance policies to the current Intune Azure portal, you can export the policies as a comma-separated file (*.csv* file). Then, use the details in the file to recreate these policies in the Intune Azure portal.

> [!IMPORTANT]
> When the Azure classic portal retires, you will no longer be able to access or view your compliance policies. Therefore, be sure to export your policies and recreate them in the Azure portal before the Azure classic portal retires.

#### Better Mobile - New Mobile Threat Defense partner <!-- 22662717 -->
You can control mobile device access to corporate resources using Conditional Access based on risk assessment conducted by Better Mobile, a Mobile Threat Defense solution that integrates with Microsoft Intune.

### Device enrollment

#### Lock the Company Portal in single app mode until user sign-in <!--1067692 --> 
You now have the option to run the Company Portal in Single App mode if you authenticate a user through the Company Portal instead of Setup Assistant during DEP enrollment. This option locks the device immediately after Setup Assistant completes so that a user must sign in to access the device. This process makes sure that the device completes onboarding and is not orphaned in a state without any user tied.

#### Assign a user and friendly name to an Autopilot device <!--1346521 -->
You can now [assign a user to a single Autopilot device](enrollment-autopilot.md). Admins will also be able to give friendly names to greet the user when setting up their device with Autopilot.
Applies to: the most recent [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) build (while in preview).

#### Use VPP device licenses to pre-provision the Company Portal during DEP enrollment <!-- 1608345 -->
You can now use Volume Purchase Program (VPP) device licenses to pre-provision the Company Portal during Device Enrollment Program (DEP) enrollments. To do so, when you [create or edit an enrollment profile](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile), specify the VPP token that you want to use to install the Company Portal. Make sure that your token doesn't expire and that you have enough licenses for the Company Portal app. In cases where the token expires or runs out of licenses, Intune will push the App Store Company Portal instead (this will prompt for an Apple ID).

#### Confirmation required to delete VPP token that is being used for Company Portal pre-provisioning <!-- 2237634 -->
A confirmation is now required to delete a Volume Purchase Program (VPP) token if it is being used to pre-provision the Company Portal during DEP enrollment.

#### Block Windows personal device enrollments <!-- 1849498 -->
You can [block Windows personal devices](enrollment-restrictions-set.md#set-device-type-restrictions) from enrolling with [mobile device management](windows-enroll.md) in Intune. Devices enrolled with [Intune PC agent](manage-windows-pcs-with-microsoft-intune.md) can't be blocked with this feature. This feature is rolling out over the next couple weeks so you might not see it immediately in the user interface.

#### Specify machine name patterns in an Autopilot profile <!--1849855-->
You can [specify a computer name template](enrollment-autopilot.md#create-an-autopilot-deployment-profile) to generate and set the [computer name](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) during Autopilot enrollment. Applies to: the most recent [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) build (while in preview).

#### For Windows Autopilot profiles, hide the change account options on the company sign-in page and domain error page <!--1901669 -->
There are [new Windows Autopilot profile options](enrollment-autopilot.md#create-an-autopilot-deployment-profile) for admins to hide the change account options on the company sign-in and domain error pages. Hiding these options requires Company Branding to be configured in Azure Active Directory. 
Applies to: the most recent [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) build (while in preview).

### macOS support for Apple Device Enrollment Program <!-- 747651 -->
Intune now supports enrolling macOS devices into the Apple Device Enrollment Program (DEP). For more information, see [Automatically enroll macOS devices with Apple's Device Enrollment Program](device-enrollment-program-enroll-macos.md).

### Device management

#### Delete Jamf devices <!-- 2653306-->
You can delete JAMF-managed devices by going to **Devices** > choose the Jamf device > **Delete**.

#### Change terminology to "retire" and "wipe" <!-- 2175759 -->
To be consistent with the Graph API, the Intune user interface and documentation has changed the following terms:
- **Remove company data** will be changed to "retire"
- **Factory reset** will be changed to **wipe**

#### Confirmation dialog if admin tries to delete MDM Push Certificate <!-- 297909500-->
If anyone tries to delete an Apple MDM Push certificate, a confirmation dialog box displays the number of related iOS and macOS devices. If the certificate is deleted, these devices will need to be re-enrolled.

#### Additional security settings for Windows installer <!-- 2282430 -->
You can allow users to control app installs. If enabled, installations that may otherwise be stopped due to a security violation would be permitted to continue. You can direct the Windows installer to use elevated permissions when it installs any program on a system. Additionally, you can enabled Windows Information Protection (WIP) items to be indexed and the metadata about them stored in an unencrypted location. When the policy is disabled, the WIP protected items are not indexed and do not show up in the results in Cortana or file explorer. The functionality for these options are disabled by default. 

#### New user experience update for the Company Portal website <!--2000968 -->
We’ve added new features, based on feedback from customers, to the Company Portal website. You'll experience a significant improvement in existing functionality and usability from your devices. Areas of the site&ndash;such as device details, feedback and support, and device overview&ndash;have received a new, modern, responsive design. You'll also see:

- Streamlined workflows across all device platforms
- Improved device identification and enrollment flows
- More helpful error messages
- Friendlier language, less tech jargon
- Ability to share direct links to apps
- Improved performance for large app catalogs
- Increased accessibility for all users  

The [Intune Company Portal website documentation](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website) has been updated to reflect these changes. To view an example of the app enhancements, see [UI updates for Intune end-user apps](whats-new-app-ui.md).  

### Monitor and troubleshoot

#### Enhanced jailbreak detection in compliance reporting<!-- 2198738 -->
The enhanced jailbreak detection setting states now appears in all compliance reporting in the admin console.

### Role-based access control

#### Scope tags for policies <!--1081974 -->
You can [create scope tags](scope-tags.md) to limit access to Intune resources. Add a scope tag to a role assignment and then add the scope tag to a configuration profile. The role will only have access to resources with configuration profiles that have matching scope tags (or no scope tag).

<!-- ########################## -->
## July 2018

### App management

#### Line-of-business (LOB) app support for macOS <!-- 1895847 -->
Microsoft Intune allows macOS LOB apps to be deployed as **Required** or **Available with enrollment**. End users can get apps deployed as **Available** using the Company Portal for macOS or the [Company Portal website](https://portal.manage.microsoft.com).

#### iOS built-in app support for kiosk mode <!-- 2051098 -->
In addition to Store Apps and Managed Apps, you can now select a Built-In App (such as Safari) that runs in kiosk mode on an iOS device.

#### Edit your Office 365 Pro Plus app deployments <!-- 2150145 -->
As the Microsoft Intune admin, you have greater ability to edit your Office 365 Pro Plus app deployments. Additionally, you no longer have to delete your deployments to change any of the suite’s properties. In the Azure portal, select **Microsoft Intune** > **Client apps** > **Apps**. From the list of apps, select your Office 365 Pro Plus Suite.  

#### Updated Intune App SDK for Android is now available <!-- 2744271-->
An updated version of the Intune App SDK for Android is available to support the Android P release. If you are an app developer and use the Intune SDK for Android, you must install the updated version of the Intune app SDK to ensure that Intune functionality within your Android apps continue to work as expected on Android P devices. This version of the Intune App SDK provides a built-in plugin that performs the SDK updates. You do not need to rewrite any existing code that’s integrated. For details, see [Intune SDK for Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android). If you are using the old badging style for Intune, we recommend that you use the briefcase icon. For branding details, see [this GitHub repository](https://github.com/msintuneappsdk/intune-app-partner-badge).

#### More opportunities to sync in the Company portal app for Windows  
The Company Portal app for Windows now lets you initiate a sync directly from the Windows taskbar and Start menu. This feature is especially useful if your only task is to sync devices and get access to corporate resources. To access the new feature, right-click the Company portal icon that's pinned to your taskbar or Start menu. In the menu options (also referred to as a jump list), select **Sync this device**. The Company Portal will open to the **Settings** page and initiate your sync. For a look at the new functionality see [What's new in the UI](whats-new-app-ui.md).   

#### New browsing experiences in the Company portal app for Windows  
Now when browsing or searching for apps in the Company Portal app for Windows, you can toggle between the existing **Tiles** view and the newly added **Details** view. The new view lists application details such as name, publisher, publication date and installation status.  

The **Apps** page's **Installed** view lets you see details about completed and in-progress app installations. To see what the new view looks like, see [What's new in the UI](whats-new-app-ui.md).  

#### Improved Company Portal app experience for device enrollment managers  
When a device enrollment manager (DEM) signs in to the Company Portal app for Windows, the app will now only list the DEM's current, running device. This improvement will reduce timeouts that previously occurred when the app tried to show all DEM-enrolled devices.  

#### Block app access based on unapproved device vendors and models  <!-- 1425689 ! -->
The Intune IT admin can enforce a specified list of Android manufacturers, and/or iOS models through Intune App Protection Policies. The IT admin can provide a semicolon separated list of manufacturers for Android policies and device models for iOS policies. Intune App Protection Policies are for Android and iOS only. There are two separate actions that can be performed on this specified list:
- A block from app access on devices that are not specified.
- Or, a selective wipe of corporate data on devices that are not specified. 

The user will be unable to access the targeted application if the requirements through the policy are not met. Based on settings, the user may either be blocked, or selectively wiped of their corporate data within the app. On iOS devices, this feature requires the participation of applications (such as WXP, Outlook, Managed Browser, Yammer) to integrate the Intune APP SDK for this feature to be enforced with the targeted applications. This integration happens on a rolling basis and is dependent on the specific application teams. On Android, this feature requires the latest Company Portal. 

On end-user devices, the Intune client will take action based on a simple matching of the strings specified in the Intune blade for Application Protection Policies. This depends entirely on the value that the device reports. As such, the IT administrator is encouraged to ensure that the intended behavior is accurate. This can be accomplished by testing this setting based on a variety of device manufacturers and models targeted to a small user group. In Microsoft Intune, select **Client apps** > **App protection policies** to view and add app protection policies. For more information about app protection policies, see [What are app protection policies](app-protection-policy.md) and [Selectively wipe data using app protection policy access actions in Intune](app-protection-policies-access-actions.md).

#### Access to macOS Company Portal pre-release build <!-- 1734766 -->
Using Microsoft AutoUpdate, you can sign up to receive builds early by joining the Insider program. Signing up will enable you to use the updated Company Portal before it’s available to your end users. For more information, see the [Microsoft Intune blog](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/).

### Device configuration

#### Create device compliance policy using Firewall settings on macOS devices <!-- 1497640 -->
When you create a new macOS compliance policy (**Device compliance** > **Policies** > **Create policy** > **Platform: macOS** > **System security**), there are some new **Firewall** settings available: 

- **Firewall**: Configure how incoming connections are handled in your environment.
- **Incoming connections**: **Block** all incoming connections except those required for basic internet services, such as DHCP, Bonjour, and IPSec. This setting also blocks all sharing services.
- **Stealth Mode**: **Enable** stealth mode to prevent the device from responding to probing requests. The device continues to answer incoming requests for authorized apps.

Applies to: macOS 10.12 and later

#### New Wi-Fi device configuration profile for Windows 10 and later <!-- 1879077 -->
Currently, you can import and export Wi-Fi profiles using XML files. With this update, you can create a Wi-Fi device configuration profile directly in Intune, just like some other platforms.

To create the profile, open **Device configuration** > **Profiles** > **Create Profile** > **Windows 10 and later** > **Wi-Fi**. 

Applies to Windows 10 and later.

#### Kiosk - obsolete is grayed out, and can't be changed <!-- 2149998 -->
The Kiosk (preview) feature (**Device configuration** > **Profiles** > **Create profile** > **Windows 10 and later** > **Device restrictions**) is obsolete, and replaced with [Kiosk settings for Windows 10 and later](kiosk-settings.md). With this update, the **Kiosk - Obsolete** feature is grayed out, and the user interface can't be changed or updated. 

To enable kiosk mode, see [Kiosk settings for Windows 10 and later](kiosk-settings.md).

Applies to Windows 10 and later, Windows Holographic for Business

#### APIs to use 3rd party certification authorities <!-- 2184013 -->
In this update, there is a Java API that enables third-party certificate authorities to integrate with Intune and SCEP. Then, users can add the SCEP certificate to a profile, and apply it to devices using MDM.

Currently, Intune supports [SCEP requests using Active Directory Certificate Services](certificates-scep-configure.md).

#### Toggle to show or not show the End Session button on a Kiosk browser <!-- 2455253 -->
You can now configure whether or not Kiosk browsers show the End Session button. You can see the control at **Device configuration** > **Kiosk (preview)** > **Kiosk Web Browser**. If turned on, when a user clicks the button, the app prompts for confirmation to end the session. When confirmed, the browser clears all browsing data and navigates back to the default URL.

#### Create an eSIM cellular configuration profile <!-- 2564077 -->
In **Device configuration**, you can create an eSIM cellular profile. You can import a file that contains cellular activation codes provided by your mobile operator. You can then deploy these profiles to your eSIM LTE enabled Windows 10 devices, such as the Surface Pro LTE and other eSIM capable devices.

Check to see if your [devices support eSIM profiles](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

Applies to Windows 10 and later. 

#### Select device categories by using the Access Work or School settings <!-- 1058963 eenotready --> 
If you've enabled [device group mapping](https://docs.microsoft.com/intune/device-group-mapping), users on Windows 10 will now be prompted to select a device category after enrolling through the **Connect** button in **Settings** > **Accounts** > **Access work or school**. 

#### Use sAMAccountName as the account username for email profiles <!-- 1500307 -->
You can use the on-premises **sAMAccountName** as the account username for email profiles for Android, iOS, and Windows 10. You can also get the domain from the `domain` or `ntdomain` attribute in Azure Active Directory (Azure AD). Or, enter a custom static domain.

To use this feature, you must sync the `sAMAccountName` attribute from your on-premises Active Directory environment to Azure AD.

Applies to [Android](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 and later](email-settings-windows-10.md)

#### See device configuration profiles in conflict <!-- 1556983 -->
In **Device Configuration**, a list of the existing profiles is shown. With this update, a new column is added that provides details on profiles that have a conflict. You can select a conflicting row to see the setting and profile that has the conflict. 

More on [manage configuration profiles](device-profile-monitor.md#view-conflicts).

#### New status for devices in device compliance <!-- 2308882 -->
In **Device compliance** > **Policies** > select a policy > **Overview**, the following new states are added:
- succeeded
- error
- conflict
- pending
- not-applicable
An image that shows the device count of a different platform is also shown. For example, if you're looking at an iOS profile, the new tile shows the count of non-iOS devices that are also assigned to this profile. See [Device compliance policies](compliance-policy-monitor.md#view-status-of-device-policies).

#### Device compliance supports 3rd party anti-virus solutions <!-- 2325484 -->
When you create a device compliance policy (**Device compliance** > **Policies** > **Create policy** > **Platform: Windows 10 and later** > **Settings** > **System Security**), there are new **[Device Security](compliance-policy-create-windows.md)** options: 
- **Antivirus**: When set to **Require**, you can check compliance using antivirus solutions that are registered with Windows Security Center, such as Symantec and Windows Defender. 
- **AntiSpyware**: When set to **Require**, you can check compliance using antispyware solutions that are registered with Windows Security Center, such as Symantec and Windows Defender. 

Applies to: Windows 10 and later 

### Device enrollment

#### Automatically mark Android devices enrolled by using Samsung Knox Mobile Enrollment as "corporate". <!-- 2404851 -->
By default, Android devices enrolled using Samsung Knox Mobile Enrollment are now marked as **corporate** under **Device Ownership**. You don't need to manually identify corporate devices using IMEI or serial numbers prior to enrolling using Knox Mobile Enrollment.

#### Devices without profiles column in the list of enrollment program tokens <!-- 1853904 -->
In the enrollment program tokens list, there is a new column showing the number of devices without a profile assigned. This helps admins assign profiles to these devices before handing them out to users. To see the new column, go to **Device enrollment** > **Apple enrollment** > **Enrollment program tokens**.

### Device management

#### Bulk delete devices on devices blade <!-- 1793693 -->
You can now delete multiple devices at a time on the Devices blade. Choose **Devices** > **All devices** > select the devices you want to delete > **Delete**. For devices that can't be deleted, an alert will be displayed.

#### Google name changes for Android for Work and Play for Work <!--842873 -->
Intune has updated "Android for Work" terminology to reflect Google branding changes. The terms "Android for Work" and "Play for Work" are no longer be used. Different terminology is used depending on the context:
- "Android enterprise" refers to the overall modern Android management stack.
- "Work profile" or "Profile Owner" refers to BYOD devices managed with work profiles.
- "Managed Google Play" refers to the Google app store.

#### Rules for removing devices <!-- 1609459 -->
New rules are available that let you automatically remove devices that haven't checked in for a number of days that you set. To see the new rule, go to the **Intune** pane, select **Devices**, and select **Device cleanup rules**.

#### Corporate-owned, single use support for Android devices <!-- 1630973 -->

Intune now supports highly-managed, locked-down, kiosk-style Android devices. This allows admins to further lock down the usage of a device to a single app or small set of apps, and prevents users from enabling other apps or performing other actions on the device. To set up Android kiosk, go to Intune > **Device enrollment** > **Android enrollment** > **Kiosk and task device enrollments**. For more information, see [Set up enrollment of Android enterprise kiosk devices](android-kiosk-enroll.md).

#### Per-row review of duplicate corporate device identifiers uploaded <!-- 2203794-->
When uploading corporate IDs, Intune now provides a list of any duplicates and gives you the option to replace or keep the existing information. The report will appear if there are duplicates after you choose **Device enrollment** > **Corporate Device Identifiers** > **Add Identifiers**. 

#### Manually add corporate device identifiers <!-- 2203803 -->
You can now manually add corporate device IDs. Choose **Device enrollment** > **Corporate Device Identifiers** > **Add**. 

<!-- ########################## -->
## June 2018

### App management

#### Microsoft Edge mobile support for Intune app protection policies <!-- 1817882 -->
The Microsoft Edge browser for mobile devices now supports app protection policies defined in Intune.

#### Retrieve the associated app user model ID (AUMID) for Microsoft Store for Business apps in kiosk mode <!-- 1560077 ! -->
Intune can now retrieve the app user model IDs (AUMIDs) for Microsoft Store for Business (WSfB) apps to provide improved configuration of the kiosk profile.

For more information about Microsoft Store for Business apps, see [Manage apps from Microsoft Store for Business](windows-store-for-business.md).

#### New Company Portal branding page <!-- 1916370 -->
The Company Portal branding page has a new layout, messages, and tooltips.

### Device configuration

#### Pradeo - New Mobile Threat Defense partner <!-- 1169249 -->
You can control mobile device access to corporate resources using Conditional Access based on risk assessment conducted by Pradeo, a Mobile Threat Defense solution that integrates with Microsoft Intune.

#### Use FIPS mode with the NDES Certificate connector <!-- 1333688 -->
When you install the NDES Certificate connector on a computer with Federal Information Processing Standard (FIPS) mode enabled, issuing and revoking certificates didn't work as expected. With this update, support for FIPS is included with the NDES Certificate connector. 

This update also includes:

- The NDES Certificate connector requires .NET 4.5 Framework, which is automatically included with Windows Server 2016 and Windows Server 2012 R2. Previously, .NET 3.5 Framework was the minimum required version.
- TLS 1.2 support is included with the NDES Certificate connector. So if the server with NDES Certificate connector installed supports TLS 1.2, then TLS 1.2 is used. If the server doesn't support TLS 1.2, then TLS 1.1 is used. Currently, TLS 1.1 is used for authentication between the devices and server.

For more information, see [Configure and use SCEP certificates](certificates-scep-configure.md) and [Configure and use PKCS certificates](certficates-pfx-configure.md).

#### Support for Palo Alto Networks GlobalProtect VPN profiles <!-- 1333680 ! -->
With this update, you can choose Palo Alto Networks GlobalProtect as a VPN connection type for VPN profiles in Intune (**Device configuration** > **Profiles** > **Create profile** > **Profile type** > **VPN**). In this release, the following platforms are supported: 

- iOS
- Windows 10

#### Additions to Local Device Security Options settings <!-- 1403702 -->
You can now configure additional Local Device Security Options settings for Windows 10 devices. Additional settings are available in the areas of Microsoft Network Client, Microsoft Network Server, Network access and security, and Interactive logon. Find these settings in the Endpoint Protection category when you create a Windows 10 device configuration policy.

#### Enable kiosk mode on Windows 10 devices <!-- 1560072 ! -->
On Windows 10 devices, you can create a configuration profile and enable kiosk mode (**Device Configuration** > **Profiles** > **Create profile** > **Windows 10** > **Device Restrictions** > **Kiosk**). In this update, the **Kiosk (preview)** setting is renamed to **Kiosk (obsolete)**. **Kiosk (obsolete)** is no longer recommended for use, but will continue to function until the July update. **Kiosk (obsolete)** is replaced by the new **Kiosk** profile type (**Create profile** > **Windows 10** > **Kiosk (preview)**), which will contain the settings to configure Kiosks on Windows 10 RS4 and later.

Applies to Windows 10 and later.

#### Device profile graphical user chart is back <!-- 2160133 -->
While improving the numeric counts shown on the device profile graphical chart (**Device configuration** > **Profiles** > select an existing profile > **Overview**), the graphical user chart was temporarily removed.

With this update, the graphical user chart is back, and shown in the Azure portal.

### Device enrollment

#### Support for Windows Autopilot enrollment without user authentication <!-- 1165118 -->
Intune now supports Windows Autopilot enrollment without user authentication. This is a new option in the Windows Autopilot deployment profile "Autopilot Deployment mode" set to "Self-Deploying".  The device must be running Windows 10 Insider Preview Build 17672 or later and possess a TPM 2.0 chip to successfully complete this type of enrollment. Since no user authentication is required, you should only assign this option to devices that you have physical control over.

#### New language/region setting when configuring OOBE for Autopilot <!-- 1821766 -->
A new configuration setting is available to set the language and region for Autopilot profiles during the Out of Box Experience. To see the new setting, choose **Device enrollment** > **Windows enrollment** > **Deployment profiles** > **Create profile** > **Deployment mode** = **Self-deploying** > **Defaults configured**.

#### New setting for configuring device keyboard <!-- 1821768 -->
A new setting will be available to configure the keyboard for Autopilot profiles during the Out of Box Experience. To see the new setting, choose **Device enrollment** > **Windows enrollment** > **Deployment profiles** > **Create profile** > **Deployment mode** = **Self-deploying** > **Defaults configured**.

#### Autopilot profiles moving to group targeting <!-- 1877935 -->
AutoPilot deployment profiles can be assigned to Azure AD groups containing AutoPilot devices.

### Device management

#### Set compliance by device location <!-- 851881 ! -->
In some situations, you may want to restrict access to corporate resources to a specific location, defined by a network connection. You can now create a compliance policy (**Device compliance** > **Locations**) based on the IP address of the device. If the device moves outside the IP range, then the device cannot access corporate resources.

Applies to: Android devices 6.0 and higher, with the updated Company Portal app

#### Prevent consumer apps and experiences on Windows 10 Enterprise RS4 Autopilot devices<!-- 1621980 -->
You will be able to prevent the installation of consumer apps and experiences on your Windows 10 Enterprise RS4 AutoPilot devices. To see this feature, go to **Intune** > **Device configuration** > **Profiles** > **Create profile** > **Platform** = **Windows 10 or later** > **Profile type** = **Device restrictions** > **Configure** > **Windows Spotlight** > **Consumer features**. 

#### Uninstall the latest from Windows 10 software updates <!-- 1732948 -->
Should you discover a breaking issue on your Windows 10 machines, you can choose to uninstall (rollback) the latest feature update or the latest quality update. Uninstalling a feature or quality update is only available for the servicing channel the device is on. Uninstalling will trigger a policy to restore the previous update on your Windows 10 machines. For feature updates specifically, you can limit the time from 2-60 days that an uninstall of the latest version can be applied. To set software update uninstall options, select **Software updates** from the **Microsoft Intune** blade within the Azure portal. Then, select **Windows 10 Update Rings** from the **Software updates** blade. You can then choose the **Uninstall** option from the **Overview** section.

#### Search all devices for IMEI and serial number <!-- 1793685 -->
You can now search for IMEI and serial numbers on the All devices blade (email, UPN, device name, and management name are still available). In Intune, choose **Devices** > **All devices** > enter your search in the search box.

#### Management name field will be editable <!-- 1875989 -->
You can now edit the management name field on a device’s **Properties** blade. To edit this field, choose **Devices** > **All devices** > choose the device > **Properties**. You can use the management name field to uniquely identify a device.

#### New All devices filter: Device category <!-- 1878520 -->
You can now filter the **All devices** list by device category. To do so, choose **Devices** > **All devices** > **Filter** > **Device category**.

#### Use TeamViewer to screen share iOS and MacOS devices <!-- 1985547 -->
Administrators can now connect to [TeamViewer](teamviewer-support.md), and start a screen sharing session with iOS and macOS devices. iPhone, iPad, and macOS users can share their screens live with any other desktop or mobile device. 

#### Multiple Exchange Connector support <!-- 2070451 -->
You're no longer limited to one Microsoft Intune Exchange Connector per tenant. Intune now supports multiple Exchange Connectors so that you can set up Intune Conditional Access with multiple on-premises Exchange organizations.

With an Intune on-premises Exchange connector, you can manage device access to your on-premises Exchange mailboxes based on whether a device is enrolled in Intune and complies with Intune device compliance policies. To set up a connector, you download the Intune on-premises Exchange connector from the Azure portal and install it on a server in your Exchange organization. On the Microsoft Intune dashboard, choose **On-premises access**, and then under **Setup**, choose **Exchange ActiveSync connector**. Download the Exchange on-premises connector and install it on a server in your Exchange organization. Now that you're no longer limited to one Exchange connector per tenant, if you have additional Exchange organizations, you can follow this same process to download and install a connector for each additional Exchange organization.

#### New device hardware detail: CCID <!-- 2156657 -->
The Chip Card Interface Device (CCID) information is now included for each device. To see it, choose **Devices** > **All devices** > choose a device > **Hardware**> check under **Network details**>

#### Assign all users and all devices as scope groups <!-- 2196803 -->
You can now assign all users, all devices, and all users and all devices in scope groups. To do this, choose **Intune roles** > **All roles** > **Policy and profile manager** > **Assignments** > choose an assignment > **Scope (groups)**.

#### UDID information now included for iOS and macOS devices <!-- 2219806 -->
To see the Unique Device Identifier (UDID) for iOS and macOS devices, go to **Devices** > **All devices** > choose a device > **Hardware**. UDID is only available for corporate devices (as set under **Devices** > **All devices** > choose a device > **Properties** > **Device ownership**).

### Intune apps

#### Improved troubleshooting for app installation <!-- 928990 -->
On Microsoft Intune MDM-managed devices, sometimes app installations can fail. When these app installs fail, it can be challenging to understand the failure reason or troubleshoot the issue. We're shipping a Public Preview of our App Troubleshooting features. You will notice a new node under each individual device called **Managed Apps**. This lists the apps that have been delivered via Intune MDM. Inside the node, you'll see a list of app install states. If you select an individual app, you'll see the troubleshooting view for that specific app. In the troubleshooting view, you'll see the end-to-end lifecycle of the app, such as when the app was created, modified, targeted, and delivered to a device. Additionally, if the app install was not successful, you'll be presented with the error code and a helpful message about the cause of the error. 

#### Intune app protection policies and Microsoft Edge <!-- 1818968 -->
The Microsoft Edge browser for mobile devices (iOS and Android) now supports Microsoft Intune app protection policies. Users of iOS and Android devices who sign in with their corporate Azure AD accounts in the Microsoft Edge application will be protected by Intune. On iOS devices, the **Require managed browser for web content** policy will allow users to open links in Microsoft Edge when it is managed.

<!-- ########################## -->
## May 2018

### App management

#### Configuring your app protection policies <!-- 2144597 Part 2 -->

In the Azure portal, instead of going to the Intune App Protection service blade, you now just go to Intune. There is now only one location for app protection policies within Intune. Note that all of your app protection policies are on the **Mobile app** blade in Intune under **App protection policies**. This integration helps to simplify your cloud management administration. Remember, all app protection policies are already in Intune and you can modify any of your previously configured policies. Intune App Policy Protection (APP) and Conditional Access (CA) policies are now under **Conditional Access**, which can be found under the **Manage** section in the **Microsoft Intune** blade or under the **Security** section in the **Azure Active Directory** blade. For more information about modifying Conditional Access policies, see [Conditional Access in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). For additional information, see [What are app protection policies?](app-protection-policy.md)

### Device configuration

#### Require installation of policies, apps, certificate and network profiles <!-- 1553555 -->
Admins can block end users from accessing the Windows 10 RS4 desktop until Intune installs policies, apps, and certificate and network profiles during the provisioning of AutoPilot devices. For more info, see [Set up an enrollment status page](windows-enrollment-status.md).

### Device enrollment

#### Samsung Knox mobile enrollment support <!--1112863-->
When using Intune with Samsung Knox Mobile Enrollment (KME), you can enroll large numbers of company-owned Android devices. Users on WiFi or cellular networks can enroll with just a few taps when they turn on their devices for the first time. When using the Knox Deployment App, devices can be enrolled using Bluetooth or NFC. For more information, see [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md).

### Monitor and troubleshoot 

#### Requesting help in the Company Portal for Windows 10 <!-- 1874137 -->
The Company Portal for Windows 10 will now send app logs directly to Microsoft when the user initiates the workflow to get help with an issue. This will make it easier to troubleshoot and resolve issues that are raised to Microsoft.

<!-- ########################## -->
## April 2018

### App management

#### Passcode support for MAM PIN on Android<!-- 1438086 -->

Intune admins can set an application launch requirement to enforce a passcode instead of a numeric MAM PIN. If configured, the user is required to set and use a passcode when prompted before getting access to MAM-enlightened applications. A passcode is defined as a numeric PIN with at least one special character or upper/lowercase alphabet. Intune supports passcode in a similar way to the existing numeric PIN... being able to set a minimum length, allowing repeat characters and sequences through the admin console. This feature requires the latest version of Company Portal on Android. This feature is already available for iOS.

#### Line-of-business (LOB) app support for macOS <!-- 1473977 -->
Microsoft Intune will provide the capability to install macOS LOB apps from the Azure portal. You will be able to add a macOS LOB app to Intune after it has been pre-processed by the tool available in GitHub. In the Azure portal, choose **Client apps** from the **Intune** blade. On the **Client apps** blade, choose **Apps** > **Add**. On the **Add App** blade, select **Line-of-business app**. 

#### Built-in All Users and All Devices Group for Android Enterprise work profile app assignment <!-- 1813073 -->
You can leverage the built-in **All Users** and **All Devices** groups for Android Enterprise work profile app assignment. For more information, see [Include and exclude app assignments in Microsoft Intune](apps-inc-exl-assignments.md).

#### Intune will reinstall required apps that are uninstalled by users <!-- 1947010 -->
If an end user uninstalls a required app, Intune automatically reinstalls the app within 24 hours rather than waiting for the 7-day re-evaluation cycle.

#### Update where to configure your app protection policies <!-- 2144597 -->

In the Azure portal within the Microsoft Intune service, we’re going to temporarily redirect you from the **Intune App Protection** service blade to the **Mobile app** blade. Note that all of your app protection policies are already on the **Mobile app** blade in Intune under app configuration. Instead of going to Intune App Protection, you’ll just go to Intune. In April 2018, we will stop the redirection and fully remove the **Intune App Protection** service blade, so that there's only one location for app protection policies within Intune. 

**How does this affect me?**
This change will affect both Intune standalone customers and hybrid (Intune with Configuration Manager) customers. This integration will help simplify your cloud management administration.

**What do I need to do to prepare for this change?**
Please tag **Intune** as a favorite instead of the **Intune App Protection** service blade and ensure you’re familiar with the App protection policy workflow in the **Mobile** app blade within Intune. We’ll redirect for a short period of time and then remove the **App Protection** blade. Remember, all app protection policies are already in Intune and you can modify any of your Conditional Access policies. For more information about modifying Conditional Access policies, see [Conditional Access in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). For additional information, see [What are app protection policies?](app-protection-policy.md) 

### Device configuration

#### Device profile chart and status list show all devices in a group <!-- 1449153 -->
When you configure a device profile (**Device configuration** > **Profiles**), you choose the device profile, such as iOS. You assign this profile to a group that includes iOS devices and non-iOS devices. The graphical chart count shows that the profile is applied to the iOS *and* the non-iOS devices (**Device configuration** > **Profiles** > select an existing profile > **Overview**). When you select the graphical chart in the **Overview** tab, the **Device status** lists all the devices in the group, instead of only the iOS devices. 

With this update, the graphical chart (**Device configuration** > **Profiles** > select an existing profile > **Overview**) only shows the count for the specific device profile. For example, if the configuration device profile applies to iOS devices, the chart only lists the count of the iOS devices. Selecting the graphical chart, and opening the **Device status** only lists the iOS devices.

While this update is being made, the graphical user chart is temporarily removed. 

#### Always On VPN for Windows 10 <!--1333666 -->

Currently, [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) can be used on Windows 10 devices by using a custom virtual private network (VPN) profile created using OMA-URI.

With this update, admins can enable Always On for Windows 10 VPN profiles directly in Intune in the Azure portal. Always On VPN profiles will automatically connect when:

- Users sign into their devices
- The network on the device changes
- The screen on the device turns back on after being turned off

#### New printer settings for education profiles <!-- 1308900 -->

For education profiles, new settings are available under the **Printers** category: **Printers**, **Default printer**, **Add new printers**.

#### Show caller ID in personal profile - Android Enterprise work profile <!--1098984 -->
When using a personal profile on a device, end users may not see the caller ID details from a work contact. 

With this update, there is a new setting in **Android Enterprise** > **Device restrictions** > **Work profile settings**:
- Display work contact caller-id in personal profile

When enabled (not configured), the work contact caller details are displayed in the personal profile. When blocked, the work contact caller number is not displayed in the personal profile. 

Applies to: Android work profile devices on Android OS v6.0 and newer

#### New Windows Defender Credential Guard settings added to endpoint protection settings <!--1102252 --><!--from 1802 and 1804-->

With this update, [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Device configuration** > **Profiles** > **Endpoint protection**) includes the following settings: 

- **Windows Defender Credential Guard**: Turns on Credential Guard with virtualization-based security. Enabling this feature helps protect credentials at the next reboot when **Platform Security Level with Secure Boot** and **Virtualization Based Security** are both enabled. Options include:
  - **Disabled**: If Credential Guard was previously turned on with the **Enabled without lock**" option, then it turns off Credential Guard remotely.

  - **Enabled with UEFI lock**: Ensures that Credential Guard cannot be disabled using a registry key or using Group Policy. To disable Credential Guard after using this setting, you must set the Group Policy to "Disabled". Then, remove the security functionality from each computer, with a physically present user. These steps clear the configuration persisted in UEFI. As long as the UEFI configuration persists, Credential Guard is enabled.

  - **Enabled without lock**: Allows Credential Guard to be disabled remotely using Group Policy. The devices that use this setting must be running at least Windows 10 (Version 1511).

The following dependent technologies are automatically enabled when configuring Credential Guard: 

- **Enable Virtualization-based Security (VBS)**: Turns on virtualization-based security (VBS) at next reboot. Virtualization-based security uses the Windows Hypervisor to provide support for security services, and requires Secure Boot.
- **Secure Boot with Direct Memory Access (DMA)**: Turns on VBS with Secure Boot and direct memory access. DMA protection require hardware support, and is only enabled on properly configured devices. 

#### Use a custom subject name on SCEP certificate <!-- 2064190 -->
You can use the **OnPremisesSamAccountName** the common name in a custom subject on an SCEP certificate profile. For example, you can use `CN={OnPremisesSamAccountName})`.

#### Block camera and screen captures on Android Enterprise work profiles <!-- 1098977 -->
Two new properties are available to block when you configure device restrictions for Android devices: 
- Camera: Blocks access to all cameras on the device
- Screen capture: Blocks the screen capture, and also prevents the content from being shown on display devices that don't have a secure video output

Applies to Android Enterprise work profiles.

#### Use Cisco AnyConnect client for iOS <!-- 1333708 -->

When you create a new VPN profile for iOS, there are now two options: **Cisco AnyConnect** and **Cisco Legacy AnyConnect**. Cisco AnyConnect profiles support 4.0.7x and newer versions. Existing iOS Cisco AnyConnect VPN profiles are labeled **Cisco Legacy AnyConnect**, and continue to work with Cisco AnyConnect 4.0.5x and older versions, as they do today.

> [!NOTE]
> This change only applies to iOS. There continues to be only one Cisco AnyConnect option for Android, Android Enterprise work profiles, and macOS platforms.

### Device enrollment

#### New enrollment steps for users on devices with macOS High Sierra 10.13.2+ <!--1734567 -->
macOS high Sierra 10.13.2 introduced the concept of "User Approved" MDM enrollment. Approved enrollments allow Intune to manage some security-sensitive settings. For more information, see Apple's support documentation here: https://support.apple.com/HT208019.

Devices enrolled using the macOS Company Portal are considered "Not User Approved" unless the end user opens System Preferences and manually provides approval. To this end, the macOS Company Portal now directs users on macOS 10.13.2 and above to go and manually approve their enrollment at the end of the enrollment process. The Intune admin console will report on if an enrolled device is user approved.

#### Jamf-enrolled macOS devices can now register with Intune <!-- 2370684 -->
Versions 1.3 and 1.4 of the macOS company portal did not successfully register Jamf devices with Intune. Version 1.4.2 of the macOS portal fixes this issue.

#### Updated help experience in Company Portal app for Android <!-- 1631531 -->
We've updated the help experience in the Company Portal app for Android to align with best practices for the Android platform. Now when users encounter a problem in the app, they can tap **Menu** > **Help** and:
- Upload diagnostic logs to Microsoft.
- Send an email that describes the problem and incident ID to a company support person.  

To check out the updated help experience go to [Send logs using email](/intune-user-help/send-logs-to-your-it-admin-by-email-android) and [Send errors to Microsoft](/intune-user-help/send-logs-to-microsoft-android).

#### New enrollment failure trend chart and failure reasons table <!-- 1471783 -->
On the Enrollment Overview page, you can view the trend of enrollment failures and the top five causes of failures. By clicking on the chart or table, you can drill into details to find troubleshooting advice and remediation suggestions.

### Device management

#### Advanced Threat Protection (ATP) and Intune are fully integrated <!-- 1629303 -->

[Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) shows the risk level of Windows 10 devices. In Windows Defender Security Center (ATP portal), you can create a connection to Microsoft Intune. Once created, an Intune compliance policy is used to determine an acceptable threat level. If the threat level is exceeded, an Azure Active Directory (AD) Conditional Access policy can then block access to different apps within your organization.

This feature allows ATP to scan files, detect threats, and report any risk on your Windows 10 devices.

See [Enable ATP with Conditional Access in Intune](advanced-threat-protection.md).

#### Support for user-less devices <!-- 1637553 -->
Intune supports the ability to evaluate compliance on a user-less device, such as the Microsoft Surface Hub. Compliance policy can target specific devices. So compliance (and noncompliance) can be determined for devices that don't have an associated user.

#### Delete Autopilot devices <!-- 1713650 -->
Intune admins can [delete Autopilot devices](enrollment-autopilot.md#delete-autopilot-devices).

#### Improved device deletion experience <!--1832333 -->
You're no longer be required to remove company data or factory reset a device before [deleting a device from Intune](devices-wipe.md#delete-devices-from-the-intune-portal).

To see the new experience, sign in to Intune and select **Devices** > **All devices** > the name of the device > **Delete**.

If you still want the wipe/retire confirmation, you can use the standard device lifecycle route by issuing a **Remove company data** and **Factory Reset** prior to **Delete**. 

#### Play sounds on iOS when in Lost mode <!-- 1947769 -->
When supervised iOS devices are in Mobile Device Management (MDM) [Lost mode](device-lost-mode.md), you can [play a sound](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Devices** > **All devices** > select an iOS device > **Overview** > **More**). The sound continues to play until the device is removed from Lost mode, or a user disables sound on the device. Applies to iOS devices 9.3 and newer.

#### Block or allow web results in searches made on an Intune device <!--1972804-->

Admins can now block web results from searches made on a device.

#### Improved error messaging for Apple MDM Push Certificate upload failure <!-- 2172331 -->

The error message explains that the same Apple ID must be used when renewing an existing MDM certificate.

#### Test the Company Portal for macOS on virtual machines <!-- 2216679 -->

We've published guidance to help IT admins test the Company Portal app for macOS on virtual machines in Parallels Desktop and VMware Fusion. Find out more in [enroll virtual macOS machines for testing](macos-enroll.md#enroll-virtual-macos-machines-for-testing).

### Intune apps

#### User experience update for the Company Portal app for iOS <!--1412866 -->
We've released a major user experience update to the Company Portal app for iOS. The update features a complete visual redesign that includes a modernized look and feel. We've maintained the functionality of the app, but increased its usability and accessibility.  

You'll also see:
- Support for iPhone X.
- Faster app launch and loading responses, to save users time.
- Additional progress bars to provide users with the most up-to-date status information.
- Improvements to the way users upload logs, so if something goes wrong, it's easier to report.  

To see the updated look, go to [What's new in the app UI](whats-new-app-ui.md).

#### Protect on-premises Exchange data using Intune APP and CA <!-- 1056954 -->
You can now use Intune App Policy Protection (APP) and Conditional Access (CA) to protect access to on-premises Exchange data with Outlook Mobile. To add or modify an app protection policy within the Azure portal, select **Microsoft Intune** > **Client apps** > **App protection policies**. Before using this feature, make sure you meet the [Outlook for iOS and Android requirements](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx).

### User interface

#### Improved device tiles in the Windows 10 Company Portal <!--2213364 -->

The tiles have been updated to be more accessible to low-vision users and to perform better for screen reading tools.

#### Send diagnostic reports in Company Portal app for macOS <!-- 2216677 -->
The Company Portal app for macOS devices was updated to improve how users report Intune-related errors. From the Company Portal app, your employees can:

- Upload diagnostic reports directly to the Microsoft developer team.
- Email an incident ID to your company's IT support team.

For more information see [Send errors for macOS](/intune-user-help/send-errors-macos).

#### Intune adapts to Fluent Design System in the Company Portal app for Windows 10 <!-- 1195010 -->
The Intune Company Portal app for Windows 10 has been updated with the [Fluent Design System's navigation view](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics). Along the side of the app, you'll notice a static, vertical list of all top-level pages. Click any link to quickly view and switch between pages. This is the first of several updates you'll see as part of our ongoing effort to create a more adaptive, empathetic, and familiar experience in Intune. To see the updated look, go to [What's new in the app UI](whats-new-app-ui.md).

<!-- ########################## -->
## March 2018

### App management

#### Alerts for expiring iOS line-of-business (LOB) apps for Microsoft Intune <!-- 748789 -->

In the Azure portal, Intune will alert you to iOS line-of-business apps that are about to expire. Upon uploading a new version of the iOS line-of-business app, Intune removes the expiration notification from the app list. This expiration notification will only be active for newly uploaded iOS line-of-business apps. A warning appears 30 days before the iOS LOB app provisioning profile expires. When it expires, the alert changes to Expired.

#### Customize your Company Portal themes with hex codes <!--1049561 -->

You can customize theme color in the Company Portal apps using hex codes. When you enter your hex code, Intune determines the text color that provides the highest level of contrast between the text color and the background color. You can preview both the text color and your company logo against the color in **Client apps** > **Company Portal**.

### Including and excluding app assignment based on groups for Android Enterprise <!-- 1813081 -->

Android Enterprise (formerly known as Android for Work) supports including and excluding groups, but does not support the pre-created **All Users** and **All Devices** built-in groups. For more information, see [Include and exclude app assignments in Microsoft Intune](apps-inc-exl-assignments.md).

### Device management

### Export all devices into CSV files in IE, Microsoft Edge, or Chrome <!-- 2258071 -->
In **Devices** > **All devices**, you can **Export** the devices into a CSV formatted list. Internet Explorer (IE) users with >10,000 devices can successfully export their devices into multiple files. Each file has up to 10,000 devices.

Microsoft Edge and Chrome users with >30,000 devices can successfully export their devices into multiple files. Each file has up to 30,000 devices.

[Manage devices](device-management.md) provides more details on what you can do with devices you manage.

#### New security enhancements in the Intune service  <!-- 1637539 -->   

We’ve introduced a toggle in Intune on Azure that Intune standalone customers can use to treat devices without any policy assigned as **Compliant** (security feature off) or treat these devices as **Not compliant** (security feature on). This will ensure access to resources only after device compliance has been evaluated.

This feature affects you differently depending on whether you already have compliance policies assigned or not.

- If you are a new or existing account, and don't have any compliance policies assigned to your devices, then the toggle is automatically set to **Compliant**. The feature is off as a default setting in the console. There is no end-user impact.
- If you are an existing account, and you have any devices with a compliance policy assigned to them, then the toggle is automatically set to **Not compliant**. The feature is on as a default setting, as the March update rolls out.

If you use compliance policies with Conditional Access (CA), and have the feature turned on, any devices without at least one compliance policy assigned are now be blocked by CA. End-users associated with these devices, who were previously allowed access to email, lose their access unless you assign at least one compliance policy to all devices.   

Note that although the default toggle status is displayed in the UI immediately with the Intune service March updates, this toggle status is not enforced right away. Any changes you make to the toggle will not impact device compliance until we flight your account to have a working toggle. We’ll inform you via the Message center when we finish flighting your account. This could take up to a few days after your Intune service is updated for March.

**Additional Information**: [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### Enhanced jailbreak detection <!-- 846515 -->

Enhanced jailbreak detection is a new compliance setting that improves how Intune evaluates jailbroken devices. The setting causes the device to check in with Intune more frequently, which uses the device’s location services and impacts battery usage.

#### Reset passwords for Android O devices <!-- 1238299 -->
You'll be able to reset the passwords for enrolled Android 8.0 devices with Work profiles. When you send a "Reset password" request to an Android 8.0 device, it sets a new device unlock password or a managed profile challenge to the current user. The password or challenge is sent and immediately takes effect.

#### Targeting compliance policies to devices in device groups <!--1307012 -->

You can target compliance policies to users in user groups. With this update, you can target compliance policies to devices in device groups. Devices targeted as part of device groups will not receive any compliance actions.

#### New Management name column <!-- 1333586 -->
 A new column named **Management name** is available on the devices blade. This is an auto-generated, non-editable name assigned per device, based on the following formula:
- Default name for all devices: <username><em><devicetype></em><enrollmenttimestamp>
- For bulk added devices: <PackageId/ProfileId><em><DeviceType></em><EnrollmentTime>

This is an optional column in the devices blade. It isn't available by default and you can only access it by using the column selector. The device name is not affected by this new column.

#### iOS devices are prompted for a PIN every 15 minutes <!--1550837 -->
After a compliance or configuration policy is applied to an iOS device, users are prompted to set a PIN every 15 minutes. Users are continually prompted until a PIN is set.

#### Schedule your automatic updates <!--1805514 -->
Intune gives you control on installing automatic updates using [Windows Update Ring settings](windows-update-for-business-configure.md). With this update, you can schedule reoccurring updates, including the week, the day, and the time.

#### Use fully distinguished name as subject for SCEP certificate <!--2221763 -->
When you create a SCEP certificate profile, you enter the Subject Name. With this update, you can use the fully distinguished name as the subject. For **Subject Name**,  select **Custom**, and then enter `CN={{OnPrem_Distinguished_Name}}`. To use the `{{OnPrem_Distinguished_Name}}` variable, be sure to sync the `onpremisesdistingishedname` user attribute using [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) to your Azure AD.

### Device configuration

#### Enable Bluetooth contact sharing - Android for Work <!--1098983 -->
By default, Android prevents contacts in the work profile from syncing with Bluetooth devices. As a result, work profile contacts are not displayed on caller ID for Bluetooth devices.

With this update, there is a new setting in **Android for Work** > **Device restrictions** > **Work profile settings**:
- Contact sharing via Bluetooth

The Intune administrator can configure these settings to enable sharing. This is useful when pairing a device with a car-based Bluetooth device that displays caller ID for hands-free usage. When enabled, work profile contacts are displayed. When not enabled, work profile contacts won't display.

#### Configure Gatekeeper to control macOS app download source <!-- 1690459 -->

You can configure Gatekeeper to protect your devices from apps by controlling where the apps can be downloaded from. You can configure the following download sources: **Mac App Store**, **Mac App Store and identified developers**, or **Anywhere**. You can configure whether users can install an app using control-click to override these Gatekeeper controls.

These settings can be found under **Device configuration** -> **Create profile** -> **macOS** -> **Endpoint protection**.

#### Configure the Mac application firewall <!-- 1690461 -->

You can configure the Mac application firewall. You can use this to control connections on a per-application basis, rather than on a per-port basis. This makes it easier to get the benefits of firewall protection, and helps prevent undesirable apps from taking control of network ports open for legitimate apps.

This feature can be found under **Device configuration** -> **Create profile** -> **macOS** -> **Endpoint protection**.

Once you enable the Firewall setting, you can configure the firewall using two strategies:

- Block all incoming connections

   You can block all incoming connections for the targeted devices. If you choose to do this, incoming connections are blocked for all apps.

- Allow or block specific apps

   You can allow or block specific apps from receiving incoming connections. You can also enable stealth mode to prevent responses to probing requests.

#### Detailed error codes and messages <!-- 1376342 -->

In your Device Configuration, there are more detailed error codes and error messages available to see. This improved reporting shows the settings, the state of these settings, and details on troubleshooting.

##### More information

- Block all incoming connections

   This blocks all sharing services (such as File Sharing and Screen Sharing) from receiving incoming connections. The system services that are still allowed to receive incoming connections are:
  - configd - implements DHCP and other network configuration services
  - mDNSResponder - implements Bonjour
  - racoon - implements IPSec

    To use sharing services, ensure **Incoming connections** is set to **Not configured** (not **Block**).

- Stealth mode

   Enable this to prevent the computer from responding to probing requests. The computer still answers incoming requests for authorized apps. Unexpected requests, such as ICMP (ping), are ignored.

#### Disable checks on device restart <!--1805490 -->
Intune gives you control to [manage software updates](windows-update-for-business-configure.md). With this update, the <strong>Restart checks</strong> property is available, and enabled by default. To skip the typical checks that occur when you restart a device (such as active users, battery levels, and so on), select <strong>Skip</strong>.

#### New Windows 10 Insider Preview channels available for deployment rings <!-- 1746293 -->
You now have the option to select the following Windows 10 Insider Preview servicing channels when you create a Windows 10 deployment ring:
- Windows Insider build &#8208; Fast
- Windows Insider build &#8208; Slow
- Release Windows Insider build 

For more information about these channels, see [Manage Insider Preview Builds](https://insider.windows.com/for-business-organization-admin/).   
For more information about creating deployment channels in Intune, see [Manage software updates in Intune](windows-update-for-business-configure.md).

### New Windows Defender Exploit Guard settings <!-- 1631893 -->

Six new <strong>Attack Surface Reduction</strong> settings and expanded <strong>Controlled folder access: Folder protection</strong> capabilities are now available. These settings can be found at: Device configuration\Profiles\
Create profile\Endpoint protection\Windows Defender Exploit Guard.

#### Attack Surface Reduction

|Setting name  |Setting options  |Description  |
|---------|---------|---------|
|Advanced ransomware protection|Enabled, Audit, Not configured|Use aggressive ransomware protection.|
|Flag credential stealing from the Windows local security authority subsystem|Enabled, Audit, Not configured|Flag credential stealing from the Windows local security authority subsystem (lsass.exe).|
|Process creation from PSExec and WMI commands|Block, Audit, Not configured|Block process creations originating from PSExec and WMI commands.|
|Untrusted and unsigned processes that run from USB|Block, Audit, Not configured|Block untrusted and unsigned processes that run from USB.|
|Executables that don’t meet a prevalence, age, or trusted list criteria|Block, Audit, Not configured|Block executable files from running unless they meet a prevalence, age, or trusted list criteria.|

#### Controlled folder access

|              Setting name               |                                                              Setting options                                                              | Description |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Folder protection (already implemented) | Not configured, Enable, Audit only (already implemented)<br><br> <strong>New</strong><br>Block disk modification, Audit disk modification |             |

Protect files and folders from unauthorized changes by unfriendly apps.<br><br>**Enable**: Prevent untrusted apps from modifying or deleting files in protected folders and from writing to disk sectors.<br><br>
**Block disk modification only**:<br>Block untrusted apps from writing to disk sectors. Untrusted apps can still modify or delete files in protected folders.|

### Intune apps

### Azure Active Directory web sites can require the Intune Managed Browser app and support Single Sign-On for the Managed Browser (Public Preview) <!-- 710595 -->

Using Azure Active Directory (Azure AD), you can now restrict access to web sites on mobile devices to the Intune Managed Browser app. In the Managed Browser, web site data will remain secure and separate from end-user personal data. In addition, the Managed Browser will support Single Sign-On capabilities for sites protected by Azure AD. Signing in to the Managed Browser, or using the Managed Browser on a device with another app managed by Intune, allows the Managed Browser to access corporate sites protected by Azure AD without the user having to enter their credentials. This functionality applies to sites like Outlook Web Access (OWA) and SharePoint Online, as well as other corporate sites like intranet resources accessed through the Azure App Proxy. For additional information, see [Access controls in Azure Active Directory Conditional Access](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls).

#### Company Portal app for Android visual updates <!--976944 -->

We've updated the Company Portal app for Android to follow Android's [Material Design](https://material.io/) guidelines. You can see the images of the new icons in the [What's new in app UI](whats-new-app-ui.md) article.

#### Company Portal enrollment improved <!-- 1874230 eeready-->
Users enrolling a device by using the Company Portal on Windows 10 build 1703 and up are now able to complete the first step of enrollment without leaving the app.
#### HoloLens and Surface Hub now appear in device lists <!--1725868 -->
We added support for showing Intune-enrolled HoloLens and Surface Hub devices to the Company Portal app for Android.

#### Custom Book categories for volume-purchase program (VPP) eBooks <!-- 1488911 -->
You can create custom eBook categories and then assign VPP eBooks to those custom eBook categories. End users can then see the newly created eBook categories and books assigned to the categories. For more information, see [Manage volume-purchased apps and books with Microsoft Intune](vpp-apps.md).  

#### Support changes for Company Portal app for Windows send feedback option <!-- 2070166 -->
Starting April 30, 2018, the **Send Feedback** option in the Company Portal app for Windows will only work on devices running the Windows 10 Anniversary Update (1607) and later. The option to send feedback is no longer supported when using the Company Portal app for Windows with:  
- Windows 10, 1507 release  
- Windows 10, 1511 release  
- Windows Phone 8.1 

If your device is running on Windows 10 RS1 or later, download the latest version of the Windows Company Portal app from the Store. If you are running an unsupported version, please continue to send feedback through the following channels: 
- The Feedback Hub app on Windows 10
- Email WinCPfeedback@microsoft.com  

#### New Windows Defender Application Guard settings <!-- 1631890 -->

- **Enable graphics acceleration**: Administrators can enable a virtual graphics processor for Windows Defender Application Guard. This setting allows the CPU to offload graphics rendering to the vGPU. This can improve performance when working with graphics intense websites or watching video within the container.

- **SaveFilestoHost**: Administrators can enable files to pass from Microsoft Edge running in the container to the host file system. Turning this on allows users to download files from Microsoft Edge in the container to the host file system.

#### MAM protection policies targeted based on management state <!-- 1665993 -->
You can target MAM policies based on the management state of the device:
- **Android devices** - You can target unmanaged devices, Intune managed devices, and Intune managed Android Enterprise Profiles (formerly Android for Work).
- **iOS devices** - You can target unmanaged devices (MAM only) or Intune managed devices.

    > [!NOTE]
    > - iOS support for this functionality is rolling out throughout April 2018.

For more information, see [Target app protection policies based on device management state](app-protection-policies.md).

#### Improvements to the language in the Company Portal app for Windows <!-- 1683758 -->
We've improved the language in the Company Portal for Windows 10 to be more user-friendly and specific to your company. To see some sample images of what we've done, see [what's new in app UI](whats-new-app-ui.md).

#### New additions to our docs about user privacy <!-- 1440709 -->
As part of our effort to give end users more control over their data and privacy, we've published updates to our docs that explain how to view and remove data stored locally by the Company Portal apps. You can find these updates at:

- **Android**: [How to remove your Android device from Intune](/intune-user-help/unenroll-your-device-from-intune-android)
- **Android, if the user has declined terms of use**: [Remove your device management if you declined "Terms of Use"](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android)
- **iOS**: [Remove your iOS device from Intune](/intune-user-help/unenroll-your-device-from-intune-ios)
- **Windows**: [Remove your Windows device from Intune](/intune-user-help/unenroll-your-device-from-intune-windows)

<!-- ########################## -->
## February 2018

### Device enrollment

#### Intune support for multiple Apple DEP / Apple School Manager accounts <!-- 747685 -->

Intune now supports enrolling devices from up to 100 different [Apple Device Enrollment Program (DEP)](device-enrollment-program-enroll-ios.md) or [Apple School Manager](apple-school-manager-set-up-ios.md) accounts. Each token uploaded can be managed separately for enrollment profiles and devices. A different enrollment profile can be automatically assigned per DEP/School Manager token uploaded. If multiple School Manager tokens are uploaded, only one can be shared with Microsoft School Data Sync at a time.

After migration, the beta Graph APIs and published scripts for managing Apple DEP or ASM over Graph will no longer work. New beta Graph APIs are in development and will be released after the migration.

#### See enrollment restrictions per user <!-- 1634444 eeready wnready -->
On the **Troubleshoot** blade, you can now see the [enrollment restrictions](enrollment-restrictions-set.md) that are in effect for each user by selecting **Enrollment restrictions** from the **Assignments** list.

#### New option for user authentication for Apple bulk enrollment <!-- 747625 eeready -->

> [!NOTE]
> New tenants see this right away. For existing tenants, this feature is being rolled out through April. Until this roll out is complete, you might not have access to these new features.

Intune now gives you the option to authenticate devices by using the Company Portal app for the following enrollment methods:

- Apple Device Enrollment Program
- Apple School Manager
- Apple Configurator Enrollment

When using the Company Portal option, Azure Active Directory multi-factor authentication can be enforced without blocking these enrollment methods.

When using the Company Portal option, Intune skips user authentication in the iOS Setup Assistant for user affinity enrollment. This means that the device is initially enrolled as a userless device, and so doesn't receive configurations or policies of user groups. It only receives configurations and policies for device groups. However, Intune will automatically install the Company Portal app on the Device. The first user to launch and sign in to the Company Portal app will be associated with the device in Intune. At this point, the user will receive configurations and policies of their user groups. The user association cannot be changed without re-enrollment.

#### Intune support for multiple Apple DEP / Apple School Manager accounts <!-- 747685 eeready -->

Intune now supports enrolling devices from up to 100 different Apple Device Enrollment Program (DEP) or Apple School Manager accounts. Each token uploaded can be managed separately for enrollment profiles and devices. A different enrollment profile can be automatically assigned per DEP/School Manager token uploaded. If multiple School Manager tokens are uploaded, only one can be shared with Microsoft School Data Sync at a time.

After migration, the beta Graph APIs and published scripts for managing Apple DEP or ASM over Graph will no longer work. New beta Graph APIs are in development and will be released after the migration.

### Remote printing over a secure network <!-- 1709994  -->
PrinterOn’s wireless mobile printing solutions will enable users to remotely print from anywhere at any time over a secure network. PrinterOn will integrate with the Intune APP SDK for both iOS and Android. You will be able to target app protection policies to this app through the Intune **App protection policies** blade in the admin console. End users will be able to download the app 'PrinterOn for Microsoft' through the Play Store or iTunes to use within their Intune ecosystem.

### macOS Company Portal support for enrollments that use the Device Enrollment Manager <!-- 1352411 -->

Users can now use the Device Enrollment Manager when enrolling with the macOS Company Portal.

### Device management

#### Windows defender health status and threat status reports <!--854704 -->

Understanding Windows Defender's health and status is key to managing Windows PCs.  With this update, Intune adds new reports and actions to the status and health of the Windows Defender agent. Using a status roll-up report in the [Device Compliance workload](compliance-policy-monitor.md), you can see devices that need any of the following:
- signature update
- Restart
- manual intervention
- full scan
- other agent states requiring intervention

A drill-in report for each status category lists the individual PCs that need attention, or those that report as **Clean**.

#### New privacy settings for device restrictions <!--1308926 -->
[Two new privacy settings](device-restrictions-windows-10.md#privacy) are now available for devices:
- **Publish user activities**: Set this to **Block** to prevent shared experiences and discovery of recently used resources in the task switcher.
- **Local activities only**: Set this to **Block** to prevent shared experiences and discovery of recently used resources in task switcher based only on local activity.

#### New settings for the Microsoft Edge browser <!--1469166 -->
[Two new settings](device-restrictions-windows-10.md#microsoft-edge-browser) are now available for devices with the Microsoft Edge browser: **Path to favorites file** and **Changes to Favorites**.

### App management

#### Protocol exceptions for applications <!--1035509 -->

You can now create exceptions to the Intune Mobile Application Management (MAM) data transfer policy to open specific unmanaged applications. Such applications must be trusted by IT. Other than the exceptions you create, data transfer is still restricted to applications that are managed by Intune when your data transfer policy is set to **managed apps only**. You can create the restrictions by using protocols (iOS) or packages (Android).

For example, you can add the Webex package as an exception to the MAM data transfer policy. This will allow Webex links in a managed Outlook email message to open directly in the Webex application. Data transfer will still be restricted in other unmanaged applications. For more information, see [Data transfer policy exceptions for apps](app-protection-policies-exception.md).

#### Windows Information Protection (WIP) encrypted data in Windows search results <!-- 1469193 -->
A setting in the Windows Information Protection (WIP) policy now allows you to control whether WIP-encrypted data is included in Windows search results. Set this app protection policy option by selecting **Allow Windows Search Indexer to search encrypted items** in the **Advanced settings** of the Windows Information Protection policy. The app protection policy must be set to the *Windows 10* platform and the app policy **Enrollment state** must be set to **With enrollment**. For more information, see [Allow Windows Search Indexer to search encrypted items](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### Configuring a self-updating mobile MSI app <!-- 1740840 -->
You can configure a known self-updating mobile MSI app to ignore the version check process. This capability is useful to avoid getting into a race condition. For instance, this type of race condition could occur when the app being auto-updated by the app developer is also being update by Intune. Both could try to enforce a version of the app on a Windows client, which could create a conflict. For these automatically updated MSI apps, you can configure the **Ignore app version** setting in the **App information** blade. When this setting is switched to **Yes**, Microsoft Intune will ignore the app version installed on the Windows client.

#### Related sets of app licenses supported in Intune <!-- 1864117 -->
Intune in the Azure portal now supports related sets of app licenses as a single app item in the UI. In addition, any Offline Licensed apps synced from Microsoft Store for Business will be consolidated into a single app entry and any deployment details from the individual packages will be migrated over to the single entry. To view related sets of app licenses in the Azure portal, select **App licenses** from the **Client apps** blade.

### Device configuration
#### Windows Information Protection (WIP) file extensions for automatic encryption <!-- 1463582 -->
A setting in the Windows Information Protection (WIP) policy now lets you specify which file extensions are automatically encrypted when copying from a Server Message Block (SMB) share within the corporate boundary, as defined in the WIP policy.

#### Configure resource account settings for Surface Hubs

You can now remotely configure resource account settings for Surface Hubs.

The resource account is used by a Surface Hub to authenticate against Skype/Exchange so it can join a meeting.
You will want to create a unique resource account so the Surface Hub can show up in the meeting as the conference room.
For example, a resource account such as **Conference Room B41/6233**.

> [!NOTE]
> - If you leave fields blank you will override previously configured attributes on the device.
>
> - Resource Account properties can change dynamically on the Surface Hub. For example, if password rotation is on. So, it's possible that the values
in the Azure console will take some time to reflect the reality on the device.
>
>   To understand what is currently configured on the Surface Hub, the Resource Account information can be included in hardware inventory
(which already has a 7 day interval) or as read-only properties. To enhance the accuracy after the remote action has taken place, you can get the state
of the parameters immediately after running the action to update the account/parameters on the Surface Hub.

##### Attack Surface Reduction

|Setting name  |Setting options  |Description  |
|---------|---------|---------|
|Execution of password-protected executable content from email|Block, Audit, Not configured|Prevent password-protected executable files downloaded over email from running.|
|Advanced ransomware protection|Enabled, Audit, Not configured|Use aggressive ransomware protection.|
|Flag credential stealing from the Windows local security authority subsystem|Enabled, Audit, Not configured|Flag credential stealing from the Windows local security authority subsystem (lsass.exe).|
|Process creation from PSExec and WMI commands|Block, Audit, Not configured|Block process creations originating from PSExec and WMI commands.|
|Untrusted and unsigned processes that run from USB|Block, Audit, Not configured|Block untrusted and unsigned processes that run from USB.|
|Executables that don’t meet a prevalence, age, or trusted list criteria|Block, Audit, Not configured|Block executable files from running unless they meet a prevalence, age, or trusted list criteria.|

##### Controlled folder access

|              Setting name               |                                                              Setting options                                                              | Description |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Folder protection (already implemented) | Not configured, Enable, Audit only (already implemented)<br><br> <strong>New</strong><br>Block disk modification, Audit disk modification |             |

Protect files and folders from unauthorized changes by unfriendly apps.<br><br>**Enable**: Prevent untrusted apps from modifying or deleting files in protected folders and from writing to disk sectors.<br><br>
**Block disk modification only**:<br>Block untrusted apps from writing to disk sectors. Untrusted apps can still modify or delete files in protected folders.|

#### Additions to System Security settings for Windows 10 and later compliance policies <!--1704133-->

Additions to the Windows 10 compliance settings are now available, including requiring Firewall and Windows Defender Antivirus.

### Intune apps

#### Support for offline apps from the Microsoft Store for Business <!--1222672-->
Offline apps that you purchased from the Microsoft Store for Business are now synchronized to the Azure portal. You can deploy these apps to device groups or user groups. Offline apps are installed by Intune, not by the store.

#### Prevent end users from manually adding or removing accounts in the work profile <!-- 1728700 -->

When you deploy the Gmail app into an Android for Work profile, you can now prevent end users from manually adding or removing accounts in the work profile by using the **Add and remove accounts** setting in the Android for Work Device restrictions profile.

<!-- ########################## -->
## January 2018

### Device enrollment

#### Alerts for expired tokens and tokens that will soon expire <!-- 1639263 -->
The overview page now shows alerts for expired tokens and tokens that will soon expire. When you click on an alert for a single token, you'll go to the token's details page.  If you click on alert with multiple tokens, you'll go to a list of all tokens with their status. Admins should renew their tokens before the expiration date.

### Device management

#### Remote "Erase" command support for macOS devices <!-- 1438084 -->

Admins can issue an Erase command remotely for macOS devices.

> [!IMPORTANT]
> The erase command can’t be reversed and should be used with caution.

The erase command removes all data, including the operating system, from a device. It also removes the device from Intune management. No warning is issued to the user and the erasure occurs immediately upon issuing the command.

You must configure a 6-digit recovery PIN. This PIN can be used to unlock the erased device, at which point reinstallation of the operating system will begin. After erasure has started, the PIN appears in a status bar on the device’s overview blade in Intune. The PIN will remain as long as the erasure is underway. After erasure is complete, the device disappears entirely from Intune management. Be sure to record the recovery PIN so that whoever is restoring the device can use it.

#### Revoke licenses for an iOS Volume Purchasing Program token <!-- 820870 -->
You can revoke the license of all iOS Volume Purchasing Program (VPP) apps for a given VPP Token.

### App management

#### Revoking iOS Volume-Purchase Program apps  <!-- 820863 -->
For a given device that has one or more iOS Volume-Purchase Program (VPP) apps, you can revoke the associated device-based app license for the device. Revoking an app license will not uninstall the related VPP app from the device. To uninstall a VPP app, you must change the assignment action to **Uninstall**. For more information, see [How to manage iOS apps purchased through a volume-purchase program with Microsoft Intune](vpp-apps-ios.md).

#### Assign Office 365 mobile apps to iOS and Android devices using built-in app type <!-- 1332318 -->
The **Built-in** app type makes it easier for you to create and assign Office 365 apps to the iOS and Android devices that you manage. These apps include 0365 apps such as Word, Excel, PowerPoint, and OneDrive. You can assign specific apps to the app type and edit the app information configuration.

#### Including and excluding app assignment based on groups <!-- 1406920 -->

During app assignment and after selecting an assignment type, you can select the groups to include, as well as the groups to exclude.

### Device configuration

#### You can assign an application configuration policy to groups by including and excluding assignments  <!-- 1480316 -->

You can assign an application configuration policy to a group of users and devices by using a combination of including and excluding assignments. Assignments can be chosen as either a custom selection of groups or as a virtual group. A virtual group can include **All users**, **All Device**, or **All Users + All Devices**.

#### Support for Windows 10 edition upgrade policy   <!-- 903672(archived), 1119689 -->  
You can create a Windows 10 edition upgrade policy that upgrades Windows 10 devices to Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education, and Windows 10 Professional Education N.
For details about Windows 10 edition upgrades, see [How to configure Windows 10 edition upgrades](edition-upgrade-configure-windows-10.md).

#### Conditional Access policies for Intune is only available from the Azure portal  <!-- 1737088 1634311 -->

Starting with this release, you must configure and manage your Conditional Access policies in the [Azure portal](https://portal.azure.com) from **Azure Active Directory** > **Conditional Access**. For your convenience, you can also access this blade from Intune in the Azure portal at **Intune** > **Conditional Access**.

#### Updates to compliance emails <!--1637547 -->

When an email is sent to report a noncompliant device, details about the noncompliant device are included.

### Intune apps

#### New functionality for the "Resolve" action for Android devices <!--1583480-->

The Company Portal app for Android is expanding the "Resolve" action for **Update device settings** to resolve [device encryption issues](/intune-user-help/encrypt-your-device-android).

#### Remote lock available in Company Portal app for Windows 10 <!--676506-->
End users can now remotely lock their devices from the Company Portal app for Windows 10. This will not be displayed for the local device they're actively using.

#### Easier resolution of compliance issues for the Company Portal app for Windows 10 <!--676546-->
End users with Windows devices will be able to tap the noncompliance reason in the Company Portal app. When possible, this will take them directly to the correct location in the settings app to fix the issue.

<!-- ########################## -->
## December 2017

### Device configuration

#### New automatic redeployment setting <!-- 1469168 -->
The **Automatic redeployment** setting allows users with administrative rights to delete all user data and settings using **CTRL + Win + R** at the device lock screen. The device is automatically reconfigured and reenrolled into management. This setting can be found under Windows 10 > Device restrictions > General > Automatic redeployment. For details, see [Intune device restriction settings for Windows 10](device-restrictions-windows-10.md#general).

#### Support for additional source editions in the Windows 10 edition upgrade policy  <!-- 903672,  1119689 -->
You can now use the Windows 10 edition upgrade policy to upgrade from additional Windows 10 editions (Windows 10 Pro, Windows 10 Pro for Education, Windows 10 Cloud, etc.). Prior to this release, the supported edition upgrade paths were more limited. For details, see [How to configure Windows 10 edition upgrades](edition-upgrade-configure-windows-10.md).

#### New Windows Defender Security Center (WDSC) device configuration profile settings <!-- 1335507 -->

Intune adds a new section of device configuration profile settings under the Endpoint protection named **Windows Defender Security Center**. IT admins can configure which pillars of the Windows Defender Security Center app end users can access. If an IT admin hides a pillar in the Windows Defender Security Center app, all notifications related to the hidden pillar do not display on the user's device.

These are the pillars admins can hide from the Windows Defender Security Center device configuration profile settings:
- Virus and threat protection
- Device performance and health
- Firewall and network protections
- App and browser control
- Family options

IT admins can also customize which notifications users receive. For example, you can configure whether the users receive all notifications generated by visible pillars in the WDSC, or only critical notifications. Non-critical notifications include periodic summaries of Windows Defender Antivirus activity and notifications when scans have completed. All other notifications are considered critical. Additionally, you can also customize the notification content itself, for example, you can provide the IT contact information to embed in the notifications that appear on the users' devices.

#### Multiple connector support for SCEP and PFX certificate handling <!-- 1361755 -->

Customers who use the on-premises NDES connector to deliver certificates to devices can now configure multiple connectors in a single tenant.

This new capability supports the following scenario:

- **High availability**

Each NDES connector pulls certificate requests from Intune.  If one NDES connector goes offline, the other connector can continue to process requests.

#### Customer subject name can use AAD_DEVICE_ID variable  <!-- 1468599 -->

When you create a SCEP certificate profile in Intune, you can now use the AAD_DEVICE_ID variable when you build the custom subject name.   When the certificate is requested using this SCEP profile, the variable is replaced with the AAD device ID of the device making the certificate request.

### Device management

#### Manage Jamf-enrolled macOS devices with Intune's device compliance engine <!-- 1592747 -->
You can now use Jamf to send macOS device state information to Intune, which will then evaluate it for compliance with policies defined in the Intune console. Based on the device compliance state as well as other conditions (such as location, user risk, etc.), Conditional Access will enforce compliance for macOS devices accessing cloud and on-premises applications connected with Azure AD, including Office 365. Find out more about [setting up Jamf integration](conditional-access-integrate-jamf.md) and [enforcing compliance for Jamf-managed devices](conditional-access-assign-jamf.md).

#### New iOS device action   <!-- 1424701 -->

You can now shut down iOS 10.3 supervised devices. This action shuts down the device immediately without warning to the end user. The **Shut down (supervised only)** action can be found at the device properties when you select a device in the **Device** workload.

#### Disallow date/time changes to Samsung Knox devices <!-- 1468103 -->

We've added a new feature that allows you to block date and time changes on Samsung Knox devices. You can find this in **Device configuration profiles** > **Device restrictions (Android)** > **General**.

#### Surface Hub resource account supported <!-- 1566442  -->

A new device action has been added so administrators can define and update the resource account associated with a Surface Hub.

The resource account is used by a Surface Hub to authenticate with Skype/Exchange so it can join a meeting. You can create a unique resource account so the Surface Hub appears in the meeting as the conference room. For example, the resource account might appear as *Conference Room B41/6233*. The resource account (known as the device account) for the Surface Hub typically needs to be configured for the conference room location and when other resource account parameters need to be changed.

When administrators want to update the resource account on a device, they must provide the current Active Directory/Azure Active Directory credentials associated with the device. If password rotation is on for the device, administrators must go to Azure Active Directory to find the password.

> [!NOTE]
> All fields get sent down in a bundle and overwrite all fields that were previously configured. Empty fields also overwrite existing fields.

The following are the settings administrators can configure:

- **Resource account**
  - **Active Directory user**

    Domainname\username or User Principle Name (UPN): user@domainname.com

  - **Password**

- **Optional resource account parameters** (must be set using the specified resource account)

  - **Password rotation period**

    Ensures the account password is updated automatically by the Surface Hub every week for security reasons. To configure any parameters after this has been enabled, the account in Azure Active Directory must have the password reset first.

  - **SIP (Session Initiation Protocol) address**

    Only used when autodiscovery fails.

  - **Email**

    Email address of the device/resource account.

  - **Exchange server**

    Only required when autodiscovery fails.

  - **Calendar sync**

    Specifies whether calendar sync and other Exchange server services are enabled. For example: meeting sync.

#### Install Office apps on macOS devices <!-- 1494311 -->
You will now be able to install Office apps on macOS devices. This new app type will allow you to install Word, Excel, PowerPoint, Outlook, and OneNote. These apps also come with the Microsoft AutoUpdate (MAU), to help keep your apps secure and up-to-date.

### App management

#### Delete an iOS  Volume Purchasing Program token <!-- 820879 -->
You can delete the iOS Volume Purchasing Program (VPP) token using the console. This may be necessary when you have duplicate instances of a VPP token.

### Intune apps

### Role-based access control

#### A new entity collection named Current User is limited to currently active user data <!-- 1667026 -->

The **Users** entity collection contains all the Azure Active Directory (Azure AD) users with assigned licenses in your enterprise. For example, a user may be added to Intune and then removed during the course of the last month. While this user is not present at the time of the report, the user and state are present in the data. You could create a report that would show the duration of the user's historic presence in your data.

In contrast, the new **Current User** entity collection only contains users who have not been removed. The **Current User** entity collection only contains currently active users. For information about the **current user** entity collection, see [Reference for current user entity](reports-ref-current-user.md).

### Updated Graph APIs <!-- 1736360 -->

In this release, we've updated a few of the Graph API's for Intune that are in beta. Please check out the monthly [Graph API changelog](https://developer.microsoft.com/graph/docs/concepts/changelog) for more information.

### Monitor and troubleshoot

#### Intune supports Windows Information Protection (WIP) denied apps <!-- 1479103 -->
You can specify denied apps in Intune. If an app is denied, it is blocked from accessing corporate information, effectively the opposite of the allowed apps list. For more information, see [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection).

<!-- ########################## -->
## November 2017

### Troubleshoot enrollment issues  <!-- 746324 -->

The **Troubleshoot** workspace now shows user enrollment issues. Details about the issue and suggested remediation steps can
help administrators and help desk operators troubleshoot problems. Certain enrollment issues aren't captured and some errors
might not have remediation suggestions.

### Group-assigned enrollment restrictions <!-- 747598 -->

As an Intune administrator, you can now [create custom Device Type and Device Limit enrollment restrictions for user groups](enrollment-restrictions-set.md).

The Intune Azure portal lets you create up to 25 instances of each restriction type, which can then be assigned to user groups. Group-assigned restrictions override the default restrictions.

All the instances of a restriction type are maintained in a strictly ordered list. This order defines a priority value for conflict resolution. A user impacted by more than one restriction instance is only restricted by the instance with the highest priority value. You can change a given instance's priority by dragging it to a different position in the list.

This functionality will be released with the migration of Android for Work settings from the Android For Work enrollment menu to the Enrollment Restrictions menu. Since this migration may take several days, your account may be upgraded for other parts of the November release before you see group assignment become enabled for Enrollment Restrictions.

### Support for multiple Network Device Enrollment Service (NDES) connectors <!-- 1528104 -->

NDES allows mobile devices running without domain credentials to obtain certificates based on the Simple Certificate Enrollment Protocol (SCEP).
With this update, multiple NDES connectors are supported.

### Manage Android for Work devices independently from Android devices <!-- 1490731 EEready-->

Intune supports managing enrollment of Android for Work devices independently from the Android platform. These settings are managed under **Device Enrollment** > **Enrollment restrictions** > **Device Type Restrictions**. (They were previously located under **Device Enrollment** > **Android for Work Enrollment** > **Android for Work Enrollment Settings**.)

By default, your Android for Work devices settings are the same as your settings for your Android devices. However, after you change your Android for Work settings that will no longer be the case.

If you block personal Android for Work enrollment, only corporate Android devices can enroll as Android for Work.

When working with the new settings, consider the following points:

#### If you have never previously onboarded Android for Work enrollment

The new Android for Work platform is blocked in the default Device Type Restrictions. After you onboard the feature, you can allow devices to enroll with Android for Work. To do so, change the default or create a new Device Type Restriction to supersede the default Device Type Restriction.

#### If you have onboarded Android for Work enrollment

If you’ve previously onboarded, your situation depends on the setting you chose:

| Setting | Android for Work status in default Device Type Restriction | Notes |
| --- | --- | --- |
| **Manage all devices as Android** | Blocked | All Android devices must enroll without Android for Work. |
| **Manage supported devices as Android for Work** | Allowed | All Android devices that support Android for Work must enroll with Android for Work. |
| **Manage supported devices for users only in these groups as Android for Work** | Blocked | A separate Device Type Restriction policy was created to override the default. This policy defines the groups you previously selected to allow Android for Work enrollment. Users within the selected groups will continue to be allowed to enroll their Android for Work devices. All other users are restricted from enrolling with Android for Work. |

In all cases, your intended regulation is preserved. No action is required on your part to maintain the global or per-group allowance of Android for Work in your environment.

### Google Play Protect support on Android <!-- 908720 -->

With the release of Android Oreo, Google introduces a suite of security features called Google Play Protect that allow users and
organizations to run secure apps and secure Android images. Intune now supports Google Play Protect features, including SafetyNet
remote attestation. Admins can set compliance policy requirements that require Google Play Protect to be configured and healthy.
The **SafetyNet device attestation** setting requires the device to connect with a Google service to verify that the device is
healthy and is not compromised. Admins can also set a configuration profile setting for Android for Work to require that
installed apps are verified by Google Play services. If a device is not compliant with Google Play Protect requirements, Conditional Access might block users from accessing corporate resources.

- Learn [How to create a device compliance policy to enable Google Play Protect](https://docs.microsoft.com/intune/compliance-policy-create-android).

### Text protocol allowed from managed Apps <!-- 1414050  -->

Apps managed by the Intune App SDK are able to send SMS messages.

### App install report updated to include Install Pending status <!-- 1249446 -->  

The **App install status** report, accessible for each app through the **App** list in the **Client apps** workload, now contains an **Install Pending** count for Users and Devices.

### iOS 11 app inventory API for Mobile Threat Detection <!-- 1391759 -->

Intune collects app inventory information from both personal and corporate-owned devices and makes it available for Mobile Threat Detection (MTD) providers to fetch, such as Lookout for Work. You can collect an app inventory from the users of iOS 11+ devices.

**App inventory**  
Inventories from both corporate-owned iOS 11+ and personally owned devices are sent to your MTD service provider. Data in the app inventory includes:

- App ID
- App Version
- App Short Version
- App Name
- App Bundle Size
- App Dynamic Size
- App is validated or not
- App is managed or not

### Migrate hybrid MDM users and devices to Intune standalone <!-- 1463747 wnready -->
New processes and tools are now available for moving users and their devices from hybrid MDM to Intune in the Azure portal, allowing you to do the following tasks:
- Copy policies and profiles from the Configuration Manager console to Intune in the Azure portal
- Move a subset of users to Intune in the Azure portal, while keeping the rest in hybrid MDM
- Migrate devices to Intune in the Azure portal without needing to re-enroll them

For details, see [Migrate hybrid MDM users and devices to Intune standalone](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

### On-premises Exchange connector high availability support  <!-- 676614 -->
After the Exchange connector creates a connection to Exchange using the specified CAS, the connector now has the ability to discovery other CASs. If the primary CAS becomes unavailable, the connector will fail over to another CAS, if available, until the primary CAS becomes available. For details, see [On-premises Exchange connector high availability support](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support).

### Remotely restart iOS device (supervised only) <!-- 1424595 -->

You can now trigger a supervised iOS 10.3+ device to restart using a device action. For more information on using the device restart action, see [Remotely restart devices with Intune](device-restart.md).

> [!Note]
> This command requires a supervised devices and the **Device Lock** access right. The device restarts immediately. Passcode-locked iOS devices will not rejoin a Wi-Fi network after restart; after restart, they may not be able to communicate with the server.

### Single Sign-on support for iOS <!-- 1333645 -->  

You can use Single Sign-on for iOS users. The iOS apps that are coded to look for user credentials in the Single Sign-on payload are functional with this payload configuration update. You can also use UPN and Intune Device ID to configure the Principal Name and Realm. For details, see [Configure Intune for iOS device single sign-on](sso-ios.md).

### Add "Find my iPhone" for personal devices <!--1427287-->
You can now view whether iOS devices have Activation Lock turned on. This feature previously could be found in the Intune in the classic portal.

### Remotely lock managed macOS device with Intune <!-- 1437691 -->

You can lock a lost macOS device, and set a 6-digit recovery PIN. When locked, the **Device overview** blade displays the PIN until another device action is sent.

For more information, see [Remotely lock managed devices with Intune](device-remote-lock.md).

### New SCEP profile details supported <!-- 1559808 -->

Administrators are now able to set additional settings when creating a SCEP profile on Windows, iOS, macOS, and Android platforms.  Administrators can set IMEI, serial number, or common name including email in the subject name format.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

### Retain data during a factory reset  <!--1588489 -->
When resetting Windows 10 version 1709 and later to factory settings, a new capability is available. Admins can specify if device enrollment and other provisioned data are retained on a device through a factory reset.

The following data is retained through a factory reset:
- User accounts associated with the device
- Machine state (domain join, Azure Active Directory-joined)
- MDM enrollment
- OEM installed apps (store and Win32 apps)
- User profile
- User data outside of user profile
- User autologon

The following data is not retained:
- User files
- User installed apps (store and Win32 apps)
- Non-default device settings

### Window 10 update ring assignments are displayed <!-- 1621837 -->
When you are **Troubleshooting,** for the user you are viewing, you are able to see any Windows 10 update rings assignments.  

### Windows Defender Advanced Threat Protection reporting frequency settings  <!-- 1455974  -->
Windows Defender Advanced Threat Protection (WDATP) service allows admins to manage reporting frequency for managed devices. With the new **Expedite telemetry reporting frequency** option, WDATP collects data and assesses risks more frequently. The default for reporting optimizes speed and performance. Increasing the frequency of reporting can be valuable for high-risk devices. This setting can be found in the **Windows Defender ATP** profile in **Device configurations**.

### Audit updates <!-- 1412961 -->  
Intune auditing provides a record of change operations related to Intune.  All create, update, delete, and remote task operations are captured and retained for one year.  The Azure portal provides a view of the last 30 days of audit data in each workload, and is filterable.  A corresponding Graph API allows retrieval of the auditing data stored for the last year.

Auditing is found under the **MONITOR** group. There is an **Audit Logs** menu item for each workload.

### Company Portal app for macOS is available <!--1541700-->
The Intune Company Portal on macOS has an updated experience, which has been optimized to cleanly display all the information and compliance notifications your users need for all the devices they have enrolled. And, once the Intune Company Portal has been deployed to a device, Microsoft AutoUpdate for macOS will provide updates to it. You can download the new Intune Company Portal for macOS by logging into the Intune Company Portal website from a macOS device.

### Microsoft Planner is now part of the mobile app management (MAM) list of approved apps  <!-- 1248473 -->
The Microsoft Planner app for iOS and Android is now part of the approved apps for mobile app management (MAM). The app can be configured through the Intune App Protection blade in the Azure portal to all tenants.
- Learn more the [MAM list of approved apps](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

### Per-App VPN requirement update frequency on iOS devices   <!-- 1547061 -->  
Administrators may now remove Per-App VPN requirements for apps on iOS devices; affected devices will after their next Intune check-in, which generally occurs within 15 minutes.  

### Support for System Center Operations Manager management pack for Exchange connector <!-- 885457 -->
The System Center Operations Manager management pack for Exchange connector is now available to help you parse the Exchange connector logs. This feature gives you different ways of monitoring the service when you need to troubleshoot issues.

### Co-management for Windows 10 devices  <!-- 1243445 -->
Co-management is a solution that provides a bridge from traditional to modern management, and it provides you with a path to make the transition using a phased approach. At its foundation, co-management is a solution where Windows 10 devices are concurrently managed by Configuration Manager and Microsoft Intune, as well as joined to Active Directory (AD) and Azure Active Directory (Azure AD).  This configuration provides you with a path to modernize over time, at the pace that’s right for your organization if you can’t move all at once.  

### Restrict Windows Enrollment by OS version <!-- 245498 -->
As an Intune administrator, you can now specify a minimum and maximum version of Windows 10 for device enrollments. You can set these restrictions in the **Platform Configurations** blade.

Intune will continue to support enrolling Windows 8.1 PCs and phones. However, only Windows 10 versions can be set with minimum and maximum limits. To permit enrollment of 8.1 devices, leave the minimum limit empty.

### Alerts for Windows AutoPilot unassigned devices  <!-- 1631236 -->
A new alert is available for Windows AutoPilot unassigned devices on the **Microsoft Intune** > **Device enrollment** > **Overview** page. This alert shows how many devices from the AutoPilot program do not have AutoPilot deployment profiles assigned. Use the information in the alert to create profiles and assign them to the unassigned devices. When you click the alert, you see a full list of Windows AutoPilot devices and detailed information about them. For more information, see [Enroll Windows devices using Windows AutoPilot deployment program](https://docs.microsoft.com/intune/enrollment-autopilot).

### Refresh button for Devices list    <!-- 1333581 -->
Because the Device list does not refresh automatically, you can use the new Refresh button to update the devices that display in the list.

### Support for Symantec Cloud Certification Authority (CA)  <!-- 1333638 -->    
Intune now supports Symantec Cloud CA, which allows the Intune Certificate Connector to issue PKCS certificates from the Symantec Cloud CA to Intune managed devices. If you're already using the Intune Certificate Connector with Microsoft Certification Authority (CA), you can use the existing Intune Certificate Connector setup to add the Symantec CA support.

### New items added to device inventory   <!--1404455 -->
The following new items are now available to the [inventory taken by enrolled devices](device-inventory.md):

- Wi-Fi MAC address
- Total storage space
- Total free space
- MEID
- Subscriber carrier

### Set access for apps by minimum Android security patch on the device<!-- 1278463 -->   
An administrator is able to define the minimum Android security patch that must be installed on the device in order to gain access to a managed application under a managed account.

> [!Note]  
> This feature only restricts security patches released by Google on Android 6.0+ devices.

### App-conditional launch support <!-- 1193313 -->
IT admins can now set a requirement through the Azure admin portal to enforce a passcode instead a numeric PIN through the mobile app management (MAM) when the application launch. If configured, the user is required to set and use a passcode when prompted before getting access to MAM-enlightened applications. A passcode is defined as a numeric PIN with at least one special character or upper/lowercase alphabet. This release of Intune will enable this feature **on iOS only**. Intune supports passcode in a similar way to numeric PIN, it sets a minimum length, allowing repeat characters and sequences. This feature requires the participation of applications (that is, WXP, Outlook, Managed Browser, Yammer) to integrate the Intune App SDK with the code for this feature in place for the passcode settings to be enforced in the targeted applications.

### App Version number for line-of-business in device install status report <!-- 1233999 -->
With this release, the Device install status report displays the app version number for the line-of-business apps for iOS and Android. You may use this information to troubleshoot your apps, or find devices that are running outdated app versions.

### Admins can now configure the Firewall settings on a device using a device configuration profile <!-- 951708 -->   
Admins can turn on firewall for devices, and also configure various protocols for domain, private, and public networks.  These firewall settings can be found in the "Endpoint protection" profile.

### Windows Defender Application Guard helps protect devices from untrusted websites, as defined by your organization <!-- 958257 -->   
Admins can define sites as "trusted" or "corporate" using a Windows Information Protection workflow or the new "Network boundary" profile under device configurations. If they are viewed with Microsoft Edge, any sites that aren't listed in on a 64-bit Windows 10 device’s trusted network boundary open instead in a browser within a Hyper-V virtual computer.

Application Guard can be found in the device configuration profiles, in the "Endpoint protection" profile. From there, admins can configure interaction between the virtualized browser and the host machine, nontrusted sites and trusted sites, and storing data generated in the virtualized browser. To use Application Guard on a device, a network boundary first must be configured. It's important to define only one network boundary for a device.  

### Windows Defender Application Control on Windows 10 Enterprise provides mode to trust only authorized apps <!-- 1031096 -->    
With thousands of new malicious files created every day, using antivirus signature-based detection to fight against malware might no longer provide an adequate defense against new attacks. Using Windows Defender Application Control on Windows 10 Enterprise, you can change device configuration from a mode where apps are trusted unless blocked by an antivirus or other security solution, to a mode where the operating system trusts only apps authorized by your enterprise. You assign trust to apps in Windows Defender Application Control.

Using Intune, you can configure the application control policies either in "audit only" mode or enforce mode. Apps aren't blocked when running in “audit only” mode. “Audit only” mode logs all events in local client logs. You can also configure whether only Windows components and Microsoft Store apps are allowed to run or whether additional apps with good reputations as defined by the Intelligent Security Graph are allowed to run.

### Window Defender Exploit Guard is a new set of intrusion prevention capabilities for Windows 10 <!-- 1063615 -->   
Window Defender Exploit Guard includes custom rules to reduce the exploitability of applications, prevents macro and script threats, automatically blocks network connections to low reputation IP addresses, and can secure data from ransomware and unknown threats. Windows Defender Exploit Guard consists of the following components:

- **Attack Surface Reduction** provides rules that allow you to prevent macro, script, and email threats.
- **Controlled Folder access** automatically blocks access to content to protected folders.
- **Network Filter** blocks outbound connection from any app to low rep IP/domain
- **Exploit Protection** provides memory, control flow, and policy restrictions that can be used to protect an application from exploits.

### Manage PowerShell scripts in Intune for Windows 10 devices <!-- 790537 -->

The Intune management extension lets you upload PowerShell scripts in Intune to run on Windows 10 devices. The extension supplements Windows 10 mobile device management (MDM) capabilities and makes it easier for you to move to modern management. For details, see [Manage PowerShell scripts in Intune for Windows 10 devices](intune-management-extension.md).

### New device restriction settings for Windows 10      <!-- 1308850 -->
- Messaging (mobile only) - disable testing or MMS messages
- Password - settings to enable FIPS and the use of Windows Hello devices secondary devices for authentication 
- Display - settings to turn on or off GDI Scaling for legacy apps

### Windows 10 kiosk mode device restrictions <!-- 1308872 -->   
You can restrict Windows 10 device users to kiosk mode, which limits users to a set of predefined apps.  To do so, create a Windows 10 device restriction profile and set the Kiosk settings.

Kiosk mode supports two modes: **single app** (allows a user to run just one app) or **multi app** (permits access to a set of apps).  You define the user account and device name, which determines the supported apps).  When the user is logged in, they're limited to the defined apps.  To learn more, see [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp). 

Kiosk mode requires:

- Intune must be the MDM authority.
- The apps must already be installed on the target device.
- The device must be [properly provisioned](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions).

### New device configuration profile for creating network boundaries <!-- 1311967 -->   
A new device configuration profile called **Network boundary** can be found with your other device configuration profiles. Use this profile to define online resources that you want to be considered corporate and trusted. You must define a network boundary for a device *before* features such as Windows Defender Application Guard and Windows Information Protection can be used on the device. It’s important to define only one network boundary for each device.

You can define enterprise cloud resources, IP address ranges, and internal proxy servers that you want to be considered trusted. Once defined, the network boundary can be consumed by other features such as Windows Defender Application Guard and Windows Information Protection.

### Two additional settings for Windows Defender Antivirus <!-- 1338409 -->  
**File blocking level**

| | |
|---|---|
| Not Configured | **Not Configured** uses the default Windows Defender Antivirus blocking level and provides strong detection without increasing the risk of detecting legitimate files. |
| High | **High** applies a strong level of detection.
| High +  | **High +** provides the High level with additional protection measures that might impact client performance.
| Zero tolerance  | **Zero tolerance** blocks all unknown executables. |

While unlikely, setting to **High** may cause some legitimate files to be detected.
We recommend you set File blocking level to the default, **Not configured**.

**Time out extension for file scanning by the cloud**  

| | |
|--|--|
| Number of seconds (0-50) | Specify the maximum amount of time that Windows Defender Antivirus should block a file while waiting for a result from the cloud. The default amount is 10 seconds: any additional time specified here (up to 50 seconds) is added to those 10 seconds. In most cases, the scan takes much less time than the maximum. Extending the time allows the cloud to thoroughly investigate suspicious files. We recommend that you enable this setting and specify at least 20 additional seconds. |

### Citrix VPN added for Windows 10 devices <!-- 1512457 -->  
You can configure Citrix VPN for their Windows 10 devices. You can choose the Citrix VPN in the *Select a connection type* list in the **Base VPN** blade when configuring a VPN for Windows 10 and later.

> [!Note]
> Citrix configuration existed for iOS and Android.

### Wi-Fi connections support pre-shared keys on iOS <!-- 1550823 -->
Customers can configure Wi-Fi profiles to use pre-shared keys (PSK) for WPA/WPA2 Personal connections on iOS devices. These profiles are pushed to user's device when the device is enrolled into Intune.

When the profile has been pushed to the device, the next step depends on the profile configuration.  If set to connect automatically, it does so when the network is next needed.  When the profile is connects manually, the user must activate the connection manually.  

### Access to managed app logs for iOS <!-- 1469920 -->
End users with the managed Browser installed can now view the management status of all Microsoft published apps and send logs for troubleshooting their managed iOS apps.

Learn how to enable the troubleshooting mode in the Managed Browser on an iOS device, see [How to access to managed app logs using the Managed Browser on iOS](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).

### Improvements to device setup workflow in the Company Portal for iOS in version 2.9.0 <!-- 1417174 -->

The device setup workflow has been improved in the Company Portal app for iOS. The language is more user-friendly and we've combined screens where possible. The language is more specific to your company by using your company name throughout the setup text. You can see this updated workflow on the [what's new in app UI page](whats-new-app-ui.md).

### User entity contains latest user data in Data Warehouse data model <!-- 1544273 -->
The first version of the Intune Data Warehouse data model only contained recent, historical Intune data. Report makers could not capture the current state of a user. In this update, the **User entity** is populated with the latest user data.

<!-- ########################## -->
## October 2017

### iOS and Android line-of-business app version number is visible <!-- 1380712 -->

Apps in Intune now display the version number for iOS and Android line-of-business apps. The number displays in the Azure portal in the app list and in the app overview blade. End users can see the app number in the Company Portal app and in the web portal.

__Full version number__
The full version number identifies a specific release of the app. The number appears as _Version_(_Build_). For example, 2.2(2.2.17560800)

The full version number has two components:

- **Version**  
  The version number is the human-readable release number of the app. This is used by end users to identify different releases of the app.

- **Build Number**  
  The build number is an internal number that can be used in app detection and to programmatically manage the app. The build number refers to an iteration of the app that references changes in the code.

Learn more about version numbers and developing line-of-business apps in [Get started with the Microsoft Intune App SDK](app-sdk-get-started.md#line-of-business-app-version-numbers).

### Device and app management integration <!-- 677972 -->   
Now that Intune’s mobile device management (MDM) and mobile application management (MAM) are both accessible from the Azure portal, Intune started integrating the IT admin experience around application and device management. These changes are geared to simplify your device and app management experience.

Learn more about the MDM and MAM changes announced in the [Intune support team blog](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

### New enrollment alerts for Apple devices <!-- 1471790 -->
The overview page for enrollment will show useful alerts for IT admins regarding management of Apple devices. Alerts will show up on Overview page when the Apple MDM push certificate is expiring or has already expired; when the Device Enrollment Program token is expiring or has already expired; and when there are unassigned devices in the Device Enrollment Program.

### Support token replacement for app configuration without device enrollment <!-- 1080364 -->

You can use tokens for dynamic values in app configurations for apps on devices that are not enrolled. For more information, see [Add app configuration policies for managed apps without device enrollment](app-configuration-policies-managed-app.md).

### Updates to the Company Portal app for Windows 10 <!--1299474-->
The Settings page in the Company Portal app for Windows 10 has been updated to make the settings and intended user actions to be more consistent across all settings. It has also been updated to match the layout of other Windows apps. You can find before/after images in the [what's new in app UI](whats-new-app-ui.md) page.

### Inform end users what device information can be seen for Windows 10 devices <!--1337920-->
We have added **Ownership Type** to the Device Details screen on the Company Portal app for Windows 10. This will allow users to find out more about privacy directly from this page from the Intune end user docs. They will also be able to locate this information on the **About** screen.

### Feedback prompts for the Company Portal app for Android <!--1165249-->
The Company Portal app for Android now requests end user feedback. This feedback is sent directly to Microsoft, and provides end users with an opportunity to review the app in the public Google Play store. Feedback is not required, and can easily be dismissed so users can continue using the app.

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### Helping your users help themselves with the Company Portal app for Android <!-- 1573324, 1573150, 1558616, 1564878 -->

The Company Portal app for Android has added instruction for end users to help them understand and, where possible, self-solve on new use cases.
- End users will be guided to the [Azure Active Directory portal](https://account.activedirectory.windowsazure.com/r/#/profile) to remove a device if they have reached the maximum number of devices that they are allowed to add.
- End users are given steps to follow to help them [fix activation errors on Samsung Knox devices](https://go.microsoft.com/fwlink/?linkid=859718) or to [turn off power-saving mode](/intune-user-help/power-saving-mode-android). If neither of those solutions resolve their issue, we will provide an explanation of how to [submit logs to Microsoft](/intune-user-help/send-logs-to-microsoft-android).

### New 'Resolve' action available for Android devices <!-- 1583480 -->

The Company Portal app for Android is introducing a 'Resolve' action on the _Update device settings_ page. Selecting this option will take the end user directly to the setting that is causing their device to be noncompliant. The Company Portal app for Android currently supports this action for the [device passcode](/intune-user-help/set-your-pin-or-password-android), [USB debugging](/intune-user-help/you-need-to-turn-off-usb-debugging-android), and [Unknown Sources](/intune-user-help/you-need-to-turn-off-unknown-sources-android) settings.

### Device setup progress indicator in Android Company Portal <!-- 1565657 -->
The Company Portal app for Android shows a device setup progress indicator when a user is enrolling their device. The indicator shows new statuses, beginning with "Setting up your device...", then "Registering your device...", then "Finishing registering your device...", then "Finishing setting up your device...".

### Certificate-based authentication support on the Company Portal for iOS <!--1029830-->
We have added support for certificate-based authentication (CBA) in the Company Portal app for iOS. Users with CBA enter their username, then tap the “Sign in with a certificate” link. CBA is already supported on the Company Portal apps for Android and Windows. You can learn more on the [sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) page.

### Apps that are available with or without enrollment can now be installed without being prompted for enrollment. <!-- 1334712 -->

Company apps that have been made available with or without enrollment on the Android Company Portal app can now be installed without a prompt to enroll.

### Windows AutoPilot Deployment Program support in Microsoft Intune  <!-- 747617  -->
You can now use Microsoft Intune with Windows AutoPilot Deployment Program to empower your users to provision their corporate devices without involving IT. You can customize the out-of-box experience (OOBE) and guide users to join their device to Azure AD and enroll in Intune. Working together, Microsoft Intune and Windows AutoPilot eliminate the need to deploy, maintain, and manage operating system images. For details, see [Enroll Windows devices using Windows AutoPilot Deployment Program](https://docs.microsoft.com/intune/enrollment-autopilot).

### Quickstart for device enrollment  <!-- 1425655 --> 
Quickstart is now available in **Device enrollment** and provides a table of references for managing platforms and configuring the enrollment process. A brief description of each item and links to documentation with step-by-step instructions provides useful documentation to simplify getting started.

### Device categorization <!-- 1427491 -->
The enrolled devices platform chart of the **Devices > Overview** blade organizes devices by platform, including Android, iOS, macOS, Windows, and Windows Mobile.  Devices running other operating systems are grouped into "Other."  This includes devices manufactured by Blackberry, NOKIA, and others.  

To learn which devices are affected in your tenant, choose **Manage > All devices** and then use **Filter** to limit the **OS** field.

### Zimperium - New Mobile Threat Defense partner   <!-- 954681 -->  
You can control mobile device access to corporate resources using Conditional Access based on risk assessment conducted by Zimperium, a Mobile Threat Defense solution that integrates with Microsoft Intune.

#### How integration with Intune works
Risk is assessed based on telemetry collected from devices running Zimperium. You can configure EMS Conditional Access policies based on Zimperium risk assessment enabled through Intune device compliance policies, which you can use to allow or block non-compliant devices to access corporate resources based on detected threats.

### New settings for Windows 10 device restriction profile  <!--- 978575, 1308849, -->  
We are adding new settings to the Windows 10 device restriction profile in the Windows Defender SmartScreen category.

For details about the Windows 10 device restriction profile, see [Windows 10 and later device restriction settings]( device-restrictions-windows-10.md).

### Remote support for Windows and Windows Mobile devices   <!-- 1070473 -->  
Intune can now use the [TeamViewer](https://www.teamviewer.com) software, purchased separately, to enable you to give remote assistance to your users who are running Windows, and Windows Mobile devices.

### Scan devices with Windows Defender <!-- 1280988  1280990   -->
You can now run a **Quick scan**, **Full scan**, and **Update signatures** with Windows Defender Antivirus on managed Windows 10 devices. From the device's overview blade, choose the action to run on the device. You are prompted to confirm the action before the command is sent to the device. 

**Quick scan**: A quick scan scans locations where malware registers to start, such as registry keys and known Windows startup folders. A quick scan takes an average of five minutes. Combined with the **Always-on real-time protection** setting that scans files when they are opened, closed, and whenever a user navigates to a folder, a quick scan helps provide protection from malware that might be in the system or the kernel. Users see the scan results on their devices when it finishes. 

**Full scan**: A full scan can be useful on devices that have encountered a malware threat to identify if there are any inactive components that require a more thorough clean-up, and is useful for running on-demand scans. Full scan can take an hour to run. Users see the scan results on their devices when it finishes. 

**Update signatures**: The update signature command updates Windows Defender Antivirus malware definitions and signatures. This helps ensure Windows Defender Antivirus is effective in detecting malware. This feature is for Windows 10 devices only, pending device internet connectivity. 

### The Enable/Disable button is removed from the Intune Certificate Authority page of the Intune Azure portal  <!-- 1400455 -->
 We are eliminating an extra step in setting up the certificate connector on Intune. Currently, you download the certificate connector and then enable it in the Intune console. However, if you disable the connector in the Intune console, the connector continues to issue certificates.

#### How does this affect me?
Starting in October, the Enable/Disable button will no longer appear on the Certificate Authority page in the Azure portal. Connector functionality remains the same. Certificates are still deployed to devices enrolled in Intune. You can continue to download and install the certificate connector. To stop certificates from being issued, you now uninstall the certificate connector rather than disable it.

#### What do I need to do to prepare for this change?
If you currently have the certificate connector disabled, you should uninstall it.

### New settings for Windows 10 Team device restriction profile   <!--- 1308838 -->
In this release, we’ve added many new settings to the Windows 10 Team device restriction profile to help you control Surface Hub devices.

For more information about this profile, see [Windows 10 Team device restriction settings](device-restrictions-windows-10-teams.md).

### Prevent users of Android devices from changing their device date and time  <!-- 1333292 -->
You can use an [Android custom device policy](custom-settings-android.md) to prevent Android device users from changing the device date and time.

To do this, configure an Android custom policy with the setting URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange
Set this to **TRUE**, and then assign it to the required groups.

### BitLocker device configuration <!-- 1397398 -->
The **Windows Encryption > Base Settings** include a new **Warning for another disk encryption** setting that lets you disable the [warning prompt](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowwarningforotherdiskencryption) for other disk encryption that might be in use on the user's device.  The warning prompt requires end user consent before setting up BitLocker on the device and blocks BitLocker setup until confirmed by the end user.  The new setting disables the end user warning.

### Volume Purchase Program for Business apps will now sync to your Intune Tenant <!-- 800882 -->  
Third-party developers can privately distribute apps to authorized Volume Purchase Program (VPP) for Business members specified in iTunes Connect. These VPP for Business members can sign in to the Volume Purchase Program App Store and purchase their apps.

With this release, the VPP for Business apps purchased by the end user will now start syncing to their Intune tenants.

### Select Apple country store to sync VPP apps  <!-- 1332311 -->  
You can configure the Volume Purchase Program (VPP) country store when uploading your VPP token. Intune synchronizes VPP apps for all locales from the specified VPP country store.

> [!NOTE]  
> Today, Intune only synchronizes VPP apps from the VPP country store that match the Intune locale in which the Intune tenant was created.

### Block copy and paste between work and personal profiles in Android for Work <!-- 1098994 -->
With this release, you are able to configure the work profile for  Android for Work to block copy and paste between work and personal apps. You can find this new setting in the **Device restrictions** profile for the **Android for Work** Platform in **Work profile settings**.

### Create iOS apps limited to specific regional Apple App Stores <!-- 1281692 -->
You will be able to specify the country locale during the creation of an Apple App Store managed app.

> [!Note]  
> Currently, you can only create Apple App Store managed apps that are present in the US country store.

### Update iOS VPP user and device licensed apps  <!-- 1305564 -->  
You will be able to configure the iOS VPP token to update all apps purchased for that token through the Intune service. Intune
will detect the VPP app updates inside the app store and automatically push them to the device when the device checks-in.

For steps to set a VPP token and enable automatic updates, see [How to manage iOS apps purchased through a volume-purchase program with Microsoft Intune]
(/intune/vpp-apps-ios).

### User device association entity Collection added to Intune Data Warehouse data model <!-- 1187917 -->
You can now build reports and data visualizations using the user device association information that associates user and device entity collections. The data model can be accessed through the Power BI file (PBIX) retrieved from the Data Warehouse Intune page, through the OData endpoint, or by developing a custom client.

### Review policy compliance for Windows 10 update rings <!-- 1067886 -->
You will be able to review a policy report for your Windows 10 update rings from Software updates > Per update ring deployment state. The policy report includes deployment status for the update rings that you have configured. 

### New report that lists iOS devices with older iOS versions   <!-- 1352223 -->
The **Out-of-date iOS Devices** report is available from the **Software updates** workspace. In the report, you can view a list of supervised iOS devices that were targeted by an iOS update policy and have available updates. For each device, you can view a status for why the device has not been automatically updated. 

### View app protection policy assignments for troubleshooting <!--  1475003 -->
In this upcoming release, **App protection policy** option will be added to the **Assignments** drop-down list available on the troubleshooting blade. You can now select app protection policies to see app protection policies assigned to the selected users.

### Improvements to device setup workflow in Company Portal <!--1490692-->
We've improved the device setup workflow in the Company Portal app for Android. The language is more user-friendly and specific to your company, and we've combined screens where possible. You can see these on the [what's new in app UI](whats-new-app-ui.md#week-of-october-2-2017) page.

### Improved guidance around the request for access to contacts on Android devices <!--1484985-->

The Company Portal app for Android often requires the end user to accept the Contacts permission. If an end user declines this access, they will now see an in-app notification that alerts them to grant it for Conditional Access. 

### Secure startup remediation for Android <!--1490712-->

End users with Android devices will be able to tap the non-compliance reason in the Company Portal app. When possible, this will take them directly to the correct location in the settings app to fix the issue. 

### Additional push notifications for end users on the Company Portal app for Android Oreo <!--1475932-->

End users will see additional notifications to indicate to them when the Company Portal app for Android Oreo is performing background tasks, such as retrieving policies from the Intune service. This increases transparency for end users about when the Company Portal is performing administrative tasks on their device. This is part of the overall [optimization of the Company Portal UI](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) for the Company Portal app for Android Oreo. 

There are further optimizations for new UI elements that are enabled in Android Oreo.  End users will see additional notifications that will indicate to them when Company Portal is performing background tasks such as retrieving policy from the Intune service.  This increases transparency for end users about when Company Portal is performing administrative tasks on the device.

### New behaviors for the Company Portal app for Android with work profiles <!-- 1485783 -->

When you enroll an Android for Work device with a work profile, it's the Company Portal app in the work profile that performs management tasks on the device. 

Unless you are using a MAM-enabled app in the personal profile, the Company Portal app for Android no longer serves any use. To improve the work profile experience, Intune will automatically hide the personal Company Portal app after a successful work profile enrollment.

The Company Portal app for Android can be enabled at any time in the personal profile by browsing for [Company Portal in the Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) and tapping **Enable**.

### Company Portal for Windows 8.1 and Windows Phone 8.1 moving to sustaining mode <!--1428681-->

Beginning in October 2017, the Company Portal apps for Windows 8.1 and Windows Phone 8.1 will move to sustaining mode. This means that the apps and existing scenarios, such as enrollment and compliance, will continue to be supported for these platforms. These apps will continue to be available for download through existing release channels, such as the Microsoft Store. 

Once in sustaining mode, these apps will only receive critical security updates. There will be no additional updates or features released for these apps. For new features, we recommend that you update devices to Windows 10 or Windows 10 Mobile. 

### Block unsupported Samsung Knox device enrollment  <!-- 1490695 -->

The Company Portal app only attempts to enroll supported Samsung Knox devices. To avoid Knox activation errors that prevent MDM enrollment, device enrollment is only attempted if the device appears in the [list of devices published by Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Samsung devices can have model numbers that support Knox while others that don't. Verify Knox compatibility with your device reseller before purchase and deployment. You can find the full list of verified devices in the [Android and Samsung Knox Standard policy settings](supported-devices-browsers.md#intune-supported-web-browsers).

### End of support for Android 4.3 and lower <!-- 1171126, 1326920 -->
Managed apps and the Company Portal app for Android will require Android 4.4 and higher to access company resources. By December, all enrolled devices will be force-retired in December, resulting in loss of access to company resources. If you are using app protection policies without MDM, apps will not receive updates, and the quality of their experience will diminish over time.

### Inform end users what device information can be seen on enrolled devices <!--1165314-->
We are adding **Ownership Type** to the Device Details screen on all Company Portal apps. This will allow users to find out more about privacy directly from the [What information can your company see?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) article. This will be rolling out across all Company Portal apps in the near future. We announced this for iOS in [September](#september-2017).

<!-- ########################## -->
## September 2017

### Intune supports iOS 11 <!--1428975-->
Intune supports iOS 11. This was previously announced on the [Intune Support blog](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/).

### End of support for iOS 8.0 <!-- 1164477 -->
Managed apps and the Company Portal app for iOS will require iOS 9.0 and higher to access company resources. Devices that aren't updated before this September will no longer be able to access the Company Portal or those apps. 

### Refresh action added to the Company Portal app for Windows 10 <!--1132468-->
The Company Portal app for Windows 10 allows users to refresh the data in the app by either pulling to refresh or, on desktops, pressing F5.

### Inform end users what device information can be seen for iOS <!--739894-->

We have added **Ownership Type** to the Device Details screen on the Company Portal app for iOS. This will allow users to find out more about privacy directly from this page from the Intune end user docs. They will also be able to locate this information on the About screen.

### Allow end users to access the Company Portal app for Android without enrollment <!---1169910--->

End users will soon not have to enroll their device to access the Company Portal app for Android. End users at organizations that are using App Protection Policies will no longer receive prompts to enroll their device when they open the Company Portal app. End users will also be able to install apps from the Company Portal without enrolling the device. 

### Easier-to-understand phrasing for the Company Portal app for Android <!---1396349--->  

The enrollment process for the Company Portal app for Android has been simplified with new text to make it easier for end users to enroll. If you have custom enrollment documentation, you will want to update it to reflect the new screens. You can find sample images on our [UI updates for Intune end user apps](whats-new-app-ui.md#week-of-september-11-2017) page.

### Windows 10 Company Portal app added to Windows Information Protection allow policy <!-- 677129 -->

The Windows 10 Company Portal app has been updated to support Windows Information Protection (WIP). The app can be added to the WIP allow policy. With this change, the app no longer has to be added to the **Exempt** list.

<!-- ########################## -->
## August 2017

### Improvements to device overview <!-- 1404453 -->  
Improvements to the device overview now display enrolled devices but excludes devices managed by Exchange ActiveSync. Exchange ActiveSync devices do not have the same management options as enrolled devices. To view the number of enrolled devices and number of enrolled devices by platform in Intune in the Azure portal, go **Devices** > **Overview**.

### Improvements to device inventory collected by Intune
<!-- 961134, 1104426, 1281327, 1333543 -->
In this release, we’ve made the following improvements to the inventory information collected by devices you manage:
 
- For Android devices, you can now add a column to device inventory that shows the latest patch level for each device. Add the **Security patch level** column to your device list to see this.
- When you filter the device view, you can now filter devices by their enrollment date. For example, you could display only devices that were enrolled after a date you specify.
- We’ve made improvements to the filter used by the **Last Check-in Date** item.
- In the device list, you can now display the phone number of corporate owned devices.
Additionally, you can use the filter pane to search for devices by phone number.

For more details about device inventory, see [How to view Intune device inventory](device-inventory.md).

### Conditional Access support for macOS devices 
<!-- 720172 -->
You can now set a Conditional Access policy that requires Mac devices to be enrolled into Intune and compliant with its device compliance policies. For example, users can download the Intune Company Portal app for macOS and enroll their Mac devices into Intune. Intune evaluate whether the Mac device is compliant or not with requirements like PIN, encryption, OS version, and System Integrity.

- Learn more about [Conditional Access support for macOS devices](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

### Company Portal app for macOS is in public preview <!---1484796--->
The Company Portal app for macOS is now available as part of the public preview for Conditional Access in Enterprise Mobility + Security. This release supports macOS 10.11 and above. Get it at [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal). 

### New device restriction settings for Windows 10    
<!--1063965, 1308850  -->
In this release, we’ve added new settings for the [Windows 10 device restriction profile](/intune/device-restrictions-windows-10) in the following categories:

- Windows Defender SmartScreen
- App store

### Updates to the Windows 10 endpoint protection device profile for BitLocker settings
<!--1459533 -->    
In this release, we’ve made the following improvements to how BitLocker settings work in a Windows 10 endpoint protection device profile:
 
- Under **Bitlocker OS drive settings**, for the setting **BitLocker with non-compatible TPM chip**, when you select **Block**, previously, this would cause BitLocker to actually be allowed. We have now fixed this to block BitLocker when it is selected.
- Under **Bitlocker OS drive settings**, for the setting **Certificate-based data recovery agent**, you can now explicitly block the certificate-based data recovery agent. By default, however, the agent is allowed.
- Under **BitLocker fixed data-drive settings**, for the setting **Data recovery agent**, you can now explicitly block the data recovery agent.
For more information, see [Endpoint protection settings for Windows 10 and later](endpoint-protection-windows-10.md).

### New signed-in experience for Android Company Portal users and App Protection Policy users <!-- 621669 -->
End users can now browse apps, manage devices, and view IT contact information using the Android Company Portal app without enrolling their Android devices. In addition, if an end user already uses an app protected by Intune App Protection Policies and launches the Android Company Portal, the end user no longer receive a prompt to enroll the device.

### New setting in the Android Company Portal app to toggle battery optimization <!--1405990-->
The **Settings** page in the Company Portal app for Android has a new setting that easily lets users turn off battery optimization for Company Portal and Microsoft Authenticator apps. The app name shown in the setting will vary depending on which app manages the work account. We recommend that users turn battery optimization off for better performance of work apps that sync email and data. 

### Multi-identity support for OneNote for iOS      <!-- 1234281 -->
End users can now use different accounts (work and personal) with Microsoft OneNote for iOS. App protection policies can be applied to corporate data in work notebooks without affecting their personal notebooks. For example, a policy can allow a user to find information in work notebooks, but will prevent the user from copying and pasting and corporate data from the work notebook to a personal notebook.
 
- Learn more about the apps that support [app protection and multi-identity](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) with Intune.

### New settings to allow and block apps on Samsung Knox Standard devices
<!-- 1305423 822899-->  
In this release, we are adding new [device restriction settings](device-restrictions-android.md) that let you specify the following app lists:
 
- Apps that users are allowed to install
- Apps that users are blocked from running
- Apps that are hidden from the user on the device
 
You can specify the app by URL, package name or from the list of apps you manage.

### New Azure AD app-based Conditional Access policy UI link from Intune
<!-- 1016201 -->
IT admins can now set app-based conditional policies via the new Conditional Access policy UI in the Azure AD workload. The app-based Conditional Access that is in the Intune App Protection section in the Azure portal will remain there for the time being and will be enforced side-by-side. There’s also a convenience link to the new Conditional Access policy UI in the Intune workload.

- Learn more about [app-based Conditional Access on Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).

<!-- ########################## -->
## July 2017

### Restrict Android and iOS device enrollment restriction by OS version  <!--- 1333256,  1245463 --->
Intune now supports restricting iOS and Android enrollment by operating system version number. Under **Device Type Restriction**, the IT admin can now set a platform configuration to restrict enrollment between a minimum and maximum operating system value. Android operating system versions must be specified as Major.Minor.Build.Rev, where Minor, Build and Rev are optional. iOS versions must be specified as Major.Minor.Build where Minor and Build are optional. Learn more about [device enrollment restrictions](enrollment-restrictions-set.md).

>[!NOTE]
>Does not restrict enrollment through Apple enrollment programs or Apple Configurator.

### Restrict Android, iOS, and macOS device personally owned device enrollment  <!--- 1333272,  1333275, 1245709 --->
Intune can restrict personal device enrollment by white-listing corporate device IMEI numbers. Intune has now expanded this functionality to iOS, Android, and macOS using device serial numbers. By uploading the serial numbers to Intune, you can predeclare devices as corporate-owned. Using enrollment restrictions, you can block personally owned (BYOD) devices, allowing enrollment only for corporate-owned devices. Learn more about [device enrollment restrictions](enrollment-restrictions-set.md).

To import serial numbers, go **Device enrollment** > **Corporate device identifiers** and click **Add** and then upload a .CSV file (no header, two columns for serial number and details like IMEI numbers). To restrict personally owned devices, go **Device enrollment** > **Enrollment restrictions**. Under **Device Type Restrictions**, select the **Default** and then select **Platform Configurations**. You can **Allow** or **Block** personally owned devices for iOS, Android, and macOS.

### New device action to force devices to sync with Intune <!-- 711369 -->
In this release, we've added a new device action that forces the selected device to immediately check in with Intune. When a device checks in, it immediately receives any pending actions or policies that have been assigned to it.  This action can help you to immediately validate and troubleshoot policies you’ve assigned, without waiting for the next scheduled check-in.
For details, see [Synchronize device](device-sync.md)

### Force supervised iOS devices to automatically install the latest available software update <!-- 777100 -->
A new policy is available from the Software updates workspace where you can force supervised iOS devices to automatically install the latest available software update. For details see, [Configure iOS update policies](/intune/software-updates-ios)

### Check Point SandBlast Mobile - New Mobile Threat Defense partner  <!-- 954651, 1172027 -->
You can control mobile device access to corporate resources using Conditional Access based on risk assessment conducted by Checkpoint SandBlast Mobile, a mobile threat defense solution that integrates with Microsoft Intune.

#### How integration with Intune works?
Risk is assessed based on telemetry collected from devices running Checkpoint SandBlast Mobile. You can configure EMS Conditional Access policies based on Checkpoint SandBlast Mobile risk assessment enabled through Intune device compliance policies. You can allow or block noncompliant devices access to corporate resources based on detected threats.

### Deploy an app as available in the Microsoft Store for Business <!-- 748101 -->
With this release, admins can now assign the Microsoft Store for Business as available. When set as available, end-users can install the app from the Company Portal app or website without being redirected to the Microsoft Store.

### UI updates to the Company Portal website <!--1313244 part 1-->
We made several updates to the UI of the [Company Portal website](https://portal.manage.microsoft.com) to enhance the end user experience.

- __Enhancements to app tiles__:  App icons will now display with an automatically generated background based on the dominant color of the icon (if it can be detected). When applicable, this background replaces the gray border that was previously visible on app tiles.

    The Company Portal website displays large icons whenever possible in an upcoming release. We recommend that IT admins publish apps using high-resolution icons with a minimum size of 120 x120 pixels. 

- __Navigation changes__: Navigation bar items are moved to the hamburger menu in the top left. The Categories page is removed. Users can now filter content by category while browsing.

- __Updates to Featured Apps__: We've added a dedicated page to the site where users can browse apps that you've chosen to feature, and made some UI tweaks to the Featured section on the homepage.

### iBooks support for the Company Portal website <!--1231841-->
We've added a dedicated page to the Company Portal website that allows users to browse and download iBooks. 

### Additional help desk troubleshooting details <!---  Applies to 1263399, 1326964, 1341642 --->
Intune has updated the troubleshooting display and added to the information that it provides for admins and help desk staff. You can now see an **Assignments** table that summarizes all assignments for the user based on group membership. This list includes:
- Mobile apps
- Compliance policies
- Configuration profiles

In addition, the **Devices** table now includes **Azure AD join type** and **Azure AD compliant** columns. For more information, see [help users troubleshoot problems](help-desk-operators.md).

### Intune Data Warehouse (Public Preview)
The Intune Data Warehouse samples data daily to provide a historical view of your tenant. You can access the data using a Power BI file (PBIX), an OData link that is compatible with many analytics tools, or interacting with the REST API. For more information, see [Use the Intune Data Warehouse](reports-nav-create-intune-reports.md).

### Light and dark modes available for the Company Portal app for Windows 10 <!---676547--->
End users will be able to customize the color mode for the Company Portal app for Windows 10. The user is able to make the change in the Settings section of the Company Portal app. The change will appear after the user has restarted the app. For Windows 10 version 1607 and later, the app mode will default to the system setting. For Windows 10 version 1511 and earlier, the app mode will default to the light mode.

### Enable end users to tag their device group in the Company Portal app for Windows 10 <!---807046-->
End users are now able to select which group their device belongs to by tagging it directly from within the Company Portal app for Windows 10.

<!-- ########################## -->
## June 2017

### New role-based administration access for Intune admins   <!-- 1099990 -->  
A new Conditional Access admin role is being added to view, create, modify, and delete Azure AD Conditional Access policies. Previously, only global admins and security admins had this permission. Intune admins can be granted with this role permission so that they have access to Conditional Access policies.

### Tag corporate-owned devices with serial number <!-- 1215070 -->  
Intune now supports uploading iOS, macOS, and Android serial numbers as Corporate Device Identifiers. You can't use serial numbers to block personal devices from enrolling at this time because serial numbers are not verified during enrollment. Blocking personal devices by serial number will be released in the near future.

### New remote actions for iOS devices <!-- 854689 -->
In this release, we've added two new remote device actions for shared iPad devices that manage the Apple Classroom app:

- [Logout current user](device-logout-user.md) - Signs out the current user of an iOS device you choose.
- [Remove user](device-remove-user.md) - Deletes a user you choose from the local cache on an iOS device.

### Support for shared iPads with the iOS Classroom app <!-- 1044681 -->
In this release, we've expanded the support for managing the iOS Classroom app to include students who log into shared iPads using their managed Apple ID.

### Changes to Intune built-in apps <!-- 1332306 -->
Previously, Intune contained a number of built-in apps that you could quickly assign. Based on your feedback, we have removed this list, and you will no longer see built-in apps.
However, if you have already assigned any built-in apps, these will still be visible in the list of apps. You can continue to assign these apps as required.
In a later release, we plan to add an easier method to select and assign built-in apps from the Azure portal.

### Easier installation of Office 365 apps <!--- 1121362 --->
The new **Office 365 ProPlus** app type makes it easy for you to assign Office 365 ProPlus 2016 apps to devices that you manage which run the latest version of Windows 10. Additionally, you can also install Microsoft Project, and Microsoft Visio, if you own licenses for them. The apps you want are bundled together and appear as one app in the list of apps in the Intune console.
For more information, see [How to add Office 365 apps for Windows 10](apps-add-office365.md).

### Support for offline apps from the Microsoft Store for Business <!--- 777044 --->
Offline apps you purchased from the Microsoft Store for Business will now be synchronized to the Azure portal. You can then deploy these apps to device groups, or user groups. Offline apps are installed by Intune, and not by the store.

### Microsoft teams is now part of the App-based CA list of approved apps   <!-- 1257019 -->
The Microsoft Teams app for iOS and Android is now part of approved apps for app-based Conditional Access policies for Exchange and SharePoint Online. The app can be configured through the Intune App Protection blade in the Azure portal to all tenants currently using app-based Conditional Access.

### Managed browser and app proxy integration <!-- 1287310 -->
The Intune Managed Browser can now integrate with the Azure AD Application Proxy service to let users access internal web sites even when they are working remotely. Users of the browser simply enter the site URL as they normally would and the Managed Browser routes the request through the application proxy web gateway. For more information, see [Manage Internet access using Managed browser policies](app-configuration-managed-browser.md).

### New app configuration settings for the Intune Managed Browser <!-- 682951 -->
In this release, we've added further configurations for the Intune Managed Browser app for iOS and Android. You can now use an app configuration policy to configure the default home page and bookmarks for the browser.
For more information, see [Manage Internet access using Managed browser policies](app-configuration-managed-browser.md)

### BitLocker settings for Windows 10  <!-- 951707 -->
You can now configure BitLocker settings for Windows 10 devices using a new Intune device profile. For example, you can require that devices are encrypted, and also configure further settings that are applied when BitLocker is turned on.
For more information, see [Endpoint protection settings for Windows 10 and later](endpoint-protection-windows-10.md).

### New settings for Windows 10 device restriction profile <!--- 978527,  978550, 978569, 1050031, 1058611,  --->
In this release, we've added new settings for the Windows 10 device restriction profile, in the following categories:

- Windows Defender
- Cellular and connectivity
- Locked screen experience
- Privacy
- Search
- Windows Spotlight
- Microsoft Edge browser

For more information about Windows 10 settings, see [Windows 10 and later device restriction settings](device-restrictions-windows-10.md).

### Company Portal app for Android now has a new end user experience for App Protection Policies <!--1305217-->
Based on customer feedback, we've modified the Company Portal app for Android to show an **Access Company Content** button. The intent is to prevent end users from unnecessarily going through the enrollment process when they only need to access apps that support App Protection Policies, a feature of Intune mobile application management. You can see these changes on the [what's new in app UI](whats-new-app-ui.md) page.

### New menu action to easily remove Company Portal <!--1164569-->
Based on user feedback, the Company Portal app for Android has added a new menu action to initiate the removal of Company Portal from your device. This action removes the device from Intune management so that the app can be removed from the device by the user. You can see these changes on the [what's new in app UI](whats-new-app-ui.md) page and in the [Android end user documentation](/intune-user-help/unenroll-your-device-from-intune-android).

### Improvements to app syncing with Windows 10 Creators Update <!--676505-->
The Company Portal app for Windows 10 will now automatically initiate a sync for app install requests for devices with Windows 10 Creators Update (version 1703). This will reduce the issue of app installs stalling during the "Pending Sync" state. In addition, users will be able to manually initiate a sync from within the app. You can see these changes on the [what's new in app UI](whats-new-app-ui.md) page.

### New guided experience for Windows 10 Company Portal <!---1058938--->
The Company Portal app for Windows 10 will include a guided Intune walkthrough experience for devices that have not been identified or enrolled. The new experience provides step-by-step instructions that guide the user through registering into Azure Active Directory (required for Conditional Access features) and MDM enrollment (required for device management features). The guided experience will be accessible from the Company Portal home page. Users can continue to use the app if they do not complete registration and enrollment, but will experience limited functionality.

This update is only visible on devices running Windows 10 Anniversary Update (build 1607) or higher. You can see these changes on the [what's new in app UI](whats-new-app-ui.md) page.

### Microsoft Intune and Conditional Access admin consoles are generally available
We’re announcing the general availability of both the new Intune in the Azure portal admin console and the Conditional Access admin console. Through Intune in the Azure portal, you can now manage all Intune MAM and MDM capabilities in one consolidated admin experience, and leverage Azure AD grouping and targeting. Conditional Access in Azure brings rich capabilities across Azure AD and Intune together in one unified console. And from an administrative experience, moving to the Azure platform allows you to use modern browsers.

Intune is now visible without the **preview** label in the Azure portal at portal.azure.com.

There is no action required for existing customers at this time, unless you have received one of a series of messages in the message center requesting that you take action so that we can migrate your groups. You may have also received a message center notice informing you that migration is taking longer due to bugs on our side. We are diligently continuing work to migrate any impacted customer.

### Improvements to the app tiles in the Company Portal app for iOS
We updated the design of the app tiles on the homepage to reflect the branding color you set for the Company Portal. For more information, see [what's new in app UI](whats-new-app-ui.md).

### Account picker now available for the Company Portal app for iOS
Users of iOS devices might see our new account picker when they sign into the Company Portal if they use their work or school account to sign into other Microsoft apps. For more information, see [what's new in app UI](whats-new-app-ui.md).

<!-- ########################## -->
## May 2017

### Change your MDM authority without unenrolling managed devices <!--1103950-->
You can now change your MDM authority without having to contact Microsoft Support, and without having to unenroll and reenroll your existing managed devices. In the Configuration Manager console, you can [change your MDM authority](/sccm/mdm/deploy-use/change-mdm-authority) from Set to Configuration Manager (hybrid) to Microsoft Intune (standalone) or vice versa.

### Improved notification for Samsung Knox startup PINs <!--1087143-->
When end users need to set a start-up PIN on Samsung Knox devices to become compliant with encryption, the notification displayed to end users will bring them to the exact place in the Settings app when the notification is tapped.  Previously, the notification brought the end user to the password change screen.

### Device enrollment

#### Apple School Manager (ASM) support with shared iPad <!-- 748864, 770395-->

Intune now supports use of Apple School Manager (ASM) in place of Apple Device Enrollment Program to provide out-of-box enrollment of iOS devices. ASM onboarding is required to use the Classroom app for Shared iPads, and is required to enable syncing data from ASM to Azure Active Directory via Microsoft School Data Sync (SDS). For more information, see [Enable iOS device enrollment with Apple School Manager](apple-school-manager-set-up-ios.md).

> [!NOTE]
> Configuring Shared iPads to work with the Classroom app requires iOS Education configurations in Azure are that not yet available.  This functionality will be added soon.

### Device management

#### Provide remote assistance to Android devices using TeamViewer <!-- 675418 -->

Intune can now use the [TeamViewer](https://www.teamviewer.com) software, purchased separately, to enable you to give remote assistance to your users who are running Android devices. For more information, see [Provide remote assistance for Intune managed Android devices](device-profile-android-teamviewer.md).

### App management

#### New app protection policies conditions for MAM <!-- 679864 -->

You can now set a requirement for MAM without enrollment users that enforces the following policies:

- Minimum application version
- Minimum operating system version
- Minimum Intune APP SDK version of the targeted application (iOS only)

This feature is available on both Android and iOS. Intune supports minimum version enforcement for OS platform versions, application versions, and Intune APP SDK. On iOS, applications that have the SDK integrated can also set a minimum version enforcement at the SDK level. The user will be unable to access the targeted application if the minimum requirements through the app protection policy are not met at the three different levels mentioned above. At this point, the user may either remove their account (for multi-identity applications), close the application, or update the version of the OS or application.

You can also configure additional settings to provide a non-blocking notification that recommends an OS or application upgrade. This notification can be closed and the application may be used as normal.

For more information, see [iOS app protection policy settings](app-protection-policy-settings-ios.md) and [Android app protection policy settings](app-protection-policy-settings-android.md).

#### Configure app configurations for Android for Work <!-- 621621 -->
Some Android apps from the store support managed configuration options that let an IT admin control how an app runs in the work profile. With Intune, you can now view the configurations supported by an app, and configure them from the Azure portal with a configuration designer or a JSON editor. For more information, see [Use app configurations for Android for Work](app-configuration-policies-use-android.md).

#### New app configuration capability for MAM without enrollment <!-- 677969 -->
You can now create app configuration policies through the MAM without enrollment channel. This feature is equivalent to the app configuration policies available in the mobile device management (MDM) app configuration. For an example of app configuration using MAM without enrollment, see  [Manage Internet access using Managed browser policies with Microsoft Intune](app-configuration-managed-browser.md).

#### Configure allowed and blocked URL lists for the Managed Browser <!-- 682960 -->
You can now configure a list of allowed and blocked domains and URLs for the Intune Managed Browser using app configuration settings in the Azure portal. These settings can be configured regardless of whether it is being used on a managed or unmanaged device. For more information, see [Manage Internet access using Managed browser policies with Microsoft Intune](app-configuration-managed-browser.md).

#### App protection policy helpdesk view <!-- 1069473 -->
IT Helpdesk users can now check user license status and the status of app protection policy apps assigned to users in the Troubleshooting blade. For details, see [Troubleshooting](./help-desk-operators.md).

### Device configuration

#### Control website visits on iOS devices <!-- 723832 -->
You can now control which websites users of iOS devices can visit using one of the following two methods:

- Add permitted, and blocked URLs using Apples built-in web content filter.

- Allow only specified websites to be accessed by the Safari browser. Bookmarks are created in Safari for each site you specify.

For more information, see [Web content filter settings for iOS devices](web-content-filter-settings-ios.md).

#### Preconfigure device permissions for Android for Work apps <!-- 621614 -->
For apps deployed to Android for Work device work profiles, you can now configure the permissions state for individual apps.  By default, Android apps that require device permissions such as access to location or the device camera will prompt users to accept or deny permissions.  For example, if an app uses the device's microphone, then the end user is prompted to grant the app permission to use the microphone. This feature allows you to define permissions on behalf of the end user.  You can configure permissions to a) automatically deny without notifying the user, b) automatically approve without notifying the user, or c) prompt the user to accept or deny. For more information, see [Android for Work device restriction settings in Microsoft Intune](device-restrictions-android-for-work.md).

#### Define app-specific PIN for Android for Work devices <!-- 728976, 1102534 -->
Android 7.0 and above devices with a work profile managed as an Android for Work device let the administrator define a passcode policy that only applies to apps in the work profile.  Options include:

- Define just a device-wide passcode policy - This is the passcode that the user must use to unlock their entire device.
- Define just a work profile passcode policy - Users will be prompted to enter a passcode whenever any app in the work profile is opened.
- Define both a device and work profile policy - IT admin has the choice to define both a device passcode policy and a work profile passcode policy at differing strengths (for example, a four-digit PIN to unlock the device, but a six-digit PIN to open any work app).

For more information, see [Android for Work device restriction settings in Microsoft Intune](device-restrictions-android-for-work.md).

> [!NOTE]
> This is only available on Android 7.0 and above.  By default, the end user can use the two separately defined PINs or they can elect to combine the two defined PINs into the strongest of the two.

#### New settings for Windows 10 devices <!-- 978585 -->
We've added new [Windows device restriction settings](device-restrictions-windows-10.md) that control features like wireless displays, device discovery, task switching, and SIM card error messages.

#### Updates to certificate configuration <!-- 918991 and 823198 -->
When creating a SCEP certificate profile, for <strong>Subject name format</strong>, the <strong>Custom</strong> option is available for iOS, Android, and Windows devices. Before this update, the <strong>Custom</strong> field was available for iOS devices only. For more information, see [Create a SCEP certificate profile](certificates-scep-configure.md#create-a-scep-certificate-profile).

When creating a PKCS certificate profile, for **Subject alternative name**, the **Custom Azure AD attribute** is available. The **Department** option is available when you select **Custom Azure AD attribute**. For more information, see [create a PKCS certificate profile](certficates-pfx-configure.md#create-a-pkcs-certificate-profile).

#### Configure multiple apps that can run when an Android device is in kiosk mode <!-- 662059 -->
When an Android device is in kiosk mode, you could previously only configure one app that was allowed to run. You can now configure multiple apps using the app ID, store URL, or by selecting an Android app you already manage. For more information, see [Kiosk mode settings](device-restrictions-android.md#kiosk).

<!-- ########################## -->
## April 2017

### Support for managing the Apple Classroom app
You can now manage the iOS Classroom app on iPad devices. Set up the Classroom app on the teachers iPad with the correct class and student data, then configure student iPads registered to a class, so that you can control them using the app.
For details, see [Configure iOS education settings](education-settings-configure-ios.md).

### Support for managed configuration options for Android apps <!-- 621621 -->
Android apps in the Play store that support managed configuration options can now be configured by Intune.  This feature lets IT view the list of configuration values supported by an app, and provides a guided, first-class UI to allow them to configure those values.

### New Android policy for complex PINs <!-- 722069 -->
You can now set a required [password](device-restrictions-android.md#password) type of Numeric complex in an Android device profile for devices that run Android 5.0 and above.  Use this setting to prevent device users from creating a PIN that contains repeating, or consecutive numbers, like 1111, or 1234.

### Additional support for Android for Work devices
- **Manage password and work profile settings** <!-- 612808 -->

  This new Android for Work device restriction policy now lets you manage password and work profile settings on Android for Work devices you manage.

- **Allow data sharing between work and personal profiles** <!-- 1045102 -->

This Android for Work device restriction profile now has new options to help you configure data sharing between work and personal profiles.

- **Restrict copy and paste between work and personal profiles** <!-- 1046094 -->

  A new custom device profile for Android for Work devices now lets you restrict whether copy and paste actions between work and personal apps are allowed.

For more information, see [Device restrictions for Android for Work](device-restrictions-android-for-work.md).

### Assign LOB apps to iOS and Android devices <!-- 1057568 -->
You can now assign line of business (LOB) apps for [iOS](lob-apps-ios.md) (.ipa files) and [Android](lob-apps-android.md) (.apk files) to users or devices.

### New device policies for iOS <!-- 723774, 723815, 723826, 723830 -->
- **Apps on Home screen** - Controls which apps users see on the [Home screen of their iOS device](home-screen-settings-ios.md). This policy changes the layout of the Home screen, but does not deploy any apps.

- **Connections to AirPrint devices** - Controls which [AirPrint devices](air-print-settings-ios-macos.md) (network printers) that end users of iOS device can connect to.

- **Connections to AirPlay devices** - Controls which [AirPlay devices](airplay-settings-ios.md) (like Apple TV) that end users of iOS device can connect to.

- **Custom lock screen message** - Configures a custom message that users will see on the lock screen of their iOS device, that replaces the default lock screen message. For more information, see [Activate lost mode on iOS devices](device-lost-mode.md)

### Restrict push notifications for iOS apps <!-- 723767 -->
In an Intune device restriction profile, you can now configure the following [notification settings](app-notification-settings-ios.md) for iOS devices:

- Fully turn on or off notification for a specified app.
- Turn on or off, the notification in the notification center for a specified app.
- Specify the alert type, either **None**, **Banner**, or **Modal Alert**.
- Specify whether badges are allowed for this app.
- Specify whether notification sounds are allowed.

### Configure iOS apps to run in single app mode autonomously <!-- 737837 -->
You can now use an Intune device profile to configure iOS devices to run specified apps in [autonomous single app mode](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only). When this mode is configured, and the app is run, the device is locked so that it can only run that app. An example of this is when you configure an app that lets users take a test on the device. When the app's actions are complete, or you remove this policy, the device returns to its normal state.

### Configure trusted domains for email and web browsing on iOS devices <!-- 723765 -->
From an iOS device restriction profile, you can now configure the following [domain settings](device-restrictions-ios.md#domains):

- **Unmarked email domains** - Emails that the user sends or receives which don't match the domains you specify here will be marked as untrusted.

- **Managed web domains** - Documents downloaded from the URLs you specify here will be considered managed (Safari only).  

- **Safari password auto-fill domains** - Users can save passwords in Safari only from URLs matching the patterns you specify here. To use this setting, the device must be in supervised mode and not configured for multiple users. (iOS 9.3+)

### VPP apps available in iOS Company Portal <!-- 748782 -->
You can now assign iOS volume-purchased (VPP) apps as **Available** installs to end users. End users will need an Apple Store account to install the app.

### Synchronize eBooks from Apple VPP Store <!-- 800878 -->
You can now [synchronize books](vpp-apps-ios.md) you purchased from the Apple volume-purchase program store with Intune, and assign the books to users.

### Multi-user management for Samsung Knox Standard devices <!-- 971988 -->
Devices that run Samsung Knox Standard are now supported for [multi-user management](android-enroll.md) by Intune. This means that end users can sign in and out of the device with their Azure Active Directory credentials, and the device is centrally managed whether it’s in use or not.  When end-users sign-in, they have access to apps and get any policies applied to them. When users sign out, all app data is cleared.

### Additional Windows device restriction settings <!-- 818566 -->
We've added support for additional [Windows device restriction settings](device-restrictions-windows-10.md) like additional Microsoft Edge browser support, device lock screen customization, start menu customizations, Windows Spotlight search set wallpaper, and proxy setting.

### Multi-user support for Windows 10 Creators Update <!-- 822547 -->
We've added support for [multi-user management](windows-enroll.md) for devices that run the Windows 10 Creators Update and are Azure Active Directory domain-joined. This means that when different standard users log into the device with their Azure AD credentials, they will receive any apps and policies that were assigned to their user name. Users cannot currently use the Company Portal for self-service scenarios like installing apps.

### Fresh Start for Windows 10 PCs<!-- 1004830 -->
A new [Fresh Start device action](device-fresh-start.md) for Windows 10 PCs is now available.  When you issue this action, any apps that were installed on the PC are removed, and the PC is automatically updated to the latest version of Windows. This can be used to help remove pre-installed OEM apps that are often delivered with a new PC. You can configure if user data is retained when this device action is issued.

### Additional Windows 10 upgrade paths <!-- 903672 -->
You can now create an [edition upgrade policy to upgrade devices](edition-upgrade-configure-windows-10.md) to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### Bulk Enroll Windows 10 devices <!-- 747607 -->
You can now join large numbers of devices that run the Windows 10 Creators update to Azure Active Directory and Intune with Windows Configuration Designer (WCD). To enable [bulk MDM enrollment](windows-bulk-enroll.md) for your Azure AD tenant, create a provisioning package that joins devices to your Azure AD tenant using Windows Configuration Designer, and apply the package to corporate-owned devices you'd like to bulk enroll and manage. Once the package is applied to your devices, they will join Azure AD, enroll in Intune, and be ready for your Azure AD users to sign in.  Azure AD users are standard users on these devices and receive assigned policies and required apps. Self-service and Company Portal scenarios are not supported currently.

### New MAM settings for PIN and managed storage locations <!-- 581122, 736644 -->
Two new app settings are now available to help you with mobile application management (MAM) scenarios:

- **Disable app PIN when device PIN is managed** - Detects if a device PIN is present on the enrolled device, and if so, bypasses the app PIN triggered by the app protection policies. This setting will allow for a reduction in the number of times a PIN prompt is displayed to users opening a MAM-enabled application on an enrolled device. This feature is available for both Android and iOS.

- **Select which storage services corporate data can be saved to** -Allows you to specify which storage locations in which to save corporate data. Users can save to the selected storage location services, which means all other storage location services not listed will be blocked.

  List of supported storage location services:

  - OneDrive
  - Business SharePoint Online
  - Local storage

### Help desk troubleshooting portal <!-- 907448 -->
The new [troubleshooting portal](help-desk-operators.md) lets help desk operators and Intune administrators view users and their devices, and perform tasks to resolve Intune technical problems.

<!-- ########################## -->
## March 2017

### Support for iOS Lost Mode <!--431695-->
For iOS 9.3 and later devices, Intune added support for **Lost Mode**. You can now lock down a device to prevent all use and display a message and contact phone number of the device lock screen.

The end user will not be able to unlock the device until an admin disables Lost Mode. When Lost Mode is enabled, you can use the **Locate device** action to display the geographical location of the device on a map in the Intune console.

The device must be a corporate-owned iOS device, enrolled through DEP, that is in supervised mode.

For more information, see [What is Microsoft Intune device management](device-management.md)?

### Improvements to Device Actions report <!--677150-->
We’ve made improvements to the Device Actions report to improve performance. Additionally, you can now filter the report by state. For example, you could filter the report to show only device actions that were completed.”

### Custom app categories <!--748805-->
You can now create, edit, and assign categories for apps you add to Intune. Currently, categories can only be specified in English.
See [How to add an app to Intune](apps-add.md).

### Assign LOB apps to users with unenrolled devices <!--748823-->
You can now assign line-of-business apps from the store to users whether or not their devices are enrolled with Intune. If the user's device is not enrolled with Intune, they must go to the Company Portal website to install it, instead of the Company Portal app.

### New compliance reports <!--846671-->
You now have compliance reports that give you the compliance posture of devices in your company and allow you to quickly troubleshoot compliance-related issues encountered by your users. You can view information about

- Overall compliance state of devices
- Compliance state for an individual setting
- Compliance state for an individual policy

You can also use these reports to drill down into an individual device to view specific settings and policies that affect that device.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### Direct access to Apple enrollment scenarios <!--951869-->
For Intune accounts created after January 2017, Intune has enabled direct access to Apple enrollment scenarios using the Enroll Devices workload in the Azure portal. Previously, the Apple enrollment preview was only accessible from links in the Azure portal. Intune accounts created before January 2017 will require a one-time migration before these features are available in Azure. The schedule for migration has not been announced yet, but details will be made available as soon as possible. We strongly recommend creating a trial account to test out the new experience if your existing account cannot access the preview.

<!-- ########################## -->
## February 2017

### Ability to restrict mobile device enrollment <!--747600, 795782-->
Intune is adding new enrollment restrictions that control which mobile device platforms are allowed to enroll. Intune separates mobile device platforms as iOS, macOS, Android, Windows and Windows Mobile.

* Restricting mobile device enrollment does not restrict PC client enrollment.  
* For iOS and Android only, there is one additional option to block the enrollment of personally owned devices.

Intune marks all new devices as personal unless the IT admin takes action to mark them as corporate owned, as explained in [this article](device-enrollment.md).

### View all actions on managed devices <!--677150-->
A new __Device Actions__ report shows who has performed remote actions like factory reset on devices, and additionally shows the status of that action. See [What is device management?](device-management.md).

### Non-managed devices can access assigned apps <!--664691-->
As part of the design changes on the Company Portal website, iOS and Android users will be able to install apps assigned to them as "available without enrollment" on their non-managed devices. Using their Intune credentials, users will be able to log into the Company Portal website and see the list of apps assigned to them. The app packages of the "available without enrollment" apps are made available for download via the Company Portal website. Apps which require enrollment for installation are not affected by this change, as users will be prompted to enroll their device if they wish to install those apps.

### Custom app categories <!--748805-->
You can now create, edit, and assign categories for apps you add to Intune. Currently, categories can only be specified in English.
See [How to add an app to Intune](apps-add.md).

### Display device categories <!--814654-->
You can now view the device category as a column in the device list. You can also edit the category from the properties section of the device properties blade. See [How to add an app to Intune](apps-add.md).

### Configure Windows Update for Business settings <!--776716-->

Windows as a Service is the new way of providing updates for Windows 10. Starting with Windows 10, any new Feature Updates and Quality Updates will contain the contents of all previous updates. This means that as long as you've installed the latest update, you know that your Windows 10 devices are completely up-to-date. Unlike with previous versions of Windows, you now must install the entire update instead of part of an update.

By using Windows Update for Business, you can simplify the update management experience so that you don’t need to approve individual updates for groups of devices. You can still manage risk in your environments by configuring an update rollout strategy and Windows Update will make sure that updates are installed at right time. Microsoft Intune provides the ability to configure update settings on devices and gives you the ability to defer update installation. Intune doesn’t store the updates, but only the update policy assignment. Devices access Windows Update directly for the updates.Use Intune to configure and manage **Windows 10 update rings**. An update ring contains a group of settings that configure when and how Windows 10 updates get installed. For details, see [Configure Windows Update for Business settings](windows-update-for-business-configure.md).
