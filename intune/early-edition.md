---
# required metadata

title: Early edition
description:
keywords:
author: ErikjeMS  
ms.author: erikje
manager: dougeby
ms.date: 06/21/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d

# optional metadata

ROBOTS: NOINDEX,NOFOLLOW
#audience:
#ms.devlang:
ms.reviewer: cacampbell
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-classic
---

# The early edition for Microsoft Intune - June 2018

> [!Note]
> NDA notification: The following changes are under development for Intune. This information is shared under NDA on a very limited basis. Do not post any of this information on social media or public websites such as Twitter, UserVoice, Reddit, and so on. 


The **early edition** provides a list of features, shared under NDA, that are coming in upcoming releases of Microsoft Intune. This information is provided on a limited basis and is subject to change. Do not tweet, post on UserVoice, or otherwise share this information outside of your company. Some features listed here are at risk of not making the cutoff dates and may be delayed until a future release. Other features are being tested in a pilot (flighting) to ensure they're customer-ready. Reach out to your Microsoft product group contact if you have any questions or concerns.

This page is updated periodically. Check back for additional updates.

> [!Note]
>The following changes are under development for Intune. For more information about new hybrid features, check out the [hybrid What’s New page](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## Intune in the Azure portal

<!-- 1806 start -->

### See device configuration profiles in conflict <!-- 1556983 -->
In **Device Configuration**, a list of the existing profiles is shown. With this update, a new column is added that provides details on profiles that have a conflict. You can select a conflicting row to see the setting and profile that has the conflict. 

More on [device configuration profiles](device-profiles.md).

### Use FIPS mode with the NDES Certificate connector <!-- 1333688 -->

When you install the NDES Certificate connector on a computer with Federal Information Processing Standard (FIPS) mode enabled, issuing and revoking certificates doesn't work as expected. With this update, support for FIPS is included with the NDES Certificate connector. 

This update also includes:

- The NDES Certificate connector requires .NET 4.5 Framework, which is automatically included with Windows Server 2016 and Windows Server 2012 R2. Currently, .NET 3.5 Framework is the minimum required version.
- TLS 1.2 support is included with the NDES Certificate connector. So if the server with NDES Certificate connector installed supports TLS 1.2, then TLS 1.2 is used. If the server doesn't support TLS 1.2, then TLS 1.1 is used. Currently, TLS 1.1 is used for authentication between the devices and server.

### Corporate-owned, single use (COSU) support for Android devices <!-- 1630973 -->

Intune will support highly managed, locked-down, kiosk-style Android devices. This allows admins to further lock down the usage of a device to a single app or small set of apps, and prevents users from enabling other apps or performing other actions on the device.

### macOS support for Apple Device Enrollment Program <!-- 747651 -->

Intune will support enrolling macOS devices into the Apple Device Enrollment Program (DEP). To do so:

1. At deploy.apple.com, assign macOS serial numbers to an MDM server.
2. Import the serial numbers into Intune.
3. Create an enrollment program profile specific to macOS devices.

### Google name changes for Android for Work and Play for Work <!--842873 -->
Intune will update "Android for Work" terminology to reflect Google branding changes.  The terms "Android for Work" and "Play for Work" will no longer be used. Different terminology will be used depending on the context:

- "Android enterprise" refers to the overall modern Android management stack.
- "Work Profile" or "Profile Owner" refers to BYOD devices managed with work profiles.
- "Managed Google Play" refers to the Google app store.

### Monitor iOS  app configuration status per device <!-- 880037 eeready eestaged -->

As the Microsoft Intune admin, you will be able to monitor iOS app configuration status for each managed device. From **Microsoft Intune** in the Azure portal, select **Devices** > **All devices**. From the list of managed devices, select a specific device to display a blade for the device. On the device blade, select **App configuration**.  

### 3rd-party keyboards can be blocked by APP settings on iOS <!-- 1248481 -->
On iOS devices, Intune admins will be able to block the use of 3rd-party keyboards when accessing organization data in policy protected apps. When the Application Protection Policy (APP) is set to block 3rd-party keyboards, the device user will receive a message the first time they interact with corporate data when using a 3rd-party keyboard. All options, other than the native keyboard, will be blocked and device users will not see them. Device users will only see the dialog message once. 

### Create device compliance policy using Firewall settings on macOS devices <!-- 1497640 -->
When you create a new macOS compliance policy (**Device compliance** > **Policies** > **Create policy** > **Platform: macOS** > **System security**), there will be some new **Firewall** settings available: 
- **Firewall**: Configure how incoming connections are handled in your environment.
- **Incoming connections**: **Block** all incoming connections except those required for basic internet services, such as DHCP, Bonjour, and IPSec. This setting also blocks all sharing services.
- **Stealth Mode**: **Enable** stealth mode to prevent the device from responding to probing requests. The device continues to answer incoming requests for authorized apps.

Applies to: macOS 10.12 and later

### Use sAMAccountName as the account username for email profiles <!-- 1500307 -->

You'll be able to use the on-premises **sAMAccountName** as the account username for email profiles for Android, iOS, and Windows 10. You'll also be able get the domain from the `domain` or `ntdomain` attribute in Azure Active Directory (Azure AD). Or, enter a custom static domain.

To use this feature, you must sync the `sAMAccountName` attribute from your on-premises Active Directory environment to Azure AD.

Applies to: Android, iOS, Windows 10 and later

### Require non-biometric passcode on app launch and timeout <!-- 1506985 -->

By requiring a non-biometric passcode on app launch and after admin-specified timeout, Intune will provide improved security for Mobile Application Management (MAM) enabled apps by restricting the use of biometric identification for access to corporate data. The settings will affect users who rely on Touch ID (iOS), Face ID (iOS), Android Biometric, or other future biometric authentication methods to access their APP/MAM-enabled applications. These settings will enable Intune admins to have more granular control over user access, eliminating cases where a device with multiple fingerprints or other biometric access methods can reveal corporate data to an incorrect user. In the Azure portal, open **Microsoft Intune**. Select **Mobile apps** > **App protection policies** > **Add a policy** > **Settings**. Locate the **Access** section for specific settings.

### Selective wipe of organization's app data <!-- 1507030 -->
Administrators will be able to configure a selective wipe of the organization's data as a new action when the conditions of Application Protection Policies (APP) Access settings are not met.  This feature helps administrators automatically protect and remove sensitive organization data from applications based on pre-configured criteria.

### Revoking an iOS app purchased through VPP <!-- 1777384 -->
As the Microsoft Intune admin, you'll be able to revoke the license for a selected iOS app purchased through the volume-purchase program (VPP). You can notify users when an app is no longer assigned to them. Revoking an app license will not uninstall the related VPP app from the device. To uninstall a VPP app, you must change the assignment action to **Uninstall**. The reclaimed license count will be reflected in **Licensed Apps** node in the **App** workload of Intune. For more information related to iOS VPP apps, see [How to manage iOS apps purchased through a volume-purchase program with Microsoft Intune](vpp-apps-ios.md).

### Office 365 Pro Plus language packs <!-- 1833450 -->
As the Intune admin, you will be able to deploy additional languages for Office 365 Pro Plus apps managed through Intune. The list of available languages includes the **Type** of language pack (core, partial, and proofing). In the Azure portal, select **Microsoft Intune** > **Mobile apps** > **Apps** > **Add**. In the **App type** list of the **Add app** blade, select **Windows 10** under **Office 365 Suite**. Select **Languages** in the **App Suite Settings** blade.

### Revoke iOS VPP app license <!-- 1863797 -->
As the admin, you'll be able to reclaim an iOS VPP app license assigned to a user or device. Uninstalling an iOS VPP app will also allow you to reclaim the app license. Then, you can choose to assign the app license to another user or device. For more information about iOS VPP app licenses, see [Manage iOS volume-purchased apps in Microsoft Intune](vpp-apps-ios.md).

### Preview a new user experience update for the Company Portal website <!--2000968 -->
We’re adding new features, based on feedback from customers, to the Company Portal website/iOS app catalog. You'll experience a significant improvement in existing functionality and usability from your Android, iOS, and Windows devices. Areas of the site--such as device details, feedback and support, and device overview--will receive a new, modern, responsive design. You'll also see:

- Streamlined workflows across all device platforms
- Improved device identification and enrollment flows
- More helpful error messages
- Friendlier language, less tech jargon
- Ability to share direct links to apps
- Improved performance for large app catalogs
- Increased accessibility for all users

The update is currently in preview. You can register to join the preview at http://aka.ms/webcpflighting

### Updates to out-of-compliance messages in Company Portal app <!-- 1832222 -->
We're revising the messages that device users see when a device is out-of-compliance. Messages will retain their original meanings but will be updated with friendlier language and less technical jargon. We're also refreshing links to documentation and remediation steps to keep them up-to-date.  

The following before and after text is one example of the improvements in messaging you'll see:  

Before: *This device hasn’t contacted the Intune service in the specified time period required by your IT admin. To resolve this issue, please open the company portal app on your device and click on the Check Compliance button.*  

After: *Your device has not checked in with your organization in a while. To reestablish a connection, open the Company Portal app on your device and tap Check Settings for your device*.  

### Edit your Office 365 Pro Plus app deployments <!-- 2150145 -->
As the Microsoft Intune admin, you will have greater ability to edit your Office 365 Pro Plus app deployments. In the Azure portal, select **Microsoft Intune** > **Mobile apps** > **Apps**. From the list of apps, select your Office 365 Pro Plus Suite.  

### Per-row review of duplicate corporate device identifiers uploaded <!-- 2203794 -->
When uploading corporate IDs, Intune will provide a list of any duplicates and give you the option to replace or keep the existing information. The report will appear if there are duplicates after you choose **Device enrollment** > **Corporate Device Identifiers** > **Add Identifiers**. 

### Manually add corporate device identifiers <!-- 2203803 -->
You'll be able to manually add corporate device IDs. Choose **Device enrollment** > **Corporate Device Identifiers** > **Add**.

### New status for devices in device compliance <!-- 2308882 -->
In **Device compliance** > **Policies** > select a policy > **Overview**, the following new states will be added:
- succeeded
- error
- conflict
- pending
- not-applicable

An image that shows the device count of a different platform is also shown. For example, if you're looking at an iOS profile, the new tile shows the count of non-iOS devices that are also assigned to this profile. 

### Device compliance supports 3rd party anti-virus solutions <!-- 2325484 -->
When you create a device compliance policy (**Device compliance** > **Policies** > **Create policy** > **Platform: Windows 10 and later** > **Settings** > **System Security**), there will be new **Device Security** options: 
- **Antivirus**: When set to **Require**, you can check compliance using antivirus solutions that are registered with Windows Security Center, such as Symantec. 
- **AntiSpyware**: When set to **Require**, you can check compliance using antispyware solutions that are registered with Windows Security Center, such as Symantec. 

Applies to: Windows 10 and later 

<!-- 1805 start -->

### Improved troubleshooting for app installation <!-- 928990 -->
On Microsoft Intune MDM-managed devices, sometimes app installations can fail. When these app installs fail, it can be challenging to understand the failure reason or troubleshoot the issue. We're shipping a Public Preview of our App Troubleshooting features. You will notice a new node under each individual device called **Managed Apps**. This lists the apps that have been delivered via Intune MDM. Inside the node, you'll see a list of app install states. If you select an individual app, you'll see the troubleshooting view for that specific app. In the troubleshooting view, you'll see the end-to-end lifecycle of the app, such as when the app was created, modified, targeted, and delivered to a device. Additionally, if the app install was not successful, you'll be presented with the error code and a helpful message about the cause of the error.

### Require non-biometric passcode on cold app launch and timeout <!-- 1506985 --> 

By requiring a non-biometric passcode on cold app launch and after admin-specified timeout, Intune will provide improved security for Mobile Application Management (MAM) enabled apps by restricting the use of biometric identification for access to corporate data. The settings will affect users who rely on Touch ID (iOS), Face ID (iOS), Android Biometric, or other future biometric authentication methods to access their APP/MAM-enabled applications. These settings will enable Intune admins to have more granular control over user access, eliminating cases where a device with multiple fingerprints or other biometric access methods can reveal corporate data to an incorrect user. In the Azure portal, open **Microsoft Intune**. Select **Mobile apps** > **App protection policies** > **Add a policy** > **Settings**. Locate the **Access** section for specific settings.

### Block app access based on unapproved device vendors and models  <!-- 1425689 ! -->
The Intune IT admin will be able to enforce a specified list of Android manufacturers, and/or iOS models through Intune App Protection Policies. The IT admin can provide a semicolon separated list of manufacturers for Android policies and device models for iOS policies. Intune App Protection Policies are for Android and iOS only. There will be two separate actions that can be performed on this specified list:
- A block from app access on devices that are not specified.
- Or, a selective wipe of corporate data on devices that are not specified. 

The user will be unable to access the targeted application if the requirements through the policy are not met. Based on settings, the user may either be blocked, or selectively wiped of their corporate data within the app. On iOS devices, this feature requires the participation of applications (i.e WXP, Outlook, Managed Browser, Yammer) to integrate the Intune APP SDK for the minimum version settings to be enforced for the targeted applications. This integration happens on a rolling basis and is dependent on the specific application teams. On Android, this feature requires the latest Company Portal. 

On end-user devices, the Intune client would take action based on a simple matching of the strings specified in the Intune blade for Application Protection Policies. This depends entirely on the value that the device reports. As such, the IT administrator is encouraged to ensure that the intended behavior is accurate. This can be accomplished by testing this setting based on a variety of device manufacturers and models targeted to a small user group. In Microsoft Intune, select **Mobile apps** > **App protection policies** to view and add app protection policies. For more information about app protection policies, see [What are app protection policies](app-protection-policy.md).

### Access actions for app protection policies <!-- 1483510 EEready -->
You will soon be able to configure app protection policies to explicitly wipe, block, or warn non-compliant devices. The newest action *wipe* removes your company’s corporate data from a device. If a wipe occurs, the device user is notified of both the reason for the wipe and remediation steps. For some settings, like minimum OS version, you will be able to apply multiple actions, such as block and wipe. These actions are triggered when the app is launched.

### New inventory information for Windows devices <!-- 1333569 eeready -->

For Windows devices, the following inventory information will be available per device in the **Hardware** tab (**Groups** > **All mobile devices** > **Devices** > choose the user's device > **View Properties** > **Hardware**):
- TPM
- Antivirus
- Antispyware
- Firewall
- UAC
- Battery
- Domain name

For more information on how this data is retrieved by the CSP, see the DeviceStatus entries in the [DeviceStatus CSP](https://docs.microsoft.com/en-us/windows/client-management/mdm/devicestatus-csp) article.

<!-- 1804 start -->

### Rules for removing devices <!-- 1609459 -->
New rules will be available that let you automatically remove devices that haven't checked in for a number of days that you set. To see the new rule, go to the **Intune** pane, select **Devices**, and select **Device removal rules**.

<!-- 1803 start -->

### Ability to deploy required line-of-business (LOB) apps to All Users on Windows 10 Desktop devices <!-- 1627835 RS4 -->
Customers will be able to deploy required line-of-business Windows 10 apps to install in device contexts. This will enable these apps to be available to all users on the device. This is only applicable on Windows 10 Desktop devices.

### Company Portal enrollment improved <!-- 1874230-->
Users enrolling a device by using the Company Portal on Windows 10 build 1703 and up will be able to complete the first step of enrollment without leaving the app.

### Updating the Help and Feedback experience on Company Portal app for Android <!--1631531 -->

The Help and Feedback experience on the Company Portal app for Android will be updated to align with best practices for Android apps. The Company Portal app for Android will be updated over the next few months to divide the **Help and Feedback** menu item to distinct **Help** and **Send Feedback** menu items. The **Help** page will feature a **Frequently Asked Questions** section and **Email Support** button to lead end users to upload logs to Microsoft and send email to company support describing the issue. **Send Feedback** will lead the user through a standard Microsoft feedback submission, which will prompt the user to choose whether, "I like something," "I don't like something," or "I have an idea."

<!-- the following are present prior to 1801 -->

### App Protection Policies  <!-- 679615 -->
Intune App Protection Policies will offer the ability to create global, default policies to quickly enable protection across all users in the entire tenant.

<!-- the following are present prior to 1711 -->

## Notices

There are no active notices at this time.

### See also
See [What’s New in Microsoft Intune](whats-new.md) for details on recent developments.



