---
# required metadata
title: iOS device settings in Microsoft Intune - Azure | Microsoft Docs
titleSuffix:
description: Add, configure, or create settings on iOS devices to restrict features, including setting password requirements, control the locked screen, use built-in apps, add restricted or approved apps, handle bluetooth devices, connect to the cloud for backup and storage, enable kiosk mode, add domains, and control how users interact with the Safari web browser in Microsoft Intune.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/14/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology:

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
---

# iOS device settings to allow or restrict features using Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

This article lists and describes the different settings you can control on iOS devices. As part of your mobile device management (MDM) solution, use these settings to allow or disable features, set password rules, allow or restrict specific apps, and more.

These settings are added to a device configuration profile in Intune, and then assigned or deployed to your iOS devices.

> [!NOTE]
> These settings use Apple's MDM settings. For more information on these settings, see [Apple's mobile device management settings](https://support.apple.com/guide/mdm/welcome/web) (opens Apple's web site).

## Before you begin

[Create a device restrictions configuration profile](device-restrictions-configure.md#create-the-profile).

## General

- **Share usage data**: Choose **Block** to prevent the device from sending diagnostic and usage data to Apple. **Not configured** (default) allows this data to be sent.
  - **Diagnostics submission settings modification (supervised only)**: **Block** prevents the user from changing the diagnostic submission and app analytics settings in **Diagnostics and Usage** (device Settings). **Not configured** (default) allows the user to change these device settings.

    This feature applies to:  
    - iOS 9.3.2 and newer

- **Screen capture**: Choose **Block** to prevent screenshots or screen captures on the device. In iOS 9.0 and newer, it also blocks screen recordings. **Not configured** (default) lets the user capture the screen contents as an image or as a video.
  - **Remote screen observation by Classroom app (supervised only)**: Choose **Block** to prevent the Classroom app from remotely viewing the screen on the device. **Not configured** (default) allows the Apple Classroom app to view the screen.

    This feature applies to:  
    - iOS 9.3 and newer

  - **Unprompted screen observation by Classroom app (supervised only)**: If set to **Allow**, teachers can silently observe the screen of students iOS devices using the Classroom app without the students' knowledge. Student devices enrolled in a class using the Classroom app automatically give permission to that course’s teacher. **Not configured** (default) prevents this feature.
- **Untrusted TLS certificates**: Choose **Block** to prevent untrusted Transport Layer Security (TLS) certificates on the device. **Not configured** (default) allows TLS certificates.
- **Enterprise app trust**: Choose **Block** to remove the **Trust Enterprise Developer** button in Settings > General > Profiles & Device Management on the device. **Not configured** (default) lets the user choose to trust apps that aren't downloaded from the app store.
- **Account modification (supervised only)**: When set to **Block**, the user can't update the device-specific settings from the iOS settings app. For example, the user can't create new device accounts, or change the user name or password. **Not configured** (default) allows users to change these settings.

  This feature also applies to settings accessible from the iOS settings app, such as Mail, Contacts, Calendar, Twitter, and more. This feature doesn't apply to apps with account settings that aren't configurable from the iOS settings app, such as the Microsoft Outlook app.
- **Screen time (supervised only)**: Choose **Block** to prevent users from setting their own restrictions in Screen Time (device settings). **Not configured** allows the user to configure device restrictions (such as parental controls or content, and privacy restrictions) on the device.

  This setting was renamed from **Enabling restrictions in the device settings**. Impact of this change:  
  
  - iOS 11.4.1 and earlier: **Block** prevents end users from setting their own restrictions in the device settings. The behavior is the same; and there are no changes for end users.
  - iOS 12.0 and newer: **Block** prevents end users from setting their own **Screen Time** in the device settings (Settings > General > Screen Time), including content and privacy restrictions. Devices upgraded to iOS 12.0 won't see the restrictions tab in the device settings anymore (Settings > General > Device Management > Management Profile > Restrictions). These settings are in **Screen Time**.
  
- **Use of the erase all content and settings option on the device (supervised only)**: Choose **Block** so users can't use the erase all content and settings option on the device (supervised only). **Not configured** (default) gives users access to these settings.
- **Device name modification (supervised only)**: Choose **Block** so the device name can't be changed. **Not configured** (default) allows the user to change the name of the device.
- **Notification settings modification (supervised only)**: Choose **Block** so the notification settings can't be changed. **Not configured** (default) allows the user to change the device notification settings.
- **Wallpaper modification (supervised only)**: **Block** prevents the wallpaper from being changed. **Not configured** (default) allows the user to change the wallpaper on the device.
- **Enterprise app trust settings modification (supervised only)**: **Block** prevents the user from changing the enterprise app trust settings on supervised devices. **Not configured** (default) allows the user to trust apps that aren't downloaded from the app store.
- **Configuration profile changes (supervised only)**: **Block** prevents configuration profile changes on the device. **Not configured** (default) allows the user to install configuration profiles.
- **Activation Lock (supervised only)**: Choose **Allow** to enable Activation Lock on supervised iOS devices. Activation Lock makes it harder for a lost or stolen device to be reactivated.
- **Block app removal (supervised only)**: Choose **Block** to prevent users from removing apps. **Not configured** (default) allows users to remove apps from the device.
- **Blocks USB Restricted mode (supervised only)**: Choose **Block** to disable USB Restricted mode on supervised devices. USB Restricted mode prevents USB accessories from exchanging data with a device that's locked for over an hour. **Not configured** (default) allows USB Restricted mode.
- **Force automatic date and time (supervised only)**: **Require** forces supervised devices to set the Date & Time automatically. The device's time zone is updated when the device has cellular connections or has Wi-Fi with location services enabled.
- **Require students to request permission to leave Classroom course (supervised only)**: **Require** forces students enrolled in an unmanaged course using the Classroom app to request permission from the teacher to leave the course. **Not configured** (default) doesn't force the student to ask for permission.

  This feature applies to:  
  - iOS 11.3 and newer

- **Allow Classroom to lock to an app and lock the device without prompting (supervised only)**: **Enable** allows teacher to lock apps or lock the device using the Classroom app without prompting the student. Locking apps means the device can only access teacher specified apps. **Not configured** (default) prevents teachers from locking apps or devices using the Classroom app without prompting the student. 

  This feature applies to:  
  - iOS 11.0 and newer

- **Automatically join Classroom classes without prompting (supervised only)**: **Enable** automatically allows students to join a class that is in the Classroom app without prompting the teacher. **Not configured** (default) prompts the teacher that students want to join a class that is in the Classroom app.

  This feature applies to:  
  - iOS 11.0 and newer

- **Allow over-the-air PKI updates**: **Allow** lets your users  receive software updates without connecting their devices to a computer.
- **Limit ad tracking**: Choose **Limit** to disable the device advertising identifier. **Not configured** (default) keeps it enabled.
- **Block VPN creation (supervised only)**: **Block** prevents users from creating VPN configuration settings. **Not configured** (default) lets users create VPNs on the device.
- **Modifying eSIM settings (supervised only)**: **Block** prevents users from removing or adding a cellular plan to the eSIM on the device. **Not configured** (default) allows users to change these settings.

  This feature applies to:  
  - iOS 12.1 and newer

- **Defer software updates (supervised only)**: When set to **Not configured** (default), software updates are shown on the device as Apple releases them. For example, if an iOS update gets released by Apple on a specific date, then that update naturally shows up on the device around the release date.

  **Enable** allows you to delay when software updates are shown on devices, from 0-90 days. This setting doesn't control when updates are or aren't installed. 

  - **Delay visibility of software updates**: Enter a value from 0-90 days. When the delay expires, users get a notification to update to the earliest version of the OS available when the delay was triggered.

    For example, if iOS 12.a is available on **January 1**, and **Delay visibility** is set to **5 days**, then iOS 12.a isn't shown as an available update on end user devices. On the **sixth day** following the release, that update is available, and end users can install it.

    This setting applies to:  
    - iOS 11.3 and newer

## Password

- **Password**: **Require** the end user to enter a password to access the device. **Not configured** (default) allows users to access the device without entering a password.
  - **Simple passwords**: Choose **Block** to require more complex passwords. **Not configured** allows simple passwords, such as `0000` and `1234`.
  - **Required password type**: Choose the type of password your organization require. Your options:
    - **Device default**
    - **Numeric**
    - **Alphanumeric**
  - **Number of non-alphanumeric characters in password**: Enter the number of symbol characters, such as `#` or `@`, that must be included in the password.
  - **Minimum password length**: Enter the minimum length a user must enter (between 4 and 14 characters).
  - **Number of sign-in failures before wiping device**: Enter the number of failed sign-ins to allow before the device is wiped (between 4-11).
  
    iOS has built-in security that can impact this setting. For example, iOS may delay triggering the policy depending on the number of sign in failures. It may also consider repeatedly entering the same passcode as one attempt. Apple's [iOS security guide](https://www.apple.com/business/site/docs/iOS_Security_Guide.pdf) (opens Apple's web site) is a good resource, and provides more specific details on passcodes.
  
  - **Maximum minutes after screen lock before password is required**<sup>1</sup>: Enter how long the device stays idle before the user must reenter their password. If the time you enter is longer than what's currently set on the device, then the device ignores the time you enter. Supported on iOS 8.0 and newer devices.
  - **Maximum minutes of inactivity until screen locks**<sup>1</sup>: Enter the maximum number of minutes of inactivity allowed on the device until the screen locks. If the time you enter is longer than what's currently set on the device, then the device ignores the time you enter. When set to **immediately**, the screen locks based on the device's minimum time. On iPhone, it's 30 seconds. On iPad, it's two minutes.
  - **Password expiration (days)**: Enter the number of days before the device password must be changed.
  - **Prevent reuse of previous passwords**: Enter the number of new passwords that must be used until an old one can be reused.
  - **Touch ID and Face ID unlock**: Choose **Block** to prevent using a fingerprint or face to unlock the device. **Not configured** allows the user to unlock the device using these methods.

    Face ID is available on iOS 11.0 and newer. Blocking this setting also prevents using FaceID authentication to unlock the device.

- **Passcode modification (supervised only)**: Choose **Block** to stop the passcode from being changed, added, or removed. Changes to passcode restrictions are ignored on supervised devices after blocking this feature. **Not configured** (default) allows passcodes to be added, changed, or removed.

  - **Touch ID and Face ID modification (supervised only)**: **Block** stops the user from changing, adding, or removing TouchID fingerprints and Face ID. **Not configured** (default) allows the user to update the TouchID fingerprints and Face ID on the device.

    Face ID is available on iOS 11.0 and newer. Blocking this setting also stops the user from changing, adding, or removing FaceID authentication.

- **Block password AutoFill (supervised only)**: Choose **Block** to prevent using the AutoFill Passwords feature on iOS. Choosing **Block** also has the following impact:

  - Users aren't prompted to use a saved password in Safari or in any apps.
  - Automatic Strong Passwords are disabled, and strong passwords aren't suggested to users.

  **Not configured** (default) allows these features.

- **Block password proximity requests (supervised only)**: Choose **Block** so a user’s device doesn't request passwords from nearby devices. **Not configured** (default) allows these password requests.
- **Block password sharing (supervised only)**: **Block** prevents sharing passwords between devices using AirDrop. **Not configured** (default) allows passwords to be shared.
- **Require Touch ID or Face ID authentication for password or credit card information AutoFill (supervised only)**: When set to **Require**, users must authenticate using TouchID or FaceID before passwords or credit card information can be auto filled in Safari and other apps. **Not configured** (default) allows users to control this feature in the device settings.

  This feature applies to:  
  - iOS 11.0 and newer
  
<sup>1</sup>When you configure the **Maximum minutes of inactivity until screen locks** and **Maximum minutes after screen lock before password is required** settings, they're applied in sequence. For example, if you set the value for both settings to **5** minutes, the screen turns off automatically after five minutes, and the device is locked after an additional five minutes. However, if the user turns off the screen manually, the second setting is immediately applied. In the same example, after the user turns off the screen, the device locks five minutes later.

## Locked Screen Experience

- **Control Center access while device locked**: Choose **Block** to prevent access to the Control Center app while device is locked. **Not configured** (default) allows users access to the Control Center app when the device is locked.
- **Notifications while device locked**: **Block** prevents access to notifications when the device is locked. **Not configured** (default) allows the user to access the notifications without unlocking the device.
- **Wallet notifications while device locked**: **Block** prevents access to the Wallet app when the device is locked. **Not configured** (default) allows the user to access the Wallet app while the device is locked.
- **Today view while device locked**: **Block** prevents access to the Today view when the device is locked. **Not configured** (default) allows the user to see the Today view when the device is locked.

## App Store, Doc Viewing, Gaming

- **App store (supervised only)**: **Block** prevents access to the app store on supervised devices. **Not configured** (default) allows access.

  Starting with iOS 13.0, this setting requires supervised devices.

  - **Installing apps from App Store (supervised only)**: Choose **Block** to block the app store from the device home screen. End users can continue to use iTunes or the Apple Configurator to install apps. **Not configured** (default) allows the app store on the home screen.
  - **Automatic app downloads (supervised only)**: Choose **Block** to prevent automatic downloading of apps bought on other devices. It doesn't affect updates to existing apps. **Not configured** (default) allows apps bought on other iOS devices to download on the device.
- **Require iTunes Store password for all purchases**: **Require** the user to enter the Apple ID password for each in-app or ITunes purchase. **Not configured** (default) allows purchases without prompting for a password every time.
- **In-app purchases**: Choose **Block** to prevent in-app purchases from the store. **Not configured** (default) allows store purchases within a running app.
- **Explicit iTunes music, podcast, or news content (supervised only)**: Choose **Block** to prevent explicit iTunes music, podcast, or news content. **Not configured** (default) allows the device to access content rated as adult from the store. iOS 13 and newer may require supervised only devices. 

  Starting with iOS 13.0, this setting requires supervised devices.

- **Download content from iBook store flagged as 'Erotica'**: Choose **Block** to prevent stops users from downloading media from the iBook store that's tagged as erotica. **Not configured** (default) allows the user to download books with the "Erotica" category.
- **Viewing corporate documents in unmanaged apps**: **Block** prevents viewing corporate documents in unmanaged apps. **Not configured** (default) allows corporate documents to be viewed in any app. For example, you want to prevent users from saving files from the OneDrive app to Dropbox. Configure this setting as **Block**. After the device receives the policy (for example, after a restart), it no longer allows saving.
  - **Allow managed apps to write contacts to unmanaged contacts accounts**: When set to **Allow**, managed apps, such as the Outlook mobile app, can save or sync contact information, including business and corporate contacts, to the built-in iOS Contacts app. When set to **Not configured** (default), managed apps can't save or sync contact information to the built-in iOS Contacts app on the device.
  
    To use this setting, set the **Viewing corporate documents in unmanaged apps** setting to **Block**.

  - **Allow unmanaged apps to read from managed contacts accounts**: When set to **Allow**, unmanaged apps, such as the built-in iOS Contacts app, can read and access contact information from managed apps, including the Outlook mobile app. **Not configured** (default) prevents reading, including removing duplicates, from the built-in Contacts app on the device.  
  
    This setting allows or prevents reading contact information. It doesn't control syncing contacts between the apps.
  
    To use this setting, set the **Viewing corporate documents in unmanaged apps** setting to **Block**.

  For more information about these two settings and their impact on Outlook for iOS contact export synchronization, see [Support Tip: Enabling Outlook iOS Contact Sync with iOS12 MDM Controls](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Use-Intune-custom-profile-settings-with-the-iOS/ba-p/298453).
  
- **Viewing non-corporate documents in corporate apps**: **Block** prevents viewing non-corporate documents in corporate apps. **Not configured** (default) allows any document to be viewed in corporate managed apps.

    When **Viewing non-corporate documents in corporate apps** is set to **Block**, it prevents contact export synchronization in Outlook for iOS. For more information, see [Support Tip: Enabling Outlook iOS Contact Sync with iOS12 MDM Controls](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Use-Intune-custom-profile-settings-with-the-iOS/ba-p/298453).
  
- **Treat AirDrop as an unmanaged destination**: **Require** forces AirDrop to be considered an unmanaged drop target. It stops managed apps from sending data using Airdrop. 
- **Adding Game Center friends (supervised only)**: **Block** prevents users from adding Game Center friends. **Not configured** (default) allows the user to add friends in Game Center.

  Starting with iOS 13.0, this setting requires supervised devices.

- **Game Center (supervised only)**: **Block** the use of the Game Center app. **Not configured** (default) allows using the Game Center app on the device.
- **Multiplayer gaming (supervised only)**: Choose **Block** to prevent multiplayer gaming. **Not configured** (default) allows the user to play multiplayer games on the device.

  Starting with iOS 13.0, this setting requires supervised devices.

- **Ratings region**: Choose the ratings region you want to use for allowed downloads. And then choose the allowed ratings for **Movies**, **TV Shows**, and **Apps**.

## Built-in Apps

- **Camera (supervised only)**: Choose **Block** to prevent access to the camera on the device. **Not configured** (default) allows access to the device's camera.

  Starting with iOS 13.0, this setting requires supervised devices.

  - **FaceTime (supervised only)**: **Block** to prevent access to the FaceTime app. **Not configured** (default) allows access to the FaceTime app on the device.

    Starting with iOS 13.0, this setting requires supervised devices.

- **Siri**: **Block** prevents access to Siri. **Not configured** (default) allows using the Siri voice assistant on the device.
  - **Siri while device is locked**: Choose **Block** to prevent access to Siri when the device is locked. **Not configured** (default) allows using the Siri voice assistant on the device when it's locked.
  - **Siri profanity filter (supervised only)**: **Require** prevents Siri from dictating, or speaking profane language.
  - **Siri to query user-generated content from the internet (supervised only)**: **Block** prevents Siri from accessing websites to answer questions. **Not configured** (default) allows Siri to access user-generated content from the internet.
- **Server-side logging for Siri commands**: When set to **Disable**, server-side Siri logging is turned off. It can also prevent logging user requests on Siri servers. **Not configured** (default) logs Siri commands on the server-side. This setting is not dependent on the Siri setting being blocked or not configured.

  This feature applies to:  
  - iOS 12.2 and newer

- **Apple News (supervised only)**: Choose **Block** to prevent access to the Apple News app on the device. **Not configured** (default) allows using the Apple News app.
- **iBooks store (supervised only)**: **Block** prevents access to the iBooks store. **Not configured** (default) allows users to browse and buy books from the iBooks store.
- **Messages app on the device (supervised only)**: **Block** prevents users from using the Messages app for iMessage. If the device supports text messaging, the user can still send and receive text messages using SMS. **Not configured** (default) allows using the Messages app to send and read messages over the internet.
- **Podcasts (supervised only)**: **Block** prevents users using the Podcasts app. **Not configured** (default) allows using the Podcasts app.
- **Music service (supervised only)**: **Block** reverts the Music app to classic mode and disables the Music service. **Not configured** (default) allows using the Apple Music app.
- **iTunes Radio service (supervised only)**: **Block** prevents users from using the iTunes Radio app. **Not configured** (default) allows using the iTunes Radio app.
- **iTunes store (supervised only)**: **Not configured** (default) allows iTunes on the devices. **Block** prevents users from using iTunes on the device. 

  This feature applies to:  
  - iOS 4.0 and newer

- **Find my iPhone (supervised only)**: **Not configured** (default) allows using this Find My app feature to get the approximate location of the device. **Block** prevents this feature in the Find My app. 

  This feature applies to:  
  - iOS 13.0 and newer

- **Find my Friends (supervised only)**: **Not configured** (default) allows using this Find My app feature to find family and friends from an Apple device or iCloud.com. **Block** prevents this feature in the Find My app.

  This feature applies to:  
  - iOS 13.0 and newer

- **Changes to the Find My Friends app settings (supervised only)**: **Block** prevents changes to the Find My Friends app settings. **Not configured** (default) allows the user to change settings for the Find My Friends app.
- **Spotlight search to return results from internet (supervised only)**: **Block** stops Spotlight from returning any results from an Internet search. **Not configured** (default) allows Spotlight search connect to the Internet to provide search results.
- **Block removal of system apps from device (supervised only)**: Choosing **Block** disables the ability to remove system apps from the device. **Not configured** (default) allows users to remove system apps.

### Safari

- **Safari (supervised only)**: **Block** using the Safari browser on the device. **Not configured** (default) allows users to use the Safari browser.

  Starting with iOS 13.0, this setting requires supervised devices.

- **Autofill (supervised only)**: **Block** disables the autofill feature in Safari on the device. **Not configured** (default) allows users to change autocomplete settings in the web browser.

  Starting with iOS 13.0, this setting requires supervised devices.

- **Cookies**: Choose how cookies are handled on the device. Your options:
  - Allow
  - Block all cookies
  - Allow cookies from visited web sites
  - Allow cookies from current web site
- **JavaScript**: **Block** prevents Java scripts in the browser from running on the device. **Not configured** (default) allows Java scripts.
- **Fraud warnings**: **Require** fraud warnings to be shown in the web browser on the device. **Not configured** (default) disables this feature.
- **Pop-ups**: **Block** to disable the pop-up blocker in the web browser. **Not configured** (default) allows the pop-up blocker.

## Restricted apps

In the restricted apps list, you can configure one of the following lists:

- **Prohibited apps**: A list of apps not managed by Intune that you don't want installed on the device. If a user installs an app from this list, you're notified by Intune.
- **Approved apps**: A list of apps that users are allowed to install. To stay compliant, users must not install other apps. Apps that are managed by Intune are automatically allowed. If a user installs an app from this list, you're notified by Intune.

To add apps to these lists, you can:

- **Add** the iTunes App store URL of the app you want. For example, to add the Microsoft Work Folders app, enter `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  To find the URL of an app, open the iTunes App Store, and search for the app. For example, search for `Microsoft Remote Desktop` or `Microsoft Word`. Select the app, and copy the URL.

  You can also use iTunes to find the app, and then use the **Copy Link** task to get the app URL.

- Import a CSV file with details about the app, including the URL. Use the `<app url>, <app name>, <app publisher>` format. Or, Export an existing list that includes the restricted apps list in the same format.

> [!IMPORTANT]
> Device profiles that use the restricted app settings must be assigned to groups of users.

## Show or hide apps (supervised only)

In the show or hide apps list, you can configure one of the following lists on supervised devices running iOS 9.3 or newer.

- **Hidden apps**: Enter a list of apps that are hidden from users. Users can't view, or open these apps.
- **Visible apps**: Enter a list of apps that users can view and launch. No other apps can be viewed or launched.

To add apps to these lists, you can:

- **Add** the iTunes App store URL, or Bundle ID and app name of the app you want. For example, to add the Microsoft Work Folders app, enter `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  To find the URL of an app, open the iTunes App Store, and search for the app. For example, search for `Microsoft Remote Desktop` or `Microsoft Word`. Select the app, and copy the URL.

  You can also use iTunes to find the app, and then use the **Copy Link** task to get the app URL.
  
  For more information about locating a Bundle ID, see [How to find the bundle ID for an iOS app](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app).

- Import a CSV file with details about the app, including the URL. Use the `<app url>, <app name>, <app publisher>` format. Or, Export an existing list that includes the restricted apps list in the same format.

  You can also show or hide built-in apps and line-of-business apps by entering the Bundle ID and app name. For a list of built-in apps you can hide, see [built-in Apple apps](https://support.apple.com/HT208094) (opens Apple's web site).

> [!IMPORTANT]  
> For all supported iOS versions, use `iTunes` with the `apple.com` portion of the URL. If you use `apps`, it fails. This is a known issue, and is being fixed in a future release. When fixed, you can use `iTunes` or `apps` in the URL.
>  
> MS Word example:  
> - With the following URL, the app is *visible* or *hidden* on the device (works): 
>   - https://**itunes**.apple.com/de/app/microsoft-word/id586447913  
>
> - With the following URL, the app isn't *visible* or *hidden* on the device (doesn't work): 
>   - https://**apps**.apple.com/de/app/microsoft-word/id586447913 

## Wireless

- **Data roaming**: Choose **Block** to prevent data roaming over the cellular network. **Not configured** (default) allows data roaming when the device is on a cellular network.
- **Global background fetch while roaming**: **Block** prevents using the global background fetch feature when roaming over the cellular network. **Not configured** (default) allows the device to fetch data, such as email, when it's roaming on a cellular network.
- **Voice dialing**: Choose **Block** to prevent users from using the voice dialing feature on the device. **Not configured** (default) allows voice dialing on the device.
- **Voice roaming**: Choose **Block** to prevent voice roaming over the cellular network. **Not configured** (default) allows voice roaming when the device is on a cellular network.
- **Changes to app cellular data usage settings (supervised only)**: Choose **Block** to prevent changes to the app cellular data usage settings. **Not configured** (default) allows the user to control which apps are allowed to use cellular data.
- **Changes to cellular plan settings (supervised only)**: **Block** prevents users from changing any settings in the cellular plan. **Not configured** (default) allows users to make changes.

  This feature applies to:  
  - iOS 11.0 and newer

- **Personal Hotspot**: **Block** turns off the personal hotspot on the users' device with every device sync. This setting might not be compatible with some carriers. **Not configured** (default) keeps the personal hotspot configuration as the default set by the user.
- **User modification of Personal Hotspot (supervised only)**: When set to **Block**, the user can't change the personal hotspot setting. **Not configured** (default) allows end users to enable or disable their personal hotspot.

  If you block this setting and block the **Personal Hotspot** setting, the personal hotspot is turned off.

  This feature applies to:  
  - iOS 12.2 and newer

- **Join Wi-Fi networks only using configuration profiles (supervised only)**: **Require** forces the device to use only Wi-Fi networks set up through Intune configuration profiles. **Not configured** (default) allows the device to use other Wi-Fi networks.
- **Modification of Wi-Fi state (supervised only)**: **Not configured** (default) allows users to turn on, or turn off Wi-Fi on the device. **Block** prevents turning Wi-Fi on or off.
- **Cellular usage rules (managed apps only)**: Define the data types that managed apps can use when on cellular networks. Your options:
  - **Block use of cellular data**: Block using cellular data for **All managed apps** or **Choose specific apps**.
  - **Block use of cellular data when roaming**: Block using cellular data when roaming for **All managed apps** or **Choose specific apps**.

## Connected Devices

- **AirDrop (supervised only)**: **Block** prevents using AirDrop on the device. **Not configured** (default) allows using the AirDrop feature to exchange content with nearby devices.
- **Apple Watch pairing (supervised only)**: **Block** prevents pairing with an Apple Watch. **Not configured** (default) allows the device to pair with an Apple Watch.
- **Wrist detection for paired Apple watch**: **Require** forces a paired Apple watch to use wrist detection. When required, the Apple Watch won't display notifications when it's not being worn. 
- **Bluetooth modification (supervised only)**: **Block** stops the end user from changing Bluetooth settings on the device. **Not configured** (default) allows the user to change these settings.
- **Host pairing to control the devices an iOS device can pair with (supervised only)**: **Not configured** (default) allows host pairing to let the administrator control which devices an iOS device can pair with. **Block** prevents host pairing.
- **Require AirPlay outgoing requests pairing password**: **Require** a pairing password when the user uses AirPlay to stream content to other Apple devices. **Not configured** (default) allows the user to stream content using AirPlay without entering a password.
- **Block AirPrint (supervised only)**: Choose **Block** to prevent using the AirPrint feature on the device. **Not configured** (default) allows the user to use AirPrint.
  - **Block storage of AirPrint credentials in Keychain (supervised only)**: **Block** prevents using Keychain storage for username and password on the device. **Not configured** (default) allows storing the AirPrint username and password in the Keychain app.
  - **Require a trusted TLS certificate for AirPrint (supervised only)**: **Require** forces the device to use trusted certificates for TLS printing communication.
  - **Block iBeacon discovery of AirPrint printers (supervised only)**: **Block** prevents malicious AirPrint Bluetooth beacons from phishing for network traffic. **Not configured** (default) allows advertising AirPrint printers on the device.
- **Block setting up new nearby devices (supervised only)**: **Block** disables the prompt to set up new devices that are nearby. **Not configured** (default) allows prompts for users to connect to other nearby Apple devices.

  This feature applies to:  
  - iOS 11.0 and newer

## Keyboard and Dictionary

- **Word definition lookup (supervised only)**: **Block** prevents user from highlighting a word, and then looking up its definition on the device. **Not configured** (default) allows access to the definition lookup feature.
- **Predictive keyboards (supervised only)**: **Not configured** (default) allows using predictive keyboards to suggest words the user might want. **Block** prevents this feature.
- **Auto-correction (supervised only)**: **Not configured** (default) allows the device to automatically correct misspelled words. **Block** prevents using autocorrection.
- **Keyboard spell-check (supervised only)**: **Not configured** (default) allows using spellchecker on the device. **Block** allows spell checker.
- **Keyboard shortcuts (supervised only)**: **Not configured** (default) allows using keyboard shortcuts on the device. **Block** stops the user from using keyboard shortcuts.
- **Dictation (supervised only)**: **Block** stops the user from using voice input to enter text. **Not configured** (default) allows the user to use dictation input.
- **QuickPath (supervised only)**: **Not configured** (default) allows users to use QuickPath, which allows a continuous input on the device's keyboard. Users can type by swiping across the keys to create words. **Block** prevents users from using QuickPath. 

  This feature applies to:  
  - iOS 13.0 and newer

## Cloud and Storage

- **Backup to iCloud (supervised only)**: **Not configured** (default) allows the user to back up the device to iCloud. **Block** stops the user from backing up the device to iCloud.

  Starting with iOS 13.0, this setting requires supervised devices.

- **Block iCloud Document sync (supervised only)**: **Not configured** (default) allows document and key-value synchronization to your iCloud storage space. **Block** prevents iCloud from syncing documents and data.

  Starting with iOS 13.0, this setting requires supervised devices.

- **Photo stream syncing to iCloud**: **Not configured** (default) lets users enable **My Photo Stream** on their device to sync to iCloud, and have photos available on all the user's devices. **Block** prevents photo stream syncing to iCloud.
- **Encrypted backup**: **Require** so device backups must be encrypted.
- **iCloud Photo Library**: Set to **Block** to disable using iCloud photo library to store photos and videos in the cloud. Any photos not fully downloaded from iCloud Photo Library to the device are removed from the device. **Not configured** (default) allows using the iCloud photo library.
- **Managed apps sync to cloud**: **Not configured** (default) allows your Intune-manages apps to sync data to the user's iCloud account. **Block** prevents this data sync to iCloud.
- **Shared photo stream**: Choose **Block** to disable **iCloud Photo Sharing** on the device. **Not configured** (default) allows shared photo streaming.
- **Handoff**: **Not configured** (default) allows users to start work on an iOS device, and then continue the work they started on another iOS or macOS device. **Block** prevents this handoff.
- **Block iCloud Keychain sync (supervised only)**: Choose **Block** to disable syncing credentials stored in the Keychain to iCloud. **Not configured** (default) allows users to sync these credentials.

  Starting with iOS 13.0, this setting requires supervised devices.

- **Block Enterprise Book Backup**: Choose **Block** to prevent users from backing up enterprise books. **Not configured** (default) allows users to back up these books.
- **Block enterprise book metadata sync (notes and highlights)**: **Block** prevents syncing notes and highlights in enterprise books. **Not configured** (default) allows the syncing.

## Autonomous single app mode (supervised only)

Use these settings to configure iOS devices to run specific apps in autonomous single app mode. When this mode is configured, and the app is run, the device is locked. It can only run that app. For example, add an app that lets users take a test on the device. When the apps actions are complete, or you remove this policy, the device returns to its normal state.

To add apps, you can:

- Enter the **App name** and **App Bundle ID**, and select **Add**. [Bundle IDs for built-in iOS apps](bundle-ids-built-in-ios-apps.md) includes some apps with their IDs.
- **Import** a CSV file with the list of app names and their bundle IDs. Or, **Export** an existing list that includes the apps.

## Kiosk (supervised only)

- **App to run in kiosk mode**: Choose the type of apps you want to run in kiosk mode. Your options:
  - **Not configured** (default): Kiosk settings aren't applied. The device doesn't run in kiosk-mode.
  - **Store App**: Enter the URL to an app in the iTunes App store.
  - **Managed App**: Choose an app you added to Intune.
  - **Built-In App**: Enter the [bundle ID](bundle-ids-built-in-ios-apps.md) of the built-in app.

- **Assistive touch**: **Require** the Assistive Touch accessibility setting be on the device. This feature helps users with on-screen gestures that might be difficult for them. **Not configured** doesn't run or enable this feature in kiosk mode.
- **Invert colors**: **Require** the Invert Colors accessibility setting so users with visual impairments can change the display screen. **Not configured** doesn't run or enable this feature in kiosk mode.
- **Mono audio**: **Require** the Mono audio accessibility setting be on the device. **Not configured** doesn't run or enable this feature in kiosk mode.
- **VoiceOver**: **Require** the VoiceOver accessibility setting be on the device to read text on the screen out loud. **Not configured** doesn't run or enable this feature in kiosk mode.
- **Zoom**: **Require** the Zoom setting be on the device to let users use touch to zoom in on the screen. **Not configured** doesn't run or enable this feature in kiosk mode.
- **Auto lock**: **Block** prevents automatic locking of the device. **Not configured** allows this feature.
- **Ringer switch**: **Block** disables the ringer (mute) switch on the device. **Not configured** allows this feature.
- **Screen rotation**: **Block** prevents changing the screen orientation when the user rotates the device. **Not configured** allows this feature.
- **Screen sleep button**: Choose **Block** to disable the screen sleep wake button on the device. **Not configured** allows this feature.
- **Touch**: **Block** disables the touchscreen on the device. **Not configured** allows the user to use the touchscreen.
- **Volume buttons**: **Block** prevents using the volume buttons on the device. **Not configured** allows the volume buttons.
- **Assistive touch control**: **Allow** let users use the assistive touch function. **Not configured** disables this feature.
- **Invert colors control**: **Allow** invert color changes to let users adjust the invert colors function. **Not configured** disables this feature.
- **Speak on selected text**: **Allow** the Speak Selection accessibility settings be on the device. This feature reads text that the user selects out loud. **Not configured** disables this feature.
- **VoiceOver control**: **Allow** voiceover changes to let users update the VoiceOver function, such as how fast on-screen text is read out loud. **Not configured** prevents voiceover changes.
- **Zoom control**: **Allow** zoom changes by the user. **Not configured** prevents zoom changes.

> [!NOTE]
> Before you can configure an iOS device for kiosk mode, you must use the Apple Configurator tool or the Apple Device Enrollment Program to put the device into supervised mode. See Apple's guide on using the Apple Configurator tool.
> If the iOS app you enter is installed after you assign the profile, then the device doesn't enter kiosk mode until the device is restarted.

## Domains

- **Unmarked email domains** > **Email Domain URL**: Add one or more URLs to the list. When end users receive an email from a domain other than the domains you enter, the email is marked as untrusted in the iOS Mail app.

- **Managed web domains** > **Web Domain URL**; Add one or more URLs to the list. When documents are downloaded from the domains you enter, they're considered managed. This setting applies only to documents downloaded using the Safari browser.

- **Safari password autofill domains** > **Domain URL**: Add one or more URLs to the list. Users can only save web passwords from URLs in this list. This setting applies only to the Safari browser, and devices in supervised mode. If you don't enter any URLs, then passwords can be saved from all web sites.

  This setting applies to:  
  - iOS 9.3 and newer

## Settings that require supervised mode

iOS supervised mode can only be enabled during initial device setup through Apple’s Device Enrollment Program, or by using Apple Configurator. Once supervised mode is enabled, Intune can configure a device with the following functionality:

- App Lock (Single App Mode) 
- Global HTTP Proxy 
- Activation Lock Bypass 
- Autonomous Single App Mode 
- Web Content Filter 
- Set background and lock screen 
- Silent App Push 
- Always-On VPN 
- Allow managed app installation exclusively 
- iBookstore 
- iMessages 
- Game Center 
- AirDrop 
- AirPlay 
- Host pairing 
- Cloud Sync 
- Spotlight search 
- Handoff 
- Erase device 
- Restrictions UI 
- Installation of configuration profiles by UI 
- News 
- Keyboard shortcuts 
- Passcode modifications 
- Device name changes 
- Automatic app downloads 
- Changes to enterprise app trust 
- Apple Music 
- Mail Drop 
- Pair with Apple Watch 

> [!NOTE]
> Apple confirmed that certain settings move to supervised-only in 2019. We recommend taking this into consideration when using these settings, instead of waiting for Apple to migrate them to supervised-only:
> - App installation by end users
> - App removal
> - FaceTime
> - Safari
> - iTunes
> - Explicit content
> - iCloud documents and data
> - Multiplayer gaming
> - Add Game Center friends
> - Siri

## Next steps

[Assign the profile](device-profile-assign.md) and [monitor its status](device-profile-monitor.md).

You can also restrict device features and settings on [macOS](device-restrictions-macos.md) devices.
