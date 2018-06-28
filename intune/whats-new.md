---
# required metadata
title: What's new in Microsoft Intune - Azure | Microsoft Docs
titlesuffix:
description: Find out what's new in the Intune Azure portal
keywords:
author: ErikjeMS  
ms.author: erikje
manager: dougeby
ms.date: 06/04/2018
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: dougeby
ms.suite: ems
#ms.tgt_pltfrm:
/ms.custom: intune-azure
---

# What's new in Microsoft Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Learn what’s new each week in Microsoft Intune. You can also find out about [upcoming changes](#whats-coming), [important notices](#notices) about the service, and information about [past releases](whats-new-archive.md). Some features may roll out over several weeks and might not be available to all customers in the first week.

> [!Note]
> For information on new functionality in hybrid mobile device management (MDM), check out the [hybrid What’s New page](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
### App management
### Device enrollment
### Device management
### Device configuration
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->   

## Week of June 18, 2018

### Edge mobile support for Intune app protection policies <!-- 1817882 -->

The Microsoft Edge browser for mobile devices now supports app protection policies defined in Intune.

## Week of June 11, 2018

### Use FIPS mode with the NDES Certificate connector <!-- 1333688 -->
When you install the NDES Certificate connector on a computer with Federal Information Processing Standard (FIPS) mode enabled, issuing and revoking certificates didn't work as expected. With this update, support for FIPS is included with the NDES Certificate connector. 

This update also includes:

- The NDES Certificate connector requires .NET 4.5 Framework, which is automatically included with Windows Server 2016 and Windows Server 2012 R2. Previously, .NET 3.5 Framework was the minimum required version.
- TLS 1.2 support is included with the NDES Certificate connector. So if the server with NDES Certificate connector installed supports TLS 1.2, then TLS 1.2 is used. If the server doesn't support TLS 1.2, then TLS 1.1 is used. Currently, TLS 1.1 is used for authentication between the devices and server.

For more information, see [Configure and use SCEP certificates](certificates-scep-configure.md) and [Configure and use PKCS certificates](certficates-pfx-configure.md).

## Week of June 4, 2018

### App management

#### Retrieve the associated app user model ID (AUMID) for Microsoft Store for Business apps in kiosk mode <!-- 1560077 ! -->
Intune can now retrieve the app user model ids (AUMIDs) for Microsoft Store for Business (WSfB) apps to provide improved configuration of the kiosk profile.

For more information about Microsoft Store for Business apps, see [Manage apps from Microsoft Store for Business](windows-store-for-business.md).

#### New Company Portal branding page <!-- 1916370 -->
The Company Portal branding page has a new layout, messages, and tooltips.


### Device configuration

#### Support for Palo Alto Networks GlobalProtect VPN profiles <!-- 1333680 eeready ! -->
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

#### Support for Windows Autopilot enrollment without user authentication <!-- 1165118 wnready -->
Intune now supports Windows Autopilot enrollment without user authentication. This is a new option in the Windows Autopilot deployment profile "Autopilot Deployment mode" set to "Self-Deploying".  The device must be running Windows 10 Insider Preview Build 17672 or later and possess a TPM 2.0 chip to successfully complete this type of enrollment. Since no user authentication is required, you should only assign this option to devices that you have physical control over.

#### New language/region setting when configuring OOBE for Autopilot <!-- 1821766 eeready -->
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

#### Uninstall the latest from Windows 10 software updates <!-- 1732948 eeready -->
Should you discover a breaking issue on your Windows 10 machines, you can choose to uninstall (rollback) the latest feature update or the latest quality update. Uninstalling a feature or quality update is only available for the servicing channel the device is on. Uninstalling will trigger a policy to restore the previous update on your Windows 10 machines. For feature updates specifically, you can limit the time from 2-60 days that an uninstall of the latest version can be applied. To set software update uninstall options, select **Software updates** from the **Microsoft Intune** blade within the Azure portal. Then, select **Windows 10 Update Rings** from the **Software updates** blade. You can then choose the **Uninstall** option from the **Overview** section.

#### Search all devices for IMEI and serial number <!-- 1793685 -->
You can now search for IMEI and serial numbers on the All devices blade (email, UPN, device name, and management name are still available). In Intune, choose **Devices** > **All devices** > enter your search in the search box.

#### Management name field will be editable <!-- 1875989 -->
You can now edit the management name field on a device’s **Properties** blade. To edit this field, choose **Devices** > **All devices** > choose the device > **Properties**. You can use the management name field to uniquely identify a device.

#### New All devices filter: Device category <!-- 1878520 -->
You can now filter the **All devices** list by device category. To do so, choose **Devices** > **All devices** > **Filter** > **Device category**.

#### Use TeamViewer to screen share iOS and MacOS devices <!-- 1985547 -->
Administrators can now connect to [TeamViewer](device-profile-android-teamviewer.md), and start a screen sharing session with iOS and macOS devices. iPhone, iPad, and macOS users can share their screens live with any other desktop or mobile device. 

#### Multiple Exchange Connector support <!-- 2070451 -->
You're no longer limited to one Microsoft Intune Exchange Connector per tenant. Intune now supports multiple Exchange Connectors so that you can set up Intune conditional access with multiple on-premises Exchange organizations.

With an Intune on-premises Exchange connector, you can manage device access to your on-premises Exchange mailboxes based on whether a device is enrolled in Intune and complies with Intune device compliance policies. To set up a connector, you download the Intune on-premises Exchange connector from the Azure portal and install it on a server in your Exchange organization. On the Microsoft Intune dashboard, choose **On-premises access**, and then under **Setup**, choose **Exchange ActiveSync connector**. Download the Exchange on-premises connector and install it on a server in your Exchange organization. Now that you're no longer limited to one Exchange connector per tenant, if you have additional Exchange organizations, you can follow this same process to download and install a connector for each additional Exchange organization.

#### New device hardware detail: CCID <!-- 2156657 -->
The Chip Card Interface Device (CCID) information is now included for each device. To see it, choose **Devices** > **All devices** > choose a device > **Hardware**> check under **Network details**>

#### Assign all users and all devices as scope groups <!-- 2196803 -->
You can now assign all users, all devices, and all users and all devices in scope groups. To do this, choose **Intune roles** > **All roles** > **Policy and profile manager** > **Assignments** > choose an assignment > **Scope (groups)**.

#### UDID information now included for iOS and macOS devices <!-- 2219806 wnready-->
To see the Unique Device Identifier (UDID) for iOS and macOS devices, go to **Devices** > **All devices** > choose a device > **Hardware**. UDID is only available for corporate devices (as set under **Devices** > **All devices** > choose a device > **Properties** > **Device ownership**).

### Intune apps

#### Improved troubleshooting for app installation <!-- 928990 -->
On Microsoft Intune MDM-managed devices, sometimes app installations can fail. When these app installs fail, it can be challenging to understand the failure reason or troubleshoot the issue. We're shipping a Public Preview of our App Troubleshooting features. You will notice a new node under each individual device called **Managed Apps**. This lists the apps that have been delivered via Intune MDM. Inside the node, you'll see a list of app install states. If you select an individual app, you'll see the troubleshooting view for that specific app. In the troubleshooting view, you'll see the end-to-end lifecycle of the app, such as when the app was created, modified, targeted, and delivered to a device. Additionally, if the app install was not successful, you'll be presented with the error code and a helpful message about the cause of the error. 

#### Intune app protection policies and Microsoft Edge <!-- 1818968 -->
The Microsoft Edge browser for mobile devices (iOS and Android) now supports Microsoft Intune app protection policies. Users of iOS and Android devices who sign-in with their corporate Azure AD accounts in the Edge application will be protected by Intune. On iOS devices, the **Require managed browser for web content** policy will allow users to open links in Edge when it is managed.

## Week of May 14, 2018

### App management

#### Require installation of policies, apps, certificate and network profiles <!-- 1553555 -->

Admins can block end users from accessing the Windows 10 RS4 desktop until Intune installs  policies, apps, and certificate and network profiles during the provisioning of AutoPilot devices. For more info, see [Set up an enrollment status page](windows-enrollment-status.md).

#### Configuring your app protection policies <!-- 2144597 Part 2 -->

In the Azure portal, instead of going to the Intune App Protection service blade, you now just go to Intune. There is now only one location for app protection policies within Intune. Note that all of your app protection policies are on the **Mobile app** blade in Intune under **App protection policies**. This integration helps to simplify your cloud management administration. Remember, all app protection policies are already in Intune and you can modify any of your previously configured policies. Intune App Policy Protection (APP) and Conditional Access (CA) policies are now under **Conditional access**, which can be found under the **Manage** section in the **Microsoft Intune** blade or under the **Security** section in the **Azure Active Directory** blade. For more information about modifying conditional access policies, see [Conditional access in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). For additional information, see [What are app protection policies?](app-protection-policy.md)

## Week of May 7, 2018

### App management

#### Samsung Knox mobile enrollment support <!--1112863-->

When using Intune with Samsung Knox Mobile Enrollment (KME), you can enroll large numbers of company-owned Android devices. Users on WiFi or cellular networks can enroll with just a few taps when they turn on their devices for the first time. When using the Knox Deployment App, devices can be enrolled using Bluetooth or NFC. For more information, see [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md).

#### Requesting help in the Company Portal for Windows 10 <!-- 1874137 -->

The Company Portal for Windows 10 will now send app logs directly to Microsoft when the user initiates the workflow to get help with an issue. This will make it easier to troubleshoot and resolve issues that are raised to Microsoft.

## Week of April 23, 2018

### App management

#### Passcode support for MAM PIN on Android<!-- 1438086 -->

Intune admins can set an application launch requirement to enforce a passcode instead of a numeric MAM PIN. If configured, the user is required to set and use a passcode when prompted before getting access to MAM-enlightened applications. A passcode is defined as a numeric PIN with at least one special character or upper/lowercase alphabet. Intune supports passcode in a similar way to the existing numeric PIN... being able to set a minimum length, allowing repeat characters and sequences through the admin console. This feature requires the latest version of Company Portal on Android. This feature is already available for iOS.

#### Line-of-business (LOB) app support for macOS <!-- 1473977 -->
Microsoft Intune will provide the capability to install macOS LOB apps from the Azure portal. You will be able to add a macOS LOB app to Intune after it has been pre-processed by the tool available in GitHub. In the Azure portal, choose **Mobile apps** from the **Intune** blade. On the **Mobile apps** blade, choose **Apps** > **Add**. On the **Add App** blade, select **Line-of-business app**. 

#### Built-in All Users and All Devices Group for Android for Work (AFW) app assignment <!-- 1813073 -->
You can leverage the built-in **All Users** and **All Devices** groups for AFW app assignment. For more information, see [Include and exclude app assignments in Microsoft Intune](apps-inc-exl-assignments.md).

#### Intune will reinstall required apps that are uninstalled by users <!-- 1947010 -->
If an end user uninstalls a required app, Intune automatically reinstalls the app within 24 hours rather than waiting for the 7 day re-evaluation cycle.

### Device configuration

####  Device profile chart and status list show all devices in a group <!-- 1449153 eeready -->
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

#### Show caller ID in personal profile - Android for Work <!--1098984 -->
When using a personal profile on a device, end-users may not see the caller ID details from a work contact. 

With this update, there is a new setting in **Android for Work** > **Device restrictions** > **Work profile settings**:
- Display work contact caller-id in personal profile

When enabled (not configured), the work contact caller details are displayed in the personal profile. When blocked, the work contact caller number is not displayed in the personal profile. 

Applies to: Android work profile devices on Android OS v6.0 and newer

#### New Windows Defender Credential Guard settings added to endpoint protection settings <!--1102252 --><!--from 1802 and 1804-->

With this update, [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Device configuration** > **Profiles** > **Endpoint protection**) includes the following settings: 

- **Windows Defender Credential Guard**: Turns on Credential Guard with virtualization-based security. Enabling this feature helps protect credentials at the next reboot when **Platform Security Level with Secure Boot** and **Virtualization Based Security** are both enabled. Options include:
  - **Disabled**: If Credential Guard was previously turned on with the **Enabled without lock**" option​, then it turns off Credential Guard remotely.

  - **Enabled with UEFI lock**: Ensures that Credential Guard cannot be disabled using a registry key or using Group Policy. To disable Credential Guard after using this setting, you must set the Group Policy to "Disabled". Then, remove the security functionality from each computer, with a physically present user. These steps clear the configuration persisted in UEFI. As long as the UEFI configuration persists, Credential Guard is enabled.​

  - **Enabled without lock**: Allows Credential Guard to be disabled remotely using Group Policy. The devices that use this setting must be running at least Windows 10 (Version 1511).

The following dependent technologies are automatically enabled when configuring Credential Guard: 

  - **Enable Virtualization-based Security (VBS)**: Turns on virtualization-based security (VBS) at next reboot. Virtualization-based security uses the Windows Hypervisor to provide support for security services, and requires Secure Boot.
  - **Secure Boot with Direct Memory Access (DMA)**: Turns on VBS with Secure Boot and direct memory access. DMA protections require hardware support, and is only enabled on properly configured devices. 

#### Use a custom subject name on SCEP certificate <!-- 2064190 -->
You can use the **OnPremisesSamAccountName** the common name in a custom subject on an SCEP certificate profile. For example, you can use `CN={OnPremisesSamAccountName})`.

####  Block camera and screen captures on Android for Work <!-- 1098977 eeready-->
Two new properties are available to block when you configure device restrictions for Android devices: 
- Camera: Blocks access to all cameras on the device
- Screen capture: Blocks the screen capture, and also prevents the content from being shown on display devices that don't have a secure video output

Applies to Android for Work.


### Device enrollment

#### New enrollment steps for users on devices with macOS High Sierra 10.13.2+ <!--1734567 -->
macOS high Sierra 10.13.2 introduced the concept of "User Approved" MDM enrollment. Approved enrollments allow Intune to manage some security-sensitive settings. For more information, see Apple's support documentation here: https://support.apple.com/HT208019.

Devices enrolled using the macOS Company Portal are considered "Not User Approved" unless the end user opens System Preferences and manually provides approval. To this end, the macOS Company Portal now directs users on macOS 10.13.2 and above to go and manually approve their enrollment at the end of the enrollment process. The Intune admin console will report on if an enrolled device is user approved.



### Device management

#### Advanced Threat Protection (ATP) and Intune are fully integrated <!-- EEready 1629303 -->

[Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) shows the risk level of Windows 10 devices. In Windows Defender Security Center (ATP portal), you can create a connection to Microsoft Intune. Once created, an Intune compliance policy is used to determine an acceptable threat level. If the threat level is exceeded, an Azure Active Directory (AD) conditional access policy can then block access to different apps within your organization.

This feature allows ATP to scan files, detect threats, and report any risk on your Windows 10 devices.

See [Enable ATP with conditional access in Intune](advanced-threat-protection.md).

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


### User interface

#### Improved device tiles in the Windows 10 Company Portal <!--2213364 -->

The tiles have been updated to be more accessible to low-vision users and to perform better for screen reading tools.

#### Send diagnostic reports in Company Portal app for macOS <!-- 2216677 -->
The Company Portal app for macOS devices was updated to improve how users report Intune-related errors. From the Company Portal app, your employees can:

- Upload diagnostic reports directly to the Microsoft developer team.
- Email an incident ID to your company's IT support team.

For more information see [Send errors for macOS](/intune-user-help/send-errors-macos).

#### Intune adapts to Fluent Design System in the Company Portal app for Windows 10 <!-- 1195010 WNready -->
The Intune Company Portal app for Windows 10 has been updated with the [Fluent Design System's navigation view](https://docs.microsoft.com/en-us/windows/uwp/design/basics/navigation-basics). Along the side of the app, you'll notice a static, vertical list of all top-level pages. Click any link to quickly view and switch between pages. This is the first of several updates you'll see as part of our ongoing effort to create a more adaptive, empathetic, and familiar experience in Intune. To see the updated look, go to [What's new in the app UI](whats-new-app-ui.md).

## Week of April 16, 2018

#### Use Cisco AnyConnect client for iOS <!-- EEready 1333708 -->

When you create a new VPN profile for iOS, there are now two options: **Cisco AnyConnect** and **Cisco Legacy AnyConnect**. Cisco AnyConnect profiles support 4.0.7x and newer versions. Existing iOS Cisco AnyConnect VPN profiles are labeled **Cisco Legacy AnyConnect**, and continue to work with Cisco AnyConnect 4.0.5x and older versions, as they do today.

> [!NOTE]
> This change only applies to iOS. There continues to be only one Cisco AnyConnect option for Android, Android for Work, and macOS platforms.

#### Jamf-enrolled macOS devices can now register with Intune <!-- 2370684 -->

Versions 1.3 and 1.4 of the macOS company portal did not successfully register Jamf devices with Intune. Version 1.4.2 of the macOS portal fixes this issue.


## Week of April 9, 2018

#### Updated help experience in Company Portal app for Android <!-- 1631531 -->

We've updated the help experience in the Company Portal app for Android to align with best practices for the Android platform. Now when users encounter a problem in the app, they can tap **Menu** > **Help** and:
- Upload diagnostic logs to Microsoft.
- Send an email that describes the problem and incident ID to a company support person.  

To check out the updated help experience go to [Send logs using email](/intune-user-help/send-logs-to-your-it-admin-by-email-android) and [Send errors to Microsoft](/intune-user-help/send-logs-to-microsoft-android).


#### New enrollment failure trend chart and failure reasons table <!-- 1471783 -->

On the Enrollment Overview page, you can view the trend of enrollment failures and the top five causes of failures. By clicking on the chart or table,you can drill into details to find troubleshooting advice and remediation suggestions.

#### Update where to configure your app protection policies <!-- 2144597 -->

In the Azure portal within the Microsoft Intune service, we’re going to temporarily redirect you from the **Intune App Protection** service blade to the **Mobile app** blade. Note that all of your app protection policies are already on the **Mobile app** blade in Intune under app configuration. Instead of going to Intune App Protection, you’ll just go to Intune. In April 2018, we will stop the redirection and fully remove the **Intune App Protection** service blade, so that there's only one location for app protection policies within Intune. 

**How does this affect me?**
This change will affect both Intune standalone customers and hybrid (Intune with Configuration Manager) customers. This integration will help simplify your cloud management administration.

**What do I need to do to prepare for this change?**
Please tag **Intune** as a favorite instead of the **Intune App Protection** service blade and ensure you’re familiar with the App protection policy workflow in the **Mobile** app blade within Intune. We’ll redirect for a short period of time and then remove the **App Protection** blade. Remember, all app protection policies are already in Intune and you can modify any of your conditional access policies. For more information about modifying conditional access policies, see [Conditional access in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). For additional information, see [What are app protection policies?](app-protection-policy.md) 


## Week of April 2, 2018

### Intune apps

#### User experience update for the Company Portal app for iOS <!--1412866 -->
We've released a major user experience update to the Company Portal app for iOS. The update features a complete visual redesign that includes a modernized look and feel. We've maintained the functionality of the app, but increased its usability and accessibility.  

You'll also see:
- Support for iPhone X.
- Faster app launch and loading responses, to save users time.
- Additional progress bars to provide users with the most up-to-date status information.
- Improvements to the way users upload logs, so if something goes wrong, it's easier to report.  

To see the updated look, go to [What's new in the app UI](whats-new-app-ui.md).

#### Protect on-premise Exchange data using Intune APP and CA <!-- 1056954 -->
You can now use Intune App Policy Protection (APP) and Conditional Access (CA) to protect access to on-premise Exchange data with Outlook Mobile. To add or modify an app protection policy within the Azure portal, select **Microsoft Intune** > **Mobile apps** > **App protection policies**. Before using this feature, make sure you meet the [Outlook for iOS and Android requirements](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx).

## Week of March 26, 2018

### App management

#### Alerts for expiring iOS line-of-business (LOB) apps for Microsoft Intune <!-- 748789 -->

In the Azure portal, Intune will alert you to iOS line-of-business apps that are about to expire. Upon uploading a new version of the iOS line-of-business app, Intune removes the expiration notification from the app list. This expiration notification will only be active for newly uploaded iOS line-of-business apps. A warning appears 30 days before the iOS LOB app provisioning profile expires. When it expires, the alert changes to Expired.

#### Customize your Company Portal themes with hex codes <!--1049561 -->

You can customize theme color in the Company Portal apps using hex codes. When you enter your hex code, Intune determines the text color that provides the highest level of contrast between the text color and the background color. You can preview both the text color and your company logo against the color in **Mobile apps** > **Company Portal**.

### Including and excluding app assignment based on groups for Android Enterprise <!-- 1813081 -->

Android Enterprise (formerly known as Android for Work) supports including and excluding groups, but does not support the pre-created **All Users** and **All Devices** built-in groups. For more information, see [Include and exclude app assignments in Microsoft Intune](apps-inc-exl-assignments.md).


### Device management

#### New security enhancements in the Intune service  <!-- 1637539 -->   

We’ve introduced a toggle in Intune on Azure that Intune standalone customers can use to treat devices without any policy assigned as **Compliant** (security feature off) or treat these devices as **Not compliant** (security feature on). This will ensure access to resources only after device compliance has been evaluated.

This feature affects you differently depending on whether you already have compliance policies assigned or not.

- If you are a new or existing account, and don't have any compliance policies assigned to your devices, then the toggle is automatically set to **Compliant**. The feature is off as a default setting in the console. There is no end-user impact.
- If you are an existing account, and you have any devices with a compliance policy assigned to them, then the toggle is automatically set to **Not compliant**. The feature is on as a default setting, as the March update rolls out.

If you use compliance policies with Conditional Access (CA), and have the feature turned on, any devices without at least one compliance policy assigned are now be blocked by CA. End-users associated with these devices, who were previously allowed access to email, lose their access unless you assign at least one compliance policy to all devices.   

Note that although the default toggle status is displayed in the UI immediately with the Intune service March updates, this toggle status is not enforced right away. Any changes you make to the toggle will not impact device compliance until we flight your account to have a working toggle. We’ll inform you via the Message center when we finish flighting your account. This could take up to a few days after your Intune service is updated for March.

**Additional Information**: [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### Enhanced jailbreak detection <!-- 846515 -->

Enhanced jailbreak detection is a new compliance setting that improves how Intune evaluates jailbroken devices. The setting causes the device to check-in with Intune more frequently, which uses the device’s location services and impacts battery usage.

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

####  Detailed error codes and messages <!-- 1376342 -->

In your Device Configuration, there is more detailed error codes and error messages available to see. This improved reporting shows the settings, the state of these settings, and details on troubleshooting.

##### More information

- Block all incoming connections

   This blocks all sharing services (such as File Sharing and Screen Sharing) from receiving incoming connections. The system services that are still allowed to receive incoming connections are:
  - configd - implements DHCP and other network configuration services
  - mDNSResponder - implements Bonjour
  - racoon -  implements IPSec

    To use sharing services, ensure **Incoming connections** is set to **Not configured** (not **Block**).

- Stealth mode

   Enable this to prevent the computer from responding to probing requests. The computer still answers incoming requests for authorized apps. Unexpected requests, such as ICMP (ping), are ignored.

#### Disable checks on device restart <!--1805490 -->
Intune gives you control to [manage software updates]](windows-update-for-business-configure.md). With this update, the <strong>Restart checks</strong> property is available, and enabled by default. To skip the typical checks that occur when you restart a device (such as active users, battery levels, and so on), select <strong>Skip</strong>.

#### New Windows 10 Insider Preview channels available for deployment rings <!-- 1746293 -->
You now have the option to select the following Windows 10 Insider Preview servicing channels when you create a Windows 10 deployment ring:
- Windows Insider build &#8208; Fast
- Windows Insider build &#8208; Slow
- Release Windows Insider build 

For more information about these channels, see [Manage Insider Preview Builds](https://insider.windows.com/en-us/for-business-organization-admin/).   
For more information about creating deployment channels in Intune, see [Manage software updates in Intune](windows-update-for-business-configure.md).

### Intune apps

#### Company Portal enrollment improved <!-- 1874230 eeready-->
Users enrolling a device by using the Company Portal on Windows 10 build 1703 and up are now able to complete the first step of enrollment without leaving the app.
#### HoloLens and Surface Hub now appear in device lists <!--1725868 -->
We added support for showing Intune-enrolled HoloLens and Surface Hub devices to the Company Portal app for Android.

#### Custom Book categories for volume-purchase progream (VPP) eBooks <!-- 1488911 -->
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

- **Android**: [How to remove your Android device from Intune](/intune-user-help/unenroll-your-device-from-intune-android.md)
- **Android, if the user has declined terms of use**: [Remove your device management if you declined "Terms of Use"](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android.md)
- **iOS**: [Remove your iOS device from Intune](/intune-user-help/unenroll-your-device-from-intune-ios.md)
- **Windows**: [Remove your Windows device from Intune](/intune-user-help/unenroll-your-device-from-intune-windows.md)

## Week of March 19, 2018

### Export all devices into CSV files in IE, Edge, or Chrome <!-- 2258071 -->
In **Devices** > **All devices**, you can **Export** the devices into a CSV formatted list. Internet Explorer (IE) users with >10,000 devices can successfully export their devices into multiple files. Each file has up to 10,000 devices.

Edge and Chrome users with >30,000 devices can successfully export their devices into multiple files. Each file has up to 30,000 devices.

[Manage devices](device-management.md) provides more details on what you can do with devices you manage.

## Week of March 12, 2018

### Azure Active Directory web sites can require the Intune Managed Browser app and support Single Sign-On for the Managed Browser (Public Preview) <!-- 710595 -->

Using Azure Active Directory (Azure AD), you can now restrict access to web sites on mobile devices to the Intune Managed Browser app. In the Managed Browser, web site data will remain secure and separate from end-user personal data. In addition, the Managed Browser will support Single Sign-On capabilities for sites protected by Azure AD. Signing in to the Managed Browser, or using the Managed Browser on a device with another app managed by Intune, allows the Managed Browser to access corporate sites protected by Azure AD without the user having to enter their credentials. This functionality applies to sites like Outlook Web Access (OWA) and SharePoint Online, as well as other corporate sites like intranet resources accessed through the Azure App Proxy. For additional information, see [Access controls in Azure Active Directory conditional access](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls).

#### Company Portal app for Android visual updates <!--976944 -->

We've updated the Company Portal app for Android to follow Android's [Material Design](https://material.io/) guidelines. You can see the images of the new icons in the [What's new in app UI](whats-new-app-ui.md) article.

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

## Week of February 19, 2018

### Device enrollment

#### Intune support for multiple Apple DEP / Apple School Manager accounts <!-- 747685 -->

Intune now supports enrolling devices from up to 100 different [Apple Device Enrollment Program (DEP)](device-enrollment-program-enroll-ios.md) or [Apple School Manager](apple-school-manager-set-up-ios.md) accounts. Each token uploaded can be managed separately for enrollment profiles and devices. A different enrollment profile can be automatically assigned per DEP/School Manager token uploaded. If multiple School Manager tokens are uploaded, only one can be shared with Microsoft School Data Sync at a time.

After migration, the beta Graph APIs and published scripts for managing Apple DEP or ASM over Graph will no longer work. New beta Graph APIs are in development and will be released after the migration.

#### See enrollment restrictions per user <!-- 1634444 eeready wnready -->
On the **Troubleshoot** blade, you can now see the [enrollment restrictions](enrollment-restrictions-set.md) that are in effect for each user by selecting **Enrollment restrictions** from the **Assignments** list.

### Device management
#### Windows defender health status and threat status reports <!--854704 -->

Understanding Windows Defender's health and status is key to managing Windows PCs.  With this update, Intune adds new reports and actions to the status and health of the Windows Defender agent. Using a status roll up report in the [Device Compliance workload](compliance-policy-monitor.md), you can see devices that need any of the following:
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

#### New settings for the Edge browser <!--1469166 -->
[Two new settings](device-restrictions-windows-10.md#edge-browser) are now available for devices with the Edge browser: **Path to favorites file** and **Changes to Favorites**.

### App management
#### Protocol exceptions for applications <!--1035509 -->

You can now create exceptions to the Intune Mobile Application Management (MAM) data transfer policy to open specific unmanaged applications. Such applications must be trusted by IT. Other than the exceptions you create, data transfer is still restricted to applications that are managed by Intune when your data transfer policy is set to **managed apps only**. You can create the restrictions by using protocols (iOS) or packages (Android).

For example, you can add the Webex package as an exception to the MAM data transfer policy. This will allow Webex links in a managed Outlook email message to open directly in the Webex application. Data transfer will still be restricted in other unmanaged applications. For more information, see [Data transfer policy exceptions for apps](app-protection-policies-exception.md).

#### Windows Information Protection (WIP) encrypted data in Windows search results <!-- 1469193 -->
A setting in the Windows Information Protection (WIP) policy now allows you to control whether WIP-encrypted data is included in Windows search results. Set this app protection policy option by selecting **Allow Windows Search Indexer to search encrypted items** in the **Advanced settings** of the Windows Information Protection policy. The app protection policy must be set to the *Windows 10* platform and the app policy **Enrollment state** must be set to **With enrollment**. For more information, see [Allow Windows Search Indexer to search encrypted items](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### Configuring a self-updating mobile MSI app <!-- 1740840 -->
You can configure a known self-updating mobile MSI app to ignore the version check process. This capability is useful to avoid getting into a race condition. For instance, this type of race condition could occur when the app being auto-updated by the app developer is also being update by Intune. Both could try to enforce a version of the app on a Windows client, which could create a conflict. For these automatically updated MSI apps, you can configure the **Ignore app version** setting in the **App information** blade. When this setting is switched to **Yes**, Microsoft Intune will ignore the app version installed on the Windows client.

#### Related sets of app licenses supported in Intune <!-- 1864117 -->
Intune in the Azure portal now supports related sets of app licenses as a single app item in the UI. In addition, any Offline Licensed apps synced from Microsoft Store for Business will be consolidated into a single app entry and any deployment details from the individual packages will be migrated over to the single entry. To view related sets of app licenses in the Azure portal, select **App licenses** from the **Mobile apps** blade.

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


### Role-based access control
### Intune apps
#### Support for offline apps from the Microsoft Store for Business <!--1222672-->
Offline apps that you purchased from the Microsoft Store for Business are now synchronized to the Azure portal. You can deploy these apps to device groups or user groups. Offline apps are installed by Intune, not by the store.

#### Prevent end users from manually adding or removing accounts in the work profile <!-- 1728700 -->

When you deploy the Gmail app into an Android for Work profile, you can now prevent end users from manually adding or removing accounts in the work profile by using the **Add and remove accounts** setting in the Android for Work Device restrictions profile.

## Week of February 5, 2018

### Device enrollment

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

## Week of January 29, 2018

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


## Week of January 22, 2018

### Intune apps

#### New functionality for the "Resolve" action for Android devices <!--1583480-->

The Company Portal app for Android is expanding the "Resolve" action for **Update device settings** to resolve [device encryption issues](/intune-user-help/encrypt-your-device-android).

#### Remote lock available in Company Portal app for Windows 10 <!--676506-->
End users can now remotely lock their devices from the Company Portal app for Windows 10. This will not be displayed for the local device they're actively using.

#### Easier resolution of compliance issues for the Company Portal app for Windows 10 <!--676546-->
End users with Windows devices will be able to tap the noncompliance reason in the Company Portal app. When possible, this will take them directly to the correct location in the settings app to fix the issue.

## Week of December 11, 2017

### Device configuration

#### New automatic redeployment setting <!-- 1469168 -->
The **Automatic redeployment** setting allows users with administrative rights to delete all user data and settings using **CTRL + Win + R** at the device lock screen. The device is automatically reconfigured and reenrolled into management. This setting can be found under Windows 10 > Device restrictions > General > Automatic redeployment. For details, see [Intune device restriction settings for Windows 10](device-restrictions-windows-10.md#general).

#### Support for additional source editions in the Windows 10 edition upgrade policy  <!-- 903672,  1119689 -->
You can now use the Windows 10 edition upgrade policy to upgrade from additional Windows 10 editions (Windows 10 Pro, Windows 10 Pro for Education, Windows 10 Cloud, etc.). Prior to this release, the supported edition upgrade paths were more limited. For details, see [How to configure Windows 10 edition upgrades](edition-upgrade-configure-windows-10.md).

#### New Windows Defender Security Center (WDSC) device configuration profile settings <!-- 1335507 -->

Intune adds a new section of device configuration profile settings under the Endpoint protection named **Windows Defender Security Center**. IT admins can configure which pillars of the Windows Defender Security Center app end-users can access. If an IT admin hides a pillar in the Windows Defender Security Center app, all notifications related to the hidden pillar do not display on the user's device.

These are the pillars admins can hide from the Windows Defender Security Center device configuration profile settings:
- Virus and threat protection
- Device performance and health
- Firewall and network protections
- App and browser control
- Family options

IT admins can also customize which notifications users receive. For example, you can configure whether the users receive all notifications generated by visible pillars in the WDSC, or only critical notifications. Non-critical notifications include periodic summaries of Windows Defender Antivirus activity and notifications when scans have completed. All other notifications are considered critical. Additionally, you can also customize the notification content itself, for example, you can provide the IT contact information to embed in the notifications that appear on the users' devices.

#### Multiple connector support for SCEP and PFX certificate handling <!-- 1361755 -->

Customers who use the on-premise NDES connector to deliver certificates to devices can now configure multiple connectors in a single tenant.

This new capability supports the following scenario:

- **High availability**

Each NDES connector pulls certificate requests from Intune.  If one NDES connector goes offline, the other connector can continue to process requests.

#### Customer subject name can use AAD_DEVICE_ID variable  <!-- 1468599 -->

When you create a SCEP certificate profile in Intune, you can now use the AAD_DEVICE_ID variable when you build the custom subject name.   When the certificate is requested using this SCEP profile, the variable is replaced with the AAD device ID of the device making the certificate request.


### Device management

#### Manage Jamf-enrolled macOS devices with Intune's device compliance engine <!-- 1592747 -->
You can now use Jamf to send macOS device state information to Intune, which will then evaluate it for compliance with policies defined in the Intune console. Based on the device compliance state as well as other conditions (such as location, user risk, etc.), conditional access will enforce compliance for macOS devices accessing cloud and on-premises applications connected with Azure AD, including Office 365. Find out more about [setting up Jamf integration](conditional-access-integrate-jamf.md) and [enforcing compliance for Jamf-managed devices](conditional-access-assign-jamf.md).

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

## Week of December 4, 2017

### Monitor and troubleshoot

#### Intune supports Windows Information Protection (WIP) denied apps <!-- 1479103 -->
You can specify denied apps in Intune. If an app is denied, it is blocked from accessing corporate information, effectively the opposite of the allowed apps list. For more information, see [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection).



## Notices

### Plan for Change: Intune moving to TLS 1.2
Starting on October 31, 2018, Intune will support Transport Layer Security (TLS) protocol version 1.2 to provide best-in-class encryption, to ensure our service is more secure by default, and to align with other Microsoft services such as Microsoft Office 365. Office communicated this change in MC128929.

#### How does this affect me?
As of October 31, 2018, Intune will no longer support TLS protocol versions 1.0 or 1.1. All client-server and browser-server combinations should use TLS version 1.2 to ensure connection without issues to Intune. Note that this change will impact end-user devices that are no longer supported by Intune but are still receiving policy through Intune, and that cannot use TLS version 1.2. This includes devices such as those running Android 4.3 and earlier. For a list of affected devices and browsers, see Additional Information below.

After October 31, 2018, if you experience an issue related to the use of an old TLS version, you will be required to update to TLS 1.2 or to a device that supports TLS 1.2 as part of the resolution.

#### What do I need to do to prepare for this change?
We recommend that you proactively remove TLS 1.0 and 1.1 dependencies in your environments and disable TLS 1.0 and 1.1 at the operating system level where possible. Begin planning your migration to TLS 1.2 today. Check the support blog post below for the list of devices that are not supported by Intune today but might still be receiving policy, and that will not be able to communicate using TLS version 1.2. You might need to notify those end users that they’ll lose access to corporate resources.

**Additional Information**: [Intune moving to TLS 1.2 for encryption](https://blogs.technet.microsoft.com/intunesupport/2018/06/05/intune-moving-to-tls-1-2-for-encryption/)

### Plan for Change: New Windows 10 Setting for Kiosk Configuration in Intune <!-- 1560072 -->
We’re changing how and where you configure Windows 10 1709 and later (RS3 and later) desktops, in the Intune Azure portal.

#### How does this affect me? 
Our records indicate that you are using the Windows 10 > Device Restrictions > Kiosk (preview) setting. This will be renamed in May, to Windows 10 > Device Restrictions > Kiosk (obsolete) in the UI to indicate that it is no longer recommended for use. It will, however, continue to function until the July update to Intune. Then, it will be made obsolete in the backend and will no longer work. As an alternative, we’re releasing a new Device configuration profile in May: Windows 10 > Kiosk, containing the settings to configure Kiosks on Windows 10 RS4 and later.

#### What do I need to do to prepare for this change?  
When Intune releases the May service update around the end of May, we’ll share instructions for you to test and verify that you are able to migrate your Kiosk configuration from Windows 10 RS3 to Windows 10 RS4. Use these instructions to configure your devices as Kiosks using the new device configuration profile for Kiosks.

#### How does this affect me?
This change will affect both Intune standalone customers and hybrid (Intune with Configuration Manager) customers. This integration will help simplify your cloud management administration. Now, you’ll just have one blade to go to in Azure – the Intune blade – to manage groups, policies, apps, and any mobile device management.

#### What do I need to do to prepare for this change?
Please tag Intune as a favorite instead of the Intune App Protection service blade and ensure you’re familiar with the App protection policy workflow in the Mobile app blade within Intune. We’ll redirect for a short period of time and then remove the App Protection blade. Remember, all App Protection policies are already over in Intune and you can modify any of your conditional access policies by following the documentation here: [https://aka.ms/azuread_ca](https://aka.ms/azuread_ca).

**Additional Information**: [https://aka.ms/intuneapppolicy](https://aka.ms/intuneapppolicy)

### Plan for Change: Change in support for the Microsoft Intune App SDK for Cordova plugin
Intune is ending support for the [Microsoft Intune App SDK Cordova Plugin](app-sdk-cordova.md) on May 1, 2018. We recommend that you use the Intune App Wrapping Tool instead, to prepare your Cordova based apps for manageability and availability in Intune. When this change takes effect, the Microsoft Intune APP SDK for Cordova plugin will no longer be maintained or receive updates. App developers will not be able to use this plugin. Intune plans to continue supporting apps built with Cordova. However, any apps built with the Microsoft Intune APP SDK for Cordova plugin will experience reduced functionality in Intune. After wrapping with the Intune App Wrapping Tool, apps can be deployed to end users as they normally would be. For Cordova-based Android apps that are released to the Google Play Store:
- End users will be prompted for credentials to receive Intune policy on first launch.
- Apps should be released to the app store targeted for Intune users, for example “Contoso App for Intune”.

For more information about the App Wrapping Tool, see [App Wrapping Tool for iOS](app-wrapper-prepare-ios.md) and [App Wrapping Tool for Android](app-wrapper-prepare-android.md). For any issues or questions, contact [msintuneappsdk@microsoft.com](mailto:msintuneappsdk@microsoft.com).

### Plan for Change: Use Intune on Azure now for your MDM management <!-- 1227338 -->
Over a year ago, we announced [public preview of Intune on Azure](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/) and followed up six months ago with [general availability of the new admin experience](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/) for Intune. Starting on August 31, 2018, we will turn off mobile device management (MDM) in the classic Silverlight console for those customers using Intune standalone. Instead, you can use [Intune on Azure](https://aka.ms/Intune_on_Azure) for your MDM needs. If you're still using the classic console for MDM, please stop and familiarize yourself with Intune on Azure. We do not expect any end user impact with this change. Classic PC management will remain in Silverlight. You can learn more about this change and how it affects you [here](https://aka.ms/Intune_on_Azure_mdm).

### Direct access to Apple enrollment scenarios <!--951869-->
For Intune accounts created after January 2017, Intune has enabled direct access to Apple enrollment scenarios using the Enroll Devices workload in the Azure portal. Previously, the Apple enrollment preview was only accessible from links in the Intune classic portal. Intune accounts created before January 2017 require a one-time migration before these features are available in Azure. The schedule for migration has not been announced yet, but details will be made available as soon as possible. If your existing account cannot access the Azure portal, we strongly recommend creating a trial account to test out the new experience.

## What's coming

### Local device security option settings <!-- 1251887 -->
You'll be able to enable security settings on Windows 10 devices using the new Local Device Security Option settings. Find these settings in the Endpoint Protection category when you create a Windows 10 device configuration policy.

### New user experience update for the Company Portal website <!--2000968-->

We’re introducing a new Company Portal website experience in April, with UI updates, streamlined workflows and accessibility improvements. This will include customer-driven enhancements like app sharing and improved overall performance to bring you a more user-friendly experience.
We’ve added some new features, based on feedback from customers like you, that will significantly improve existing functionality and usability:

-   UI improvements throughout the website
-   Ability to share direct links to apps
- Improved performance for large app catalogs

You don't need to take any action to prepare for this change. We’ll let you know when the updated Company Portal website becomes available for you. However, you may eventually need to update end user docs with updated screenshots. Note that you may also need to update documentation for the Company Portal app on iOS, as the website powers the **Apps** section of the iOS app. You can see a sample image for this on the [what's new in app UI](whats-new-app-ui.md) page.

### Apple to require updates for Application Transport Security <!--748318-->
Apple has announced that they will enforce specific requirements for Application Transport Security (ATS). ATS is used to enforce stricter security on all app communications over HTTPS. This change impacts Intune customers using the iOS Company Portal apps. We'll keep our [Intune support blog](https://aka.ms/compportalats) with details.



## See also
* [Microsoft Intune Blog](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Cloud Platform roadmap](https://www.microsoft.com/cloud-platform/roadmap)
* [What's new in the Company Portal UI](whats-new-app-ui.md)
* [What's new in previous months](whats-new-archive.md)
