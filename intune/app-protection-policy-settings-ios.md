---
# required metadata

title: iOS app protection policy settings
titlesuffix: "Azure portal"
description: This topic describes the app protection policy settings for iOS devices."
keywords:
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 01/05/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 0f8b08f2-504c-4b38-bea2-b8a4ef0526b8

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: andcerat
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

#  iOS app protection policy settings
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

The policy settings described in this topic can be [configured](app-protection-policies.md) for an app protection policy on the **Settings** blade in the Azure portal.

There are two categories of policy settings: data relocation settings and access settings. In this topic, the term ***policy-managed apps*** refers to apps that are configured with app protection policies.

##  Data relocation settings

| Setting | How to use | Default value |
|------|------|------|
| **Prevent iTunes and iCloud backups** | Choose **Yes** to prevent this app from backing up work or school data to iTunes and iCloud. Choose **No** to allow this app to back up of work or school data to iTunes and iCloud.| Yes |
| **Allow app to transfer data to other apps** | Specify what apps can receive data from this app: <ul><li> **Policy managed apps**: Allow transfer only to other policy-managed apps.</li> <li>**All apps**: Allow transfer to any app. </li> <li>**None**: Do not allow data transfer to any app, including other policy-managed apps.</li></ul> Additionally, if you set this option to **Policy managed apps** or **None**, the iOS 9 feature that allows Spotlight Search to search data within apps will be blocked. <br><br> There are some exempt apps and services to which Intune may allow data transfer. See [data transfer exemptions](#data-transfer-exemptions) for a full list of apps and services. | All apps |
| **Allow app to receive data from other apps** | Specify what apps can transfer data to this app: <ul><li>**Policy managed apps**: Allow transfer only from other policy-managed apps.</li><li>**All apps**: Allow data transfer from any app.</li><li>**None**: Do not allow data transfer from any app, including other policy-managed apps.</li></ul> There are some exempt apps and services from which Intune may allow data transfer. See [data transfer exemptions](#data-transfer-exemptions) for a full list of apps and services. Multi-identity MAM enabled applications on non-enrolled iOS devices ignore this policy and allow all incoming data. | All apps |
| **Prevent "Save As"** | Choose **Yes** to disable the use of the Save As option in this app. Choose **No** if you want to allow the use of Save As. | No |
| **Restrict cut, copy and paste with other apps** | Specify when cut, copy, and paste actions can be used with this app. Choose from: <ul><li>**Blocked**:  Do not allow cut, copy, and paste actions between this app and any other app.</li><li>**Policy managed apps**: Allow cut, copy, and paste actions between this app and other policy-managed apps.</li><li>**Policy managed with paste in**: Allow cut or copy between this app and other policy-managed apps. Allow data from any app to be pasted into this app.</li><li>**Any app**: No restrictions for cut, copy, and paste to and from this app. | Any app |
|**Restrict web content to display in the Managed Browser** | Choose **Yes** to enforce web links in the app to be opened in the Managed Browser app. <br><br> For devices not enrolled in Intune, the web links in policy-managed apps can open only in the Managed Browser app. <br><br> If you are using Intune to manage your devices, see [Manage Internet access using managed browser policies with Microsoft Intune](app-configuration-managed-browser.md). | No |
| **Encrypt app data** | For policy-managed apps, data is encrypted at rest using the device-level encryption scheme provided by iOS. When a PIN is required, the data is encrypted according to the settings in the app protection policy. <br><br> Go to the official Apple documentation [here](https://support.apple.com/HT202739) to see which iOS encryption modules are FIPS 140-2 certified or pending FIPS 140-2 certification. <br><br> Specify when work or school data in this app is encrypted. Choose from: <ul><li>**When device is locked**: All app data that is associated with this policy is encrypted while the device is locked.</li><li>**When device is locked and there are open files**: All app data associated with this policy is encrypted while the device is locked, except for data in the files that are currently open in the app.</li><li>**After device restart**:All app data associated with this policy is encrypted when the device is restarted, until the device is unlocked for the first time.</li><li>**Use device settings**: App data is encrypted based on the default settings on the device. </li></ul> When you enable this setting, the user may be required to set up and use a PIN to access their device.  If there is no device PIN and encryption is required, the apps will not open and the user will be prompted to set a PIN with the message “Your organization has required you to first enable a device PIN to access this app.”  | When device is locked |
| **Disable contact sync** | Choose **Yes** to prevent the app from saving data to the native Contacts app on the device. If you choose **No**, the app can save data to the native Contacts app on the device. <br><br>When you perform a selective wipe to remove work or school data from the app, contacts synced directly from the app to the native Contacts app are removed. Any contacts synced from the native address book to another external source cannot be wiped. Currently this applies only to the Microsoft Outlook app. | No |
| **Disable printing** | Choose **Yes** to prevent the app from printing work or school data. | No |
| **Select which storage services corporate data can be saved to** | Users are able to save to the selected services (OneDrive for Business, SharePoint and Local Storage). All other services will be blocked. | 0 Selected |

> [!NOTE]
> None of the data relocation settings controls the Apple managed open-in feature on iOS devices. To use manage Apple open-in, see [Manage data transfer between iOS apps with Microsoft Intune](data-transfer-between-apps-manage-ios.md).

## Data transfer exemptions

There are some exempt apps and platform services that Intune app protection policy may allow data transfer to and from in certain scenarios. This list is subject to change and reflects the services and apps considered useful for secure productivity.

| App/service name(s) | Description |
| ---- | --- |
|tel; telprompt | Native phone app |
| skype | Skype |
| app-settings | Device settings |
| itms; itmss; itms-apps; itms-appss; itms-services | App Store |
| calshow | Native Calendar |




## Access settings

| Setting | How to use | Default value |
|------|------|------|
| **Require PIN for access** | Choose **Yes** to require a PIN to use this app. The user is prompted to set up this PIN the first time they run the app in a work or school context. The PIN is applied when working either online or offline. Default value = **Yes**.<br><br> Configure the following settings for PIN strength: <ul><li>**Select Type**: Set a requirement for either numeric or passcode type PINs before accessing an app that has app protection policies applied. Numeric requirements involve only numbers, while a passcode can be defined with atleast 1 letter or special character. Default value = **Numeric**.</li><li>**Number of attempts before PIN reset**: Specify the number of tries the user has to successfully enter their PIN before they must reset it. Default value = **5**. <br><br> This policy setting format supports a positive whole number.</li><li> **Allow simple PIN**: Choose **Yes** to allow users to use simple PIN sequences like 1234, 1111, abcd or aaaa. Choose **No** to prevent them from using simple sequences. Default value = **Yes**. </li><li> **PIN length**: Specify the minimum number of digits in a PIN sequence. Default value = **4**. </li><li> **Allow fingerprint instead of PIN (iOS 8.0+)**: Choose **Yes** to allow the user to use [Touch ID](https://support.apple.com/HT201371) instead of a PIN for app access. Default value = **Yes**.</li></ul> On iOS devices, you can let the user prove their identity by using [Touch ID](https://support.apple.com/HT201371) instead of a PIN. When the user tries use this app with their work or school account, they are prompted to provide their fingerprint identity instead of entering a PIN. Intune uses the [LocalAuthentication](https://developer.apple.com/documentation/localauthentication/) API like other apps to authenticate users using TouchID. More information about how TouchID works for apps can be found in the [iOS Security Guide](https://www.apple.com/business/docs/iOS_Security_Guide.pdf). When this setting is enabled, the App-switcher preview image will be blurred while using a work or school account. </li></ul><!-- <br><br>You can require a PIN expiration for targeted iOS apps. You can configure the PIN requirement and expiration date in days through the Azure portal. When required, a user will be required to set and use a new PIN before getting access to an iOS app. Only iOS apps that have app protection enabled with the Intune App SDK will support this feature.-->| Require PIN for access: Yes <br><br> Select Type: Numeric <br><br> PIN reset attempts: 5 <br><br> Allow simple PIN: Yes <br><br> PIN length: 4 <br><br> Allow fingerprint: Yes |
| **Require corporate credentials for access** | Choose **Yes** to require the user to sign in with their work or school account instead of entering a PIN for app access. If you set this to **Yes**, this overrides the requirements for PIN or Touch ID.  | No |
| **Block managed apps from running on jailbroken or rooted devices** |  Choose **Yes** to prevent this app from running on jailbroken or rooted devices. The user will continue to be able to use this app for personal tasks, but will have to use a different device to access work or school data in this app. | Yes |
| **Recheck the access requirements after (minutes)** | Configure the following settings: <ul><li>**Timeout**: This is the number of minutes before the access requirements (defined earlier in the policy) are rechecked. For example, an admin turns on PIN in the policy, a user opens a Intune-managed app, and must enter a PIN. When using this setting, the user would not have to enter a PIN on any MAM app for another **30 minutes** (default value). <br><br>**Note:** On iOS, the PIN is shared amongst all Intune-managed apps of the **same publisher**. The PIN timer for a specific PIN is reset once the app leaves the foreground on the device. The user would not have to enter a PIN on any Intune-managed app that shares its PIN for the duration of the timeout defined in this setting. <br><br> This policy setting format supports a positive whole number.</li><li>**Offline grace period**: This is the number of minutes that MAM apps can run offline, specify the time (in minutes) before the access requirements for the app are rechecked. Default value = **720** minutes (12 hours). After this period is expired, the app will require user authentication to AAD, so the app can continue to run.<br><br> This policy setting format supports a positive whole number.</li></ul>| Timeout: 30 <br><br> Offline: 720 |
| **Offline interval before app data is wiped (days)** | After this many days (defined by the admin) of running offline, the app will require the user to connect to the network and re-authenticate. If the user successfully authenticates, they can continue to access their data and the offline interval will reset.  If the user fails to authenticate, the app will perform a selective wipe of the users account and data.  See [How to wipe only corporate data from Intune-managed apps](https://docs.microsoft.com/intune/apps-selective-wipe) for more information on what data is removed with a selective wipe. <br><br> This policy setting format supports a positive whole number. | 90 days |
| **Disable app PIN when device PIN is managed** | Choose **Yes** to disable the app PIN when a device lock is detected on an enrolled device. <br><br> **Note:** Requires app to have Intune SDK version 7.0.1 or above. | No |
| **Require minimum iOS operating system** | Choose **Yes** to require a minimum iOS operating system to use this app. The user will be blocked from access if the iOS version on the device does not meet the requirement. <br> **Note:** Requires app to have Intune SDK version 7.0.1 or above. | No |
| **Require minimum iOS operating system (Warning only)** | Choose **Yes** to require a minimum iOS operating system to use this app. The user will see a notification if the iOS version on the device does not meet the requirement. This notification can be dismissed. <br> **Note:** Requires app to have Intune SDK version 7.0.1 or above. | No |
| **Require minimum app version** | Choose **Yes** to require a minimum app version to use the app. The user is blocked from access if the app version on the device does not meet the requirement.<br><br>As apps often have distinct versioning schemes between them, create a policy with one minimum app version targeting one app (for example, "Outlook version policy"). <br><br> This policy setting format supports either major.minor, major.minor.build, major.minor.build.revision. <br><br> **Note:** Requires app to have Intune SDK version 7.0.1 or above. | No | 
| **Require minimum app version (Warning only)** | Choose **Yes** to recommend a minimum app version to use this app. The user sees a notification if the app version on the device does not meet the requirement. This notification can be dismissed.<br><br>As apps often have distinct versioning schemes between them, create a policy with one minimum app version targeting one app (for example, "Outlook version policy"). <br><br> This policy setting format supports either major.minor, major.minor.build, major.minor.build.revision. <br><br> **Note:** Requires app to have Intune SDK version 7.0.1 or above. | No | 
| **Require minimum Intune app protection policy SDK version** | Choose **Yes** to require a minimum Intune app protection policy SDK version on the app to use. The user is blocked from access if the app’s Intune app protection policy SDK version does not meet the requirement. <br> <br> To learn more about the Intune app protection policy SDK, see [Intune App SDK overview](app-sdk.md). <br><br> This policy setting format supports either major.minor, major.minor.build, major.minor.build.revision. <br><br> **Note:** Requires app to have Intune SDK version 7.0.1 or above. | No |


##  Add-ins for Outlook app

Outlook recently brought add-ins to Outlook for iOS which let you integrate popular apps with the email client. Add-ins for Outlook are available on the web, Windows, Mac, and Outlook for iOS. Since add-ins are managed via Microsoft Exchange, users will be able to share data and messages across Outlook and unmanaged add-in applications unless add-ins are turned off for the user by their Exchange.

If you want to stop your end users from accessing and installing Outlook add-ins (this affects all Outlook clients), make sure you have the following changes to roles in the Exchange admin center:

- To prevent users from installing Office Store add-ins, remove the My Marketplace role from them.
- To prevent users from side loading add-ins, remove the My Custom Apps role from them.
- To prevent users from installing all add-ins, remove both, My Custom Apps and My Marketplace roles from them.

These instructions apply to Office 365, Exchange 2016, Exchange 2013 across Outlook on the web, Windows, Mac and mobile.

- Learn more about [add-ins for Outlook](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx).
- Learn more about [how to specify the administrators and users who can install and manage add-ins for Outlook app](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx).
