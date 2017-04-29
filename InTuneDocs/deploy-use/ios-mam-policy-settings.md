---
# required metadata

title: iOS MAM policy settings | Microsoft Docs
description: This topic describes the mobile app management policy settings for iOS devices.
keywords:
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/18/2017
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 673ff872-943c-4076-931c-0be90363aea9

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: maxles
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-classic

---

#  iOS mobile app protection policy settings

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

The policy settings described in this topic can be [configured](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) for an app protection policy on the **All Settings** blade in the Azure portal.

There are two categories of policy settings: data relocation settings and access settings. In this topic, the term _**policy-managed apps**_ refers to apps that are configured with app protection policies.

##  Data relocation settings

| Setting | How to use | Default value |
|------|------|------|
| **Prevent iTunes and iCloud backups** | Choose **Yes** to prevent this app from backing up work or school data to iTunes and iCloud. Choose **No** to allow this app to back up of work or school data to iTunes and iCloud.| Yes |
| **Allow app to transfer data to other apps** | Specify what apps can receive data from this app: <ul><li> **Policy managed apps**: Allow transfer only to other policy-managed apps.</li> <li>**All apps**: Allow transfer to any app. </li> <li>**None**: Do not allow data transfer to any app, including other policy-managed apps.</li></ul> Additionally, if you set this option to **Policy managed apps** or **None**, the iOS 9 feature that allows Spotlight Search to search data within apps will be blocked. <br><br> There are some exempts apps and services to which Intune may allow data transfer. See  [Data transfer exemptions](#Data-transfer-exemptions) for a full list of apps and services. | All apps |
| **Allow app to receive data from other apps** | Specify what apps can transfer data to this app: <ul><li>**Policy managed apps**: Allow transfer only from other policy-managed apps.</li><li>**All apps**: Allow data transfer from any app.</li><li>**None**: Do not allow data transfer from any app, including other policy-managed apps.</li></ul> There are some exempts apps and services from which Intune may allow data transfer. See  [Data transfer exemptions](#Data-transfer-exemptions) for a full list of apps and services.  | All apps |
| **Prevent "Save As"** | Choose **Yes** to disable the use of the Save As option in this app. Choose **No** if you want to allow the use of Save As. <p>**Select which storage services corporate data can be saved to** <br>Users are able to save to the selected services (OneDrive for Busines, SharePoint and Local Storage). All other services will be blocked.</p> | No |
| **Restrict cut, copy and paste with other apps** | Specify when cut, copy, and paste actions can be used with this app. Choose from: <ul><li>**Blocked**:  Do not allow cut, copy, and paste actions between this app and any other app.</li><li>**Policy managed apps**: Allow cut, copy, and paste actions between this app and other policy-managed apps.</li><li>**Policy managed with paste in**: Allow cut or copy between this app and other policy-managed apps. Allow data from any app to be pasted into this app.</li><li>**Any app**: No restrictions for cut, copy, and paste to and from this app. | Any app |
|**Restrict web content to display in the Managed Browser** | Choose **Yes** to enforce web links in the app to be opened in the Managed Browser app. <br><br> For devices not enrolled in Intune, the web links in policy-managed apps can open only in the Managed Browser app. <br><br> If you are using Intune to manage your devices, see [Manage Internet access using managed browser policies with Microsoft Intune](manage-internet-access-using-managed-browser-policies.md). | No |
| **Encrypt app data** | For policy-managed apps, data is encrypted at rest using the device-level encryption scheme provided by iOS. When a PIN is required, the data is encrypted according to the settings in the app protection policy. <br><br> Go to the official Apple documentation [here](https://support.apple.com/HT202739) to see which iOS encryption modules are FIPS 140-2 certified or pending FIPS 140-2 certification. <br><br> Specify when work or school data in this app is encrypted. Choose from: <ul><li>**When device is locked**: All app data that is associated with this policy is encrypted while the device is locked.</li><li>**When device is locked and there are open files**: All app data associated with this policy is encrypted while the device is locked, except for data in the files that are currently open in the app.</li><li>**After device restart**:All app data associated with this policy is encrypted when the device is restarted, until the device is unlocked for the first time.</li><li>**Use device settings**: App data is encrypted based on the default settings on the device. When you enable this setting, the user is required to set up and use a PIN to access their device.  If there is no PIN, the apps will not open and the user will be prompted to set a PIN with the message “Your organization has required you to first enable a device PIN to access this app.” </li></ul> | When device is locked |
| **Disable contact sync** | Choose **Yes** to prevent the app from saving data to the native Contacts app on the device. If you choose **No**, the app can save data to the native Contacts app on the device. <br><br>When you perform a selective wipe to remove work or school data from the app, contacts synced directly from the app to the native Contacts app are removed. Any contacts synced from the native address book to another external source cannot be wiped. Currently this applies only to the Microsoft Outlook app. | No |
| **Disable printing** | Choose **Yes** to prevent the app from printing work or school data. | No |

> [!NOTE]
> None of the data relocation settings controls the Apple managed open-in feature on iOS devices. To use manage Apple open-in, see [Manage data transfer between iOS apps with Microsoft Intune](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).

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
| **Require PIN for access** | Choose **Yes** to require a PIN to use this app. The user is prompted to set up this PIN the first time they run the app in a work or school context. Default value = **Yes**.<br><br> Configure the following settings for PIN strength: <ul><li>**Number of attempts before PIN reset**: Specify the number of tries the user has to successfully enter their PIN before they must reset it. Default value = **5**.</li><li> **Allow simple PIN**: Choose **Yes** to allow users to use simple PIN sequences like 1234 or 1111. Choose **No** to prevent them from using simple sequences. Default value = **Yes**. </li><li> **PIN length**: Specify the minimum number of digits in a PIN sequence. Default value = **4**. </li><li> **Allow fingerprint instead of PIN (iOS 8.0+)**: Choose **Yes** to allow the user to use [Touch ID](https://support.apple.com/HT201371) instead of a PIN for app access. Default value = **Yes**</li></ul> On iOS devices, you can let the user prove their identity by using [Touch ID](https://support.apple.com/HT201371) instead of a PIN. When the user tries use this app with their work or school account, they are prompted to provide their fingerprint identity instead of entering a PIN. When this setting is enabled, the App-switcher preview image will be blurred while using a work or school account. </li></ul>| Require PIN: Yes <br><br> PIN reset attempts: 5 <br><br> Allow simple PIN: Yes <br><br> PIN length: 4 <br><br> Allow fingerprint: Yes |
| **Require corporate credentials for access** | Choose **Yes** to require the user to sign in with their work or school account instead of entering a PIN for app access. If you set this to **Yes**, this overrides the requirements for PIN or Touch ID.  | No |
| **Block managed apps from running on jailbroken or rooted devices** |  Choose **Yes** to prevent this app from running on jailbroken or rooted devices. The user will continue to be able to use this app for personal tasks, but will have to use a different device to access work or school data in this app. | Yes |
| **Recheck the access requirements after (minutes)** | Configure the following settings: <ul><li>**Timeout**: This is the number of minutes before the access requirements (defined earlier in the policy) are rechecked. For example, an admin turns on PIN in the policy, a user opens a MAM app, and must enter a pin. When using this setting, the user would not have to enter a PIN on any MAM app for another **30 minutes** (default value).</li><li>**Offline grace period**: This is the number of minutes that MAM apps can run offline, specify the time (in minutes) before the access requirements for the app are rechecked. Default value = **720** minutes (12 hours). After this period is expired, the app will require user authentication to AAD, so the app can continue to run.</li></ul>| Timeout: 30 <br><br> Offline: 720 |
| **Offline interval before app data is wiped (days)** | After this many days (defined by the admin) of running offline, the app itself will do a selective wipe. This selective wipe is the same wipe as the one that can be initiated by the admin in the MAM wipe work-flow. <br><br> | 90 days |
| **Disable app PIN when device PIN is managed** | Choose **Yes** to disable the app PIN when a device lock is detected on an enrolled device. | No |

##  Add-ins for Outlook app

Outlook recently brought add-ins to Outlook for iOS which let you integrate popular apps with the email client. Add-ins for Outlook are available on the web, Windows, Mac, and Outlook for iOS. Since add-ins are managed via Microsoft Exchange, users will be able to share data and messages across Outlook and unmanaged add-in applications unless add-ins are turned off for the user by their Exchange.

If you want to stop your end users from accessing and installing Outlook add-ins (this affects all Outlook clients), make sure you have the following changes to roles in the Exchange admin center:

- To prevent users from installing Office Store add-ins, remove the My Marketplace role from them.
- To prevent users from side loading add-ins, remove the My Custom Apps role from them.
- To prevent users from installing all add-ins, remove both, My Custom Apps and My Marketplace roles from them.

These instructions apply to Office 365, Exchange 2016, Exchange 2013 across Outlook on the web, Windows, Mac and mobile.

- Learn more about [add-ins for Outlook](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx).
- Learn more about [how to specify the administrators and users who can install and manage add-ins for Outlook app](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx).
