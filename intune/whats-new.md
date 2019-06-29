---
# required metadata
title: What's new in Microsoft Intune - Azure | Microsoft Docs
titleSuffix:
description: Find out what's new in the Intune Azure portal
keywords:
author: ErikjeMS  
ms.author: erikje
manager: dougeby
ms.date: 06/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
---

# What's new in Microsoft Intune

Learn what’s new each week in Microsoft Intune. You can also find [important notices](#notices), [past releases](whats-new-archive.md), and information about [how Intune service updates are released](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728). 

> [!Note]
> Each [monthly update](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) may take up to three days to rollout and will be in the following order:
> - Day 1: Asia Pacific (APAC)
> - Day 2: Europe, Middle East, Africa (EMEA)
> - Day 3: North America
> 
> Some features may roll out over several weeks and might not be available to all customers in the first week.
>
> Check the [In development page](in-development.md) for a list of upcoming features in a release.

**RSS feed**: Get notified when this page is updated by copying and pasting the following URL into your feed reader: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->  

<!-- ########################## -->

## Week of June 24, 2019 

### App management

#### Configure which browser is allowed to link to organization data <!-- 3145939 -->
Intune App Protection Policies (APP) on Android and iOS devices now allow you to transfer Org web links to a specific browser beyond the Intune Managed Browser or Microsoft Edge.  For more about APP, see [What are app protection policies?](app-protection-policy.md).

#### All apps page identifies online/offline Microsoft Store for Business apps<!--4089647 -->
The **All apps** page now includes labeling to identify Microsoft Store for Business (MSFB) apps as online or offline apps. Each MSFB app now includes a suffix for **Online** or **Offline**. The app details page also includes **License Type** and **Supports device context installation** (offline licensed  apps only) information.

#### Company Portal app on shared devices <!--4393553 -->
Users can now access the Company Portal app on shared devices. End users will see a **Shared** label on the device tile. This applies to Company Portal app version 10.3.45609.0 and later.

#### View all installed apps from new Company Portal web page <!-- 4224326 -->
The Company Portal website's new **Installed Apps** page lists all managed apps (both required and available) that are installed on a user's devices. In addition to assignment type, users can see the app's publisher, date published, and current installation status. If you haven't made any apps required or available to your users, they'll see a message explaining that no company apps have been installed. To see the new page on the web, go to the [Company Portal website](https://portal.manage.microsoft.com) and click **Installed Apps**.  

#### New view lets app users see all managed apps installed on device <!-- 2352913 -->  
The Company Portal app for Windows now lists all managed apps (both required and available) that are installed on a user's device. Users can also see attempted and pending app installations, and their current statuses. If you haven't made apps required or available to your users, they'll see a message explaining that no company apps have been installed. To see the new view, go to the Company Portal navigation pane and select **Apps** > **Installed Apps**.    

### Device configuration

#### Configure settings for kernel extensions on macOS devices <!-- 2043024 -->
On macOS devices, you can create a device configuration profile (**Device configuration** > **Profiles** > **Create profile** > choose **macOS** for platform). This update includes a new group of settings that let you configure and use kernel extensions on your devices. You can add specific extensions, or allow all extensions from a specific partner or developer.

To learn more about this feature, see [kernel extensions overview](kernel-extensions-overview-macos.md) and [kernel extension settings](kernel-extensions-settings-macos.md).

Applies to: macOS 10.13.2 and later

#### Apps from the store only setting for Windows 10 devices includes more configuration options <!-- 2697002 -->
When you create a device restrictions profile for Windows devices, you can use the **Apps from the store only** setting so users only install apps from the Windows App Store (**Device configuration** > **Profiles** > **Create profile** > **Windows 10 and later** for platform > **Device restrictions** for profile type). In this update, this setting is expanded to support more options. 

To see the new setting, go to [Windows 10 (and newer) device settings to allow or restrict features](device-restrictions-windows-10.md#app-store).

Applies to: Windows 10 and later

#### Deploy multiple Zebra mobility extensions device profiles to a device, same user group, or same devices group <!-- 4089955 -->
In Intune, you can use Zebra mobility extensions (MX) in a device configuration profile to customize settings for Zebra devices that aren't built-in to Intune. Currently, you can deploy one profile to a single device. In this update, you can deploy multiple profiles to:
- The same user group
- The same devices group
- A single device

[Use and manage Zebra devices with Zebra Mobility Extensions in Microsoft Intune](android-zebra-mx-overview.md) shows how to use MX in Intune.

Applies to: Android

#### Some kiosk settings on iOS devices are set using "Block", replacing "Allow" <!-- 4404075  -->
When you create a device restrictions profile on iOS devices (**Device configuration** > **Profiles** > **Create profile** > **iOS** for platform > **Device restrictions** for profile type > **Kiosk**), you set the **Auto lock**, **Ringer switch**, **Screen rotation**, **Screen sleep button**, and **Volume buttons**. 

In this update, the values are **Block** (blocks the feature) and **Not configured** (allows the feature). To see the settings, go to [iOS device settings to allow or restrict features](device-restrictions-ios.md#kiosk-supervised-only). 

Applies to: iOS

#### Use Face ID for password authentication on iOS devices <!-- 4490704 -->
When you create a device restrictions profile for iOS devices, you can use a fingerprint for a password. In this update, the fingerprint password settings also allow facial recognition (**Device configuration** > **Profiles** > **Create profile** > **iOS** for platform > **Device restrictions** for profile type > **Password**). As a result, the following settings changed:

- **Fingerprint unlock** is now **Touch ID and Face ID unlock**.
- **Fingerprint modification (supervised only)** is now **Touch ID and Face ID modification (supervised only)**.

Face ID is available in iOS 11.0 and later. To see the settings, go to [iOS device settings to allow or restrict features using Intune](device-restrictions-ios.md#password).

Applies to: iOS

#### Restricting gaming and app store features on iOS devices is now dependent on ratings region <!-- 4593948 -->
On iOS devices, you can allow or restrict features related to gaming, the app store, and viewing documents (**Device configuration** > **Profiles** > **Create profile** > **iOS** for platform > **Device restrictions** for profile type > **App Store, Doc Viewing, Gaming**). You can also choose the Ratings region, such as the United States. 

In this update, the **Apps** feature is moved to be a child to **Ratings region**, and is dependent on **Ratings region**. To see the settings, go to [iOS device settings to allow or restrict features using Intune](device-restrictions-ios.md#app-store-doc-viewing-gaming).

Applies to: iOS

### Device enrollment

#### Windows Autopilot reset removes the device's primary user <!-- 4156123 -->
When Autopilot reset is used on a device, the device's primary user will be removed. The next user who signs in after the reset will be set as the primary user.

#### Windows Autopilot support for Hybrid Azure AD Join <!-- 4809146-->
Windows Autopilot for existing devices now supports Hybrid Azure AD Join (in addition to the existing Azure AD Join support). Applies to Windows 10 version 1809 and above devices. For more information, see [
Windows Autopilot for existing devices](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices).



### Device management

#### See the security patch level for Android devices <!-- 4461911 -->
You can now see the security patch level for Android devices. To do so, choose **Intune** > **Devices** > **All devices** > choose a device > **Hardware**.
 The patch level is listed in the **Operating System** section.

#### Assign scope tags to all managed devices in a security group <!-- 3173810 -->
You can now assign scope tags to a security group and all devices in the security group will also be associated with those scope tags. All devices in these groups will also be assigned the scope tag. The scope tags set with this feature will overwrite the scope tags set with the current device scope tags flow. For more information, see [Use RBAC and scope tags for distributed IT](scope-tags.md). (In a future update, the current flow to assign scope tags to devices will be made read only.)

### Device security

#### Use keyword search with Security Baselines <!-- WNready -->
When you create or edit [Security Baseline profiles](security-baselines.md#create-the-profile), you can specify keywords in the new *Search* bar to filter the available groups of settings to those that contain your search criteria. 

#### The Security Baselines feature is now generally available  <!-- 3785395 -->
The **Security Baselines** feature is out of preview and is now generally available (GA).  This means the features is ready for use in production. However, the individual baseline templates can remain in preview and are evaluated and released to GA on their own schedules.

#### The MDM Security Baseline template is now generally available   <!-- 3794072, 4217151,  3534649 -->
The MDM Security Baseline template has moved out of preview and is now generally available (GA). The GA template is identified as **MDM Security Baseline for Spring 2019 Update (19H1)**.  This is a new template and not an upgrade from the preview version.  As a new template, you’ll need to review the [settings it contains](security-baseline-settings-windows.md), and then create new profiles to deploy the template to your device. Other security baseline templates can remain in preview. For a list of available baselines, see [Available security baselines](security-baselines.md#available-security-baselines).  

In addition to being a new template, the *MDM Security Baseline for Spring 2019 Update (19H1)* template includes the two settings that we recently announced in our In Development topic:  
- Above Lock: Voice activate apps from a locked screen  
- DeviceGuard: Use virtualization-based security (VBS) at the next reboot of devices.  

The *MDM Security Baseline for Spring 2019 Update (19H1)* also includes the addition of several new settings, the removal of others, and a revision of the default value of one setting. For a detailed list of the changes from Preview to GA, see **What’s changed in the new template**.

#### Security baseline versioning  <!-- 3194322 -->
Security baselines for Intune support versioning. With this support, as new versions of each security baseline are released, you can update your existing security baseline profiles to use the newer baseline version without having to recreate and deploy a new baseline from scratch. Additionally, in the Intune console you can view information about each baseline like the number of individual profiles you have that use the baseline, how many of the different baseline versions your profiles use, and when the the latest release of a specific security baseline was.  For more information, see **Security Baselines**.

#### The Use security keys for sign-in setting has moved  <!-- 4501151 -->
The device configuration setting for identity protection named **Use security keys for sign-in** is no longer found as a sub-setting of *Configure Windows Hello for Business*. It's now a top-level setting that is always available, even when you don't enable use of Windows Hello for Business. For more information see [Identity protection](identity-protection-windows-settings.md).

### Role-based access control

#### New permissions for assigned group admins   <!-- 4504437   -->
Intune's built-in School Administrator role now has create, read, update, and delete (CRUD) permissions for Managed Apps. This update means that if you're assigned as a group admin in Intune for Education, you can now create, view, update, and delete the iOS MDM Push Certificate, iOS MDM server tokens, and iOS VPP tokens along with [all of the existing permissions you have](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions). To take any of these actions, go to **Tenant settings** > **iOS Device Management**.  

#### Applications can use the Graph API to call read operations without user credentials <!-- 4655885 -->
Applications can call Intune Graph API read operations with app identity without user credentials. For more information about accessing the Microsoft Graph API for Intune, see [Working with Intune in Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### Apply scope tags to Microsoft Store for Business apps <!-- 4392555 -->
You can now apply scope tags to Microsoft Store for Business apps. For more information about scope tags, see [Use role-based access control (RBAC) and scope tags for distributed IT](scope-tags.md).

## Week of June 17, 2019 

### App management

#### New features in Microsoft Intune app
We’ve added new features to the Microsoft Intune app (preview) for Android. Users on fully managed Android devices can now:  

* View and manage the devices they've enrolled through the Intune Company Portal or Microsoft Intune app.    
* Contact their organization for support.    
* Send their feedback to Microsoft.    
* View terms and conditions, if set by their organization.    

## Week of June 10, 2019 

### App management

#### New sample apps showing Intune SDK integration available on GitHub <!-- 2653471 -->
The msintuneappsdk GitHub account has added new sample applications for iOS (Swift), Android, Xamarin.iOS, Xamarin Forms and Xamarin.Android. These apps are meant to supplement our existing documentation and provide demonstrations of how to integrate the Intune APP SDK into your own mobile apps. If you are an app developer that needs additional Intune SDK guidance, see the following linked samples:
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) - A native iOS (Swift) instant messaging app that uses the Azure Active Directory Authentication Library (ADAL) for brokered authentication.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) - A native Android todo list app that uses ADAL for brokered authentication.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) - A Xamarin.Android todo list app that uses ADAL for brokered authentication, this repository also has the Xamarin.Forms app.
- [Xamarin.iOS sample app](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) - A barebones Xamarin.iOS sample app.

## Week of May 27, 2019 

### App management

#### Reporting for potentially harmful apps on Android devices <!-- 4223162 -->
Intune now provides additional reporting information about potentially harmful apps on Android devices. 

## Week of May 20, 2019 

### App management

#### Windows Company Portal app <!-- 3316993 -->
The Windows Company Portal app will now have a new page labeled **Devices**. The **Devices** page will show end users all of their enrolled devices. Users will see this change in the Company Portal when they use version 10.3.4291.0 and later. For information about the configuring the Company Portal, see [How to configure the Microsoft Intune Company Portal app](company-portal-app.md).

### Device enrollment

#### Autopilot device OrderID attribute name changed to Group Tag <!-- 4659453 -->

To make it more intuitive, the **OrderID** attribute name on Autopilot devices has been changed to **Group Tag**. When using CSVs to upload Autopilot device information, you must use Group Tag as the column header, not OrderID.  

## Week of May 13, 2019 

### App management

#### Intune policies update authentication method and Company Portal app installation  <!-- 1927359 idready wnready-->
On devices already enrolled via Setup Assistant through one of Apple’s corporate device enrollment methods, Intune will no longer support the Company Portal when it is manually installed by end users from the app store. This change is only relevant when you authenticate with Apple Setup Assistant during enrollment. This change also only affects iOS devices enrolled through:  
* Apple configurator

* Apple Business Manager

* Apple School Manager

* Apple Device Enrollment Program (DEP)

If users install the Company Portal app from the App store, and then try to enroll these devices through it, they will receive an error. These devices will be expected to only use the Company Portal when it's been pushed, automatically, by Intune during enrollment. Enrollment profiles in Intune in the Azure portal will be updated so that you can specify how devices authenticate and if they receive the Company Portal app. If you want your DEP device users to have the Company Portal, you will need to specify your preferences in an enrollment profile. 

In addition, the **Identify your device** screen in the iOS Company Portal is being removed. Therefore, admins who want to enable Conditional Access or deploy company apps must update the DEP enrollment profile. This requirement only applies if the DEP enrollment is authenticated with Setup Assistant. In that case, you must push the Company Portal onto the device. To do so, choose **Intune** > **Device enrollment** > **Apple enrollment** > **Enrollment program tokens** > choose a token > **Profiles** > choose a profile > **Properties** > set **Install Company Portal** to **Yes**.

To install the Company Portal on already-enrolled DEP devices, you will need to go to Intune > Client apps, and push it as a managed app with app configuration policies. 

#### Configure how end users update a line-of-business (LOB) app using an app protection policy <!-- 3568384 -->
You can now configure where your end users can get an updated version of a line-of-business (LOB) app. End users will see this feature in the **min app version** conditional launch dialog, which will prompt end users to update to a minimum version of the LOB app. You must provide these update details as part of your LOB app protection policy (APP). This feature is available on iOS and Android. On iOS, this feature requires the app to be integrated (or wrapped using the wrapping tool) with the Intune SDK for iOS v. 10.0.7 or above. On Android, this feature would require the latest Company Portal. To configure how an end user updates a LOB app, the app needs a managed app configuration policy sent to it with the key, `com.microsoft.intune.myappstore`. The value sent will define which store the end user will download the app from. If the app is deployed via the Company Portal, the value must be `CompanyPortal`. For any other store, you must enter a complete URL.

#### Intune management extension PowerShell scripts  <!-- 3734186 idready -->
You can configure PowerShell scripts to run with the user’s admin privileges on the device. For more information, see [Use PowerShell scripts on Windows 10 devices in Intune](intune-management-extension.md) and [Win32 app management](apps-win32-app-management.md).

#### Android Enterprise app management <!-- 4459905 -->
To make it easier for IT admins to configure and use Android Enterprise management, Intune will automatically add four common Android Enterprise related apps to the Intune admin console. The four Android Enterprise apps are the following:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Used for Android Enterprise fully managed scenarios.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** -  Helps you sign-in to your accounts if you use two-factor verification.
- **[Intune Company Portal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - Used for App Protection Policies (APP) and Android Enterprise work profile scenarios.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - Used for Android Enterprise dedicated/kiosk scenarios.

Previously, IT admins would need to manually find and approve these apps in the [Managed Google Play store](https://play.google.com/store/apps) as part of setup. This change removes those previously manual steps to make it easier and faster for customers to use Android Enterprise management.

Admins will see these four apps automatically added to their Intune apps list at the time that they first connect their Intune tenant to managed Google Play. For more information, see [Connect your Intune account to your Managed Google Play account](connect-intune-android-enterprise.md). For tenants that have already connected their tenant or who already use Android Enterprise, there is nothing admins need to do. Those four apps will automatically show up within 7 days of the completion of the May 2019 service roll out.

### Device configuration

#### Updated PFX Certificate Connector for Microsoft Intune  <!-- 1533038 -->
We’ve released an update for the [PFX Certificate Connector for Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) that addresses an issue where existing PFX certificates continue to be reprocessed, which causes the connector to stop processing new requests.

####  Intune security tasks for Defender ATP (In public preview)     <!-- 3208597 -->
In public preview, you can use Intune to manage [security tasks for Microsoft Defender Advanced Threat Protection (ATP)](atp-manage-vulnerabilities.md). This integration with ATP and adds a risk-based approach to discover, prioritize, and remediate endpoint vulnerabilities and misconfigurations, while reducing the time between discovery to mitigation.

#### Check for a TPM chipset in a Windows 10 device compliance policy <!-- 3617671   idstaged-->
Many Windows 10 and later devices have Trusted Platform Module (TPM) chipsets. This update includes a new compliance setting that checks the TPM chip version on the device. 

[Windows 10 and later compliance policy settings](compliance-policy-create-windows.md#device-security) describes this setting.

Applies to: Windows 10 and later

#### Prevent end users from modifying their Personal HotSpot and disable Siri server logging on iOS devices <!-- 4097904   -->  
You create a device restrictions profile on iOS device (**Device configuration** > **Profiles** > **Create profile** > **iOS** for platform > **Device restrictions** for profile type). This update includes new settings you can configure:

- **Built-in Apps**: Server-side logging for Siri commands
- **Wireless**: User modification of Personal Hotspot (supervised only)​
​
To see these settings, go to [built-in app settings for iOS](device-restrictions-ios.md#built-in-apps) and [wireless settings for iOS](device-restrictions-ios.md#wireless).

Applies to: iOS 12.2 and newer

#### New classroom app device restriction settings for macOS devices <!-- 4097905   --> 
You can create device configuration profiles for macOS devices (**Device configuration** > **Profiles** > **Create profile** > **macOS** for platform > **Device restrictions** for profile type). This update include new classroom app settings, the option to block screenshots, and the option to disable the iCloud Photo Library.

To see the current settings, go to [macOS device settings to allow or restrict features using Intune](device-restrictions-macos.md).

Applies to: macOS

#### The iOS Password to access app store setting is renamed<!-- 4557891  -->​
​The **Password to access app store** setting is renamed to **Require iTunes Store password for all purchases** (**Device configuration** > **Profiles** > **Create profile** > **iOS** for platform > **Device restrictions** for profile type > **App store, Doc viewing, and Gaming**).​
​
To see the available settings, go to [App Store, Doc Viewing, Gaming iOS settings](device-restrictions-ios.md#app-store-doc-viewing-gaming).​
​
Applies to: iOS

####  Microsoft Defender Advanced Threat Protection  baseline  (Preview)  <!--  3754134 -->
We've added a security baseline Preview for [Microsoft Defender Advanced Threat Protection](security-baseline-settings-defender-atp.md) settings. This baseline is available when your environment meets the prerequisites for using [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites).

### Device enrollment

#### Windows Enrollment Status Page (ESP) is now generally available <!-- 3605348 -->
The Enrollment Status Page is now out of preview. For more information, see [Set up an enrollment status page](windows-enrollment-status.md).


#### Intune user interface update - Autopilot enrollment profile creation  <!-- 4593669 -->
The user interface for creating an Autopilot enrollment profile has been updated to align with Azure user interface styles. For more information see, [Create an Autopilot enrollment profile](https://docs.microsoft.com/intune/enrollment-autopilot#create-an-autopilot-deployment-profile). Moving forward, additional Intune scenarios will be updated to this new UI style.

#### Enable Autopilot Reset for all Windows devices <!-- 4225665 -->
Autopilot Reset now works for all Windows devices, even those not configured to use the Enrollment Status Page. If an enrollment status page wasn't configured for the device during initial device enrollment, the device will go straight to the desktop after sign-in. It might take up to eight hours to sync and appear compliant in Intune. For more information, see [Reset devices with remote Windows Autopilot Reset](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### Exact IMEI format not required when searching All devices <!--30407680 -->
You won't need to include spaces in IMEI numbers when you search **All devices**.

#### Deleting a device in the Apple portal will be reflected in the Intune portal <!--2489996 -->
If a device is deleted from Apple's Device Enrollment Program or Apple Business Manager portals, the device will automatically be deleted from Intune during the next sync.

### The Enrollment Status Page now tracks Win32 apps <!-- 2714451 -->
This only applies to devices running Windows 10 version 1903 and above. For more information, see [Set up an enrollment status page](windows-enrollment-status.md).

### Device management

#### Reset and wipe devices in bulk by using the Graph API <!-- 3295288 -->
You can now reset and wipe up to 100 devices in bulk using the Graph API.


### Monitor and troubleshoot

#### The Encryption report is out of Public Preview   <!-- 4587546      -->
The [report for BitLocker and device encryption](encryption-monitor.md) is now generally available, and no longer part of the public preview. 

<!-- ########################## -->

#### Outlook signature and biometric settings for  iOS and Android devices <!-- 4050557 -->
You can now specify if the default signature is enabled in Outlook on iOS and Android devices. Additionally, you can choose to allow users to change the biometric setting in Outlook on iOS.

## Week of May 6, 2019 

### Device configuration

#### Network Access Control (NAC) support for F5 Access for iOS devices <!-- 4500808 -->

F5 released an update to BIG-IP 13 that allows NAC functionality for F5 Access on iOS in Intune. To use this feature:

- Update BIG-IP to 13.1.1.5 refresh. BIG-IP 14 isn't supported.
- Integrate BIG-IP with Intune for NAC. Steps in [Overview: Configuring APM for device posture checks with endpoint management systems](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html).
- Check the **Enable Network Access Control (NAC)** setting in the VPN profile in Intune.

To see the available setting, go to [Configure VPN settings on iOS devices](vpn-settings-ios.md).

Applies to: iOS

#### Updated PFX Certificate Connector for Microsoft Intune <!-- doc-vso 1521237  -->  
We’ve released an update for the [PFX Certificate Connector for Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) that drops the polling interval from 5 minutes to 30 seconds.

## Week of April 22, 2019

### Use Compliance Manager to create assessments for Microsoft Intune<!-- 4404750 -->

[Compliance Manager](https://servicetrust.microsoft.com/ComplianceManager) (opens another Microsoft site) is a workflow-based risk assessment tool in the Microsoft Service Trust Portal. It enables you to track, assign, and verify your organization’s regulatory compliance activities related to Microsoft services. You can create your own compliance assessment with Office 365, Azure, Dynamics, Professional Services, and Intune. Intune has two assessments available - FFIEC and GDPR.

Compliance Manager helps you focus your efforts by breaking down controls - controls managed by Microsoft, and controls managed by your organization. You can complete the assessments, and then export and print the assessments.

[Federal Financial Institutions Examination Council (FFIEC)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (opens another Microsoft site) compliance is a set of standards for online banking issued by FFIEC. It's the most requested assessment for financial institutions that use Intune. It interprets how Intune helps meet FFIEC cybersecurity guidelines related to public cloud workloads. Intune’s FFIEC assessment is the second FFIEC assessment in Compliance Manager.

In the following example, you can see the breakdown for FFIEC controls. Microsoft covers 64 controls. You're responsible for the remaining 12 controls.

![See a sample Intune assessment for FFIEC, including the customer actions and Microsoft actions](./media/intune-ffiec-assessment-status.png)

[General Data Protection Regulation (GDPR)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (opens another Microsoft site) is a European Union (EU) law that helps protect the rights of individuals and their data. GDPR is the most requested assessment to help comply with privacy regulations. 

In the following example, you see the breakdown for GDPR controls. Microsoft covers 49 controls. You're responsible for the remaining 66 controls.

![See a sample Intune assessment for GDPR, including the customer actions and Microsoft actions](./media/intune-assessment-status.png)

## Week of April 15, 2019

### App management

#### OpenSSL encryption for Android app protection policies <!-- 3747362 -->
Intune app protection policies (APP) on Android devices now uses an OpenSSL encryption library that is FIPS 140-2 compliant. For more information, see the [encryption](app-protection-policy-settings-android.md#encryption) section of [Android app protection policy settings in Microsoft Intune](app-protection-policy-settings-android.md).

#### Enable Win32 app dependencies <!-- 2617348  -->
As the admin, you can require that other apps are installed as dependencies before installing your Win32 app. Specifically, the device must install the dependent app(s) before it installs the Win32 app. In Intune, select **Client apps** > **Apps** > **Add** to display the **Add app** blade. Select **Windows app (Win32)** as the **App type**. After you have added the app, you can select **Dependencies** to add the dependent apps that must be installed before the Win32 app can be installed. For more information, see [Intune Standalone - Win32 app management](apps-win32-app-management.md). 

#### App version installation information for Microsoft Store for Business apps <!-- 3537391   -->
App installation reports include app version information for Microsoft Store for Business apps. In Intune, select **Client apps** > **Apps**. Select a **Microsoft Store for Business app** and then select **Device install status** under the **Monitor** section.

#### Additions to Win32 apps requirement rules <!-- 3676883   -->
You can create requirement rules based on PowerShell scripts, registry values, and file system information. In Intune, select **Client apps** > **Apps** > **Add**. Then select **Windows app (Win32)** as the **App type** in the **Add app** blade.  Select **Requirements** > **Add** to configure additional requirement rules. Then, select either **File type**, **Registry**, or **Script** as the **Requirement type**. For more information, see [Win32 app management](apps-win32-app-management.md).

 #### Configure your Win32 apps to be installed on Intune enrolled Azure AD joined devices <!-- 3695227  -->
You can assign your Win32 apps to be installed on Intune enrolled Azure AD joined devices. For more information about Win32 apps in Intune, see [Win32 app management](apps-win32-app-management.md).

#### Device overview shows Primary User <!--794259  -->
The Device overview page will show the Primary User, also called the User Device Affinity User (UDA). To see the Primary User for a device, choose **Intune** > **Devices** > **All devices** > choose a device. The Primary User will appear near the top of the **Overview** page.

#### Additional Managed Google Play app reporting for Android Enterprise work profile devices <!-- 4105925  -->
For Managed Google Play apps deployed to Android Enterprise work profile devices, you can view the specific version number of the app installed on a device. This applies to required apps only.  

#### iOS Third Party Keyboards <!-- 4111843   -->
The Intune app protection policy (APP) support for the **Third Party Keyboards** setting for iOS is no longer supported due to an iOS platform change. You will not be able to configure this setting in the Intune Admin Console and it will not be enforced on the client in the Intune App SDK.

### Device configuration

#### Set login settings and control restart options on macOS devices <!-- 1210083  -->
On macOS devices, you can create a device configuration profile (**Device configuration** > **Profiles** > **Create profile** > choose **macOS** for platform > **Device features** for profile type). This update includes new login window settings, such as showing a custom banner, choose how users sign in, show or hide the power settings, and more.

To see these settings, go to [macOS device feature settings](macos-device-features-settings.md).

#### Configure WiFi on Android Enterprise, Device Owner dedicated devices running in multi-app kiosk mode <!--3041940  -->
You can enable settings on Android Enterprise, Device Owner when running as a dedicated device in multi-app kiosk mode. In this update, you can enable users to configure and connect to WiFi networks (**Intune** > **Device configuration** > **Profiles** > **Create profile** > **Android Enterprise** for platform > **Device owner only, Device restrictions** for profile type > **Dedicated devices** > **Kiosk mode**: **Multi-app** > **WiFi configuration**). 

To see all the settings you can configure, go to [Android Enterprise device settings to allow or restrict features](device-restrictions-android-for-work.md).

Applies to: Android Enterprise dedicated devices running in multi-app kiosk mode


#### Configure Bluetooth and pairing on Android Enterprise, Device Owner dedicated devices running in multi-app kiosk mode <!-- 3041941  -->
You can enable settings on Android Enterprise, Device Owner when running as a dedicated device in multi-app kiosk mode. In this update, you can allow end users to enable Bluetooth, and pair devices over Bluetooth (**Intune** > **Device configuration** > **Profiles** > **Create profile** > **Android Enterprise** for platform > **Device owner only, Device restrictions** for profile type > **Dedicated devices** > **Kiosk mode**: **Multi-app** > **Bluetooth configuration**). 

To see all the settings you can configure, go to [Android Enterprise device settings to allow or restrict features](device-restrictions-android-for-work.md).

Applies to: Android Enterprise dedicated devices running in multi-app kiosk mode

#### Create and use OEMConfig device configuration profiles in Intune <!-- 3305883  -->
In this update, Intune supports configuring Android Enterprise devices with OEMConfig. Specifically, you can create a device configuration profile, and apply settings to Android Enterprise devices using OEMConfig (**Device configuration** > **Profiles** > **Create profile** > **Android enterprise** for platform).

Support for OEMs is currently on a per-OEM basis. If an OEMConfig app you want isn't available in the list of OEMConfig apps, contact `IntuneOEMConfig@microsoft.com`.

To learn more about this feature, go to [Use and manage Android Enterprise devices with OEMConfig in Microsoft Intune](android-oem-configuration-overview.md).

Applies to: Android enterprise

#### Windows Update notifications  <!-- 3316758, 3316782  -->
We've added two *User experience settings* to the Windows Update ring configurations that you can manage from within the Intune console. You can now:
- Block or allow users to [scan for Windows updates](windows-update-settings.md#block-user-from-scanning-for-windows-updates).
- Manage the [Windows Update notification level](windows-update-settings.md#windows-update-notification-level) that users see.

#### New device restriction settings for Android Enterprise, Device Owner <!-- 3574254  -->
On Android Enterprise devices, you can create a device restriction profile to allow or restrict features, set password rules, and more (**Device configuration** > **Profiles** > **Create profile** > choose **Android Enterprise** for platform > **Device owner only > Device restrictions** for profile type). 

This update includes new password settings, allows full access to apps in Google Play Store for fully managed devices, and more. To see the current list of settings, go to [Android Enterprise device settings to allow or restrict features](device-restrictions-android-for-work.md). 

Applies to: Android Enterprise fully managed devices

#### Check for a TPM chipset in a Windows 10 device compliance policy <!-- 3617671 -->

This feature is delayed and is planned to be released later.

#### Updated UI changes for Microsoft Edge Browser on Windows 10 and later devices <!-- 3775833   -->
When you create a device configuration profile, you can allow or restrict Microsoft Edge features on Windows 10 and later devices (**Device configuration** > **Profiles** > **Create profile** > **Windows 10 and later** for platform,  > **Device restrictions** for profile type > **Microsoft Edge Browser**). In this update, the Microsoft Edge settings are more descriptive, and easier to understand. 

To see these features, go to [Microsoft Edge Browser device restriction settings](device-restrictions-windows-10.md#microsoft-edge-browser).

Applies to: Windows 10 and later

#### Expanded support for Android Enterprise fully managed devices  (Preview)  <!--   3903241, 3903244, 3903246   -->
Still in a public preview, we've expanded our support of Android Enterprise fully managed devices ([first announced in January of 2019](whats-new.md#week-of-january-14-2019) to include the following: 

- On fully managed and dedicated devices, you can create [compliance policies](compliance-policy-create-android-for-work.md) to include password rules and operating system requirements (**Device compliance** > **Policies** > **Create policy** > **Android Enterprise** for platform > **Device owner** for profile type). 

  On dedicated devices, the device may show as **Not compliant**. Conditional Access isn't available on dedicated devices. Be sure to complete any tasks or actions to get dedicated devices compliant with your assigned policies.

- [Conditional Access](conditional-access.md) - Conditional Access policies that apply to Android also apply to Android Enterprise fully managed devices. Users can now register their fully managed device in Azure Active Directory using the **Microsoft Intune app**. Then, see and resolve any compliance issues to access organizational resources.

- New end user app (Microsoft Intune app) - There is a new end user app for Android fully managed devices called **Microsoft Intune**. This new app is light-weight and modern, and provides similar functionally as the Company Portal app, but for fully managed devices. For more information, see [Microsoft Intune app on Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune).

To set up Android fully managed devices, go to **Device enrollment** > **Android enrollment** > **Corporate-owned, fully managed user devices**. Support for fully managed Android devices remains in preview, and some Intune features might not be fully functional.  

To learn more about this preview, see our blog, [Microsoft Intune - Preview 2 for Android Enterprise Fully Managed devices](https://aka.ms/preview2_AE_fullymanaged).


### Device enrollment

#### Configure profile to skip some screens during Setup Assistant <!-- 2276470  wnstaged-->
When you create a macOS enrollment profile, you can configure it to skip any of the following screens when a user goes through the Setup Assistant:
- Appearance
- Display Tone
- iCloudStorage
If you create a new profile or edit a profile, the selected skip screens need to sync with the Apple MDM server.  Users can issue a manual sync of the devices so that there is no delay in picking up the profile changes.
For more information, see [Automatically enroll macOS devices with the Device Enrollment Program or Apple School Manager](device-enrollment-program-enroll-macos.md).

#### Bulk device naming when enrolling corporate iOS devices<!--3566569  -->
When using one of Apple's corporate enrollment methods (DEP/ABM/ASM), you can set a device name format to automatically name incoming iOS devices. You can specify a format that includes the device type and serial number in your template. To do so, choose **Intune** > **Device enrollment** > **Apple enrollment** > **Enrollment program tokens** > **Select a token** >**Create profile** > **Device naming format**. You can edit existing profiles, but only newly synced devices will have the name applied.

#### Updated default timeout message on Enrollment Status Page <!-- 3959331 -->
We've updated the default timeout message users see when the Enrollment Status Page (ESP) exceeds the timeout value specified in the ESP profile. The new default message is what users see and helps them understand the next actions to take with their ESP deployment.  

### Device management

#### Retire noncompliant devices  <!-- 1827291   -->
This feature has been delayed and is planned for a future release.


### Monitor and troubleshoot

#### Intune Data Warehouse V1.0 changes reflecting back to beta <!-- 4403765 -->
When V1.0 was first introduced in 1808, it differed in some significant ways from the beta API. In 1903 those changes will be reflected back into the beta API version. If you have important reports that use the beta API version, we strongly recommend switching those reports to V1.0 to avoid breaking changes. For more information, see [Change log for the Intune Data Warehouse API](reports-changelog.md#1903-part-2).

#### Monitor Security Baseline status (public preview) <!-- 3082047 --> 
We've added a [per-category view](security-baselines-monitor.md#per-category-view) to the monitoring of security baselines. (Security baselines remain in preview). The per-category view displays each category from the baseline along with the percentage of devices that fall into each status group for that category. You can now see how many devices don't match the individual categories, are misconfigured, or are not applicable.

### Role-based access control

#### Scope tags for Apple VPP tokens <!--2371886  -->
You can now add scope tags to Apple VPP tokens. Only users assigned with the same scope tag will have access to the Apple VPP token with that tag. VPP apps and ebooks purchased with that token inherit its scope tags. For more information about scope tags, see [Use RBAC and scope tags](scope-tags.md).







## Week of April 1, 2019

### Device configuration

#### Updated certificate connectors  <!-- ICM 113304612 -->
We’ve released updates for both the [Intune Certificate Connector and the PFX Certificate Connector for Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors). The new releases fix several known issues.  

### App management

#### User experience update for the Company Portal app for iOS <!-- 2536024 -->
The home page of the Company Portal app for iOS devices has been redesigned. With this change, the home page will better follow iOS UI patterns, and also provide improved discoverability for apps and ebooks.

#### Changes to Company Portal enrollment for iOS 12 device users <!--3448635 -->  
The Company Portal for iOS enrollment screens and steps have been updated to align with the MDM enrollment changes released in Apple iOS 12.2. The updated workflow prompts users to:  

* Allow Safari to open the Company Portal website and download the management profile before returning to the Company Portal app.  
* Open the Settings app to install the management profile on their device.
* Return to the Company Portal app to complete enrollment.  

For updated enrollment steps and screens, see [Enroll iOS device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).  

## Week of March 25, 2019

### Monitor and troubleshoot

### Support for the Power BI Compliance app from the Data Warehouse blade in Microsoft Intune <!-- 4260871 -->
Previously, the **Download Power BI file** link in the **Intune Data Warehouse** blade downloaded an Intune Data Warehouse report (.pbix file). This report has been replaced with the Power BI Compliance app. The Power BI Compliance app will not require special loading or setup. It will open directly in the Power BI online portal and display data specifically for your Intune tenant based on your credentials. In Intune, select the **Set up Intune Data Warehouse** link on the right side of the Intune blade. Then, click **Get Power BI App**. For more information, see [Connect to the Data Warehouse with Power BI](reports-proc-get-a-link-powerbi.md).

## Week of March 18, 2019

### App management

#### Deploy Microsoft Visio and Microsoft Project <!-- 3725386  -->
You can now deploy Microsoft Visio Pro for Office 365 and Microsoft Project Online Desktop Client as independent apps to Windows 10 devices using Microsoft Intune, if you own licenses for these apps. From Intune, select **Client apps** > **Apps** > **Add** to display the **Add app** blade. On the **Add app** blade, select **Windows 10** as the **App type**. Then, select **Configure App Suite** to select apps to install. For more information about Office 365 apps for Windows 10 devices, see [Assign Office 365 apps to Windows 10 devices with Microsoft Intune](apps-add-office365.md).

#### Microsoft Visio Pro for Office 365 product name change <!-- 3593653  -->
**Microsoft Visio Pro for Office 365** will now be known as **Microsoft Visio Online Plan 2**.  For more information about Microsoft Visio, see [Visio Online Plan 2](https://products.office.com/visio/visio-online-plan-2). For more information about Office 365 apps for Windows 10 devices, see [Assign Office 365 apps to Windows 10 devices with Microsoft Intune](apps-add-office365.md).

#### Intune app protection policy (APP) character limit setting <!-- 3291302  -->
Intune admins can specify an exception to the Intune APP  **Restrict cut, copy, and paste with other apps** policy setting.  As the admin, you can specify the number of characters that may be cut or copied from a managed app. This setting will allow sharing of the specified number of characters to any app, regardless of the "Restrict cut, copy, and paste with other apps" setting. Note that the Intune Company Portal app version for Android requires version 5.0.4364.0 or later. For more information, see [iOS data protection](app-protection-policy-settings-ios.md#data-protection), [Android data protection](app-protection-policy-settings-android.md#data-protection), and [Review client app protection logs](app-protection-policy-settings-log.md#app-protection-policy-settings).

#### Office Deployment Tool (ODT) XML for Office ProPlus deployment <!-- 3192477   -->
You will be able to provide Office Deployment Tool (ODT) XML when creating an instance of Office Pro Plus in the Intune admin console. This will allow greater customizability if the existing Intune UI options do not meet your needs. For more information, see [Assign Office 365 apps to Windows 10 devices with Microsoft Intune](https://docs.microsoft.com/intune/apps-add-office365) and [Configuration options for the Office Deployment Tool](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

#### App icons will now be displayed with an automatically generated background <!-- 1429026  -->
In the Windows Company Portal app, app icons will now be displayed with an automatically generated background based on the dominant color of the icon (if it can be detected). When applicable, this background will replace the gray border that was previously visible on app tiles. Users will see this change in versions of Company Portal later than 10.3.3451.0.

#### Install available apps using the Company Portal app after Windows bulk enrollment <!-- 2751523   -->
Windows devices that enrolled into Intune using [Windows bulk enrollment](windows-bulk-enroll.md) (provisioning packages) will be able to use the Company Portal app to install available apps. For more information about the Company Portal app, see [Manually add the Windows 10 Company Portal](store-apps-company-portal-app.md) and [How to configure the Microsoft Intune Company Portal app](company-portal-app.md).

#### The Microsoft Teams app can be selected as part of the Office app suite <!-- 3828932  -->
The Microsoft Teams app can be included or excluded as part of the Office Pro Plus app suite installation. This feature works for Office Pro Plus build number 16.0.11328.20116+. The user must sign out and then sign in to the device for the installation to complete. In Intune, select **Client apps** > **Apps** > **Add**. Select one of the **Office 365 Suite** app types and then select **Configure  App Suite**.

### Device configuration

#### Automatically start an app when running multiple apps in kiosk mode on Windows 10 and later devices <!-- 2351390 -->

On Windows 10 and later devices, you can run a device in kiosk mode, and run many apps. In this update, there's an **AutoLaunch** setting (**Device configuration** > **Profiles** > **Create profile** > **Windows 10 and later** for platform > **Kiosk** for profile type > **Multi-app kiosk**). Use this setting to automatically start an app when the user signs in to the device.

To see a list and description of all the kiosk settings, see [Windows 10 and later device settings to run as a kiosk in Intune](kiosk-settings-windows.md).

Applies to: Windows 10 and later

#### Operational logs also show details on non-compliant devices <!-- 4063755  -->
When routing Intune logs to Azure monitor features, you can also route the operational logs. In this update, the operational logs also provide information on non-compliant devices. 

For more information on this feature, see [Send log data to storage, event hubs, or log analytics in Intune](review-logs-using-azure-monitor.md).

#### Route logs to Azure Monitor in more Intune workloads <!-- 3804627 -->
In Intune, you can route audit and operational logs to events hubs, storage, and log analytics in Azure Monitor (**Intune** > **Monitoring** > **Diagnostics settings**). In this update, you can route these logs in more Intune workloads, including compliance, configurations, client apps, and more. 

To learn more about routing logs to Azure Monitor, see [send log data to storage, event hubs, or log analytics](review-logs-using-azure-monitor.md).

#### Create and use mobility extensions on Android Zebra devices in Intune <!-- 3305880   -->
In this update, Intune supports configuring Android Zebra devices. Specifically, you can create a device configuration profile, and apply settings to Android Zebra devices using Mobility Extensions (MX) profiles generated by StageNow (**Device configuration** > **Profiles** > **Create profile** > **Android** for platform > **MX profile (Zebra only)** for profile type).

For more information on this feature, see [Use and manage Zebra devices with mobility extensions in Intune](android-zebra-mx-overview.md).

Applies to: Android

### Device management

#### Encryption report for Windows 10 Devices (in public preview)<!-- 2351538 -->  
Use the new [Encryption report (Preview)](encryption-monitor.md) to view details about the encryption status of your Windows 10 devices. Available details include a devices TPM version, encryption readiness and status, error reporting, and more.  

#### Access BitLocker recovery keys from the Intune portal (in public preview) <!-- 2351547   -->  
You can now use Intune to [view details](encryption-monitor.md) about BitLocker Key ID and BitLocker recovery keys, from Azure Active Directory.

#### Microsoft Edge support for Intune scenarios on iOS and Android devices <!-- 3411007 -->
Microsoft Edge will support all of the same management scenarios as the Intune Managed Browser with the addition of improvements to end user experience. Microsoft Edge enterprise features that are enabled by Intune policies include dual-Identity, app protection policy integration, Azure application proxy integration, and managed favorites and home page shortcuts. For more information, see [Microsoft Edge support](app-configuration-managed-browser.md#microsoft-edge-support).

#### Exchange Online/Intune Connector deprecate support for EAS only devices <!--3105122  -->
The Intune console no longer supports viewing and managing EAS-only devices connected to Exchange Online with the Intune Connector. Instead, you have the following options:
- Enroll devices in Mobile Device Management (MDM)
- Use Intune App Protection Policies to manage your devices
- Use Exchange controls as outlined in [Clients and mobile in Exchange Online](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)

### Search the All devices page for an exact device by using [name] <!--4254930 -->
You can now search for an exact device name. Go to **Intune** > **Devices** > **All devices** > in the search box, surround the device name with {} to search for an exact match. For example, **{Device12345}**.

### Monitor and troubleshoot

#### Support for additional connectors on the Tenant Status page <!-- 3617202  -->
The [Tenant Status page](tenant-status.md) now displays status information for additional connectors, including *Windows Defender Advanced Threat Protection* (ATP) and other Mobile Threat Defense connectors.

### Role-based access control

#### Granting Intune read only access to some Azure Active Directory roles <!-- 3637917  -->
Intune read only access has been granted to the following Azure AD roles. Permissions granted with Azure AD roles supersede permissions granted with Intune role-based access control (RBAC).

Read only access to Intune audit data:

- Compliance Administrator
- Compliance Data Administrator

Read only access to all Intune data:

- Security Administrator
- Security Operator
- Security Reader

For more information, see [Role-based access control](role-based-access-control.md).

#### Scope tags for iOS app provisioning profiles <!--2934430   -->
You can add a scope tag to an iOS app provisioning profile so that only people with roles also assigned that scope tag have access to the iOS app provisioning profile. For more information, see [Use RBAC and scope tags](scope-tags.md).

#### Scope tags for app configuration policies <!--2371891   -->
You can add a scope tag to an app configuration policy so that only people with roles also assigned that scope tag have access to the app configuration policy. The app configuration policy can only be targeted to or associated with apps assigned the same scope tag. For more information, see [Use RBAC and scope tags](scope-tags.md).

### Microsoft Edge support for Intune scenarios on iOS and Android devices <!-- 3411007 -->
Microsoft Edge will support all of the same management scenarios as the Intune Managed Browser with the addition of improvements to the end-user experience. Microsoft Edge enterprise features that are enabled by Intune policies include dual-Identity, app protection policy integration, Azure application proxy integration, and managed favorites and home page shortcuts. For more information, see [Microsoft Edge support](app-configuration-managed-browser.md#microsoft-edge-support).

## Week of February 25, 2019

### Device configuration

#### Intune PowerShell module <!-- 951068  -->
The Intune PowerShell module, which provides support for the Intune API through Microsoft Graph, is now available in the [Microsoft PowerShell Gallery](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10).

- [Details about how use this module](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [Scenario examples using this module](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### Improved support for delivery optimization  <!--3183757  -->
We've expanded the support in Intune for configuring delivery optimization. You can now configure an expanded list of [Delivery Optimization settings](delivery-optimization-settings.md) and target it to your devices right from Intune console.


## Week of February 18, 2019

### App management

#### Intune will leverage Google Play Protect APIs on Android devices <!-- 2577355   -->
Some IT admins are faced with a BYOD landscape where end users may end up rooting or jailbreaking their mobile phone. This behavior, while sometimes not ill-intentioned, results in a bypass of many Intune policies that are set in order to protect the organization's data on end user devices. Thus, Intune provides root and jailbreak detection for both enrolled and unenrolled devices. With this release, Intune will now leverage Google Play Protect APIs to add to our existing root detection checks for unenrolled devices. While Google does not share the entirety of the root detection checks that occur, we expect these APIs to detect users who have rooted their devices for any reason from device customization to being able to get newer OS updates on older devices. These users can then be blocked from accessing corporate data, or their corporate accounts can be wiped from their policy enabled apps. For additional value, the IT admin will now have several reporting updates within the Intune App Protection blade - the "Flagged Users" report will show which users are detected via Google Play Protect's SafetyNet API scan, the "Potentially Harmful Apps" report will show which apps are detected via Google's Verify Apps API scanning. This feature is available on Android.

#### Win32 app information available in Troubleshooting blade <!-- 2617342   -->
You can now collect failure log files for a Win32 app installation from the Intune app **Troubleshooting** blade. For more information about app installation troubleshooting, see [Troubleshoot app installation issues](troubleshoot-app-install.md) and [Troubleshoot Win32 app issues](apps-win32-app-management.md#troubleshoot-win32-app-issues).

#### App status details for iOS apps <!-- 3761235   -->
There are new app installation error messages related to the following:
- Failure for VPP apps when installing on shared iPad
- Failure when app store is disabled
- Failure to find VPP license for app
- Failure to install system apps with MDM provider
- Failure to install apps when device is in lost mode or kiosk mode
- Failure to install app when user is not signed in to the App Store

In Intune, select **Client apps** > **Apps** > "App name" > **Device install status**. New error messages will be available in the **Status details** column.

#### New App categories screen in the Company Portal app for Windows 10<!-- 3834780  -->
A new screen called **App categories** has been added to improve the app browsing and selection experience in Company Portal for Windows 10. Users will now see their apps sorted under categories such as **Featured**, **Education**, and **Productivity**. This change appears in Company Portal versions 10.3.3451.0 and later. To view the new screen, see [What's new in the app UI](https://docs.microsoft.com/intune/whats-new-app-ui). For more information about apps in the Company Portal, see [Install and share apps on your device](/intune-user-help/install-apps-cpapp-windows).  

#### Power BI Compliance app <!-- 1455231 doc-work-item -->
Access your Intune Data Warehouse in Power BI Online using the [Intune Compliance (Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) app. With this Power BI app, you can now access and share pre-created reports without any setup and without leaving your web browser. For additional information, see [Change log - Power BI Compliance app](reports-changelog.md#power-bi-compliance-app).


### Device configuration

#### PowerShell scripts can run in a 64-bit host on 64-bit devices <!-- 1862675   -->
When you add a PowerShell script to a device configuration profile, the script always executes in 32-bit, even on 64-bit operating systems. With this update, an administrator can run the script in a 64-bit PowerShell host on 64-bit devices (**Device configuration** > **PowerShell scripts** > **Add** > **Configure** > **Run script in 64 bit PowerShell Host**).

For more details on using PowerShell, see [PowerShell scripts in Intune](intune-management-extension.md).

Applies to:
Windows 10 and later

#### macOS users are prompted to update their password <!-- 1873216 -->
Intune is enforcing the **ChangeAtNextAuth** setting on macOS devices. This setting impacts end-users and devices that have compliance password policies or device restriction password profiles. End users are prompted once to update their password. This prompt happens whenever a user first runs a task that requires authentication, such as signing in to the device. Users can also be prompted to update their password when doing anything that requires administrative privileges, such as requesting keychain access. 

Any new or existing password policy changes by the administrator prompts end users again to update their password.

Applies to:  
macOS

#### Assign SCEP certificates to a userless macOS device  <!-- 2340521  -->
You can assign Simple Certificate Enrollment Protocol (SCEP) certificates using device attributes to macOS devices, including devices without user affinity, and associate the certificate profile with Wi-Fi or VPN profiles. This expands the support we already have to [assign SCEP certificates to devices with and without user affinity](certificates-scep-configure.md#create-a-scep-certificate-profile) that run Windows, iOS, and Android.  This update adds the option to select a Certificate type of *Device* when you configure a SCEP certificate profile for the macOS.

Applies to: 
- macOS

#### Intune Conditional Access UI update   <!-- 2432313   -->
We've made improvements to the UI for Conditional Access in the Intune console. These include:
-  Replaced the Intune *Conditional Access* blade with the blade from Azure Active Directory. This ensures you'll have access to the full range of settings and configurations for [Conditional Access](conditional-access.md) (which remains an Azure AD technology), from within the Intune console. 
- We've renamed the *On-premises access* blade to *Exchange access*, and relocated the *Exchange service connector* setup to this renamed blade.  This change consolidates where you [configure and monitor details related to Exchange online and on-premises](exchange-connector-install.md).  

#### Kiosk Browser and Microsoft Edge Browser apps can run on Windows 10 devices in kiosk mode <!-- 2935135   -->
You can use Windows 10 devices in kiosk mode to run one app, or many apps. This update includes several changes to using browser apps in kiosk mode, including:

- Add the Microsoft Edge Browser or Kiosk Browser to run as apps on the kiosk device (**Device configuration** > **Profiles** > **New profile** > **Windows 10 and later** for platform > **Kiosk** for profile type).
- New features and settings are available to allow or restrict (**Device configuration** > **Profiles** > **New profile** > **Windows 10 and later** for platform > **Device restrictions** for profile type), including:

  - Microsoft Edge Browser:​
  - Use Microsoft Edge kiosk mode​
  - Refresh browser after idle time​
​
 - Favorites and search:​
  - Allow changes to search engine

For a list of these settings, see:

- [Windows 10 and later device settings to run as a kiosk](kiosk-settings-windows.md)
- [Microsoft Edge Browser device restrictions](device-restrictions-windows-10.md#microsoft-edge-browser)
- [Favorites and search device restrictions](device-restrictions-windows-10.md##favorites-and-search)

Applies to:
Windows 10 and later

#### New device restriction settings for iOS and macOS devices <!-- 3448774   -->
You can restrict some settings and features on devices running iOS and macOS (**Device configuration** > **Profiles** > **New profile** > **iOS** or **macOS** for platform > **Device restrictions** for profile type). This update adds more features and settings you can control, including setting screen time, changing eSIM settings and cellular plans, and more on iOS devices. Also, delaying the user's visibility of software updates and blocking content caching on macOS devices. 

To see the features and settings you can restrict, see:

- [iOS device restriction settings](device-restrictions-ios.md)
- [macOS device restriction settings](device-restrictions-macos.md)

Applies to:

- iOS
- macOS

#### "Kiosk" devices are now called "Dedicated devices" on Android Enterprise devices <!-- 3598402   -->
To align with Android terminology, **kiosk** is changed to **dedicated devices** for Android enterprise devices (**Device configuration** > **Profiles** > **Create profile** > **Android enterprise for platform > **Device Owner Only** > **Device Restrictions** > **Dedicated devices**).

To see the available settings, go to [Device settings to allow or restrict features](device-restrictions-android-for-work.md#dedicated-device-settings).

Applies to:  
Android Enterprise

#### Safari and Delaying user software update visibility iOS settings are moving in the Intune UI <!-- 3640850, 3803313   -->
For iOS devices, you can set Safari settings and configure Software Updates. In this update, these settings are moving to different parts of the Intune UI:

- The Safari settings moved from **Safari** (**Device configuration** > **Profiles** > **New profile** > **iOS** for platform > **Device restrictions** for profile type) to **[Built-in Apps](device-restrictions-ios.md#built-in-apps)**.
- The **Delaying user software update visibility for supervised iOS devices** setting (**Software updates** > **Update policies for iOS**) is moving to **Device restrictions** > **[General](device-restrictions-ios.md#general)**.  For details on the impact to existing policies, see [iOS software updates](software-updates-ios.md#configure-the-policy). 

For a list of the settings, see:

- [iOS device restrictions](device-restrictions-ios.md) 
- [iOS software updates](software-updates-ios.md)

This feature applies to: 

- iOS

#### Enabling restrictions in the device settings is renamed to Screen Time on iOS devices <!-- 3699164   -->
You can configure the **Enabling restrictions in the device settings** on supervised iOS devices (**Device configuration** > **Profiles** > **New profile** > **iOS** for platform > **Device restrictions** for profile type > **General**). In this update, this setting is renamed to **Screen Time (supervised only)**. 

The behavior is the same. Specifically: 

- iOS 11.4.1 and earlier: **Block** prevents end users from setting their own restrictions in the device settings. 
- iOS 12.0 and later: **Block** prevents end users from setting their own **Screen Time** in the device settings, including content & privacy restrictions. Devices upgraded to iOS 12.0 won't see the restrictions tab in the device settings anymore. These settings are in **Screen Time**. 

For a list of the settings, see [iOS device restrictions](device-restrictions-ios.md#general).

Applies to: 
- iOS


### Device management

#### Rename an enrolled Windows device <!-- 1911112  -->
You can now rename an enrolled Windows 10 device (RS4 or later). To do, choose **Intune** > **Devices** > **All devices** > choose a device > **Rename device**. This feature does not currently support renaming hybrid Azure AD Windows devices.

#### Auto-assign scope tags to resources created by an admin with that scope <!-- 3173823  -->
When an admin creates a resource, any scope tags assigned to the admin will automatically be assigned to those new resources.

### Monitor and troubleshoot

#### Failed enrollment report moves to the Device Enrollment blade <!-- 3560202  -->
The **Failed enrollments** report has been moved to the **Monitor** section of the **Device enrollment** blade. Two new columns (Enrollment Method and OS Version) have been added.

#### Company Portal abandonment report renamed to Incomplete user enrollments <!--3815076 eemiss -->
The **Company Portal abandonment** report has been renamed to **Incomplete user enrollments**.


<!-- ########################## -->
## Week of February 4, 2019

### App management

#### Intune macOS Company Portal Dark Mode <!-- 3300524  -->
The Intune macOS Company Portal now supports Dark Mode for macOS. When you enable Dark Mode on a macOS 10.14+ device, the Company Portal will adjust its appearance to colors that reflect that mode.

<!-- ########################## -->
## Week of January 21, 2019

### App management

#### Toast notifications for Win32 apps <!-- 3136566   -->
You can suppress showing end user toast notifications per app assignment. From Intune, select **Client apps** > **Apps** > select the app > **Assignments** > **Include Groups**. 

#### Intune app protection policies UI update <!-- 3251427  -->
We’ve changed the labels for settings and buttons for Intune app protection to make each easier to understand. Some of the changes include:  
- Controls are changed from **yes** / **no** controls to primarily **block** / **allow** and **disable** / **enable** controls. The labels are also updated.  
- Settings are reformatted, so the setting and its label are side-by-side in the control, to provide better navigation.   

The default settings and number of settings remain the same, but this change allows the user to understand, navigate, and utilize the settings more easily to apply selected app protection policies. For information, see [iOS settings](app-protection-policy-settings-ios.md) and [Android settings](app-protection-policy-settings-android.md).

### Additional settings for Outlook <!-- 3301182  -->
You can now configure the following additional settings for Outlook for iOS and Android using Intune:

- Only allow work or school accounts to be used in Outlook in iOS and Android
- Deploy modern authentication for Office 365 and hybrid modern authentication on-premises accounts
- Use `SAMAccountName` for the username field in the email profile when basic authentication is selected
- Allow contacts to be saved
- Configure external recipients MailTips
- Configure **Focused Inbox**
- Require biometrics to access Outlook for iOS
- Block external images

> [!NOTE]
> If you are using Intune App Protection policies to manage access for corporate identities, you should consider not enabling **require biometrics**. For more information, see **Require corporate credentials for access** for [iOS Access Settings](app-protection-policy-settings-ios.md#access-requirements) and [Android Access Settings](app-protection-policy-settings-android.md#access-requirements).

For more information, see [Microsoft Outlook configuration settings](app-configuration-policies-outlook.md).

#### Delete Android Enterprise apps <!-- 1352553 -->
You can delete managed Google Play apps from Microsoft Intune. To delete a managed Google Play app, open Microsoft Intune in the Azure portal and select **Client apps** > **Apps**. From the app list, select the ellipses (...) to the right of the managed Google Play app, then select **Delete** from the displayed list. When you delete a managed Google Play app from the app list, the managed Google Play app is automatically unapproved.

#### Managed Google Play app type <!-- 1352580 -->
The **managed Google Play** app type will allow you to specifically add [managed Google Play apps](https://play.google.com/work/search?q=microsoft&c=apps) to Intune. As the Intune admin, you can now browse, search, approve, sync and assign approved managed Google Play apps within Intune.  You no longer need to browse to the managed Google Play console separately, and you no longer have to reauthenticate.  In Intune, select **Client apps** > **Apps** > **Add**. In the **App type** list, select **Managed Google Play** as the app type.

### Default Android PIN keyboard <!-- 3802457 -->
For end users who have set an Intune App Protection Policy (APP) PIN on their Android devices with PIN type of 'Numeric', they will now see the default Android keyboard instead of the fixed Android keyboard UI that was previously designed. This change was made to be consistent when using default keyboards on both Android and iOS, for both PIN types of 'Numeric' and/or 'Passcode'. For more information about end user Access settings on Android, such as APP PIN, see [Android access requirements](app-protection-policy-settings-android.md#access-requirements).

### Device configuration

#### Use Microsoft-recommended settings with Security Baselines (Public Preview) <!-- 2055484   -->

Intune integrates with other services that focus on security, including Windows Defender ATP and Office 365 ATP. Customers are asking for a common strategy and a cohesive set of end-to-end security workflows across the Microsoft 365 services. Our goal is to align strategies to build solutions that bridge security operations and common administrator tasks. 
In Intune, we aim to accomplish this goal by publishing a set of Microsoft recommended “Security baselines” (**Intune** > **Security baselines**).  An administrator can create security policies directly from these baselines, and then deploy them to their users. You can also customize the best practice recommendations to meet the needs of your organization. Intune makes sure that devices stay in compliance with these baselines, and notifies administrators of users or devices that aren't in compliance.

This feature is in public preview so any profiles created now will not move over to Security Baselines templates that are generally available (GA). You shouldn’t plan to use these preview templates in your production environment.

To learn more about security baselines, see [Create a Windows 10 security baseline in Intune](security-baselines-monitor.md).

This feature applies to:
Windows 10 and later

#### Non-Administrators can enable BitLocker on Windows 10 devices joined to Azure AD<!-- 2147379   -->​
When you enable BitLocker settings on Windows 10 devices (**Device configuration** > **Profiles** > **Create profile** > **Windows 10 and later** for platform > **Endpoint protection** for profile type > **Windows Encryption**), you add BitLocker settings. ​
​
This update includes a new BitLocker setting to allow standard users (non-administrators) to enable encryption. ​
​
To see the settings, go to [Endpoint protection settings for Windows 10](endpoint-protection-windows-10.md#windows-encryption).​

#### Check for Configuration Manager compliance <!-- 2192052  eepublished  -->
This update includes a new System Center Configuration Manager compliance setting (**Device compliance** > **Policies** > **Create policy** > **Windows 10 and later** > **Configuration Manager Compliance**). Configuration Manager sends signals to Intune compliance. Using this setting, you can require all Configuration Manager signals to return "compliant".

For example, you require all software updates to be installed on devices. In Configuration Manager, this requirement has the “Installed” state. If any programs on the device are in unknown state, then the device is non-compliant in Intune.

[Configuration Manager Compliance](compliance-policy-create-windows.md#configuration-manager-compliance) describes this setting.

Applies to: 
Windows 10 and later

#### Customize wallpaper on supervised iOS devices using a device configuration profile <!-- 2809324   -->
When you create a device configuration profile for iOS devices, you can customize some features (**Device configuration** > **Profiles** > **Create profile** > **iOS** for platform > **Device features** for profile type). This update includes new **Wallpaper** settings that allow an Administrator to use a .png, .jpg, or .jpeg image on the home screen or lock screen. These wallpaper settings apply only to supervised devices. 

For a list of these settings, see [iOS device feature settings](ios-device-features-settings.md).

#### Windows 10 kiosk is generally available <!-- 3594661  -->
In this update, the Kiosk feature on Windows 10 and later devices is generally available (GA). To see all the settings you can add and configure, see [Kiosk settings for Windows 10 (and later)](kiosk-settings.md).

#### Contact Sharing via Bluetooth is removed in Device Restrictions > Device Owner for Android Enterprise <!-- 3598396   -->
When you create a device restrictions profile for Android Enterprise devices, there is a **Contact Sharing via Bluetooth** setting. In this update, the **Contact Sharing via Bluetooth** setting is removed (**Device configuration** > **Profiles** > **Create profile** > **Android Enterprise** for platform > **Device Restrictions > Device owner** for profile type > **General**). 

The **Contact Sharing via Bluetooth** setting isn't supported for Android Enterprise Device Owner management. So when this setting is removed, it won't impact any devices or tenants, even if this setting is enabled and configured in your environment.

To see the current list of settings, go to [Android Enterprise device settings to allow or restrict features](device-restrictions-android-for-work.md).

Applies to: Android Enterprise Device Owner

### Device management

#### Selective wipe support for WIP Without Enrollment devices <!-- 1434452 -->
Windows Information Protection Without Enrollment (WIP-WE) allows customers to protect their corporate data on Windows 10 devices without the need for full MDM enrollment. Once documents are protected with a WIP-WE policy, the protected data can be selectively wiped by an Intune administrator. By selecting the user and device, and sending a wipe request, all data that was protected via the WIP-WE policy will become unusable. From the Intune in the Azure portal, select **Mobile app** > **App selective wipe**.

### Monitor and troubleshoot

#### New operational logs, and ability to send logs to Azure Monitor services <!-- 3762211  -->
Intune has built-in audit logging that tracks events as changes are made. This update includes new logging features, including: 
- Operational logs (preview) that show details on users and devices that enrolled, including success and failed attempts.
- The audit logs and operational logs can be sent to Azure Monitor, including storage accounts, event hubs, and log analytics. These services allow you to store, use analytics such as Splunk and QRadar, and get visualizations of your logging data.

[Send log data to storage, event hubs, or log analytics in Intune](review-logs-using-azure-monitor.md) provides more information on this feature.

### Skip more Setup Assistant screens on an iOS DEP device <!-- 2687509  -->
In addition to the screens you can currently skip, you can set iOS DEP devices to skip the following screens in the Setup Assistant when a user enrolls the device: Display Tone, Privacy, Android Migration, Home Button, iMessage & FaceTime, Onboarding, Watch Migration, Appearance, Screen Time, Software Update, SIM Setup.
To choose which screens to skip, go to **Device enrollment** > **Apple enrollment** > **Enrollment program tokens** > choose a token > **Profiles** > choose a profile > **Properties** > **Setup Assistant customization** > choose **Hide** for any screens that you want to skip > **OK**.
If you create a new profile or edit a profile, the selected skip screens need to sync with the Apple MDM server. Users can issue a manual sync of the devices so that there is no delay in picking up the profile changes.

#### Android Enterprise APP-WE app deployment <!-- 1171203 -->
For Android devices in a non-enrolled App Protection Policy Without Enrollment (APP-WE) deployment scenario, you can now use managed Google Play to deploy store apps and LOB apps to users. Specifically, you can provide end users with an app catalog and installation experience that no longer requires end users to loosen the security posture of their devices by allowing installations from unknown sources. In addition, this deployment scenario will provide an improved end user experience.

<!-- ########################## -->
## Week of January 14, 2019

### Preview of support for Android corporate-owned, fully managed devices <!-- 1574342  -->
Intune now supports fully managed Android devices, a corporate-owned "device owner" scenario where devices are tightly managed by IT and are affiliated with individual users. This allows admins to manage the entire device, enforce an extended range of policy controls unavailable to work profiles, and restricts users to installing apps from managed Google Play only. For more information, see [Set up Intune enrollment of Android fully managed devices](android-fully-managed-enroll.md) and [Enroll your dedicated devices or fully managed devices](android-dedicated-devices-fully-managed-enroll.md).  Please note that this feature is in preview. Some Intune capabilities, such as certificates, compliance, and Conditional Access, are not currently available with Android fully managed user devices.

<!-- ########################## -->
## Week of January 7, 2019

### App management

#### Intune app PIN <!-- 2298397 -->
As the IT admin, you can now configure the number of days an end user can wait until their Intune app PIN must be changed. The new setting is *PIN reset after number of days* and is available in the Azure portal by selecting **Intune** > **Client apps** > **App protection policies** > **Create Policy** > **Settings** > **Access requirements**. Available for [iOS](app-protection-policy-settings-ios.md) and [Android](app-protection-policy-settings-android.md) devices, this feature supports a positive integer value.


#### Intune device reporting fields <!-- 2748738 -->
Intune provides additional device reporting fields, including App Registration ID, Android manufacturer, model, and security patch version, as well as iOS model. In Intune, these fields are available by selecting **Client apps** > **App protection status** and choosing **App Protection Report: iOS, Android**. In addition, these parameters will help you configure the **Allow** list for device manufacturer (Android), the **Allow** list for device model (Android and iOS), and the minimum Android security patch version setting. 


### Device configuration

#### Administrative templates are in public preview, and moved to their own configuration profile <!-- 3322847 -->

Administrative templates in Intune (**Device configuration** > **Administrative templates**) are currently in public preview. With this update:

- Administrative templates include about 300 settings that can be managed in Intune. Previously, these settings only existed in the group policy editor.
- Administrative templates are available in public preview.
- Administrative templates are moving from **Device configuration** > **Administrative templates** to **Device configuration** > **Profiles** > **Create profile** > in **Platform**, choose **Windows 10 and later** > in **Profile type**, choose **Administrative templates**.
- Reporting is enabled

To read more about this feature, go to [Windows 10 templates to configure group policy settings](administrative-templates-windows.md).

Applies to: Windows 10 and later

#### Use S/MIME to encrypt and sign multiple devices for a user  <!-- 1333642 -->
This update includes S/MIME email encryption using a new imported certificate profile (**Device configuration** > **Profiles** > **Create profile** > select the platform > **PKCS imported certificate** profile type). In Intune, you can import certificates in PFX format. Intune can then deliver those same certificates to multiple devices enrolled by a single user. This also includes:
- The native iOS email profile supports enabling S/MIME encryption using imported certificates in PFX format.
- The native mail app on Windows Phone 10 devices automatically use the S/MIME certificate.
- The private certificates can be delivered across multiple platforms. But, not all email apps support S/MIME.
- On other platforms, you may need to manually configure the mail app to enable S/MIME.  
- Email apps that support S/MIME encryption may handle retrieving certificates for S/MIME email encryption in a way that an MDM cannot support, such as reading from their publisher's certificate store.
For more information on this feature, see [S/MIME overview to sign and encrypt email](certificates-s-mime-encryption-sign.md).
Supported on: Windows, Windows Phone 10, macOS, iOS, Android

#### New options to automatically connect and persist rules when using DNS settings on Windows 10 and later devices <!-- 1333665, 2999078 -->
On Windows 10 and later devices, you can create a VPN configuration profile that includes a list of DNS servers to resolve domains, such as contoso.com. This update includes new settings for name resolution (**Device configuration** > **Profiles** > **Create profile** > Choose **Windows 10 and later** for platform > Choose **VPN** for profile type > **DNS settings** >**Add**): 
- **Automatically connect**: When **Enabled**, the device automatically connects to the VPN when a device contacts a domain you enter, such as contoso.com.
- **Persistent**: By default, all Name Resolution Policy table (NRPT) rules are active as long as the device is connected using this VPN profile. When this setting is **Enabled** on an NRPT rule, the rule remains active on the device, even when the VPN disconnects. The rule stays until the VPN profile is removed or until the rule is manually removed, which can be done using PowerShell.
[Windows 10 VPN settings](vpn-settings-windows-10.md) describes the settings. 

#### Use trusted network detection for VPN profiles on Windows 10 devices <!-- 1500165 -->​
​When using trusted network detection, you can prevent VPN profiles from automatically creating a VPN connection when the user is already on a trusted network. With this update, you can add DNS suffixes to enable trusted network detection on devices running Windows 10 and later (**Device configuration** > **Profiles** > **Create profile** > **Windows 10 and later** for platform > **VPN** for profile type).
​[Windows 10 VPN settings](vpn-settings-windows-10.md) lists the current VPN settings.​

#### Manage Windows Holographic for Business devices used by multiple users <!-- 1907917, 1063203 -->
Currently, you can configure shared PC settings on Windows 10 and Windows Holographic for Business devices using a custom OMA-URI setting. With this update, a new profile is added to configure shared device settings (**Device configuration** > **Profiles** > **Create Profile** > **Windows 10 and later** > **Shared multi-user device**).
To learn more about this feature, go to [Intune settings to manage shared devices](shared-user-device-settings.md).
Applies to: Windows 10 and later, Windows Holographic for Business

#### New Windows 10 Update settings <!--2626030  2512994  -->
For your [Windows 10 Update Rings](windows-update-for-business-configure.md), you can configure:
- **Automatic update behavior** - Use a new option, *Reset to default* to restore the original auto update settings on a Windows 10 machine on machines running the *October 2018 Update*
- **Block user from pausing Windows updates** - Configure a new Software updates setting that lets you block or allow your users to pause update installation from the *Settings* of their machines. 

#### iOS email profiles can use S/MIME signing and encryption <!-- 2662949 -->
You can create an email profile that includes different settings. This update includes S/MIME settings that can be used for signing and encrypting email communications on iOS devices (**Device configuration** > **Profiles** > **Create profile** > Choose **iOS** for platform > **Email** for profile type).
[iOS email configuration settings](email-settings-ios.md) lists the settings.

#### Some BitLocker settings support Windows 10 Pro edition<!-- 2727036 -->​
You can create a configuration profile that sets endpoint protection settings on Windows 10 devices, including BitLocker. This update adds support for Windows 10 Professional edition for some BitLocker settings. ​
To see these protection settings, go to [Endpoint protection settings for Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### Shared device configuration is renamed to Lock Screen Message for iOS devices in the Azure portal<!-- 2809362 -->
When you create a configuration profile for iOS devices, you can add **Shared Device Configuration** settings to show specific text on the lock screen. This update includes the following changes: 
- The **Shared Device Configuration** settings in the Azure portal are renamed to "Lock Screen Message (supervised only)" (**Device configuration** > **Profiles** > **Create profile** > Choose **iOS** for platform > Choose **Device features** for profile type > **Lock Screen Message**).
- When adding lock screen messages, you can insert a serial number, a device name, or another device-specific value as a variable in **Asset tag information** and **Lock screen footnote**. For example, you can enter `Device name: {{devicename}}` or `Serial number is {{serialnumber}}` using curly brackets. [iOS tokens](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) lists the available tokens that can be used.
[Settings to display messages on the lock screen](shared-device-settings-ios.md) lists the settings.

#### New App Store, Doc Viewing, Gaming device restriction settings added to iOS devices <!-- 2827760-->
In **Device Configuration** > **Profiles** > **Create profile** > **iOS** for platform > **Device restrictions** for profile type > **App Store, Doc Viewing, Gaming**, the following settings are added: 
Allow managed apps to write contacts to unmanaged contacts accounts 
Allow unmanaged apps to read from managed contacts accounts 
To see these settings, go to [iOS device restrictions](device-restrictions-ios.md#app-store-doc-viewing-gaming).

#### New notification, hints, and keyguard settings to Android Enterprise device owner devices <!-- 3201839 3201843 -->
​This update includes several new features on Android Enterprise devices when running as device owner. To use these features, go to **Device Configuration** > **Profiles** > **Create profile** > In **Platform**, choose **Android Enterprise** > In **Profile type**, choose **Device owner only** > **Device Restrictions**.​

​New features include: ​

- Disable system notifications from showing, including incoming calls, system alerts, system errors, and more.
- Suggests skip starting tutorials and hints for apps that are opened the first time​.
- Disable advanced keyguard settings, such as the camera, notifications, fingerprint unlock, and more​.
​

To see the settings, go to [Android Enterprise device restriction settings](device-restrictions-android-for-work.md).​

#### Android enterprise device owner devices can use Always On VPN connections <!-- 3202194 -->
In this update, you can use Always-on VPN connections on Android enterprise device owner devices. Always-on VPN connections stay connected, or immediately reconnect when the user unlocks their device, when the device restarts, or when the wireless network changes. You can also put the connection in "lockdown" mode, which blocks all network traffic until the VPN connection is active.
You can enable Always-on VPN in **Device configuration** > **Profiles** > **Create profile** > **Android enterprise** for platform > **Device restrictions** for Device Owner Only > **Connectivity** settings. 
To see the settings, go to [Android Enterprise device restriction settings](device-restrictions-android-for-work.md).

#### New setting to end processes in Task manager on Windows 10 devices <!-- 3285177 --> 
This update includes a new setting to end processes using Task Manager on Windows 10 devices. Using a device configuration profile (**Device configuration** > **Profiles** > **Create profile** > In **Platform**, choose **Windows 10** > In **Profile type**, choose **Device restrictions** > **General** settings), you choose to allow or prevent this setting.
To see these settings, go to [Windows 10 device restriction settings](device-restrictions-windows-10.md).
Applies to: Windows 10 and later


### Device enrollment

#### More detailed enrollment restriction failure messaging <!-- 3111564 -->
More detailed error messages are available when enrollment restrictions are not met. To see these messages, go to **Intune** > **Troubleshoot** > and check the Enrollment Failures table. For more information, see the [enrollment failures list](help-desk-operators.md#enrollment-failure-reference).

### Monitor and troubleshoot

#### Tenant Status dashboard  <!-- 1124854 -->
The new [Tenant Status page](tenant-status.md) provides a single location where you can view status and related details for your tenant.  The dashboard is divided into four areas:
- **Tenant Details** - Displays information that includes your Tenant name and location, your MDM Authority, the total enrolled devices in your tenant, and your license counts. This section also lists the current service release for your tenant.
- **Connector Status** - Displays information about available connectors you have configured and can also list those which you have not yet enabled.  
   Based on the current state of each connector,  they are flagged as Healthy, Warning, or Unhealthy. Select a connector to drill through and view details or configure additional information for it.
-  **Intune Service Health** - Displays details about active incidents or outages for your tenant. The information in this section is retrieved directly from the Office Message Center.
-  **Intune News** - Displays active messages for your tenant. Messages include things like notifications when your tenant receives the latest Intune features.  The information in this section is retrieved directly from the Office Message Center.

#### New help and support experience in Company Portal for Windows 10 <!-- 1488939-->
The new Company Portal Help & support page helps users troubleshoot and request help for app and access problems. From the new page, they can email error and diagnostic log details and find their organization's Helpdesk details. They'll also find a FAQ section with links to the relevant Intune documentation. 

#### New Help and Support experience for Intune   <!-- #3307080 -->
We are rolling out the new Help and Support experience to all tenants over the next few days. This new experience is available for Intune and can be accessed when using the Intune blades in the [Azure portal](https://portal.azure.com/).
The new experience lets you describe your problem in your own words and receive troubleshooting insight and web-based remediation content. These solutions are offered via a rule-based machine learning algorithm, driven by user inquires. 
In addition to issue-specific guidance, you use the new case creation workflow to open a support case by email or phone. 
This new experience replaces the previous Help and Support experience of a static set of pre-selected options that are based on the area of the console you are in when you open Help and Support. 
For more information, see [How to get support for Microsoft Intune](get-support.md).

### Role-based access control

#### Scope tags for apps <!-- 1081941 -->
You can create scope tags to limit access for roles and apps. You can add a scope tag to an app so that only people with roles also assigned that scope tag have access to the app. Currently, apps added to Intune from managed Google Play or apps purchased using Apple Volume Purchase Program (VPP) can't be assigned scope tags (future support is planned). For more information, see [Use scope tags to filter policies](scope-tags.md).

<!-- ########################## -->
## Week of December 10, 2018

### App management

#### Updates for Application Transport Security <!-- 748318 -->

Microsoft Intune supports Transport Layer Security (TLS) 1.2+ to provide best-in-class encryption, to ensure Intune is more secure by default, and to align with other Microsoft services such as Microsoft Office 365. In order to meet this requirement, the iOS and macOS company portals will enforce Apple's updated Application Transport Security (ATS) requirements, which also require TLS 1.2+. ATS is used to enforce stricter security on all app communications over HTTPS. This change impacts Intune customers using the iOS and macOS Company Portal apps. For more information, see the [Intune support blog](https://aka.ms/compportalats).

#### The Intune App SDK will support 256-bit encryption keys <!-- 1832174 -->
The Intune App SDK for Android now uses 256-bit encryption keys when encryption is enabled by App Protection Policies. The SDK will continue to provide support of 128-bit keys for compatibility with content and apps that use older SDK versions.

### Microsoft Auto Update version 4.5.0 required for macOS devices <!-- 3503442 -->
To continue receiving updates for the Company Portal and other Office applications, macOS devices managed by Intune must upgrade to Microsoft Auto Update 4.5.0. Users might already have this version for their Office apps.

### Intune requires macOS 10.12 or later <!-- 2827778 -->
Intune now requires macOS version 10.12 or later. Devices using prior macOS versions can't use the Company Portal to enroll into Intune. To receive support assistance and new features, users must upgrade their device to macOS 10.12 or later and upgrade the Company Portal to the latest version.

<!-- ########################## -->
## Week of November 26, 2018

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

#### Select apps tracked on the Enrollment Status Page<!-- 2531007 -->
You can choose which apps are tracked on the enrollment status page. Until these apps are installed, the user can't use the device. For more information, see [Set up an enrollment status page](windows-enrollment-status.md).

#### Search for Autopilot device by serial number <!--2595788 -->
You can now search for Autopilot devices by serial number. To do so, choose **Device enrollment** > **Windows enrollment** > **Devices** > type a serial number in the **Search by serial number** box > press Enter.

#### Track installation of Office ProPlus <!--2620217 -->
Users can track the installation progress of [Office ProPlus](apps-add-office365.md) using the [Enrollment Status Page](windows-enrollment-status.md). For more information, see [Set up an enrollment status page](windows-enrollment-status.md).

#### Alerts for expiring VPP token or Company Portal license running low <!-- 2237572 -->
If you are using Volume Purchase Program (VPP) to pre-provision the Company Portal during DEP enrollment, Intune will alert you when the VPP token is about to expire and when the licenses for the Company Portal are running low.

### macOS Device Enrollment Program support for Apple School Manager accounts <!--3006133 -->
Intune now supports using the Device Enrollment Program on macOS devices for Apple School Manager accounts.  For more information, see [Automatically enroll macOS devices with Apple School Manager or Device Enrollment Program](device-enrollment-program-enroll-macos.md).

### New Intune device subscription SKU <!--3312071-->
To help lower the cost of managing devices in enterprises, a new device-based subscription SKU is now available. This Intune device SKU is licensed per device on a monthly basis. Price varies by the licensing program. It's available directly through the Microsoft 365 admin center, and through the [Enterprise Agreement](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2) (EA), [Microsoft Products and Services Agreement](https://www.microsoft.com/licensing/mpsa/default) (MPSA), [Microsoft Open Agreements](https://partner.microsoft.com/licensing/licensing-agreements), and [Cloud Solution Provider](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP).

### Device management

#### Temporarily pause kiosk mode on Android devices to make changes <!-- 3041935 -->
When using Android devices in multi-app kiosk mode, an IT administrator may need to make changes to the device. This update includes new multi-app kiosk settings that allows an IT Administrator to temporarily pause kiosk-mode using a PIN, and get access to the entire device.
To see the kiosk settings, see [Android Enterprise device restrictions](device-restrictions-android-for-work.md).

#### Enable virtual home button on Android Enterprise kiosk devices  <!-- 3042021 -->
A new setting will allow users to tap a soft-key button on their device to switch between the Managed Home Screen app and other assigned apps on their multi-app kiosk device. This setting is particularly helpful in scenarios where a user's kiosk app does not respond appropriately to the "back" button. You'll be able to configure this setting for corporate-owned, single use Android devices. To enable or disable the **Virtual home button**, go to Intune in the Azure portal > Device configuration. Select a current device configuration profile or create a new one to edit its kiosk settings.
To see the kiosk settings, see [Android Enterprise device restrictions](device-restrictions-android-for-work.md).

<!-- ########################## -->
## Week of November 12, 2018

### Network Access Control (NAC) support for Citrix SSO for iOS <!-- 3259404 -->

Citrix released an update to Citrix Gateway to allow Network Access Control (NAC) for Citrix SSO for iOS in Intune. You can opt in to include a device ID within a VPN profile in Intune, and then push this profile to your iOS devices. You will need to install the latest update to Citrix Gateway to use this functionality.

[Configure VPN settings on iOS devices](vpn-settings-ios.md#base-vpn-settings) provides more information on using NAC, including some additional requirements. 

<!-- ########################## -->
## Week of November 5, 2018

### Support for iOS 12 OAuth in iOS email profiles <!--2155106 -->

Intune's iOS email profiles support iOS 12 Open Authorization (OAuth). To see this feature, create a new profile (**Device Configuration** > **Profiles** > **Create profile** > **iOS** for platform > **Email** for profile type), or update an existing iOS email profile. If you enable OAuth in a profile that's already deployed to users, then users are prompted to reauthenticate, and download their email again.

[iOS email profiles](email-settings-ios.md) has more information on using OAuth in an email profile.

### Autopilot support for hybrid Azure Active Directory joined devices (Preview) <!-- 1048100-->
You can now set up hybrid Azure Active Directory joined devices by using Autopilot. Devices must be joined to your organization's network to use the hybrid Autopilot feature. For more information, see [Deploy hybrid Azure AD joined devices using Intune and Windows Autopilot](windows-autopilot-hybrid.md).
This feature is rolling out across the user base over the next few days. Therefore, you might not be able to follow these steps until it rolls out to your account.

<!-- ########################## -->
## Week of October 29, 2018

### App management

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

### PowerShell module for Intune – Preview available <!-- 951068 -->
A new PowerShell module, which provides support for the Intune API through Microsoft Graph, is now available for preview on [GitHub]( https://aka.ms/intunepowershell). For details about how to use this module, see the README in that location. 


<!-- ########################## -->
## Week of October 15, 2018

### PIN prompt when you change fingerprints or face ID on an iOS device  <!-- 2637704  -->
Users are now prompted for a PIN after making biometric changes on their iOS device. This includes changes to registered fingerprints or face ID. The timing of the prompt depends on how the configuration of the *Recheck access requirements after (minutes)* timeout.  When no PIN is set, the user is prompted to set one. 
 
This feature is only available for iOS, and requires the participation of applications that integrate the Intune APP SDK for iOS, version 9.0.1 or later. Integration of the SDK is necessary so that the behavior can be enforced on the targeted applications. This integration happens on a rolling basis and is dependent on the specific application teams. Some apps that participate include WXP, Outlook, Managed Browser, and Yammer.


<!-- ########################## -->
## Week of October 1, 2018

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

####  Windows line-of-business (LOB) apps file extensions <!-- 1884873 -->
The file extensions for Windows LOB apps will now include *.msi*, *.appx*, *.appxbundle*, *.msix*, and *.msixbundle*. You can add an app in Microsoft Intune by selecting **Client apps** > **Apps** > **Add**. The **Add app** pane is displayed which allows you to select the **App type**. For Windows LOB apps, select **Line-of-business** app as the app type, select the **App package file**, and then enter an installation file with the appropriate extension.

#### Windows 10 app deployment using Intune <!-- 2309001 -->
Building upon the existing support for line-of-business (LOB) apps and Microsoft Store for Business apps, administrators can use Intune to deploy most of their organization’s existing applications to end users on Windows 10 devices. Administrators can add, install, and uninstall applications for Windows 10 users in a variety of formats, such as MSIs, Setup.exe, or MSP. Intune will evaluate requirement rules before downloading and installing, notifying end users of the status or reboot requirements using the Windows 10 Action Center. This functionality will effectively unblock organizations interested in shifting this workload to Intune and the cloud. This feature is currently in public preview and we expect to add significant new capabilities to the feature over the next few months. 

#### App Protection Policy (APP) settings for web data <!-- 2662995 -->
APP policy settings for web content on both Android and iOS devices will be updated to better handle both http and https web links, as well as data transfer via iOS Universal Links and Android App Links. 

#### End user device and app content menu <!-- 2771453 -->
End users can now use the context menu on device and apps to trigger common actions like renaming a device or checking compliance. 

#### Windows Company Portal keyboard shortcuts <!-- 2771518 -->
End users will now be able to trigger app and device actions in the Windows Company Portal using keyboard shortcuts (accelerators).

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
>  - `{{FullyQualifiedDomainName}}` only works for Windows and domain-joined devices. 
>  -  When specifying device properties such as IMEI, Serial Number, and Fully Qualified Domain Name in the subject or SAN for a device certificate, be aware that these properties could be spoofed by a person with access to the device. 

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




### Device enrollment

#### Apply Autopilot profile to enrolled Win 10 devices not already registered for Autopilot <!-- 1558983 -->
You can apply Autopilot profiles to enrolled Win 10 devices that have not already been registered for Autopilot. In the Autopilot profile, choose the **Convert all targeted devices to Autopilot** option to automatically register non-Autopilot devices with the Autopilot deployment service. Allow 48 hours for the registration to be processed. When the device is unenrolled and reset, Autopilot will provision it.

#### Create and assign multiple Enrollment Status  Page profiles to Azure AD groups <!-- 2526564 -->
You can now [create and assign](windows-enrollment-status.md) multiple Enrollment Status Page profiles to Azure ADD groups.

#### Migration from Device Enrollment Program to Apple Business Manager in Intune <!--2748613-->
Apple Business Manager (ABM) works in Intune and you can upgrade your account from Device Enrollment Program (DEP) to ABM. The process in Intune is the same. To upgrade your Apple account from DEP to ABM, go to [ https://support.apple.com/HT208817]( https://support.apple.com/HT208817).

### Alert and enrollment status tabs on the Device enrollment overview page <!--2748656-->
Alerts and enrollment failures now appear on separate tabs on the Device enrollment overview page.

### Device management

#### Restricts apps, and block access to company resources on Android devices <!-- 2451462  -->  
In **Device compliance** > **Policies** > **Create policy** > **Android** > **System Security**, there is a new setting under the *Device Security* section, named **Restricted apps**. The **Restricted apps** setting uses a compliance policy to block access to company resources if certain apps are installed on the device. The device is considered non-compliant until the restricted apps are removed from the device.
Applies to: 
- Android

<!-- ########################### -->
## Notices

[!INCLUDE [Intune notices](./includes/intune-notices.md)]
