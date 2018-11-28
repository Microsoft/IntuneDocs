---
# required metadata

title: Microsoft Intune device restrictions settings for iOS
titleSuffix:
description: Learn the Intune settings you can use to control device settings and functionality on devices running iOS.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/23/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Microsoft Intune iOS device restriction settings

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

This article shows you the Microsoft Intune device restrictions settings that you can configure for devices running iOS.

## General

-   **Share usage data** - Allow or block the device from sending diagnostic and usage telemetry data to Apple.
-   **Diagnostic data submission** - Allow or block the device from submitting diagnostic data to Apple.
-   **Screen capture** - Allow the user to capture the contents of the screen as an image.
    - **Remote screen observation by Classroom app (supervised only)** - Allow or block the Apple Classroom app from viewing the screen of iOS devices.
    - **Unprompted screen observation by Classroom app (supervised only)** - If allowed, teachers can silently observe the screen of students iOS devices  using the Classroom app without the students knowledge.
-   **Untrusted TLS certificates** - Allow untrusted Transport Layer Security certificates on the device.
-   **Enterprise app trust** - Lets the user select to trust apps that were not downloaded from the app store.
- **Account modification (supervised only)** - When blocked, this prevents the user from modifying device-specific settings from the iOS settings app, like creating new device accounts, and changing the user name or password.
This also applies to settings accessible from the iOS settings app like Mail, Contacts, Calendar, Facebook, and Twitter. This does not apply to apps with account settings that are not configurable from the iOS settings app, for example, the Microsoft Outlook app.
- **Enabling restrictions in the device settings (supervised only)** - Allow the user to configure device restrictions (parental controls) on the device.
- **Use of the erase all content and settings option on the device (supervised only)** - Allow the user to use the option of erasing all content and settings on the device.
- **Device name modification (supervised only)** - Allow the user to change the name of the device.
- **Notification settings modification (supervised only)** - Allow the user to change the device notification settings.
- **Enterprise app trust settings modification (supervised only)** - Lets the user select to trust apps that were not downloaded from the app store.
- **Configuration profile changes (supervised only)** - Allow the user to install configuration profiles.
- **Activation Lock (supervised only)** - Enable Activation Lock on supervised iOS devices.

## Configurations requiring supervision

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
> Apple confirmed that certain settings will move to supervised-only in 2019. We recommend taking this into consideration when using these settings instead of waiting for Apple to migrate them to supervised-only:
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

## Password
-   **Password** - Require the end user to enter a password to access the device.
    -   **Simple passwords** - Allow simple passwords like 0000 and 1234.
    -   **Required password type** - Specify the type of password that is required, such as numeric only or alphanumeric.
    -   **Number of non-alphanumeric characters in password** - Specify the number of symbol characters (like **#** or **@**) that must be included in the password.
    -   **Minimum password length** - Specify the minimum number of characters in the password.
    -   **Number of sign-in failures before wiping device** - Specify the number of unique bad password attempts before this setting wipes the device.
    -   **Maximum minutes after screen lock before password is required**<sup>1</sup> - Specify how long the device can remain idle before the user must reenter their password.
    -   **Maximum minutes of inactivity until screen locks**<sup>1</sup> - Enter the maximum minutes of inactivity until the screen locks. If the time you enter is longer than what's currently set on the device, then this value is ignored by the device. When set to **Immediately**, devices use the minimum possible value per device.
    -   **Password expiration (days)** - Specify the number of days before the device password must be changed.
    -   **Prevent reuse of previous passwords** - Specify the number of previously used passwords that the device remembers.
    -   **Fingerprint unlock** - Allow using a fingerprint to unlock compatible devices.
- **Passcode modification (supervised only)** - Stops the passcode from being changed, added, or removed.
    - **Fingerprint modification (supervised only)** - Stops the user from changing, adding, or removing TouchID settings.

<sup>1</sup>When you configure the settings **Maximum minutes of inactivity until screen locks** and **Maximum minutes after screen lock before password is required**, they are applied in sequence. For example, if you set the value for both settings to **5** minutes, the screen will turn off automatically after five minutes, and the device will be locked after an additional five minutes. However, if the user turns off the screen manually, the second setting is immediately applied. In the same example, after the user turns off the screen, the device will lock five minutes later.

## Locked Screen Experience

-   **Control Center access while device locked** - Allow the user to access the control center app when the device is locked.
-   **Notifications while device locked** - Allow the user to access the notifications view without unlocking the device.
-   **Wallet notifications while device locked** - Allow the user to access the Wallet app while the device is locked.
-   **Today view while device locked** - Allow the user to see the Today view when the device is locked.

## App Store, Doc Viewing, Gaming


-   **App store** - Block access to the app store on supervised devices.
    - **Installing apps from App Store (supervised only)** - Blocks the app store from the device home screen. End users can continue to use iTunes or the Apple Configurator to install apps.
    - **Automatic app downloads (supervised only)** - Stops apps that were purchased on another iOS device from being downloaded to this device.
-   **Password to access app store** - Require the user to enter a password before they can visit the app store.
-   **In-app purchases** - Allow store purchases to be made from within a running app.
-   **Explicit iTunes music, podcast, or news content (supervised only)** - Allow the device to access content rated as adult from the store.
-   **Download content from iBook store flagged as 'Erotica'** - Allow the user to download books with the "Erotica" category.
-   **Viewing corporate documents in unmanaged apps** - Allow corporate documents to be viewed in any app.<br>**Example:** You want to prevent users from saving files from the OneDrive app to Dropbox. Configure this setting as no. After the device receives the policy (for example, after a restart), it will no longer allow saving.
-   **Viewing non-corporate documents in corporate apps** - Allow any document to be viewed in corporate managed apps.
-   **Treat AirDrop as an unmanaged destination** - Stops managed apps from being able to send data via. Airdrop.
-   **Adding Game Center friends (supervised only)** - Allow the user to add friends in Game Center.
-   **Game Center (supervised only)** - Block or enable the use of the Game Center app.
-   **Multiplayer gaming (supervised only)** - Allow the user to play multiplayer games on the device.
-   **Ratings region** - Choose the ratings region for which you want to configure allowed downloads, then choose the allowed ratings for **Movies** and **TV Shows**.
-   **Apps** - Choose the allowed age rating of apps that users can download, or you can choose **Allow All Apps**.

## Built-in Apps

-   **Camera** - Select whether the camera on the device can be used.
    -   **FaceTime** - Allow the FaceTime app to be used on the device.
-   **Siri** - Allow use of the Siri voice assistant on the device.
    -   **Siri while device is locked** - Allow use of the Siri voice assistant on the device while it is locked.
    -   **Siri profanity filter (supervised only)** - Prevents Siri from dictating, or speaking profane language.
    -   **Siri to query user-generated content from the internet (supervised only)** - Allow Siri to access websites to answer questions.
- **Apple News (supervised only)** - Allow use of the Apple News app.
- **iBooks store (supervised only)** - Allow the user to browse and purchase books from the iBooks store.
- **Messages app on the device (supervised only)** - Allow use of the Messages app to send and read text messages.
- **Podcasts (supervised only)** - Allow use of the Podcasts app.
- **Music service (supervised only)** - Allow use of the Apple Music app.
- **iTunes Radio service (supervised only)** - Allow use of the iTunes Radio app.
- **Changes to the Find My Friends app settings (supervised only)** - Allow the user to change settings for the Find My Friends app.
- **Spotlight search to return results from internet (supervised only)** - Let Spotlight search connect to the Internet to provide further results.

## Restricted apps

In the restricted apps list, you can configure one of the following lists:

- A **Prohibited apps** list - List the apps (not managed by Intune) that users are not allowed to install and run. Users are not prevented from installing a prohibited app, but if they do so, this is reported to you.
- An **Approved apps** list - List the apps that users are allowed to install. Users must not install apps that are not listed. Apps that are managed by Intune are automatically allowed. Users are not prevented from installing an app that is not on the approved list, but if they do so, this is reported to you.

To configure the list, click **Add**, then specify a name of your choice, optionally the app publisher, and the URL to the app in the app store.

### How to specify the URL to an app in the store

To specify an app URL in the apps list, use the following format:

Using a search engine, find the app that you want to use in the iTunes App Store and open the page for the app.
Copy the URL of the page and use this as the URL to configure the allowed or prohibited apps list or an app that you want to run in kiosk mode.
Device profiles that contain restricted app settings must be assigned to groups of users.

Example: Search for Microsoft Word for iPad. The URL that you use is https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8.

> [!Note]
> You can also use iTunes to find the app and then use the **Copy Link** command to get the app URL.

### Additional options

You can also click **Import** to populate the list from a csv file in the format <*app url*>, <*app name*>, <*app publisher*> or click **Export** to create a csv file containing the contents of the restricted apps list in the same format.

## Show or hide apps (supervised only)

In the show or hide apps list, you can configure one of the following lists (requires supervised devices running iOS 9.3 or later).

- A **Hidden apps** list - Specify a list of apps that is hidden from users. Users cannot view, or launch these apps.
- A **Visible apps** list - Specify a list of apps that users can view and launch. No other apps can be viewed or launched.

To configure the list, click **Add**, then specify a name of your choice, optionally the app publisher, and the URL to the app in the app store.

### How to specify the URL to an app in the store

To specify an app URL in the apps list, use the following format:

Using a search engine, find the app that you want to use in the iTunes App Store and open the page for the app.
Copy the URL of the page and use this as the URL to configure the allowed or prohibited apps list or an app that you want to run in kiosk mode.

Example: Search for Microsoft Word for iPad. The URL that you use is https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8.

> [!Note]
> You can also use the iTunes software to find the app and then use the **Copy Link** command to get the app URL.

### Additional options

You can also click **Import** to populate the list from a csv file in the format <*app url*>, <*app name*>, <*app publisher*> or click **Export** to create a csv file containing the contents of the hidden or visible apps list in the same format.


## Wireless
-   **Data roaming** - Allow data roaming when the device is on a cellular network.
-   **Global background fetch while roaming** - Allow the device to fetch data such as email while it is roaming on a cellular network.
-   **Voice dialing** - Allow use of the voice dialing feature on the device.
-   **Voice roaming** - Allow voice roaming when the device is on a cellular network.
-   **Changes to app cellular data usage settings (supervised only)** - Allow the user to control which apps are allowed to use cellular data.
-   **Personal Hotspot** - Don't allow the device to be used as a personal hotspot. This setting might not be compatible with some carriers.
-   **Join Wi-Fi networks only using configuration profiles (supervised only)** - Only allow the device to join Wi-Fi networks that have been configured with an Intune Wi-Fi profile.

- **Cellular usage rules (managed apps only)** - Lets you define the data types that managed apps can use when on cellular networks. Choose from:
    - **Block use of cellular data** - You can block use of cellular data for **All managed apps** or **Choose specific apps**.
    - **Block use of cellular data when roaming** - You can block use of cellular data when roaming for **All managed apps** or **Choose specific apps**.

## Connected Devices

-   **AirDrop (supervised only)** - Allow use of the AirDrop feature to exchange content with nearby devices.
-   **Apple Watch pairing (supervised only)** - Allow the device to pair with an Apple Watch.
-   **Wrist detection for paired Apple watch** - When enabled, the Apple Watch won't display notifications when it is not being worn.
-   **Bluetooth modification (supervised only)** - Block the end user from changing Bluetooth settings on the device.
-   **Host pairing to control the devices an iOS device can pair with (supervised only)** - Allow host pairing to let the administrator control which devices an iOS device can pair with.
-   **Require AirPlay outgoing requests pairing password** - Require a pairing password when the user uses AirPlay to stream content to other Apple devices.

## Keyboard and Dictionary

-   **Word definition lookup (supervised only)** - Allow the iOS feature that lets you highlight a word and look up its definition.
-   **Predictive keyboards (supervised only)** - Allow the use of predictive keyboards that suggest words the user might want.
-   **Auto-correction (supervised only)** - Lets the device automatically correct misspelled words.
-   **Keyboard spell-check (supervised only)** - Allows the device spell checker.
-   **Keyboard shortcuts (supervised only)** - Allows use of keyboard shortcuts.
-   **Dictation (supervised only)** - Stops the user from using voice input to enter text.

## Cloud and Storage
-   **Backup to iCloud** - Allow the user to back up the device to iCloud.
-   **Document sync to iCloud (supervised only)** - Allow document and key-value synchronization to your iCloud storage space.
-   **Photo stream syncing to iCloud** - Lets users enable **My Photo Stream** on their device, which allows photos to sync to iCloud and be available on all the users devices.
-   **Encrypted backup** - Require any device backups to be encrypted.
-   **iCloud Photo Library** - If set to **No**, disables the use of iCloud photo library, which lets users store photos and videos in the cloud.   Any photos not fully downloaded from iCloud Photo Library to the device is removed from the device if this is set to **No**.
-   **Managed apps sync to cloud** - Allow apps that you manage with Intune to sync data to the user's iCloud account.
-   **Shared photo stream** - Set to **No** to disable **iCloud Photo Sharing** on the device..
-   **Activity continuation** - Allow the user to continue work that they started on an iOS device on another iOS or macOS device (Handoff).

## Autonomous single app mode (supervised only)

Use these settings to configure iOS devices to run specified apps in autonomous single app mode. When this mode is configured, and the app is run, the device is locked so that it can only run that app. An example of this is when you configure an app that lets users take a test on the device. When the apps actions are complete, or you remove this policy, the device returns to its normal state.

### Settings

- **App name** - Enter the name of the app as it appears in the apps list on this blade.
- **App Bundle ID** - Enter the bundle ID of the app. For help, see **Bundle ID reference for built-in iOS apps** in this topic.

After you specify each app name and bundle ID, choose **Add** to append it to the list.

- **Import** - Import a comma-separated values (.csv) file containing a list of app names, and their associated bundle IDs.
- **Export** - Export the app names, and associated bundle IDs you have configured to a comma-separated values (.csv) file.

## Kiosk (supervised only)
-   **App that runs in kiosk mode** - Choose **Managed App** to select an app you've added to Intune, **Store App** to specify the URL to an app in the store, or **Built-In App** to specify the bundle ID of the built-in app. For more information, see [Bundle ID reference for built-in iOS apps](device-restrictions-ios.md#bundle-id-reference-for-built-in-ios-apps) and [How to specify the URL to an app in the store](device-restrictions-ios.md#how-to-specify-the-url-to-an-app-in-the-store-1).
    -   **Assistive touch** - Enable or disable the **Assistive Touch** accessibility setting, which helps the user perform on-screen gestures that might be difficult for them to perform.
    -   **Invert colors** - Enable or disable the Invert Colors accessibility setting, which adjusts the display to help users with visual impairments.
    -   **Mono audio** - Enable or disable the accessibility setting Mono audio.
    -   **VoiceOver** - Enable or disable the accessibility setting **VoiceOver**, which reads aloud text on the device display.
    -   **Zoom** - Enable or disable the **Zoom** accessibility setting, which lets the user use touch to zoom in to the device display.
    -   **Auto lock** - Enable or disable automatic locking of the device.
    -   **Ringer switch** - Enable or disable the ringer (mute) switch on the device.
    -   **Screen rotation** - Enable or disable changing the screen orientation when the user rotates the device.
    -   **Screen sleep button** - Enable or disable the screen sleep wake button on the device. This is a policy that can disable the Sleep/Wake button, so in the Intune policy, “Not Configured” means the button is enabled while “Allow" means the button will be disabled.
    -   **Touch** - Enable or disable the touchscreen on the device.
    -   **Volume buttons** - Enable or disable the use of the volume buttons on the device.
    -   **Assistive touch control** - Enable or disable assistive touch adjustments, which let the user adjust the assistive touch function.
    -   **Invert colors control** - Enable or disable invert colors adjustments, which let the user adjust the invert colors function.
    -   **Speak on selected text** - Enable or disable the Speak Selection accessibility settings, which can read aloud the text that the user selects.
    -   **VoiceOver control** - Enable or disable voiceover adjustments, which let the user adjust the VoiceOver function (for example, how fast on-screen text is read aloud).
    -   **Zoom control** - Enable or disable zoom adjustments, which let the user adjust the zoom function.

>[!NOTE]
> Before you can configure an iOS device for kiosk mode, you must use the Apple Configurator tool or the Apple Device Enrollment Program to put the device into supervised mode. For more information about the Apple Configurator tool, see your Apple documentation.
>If the iOS app that you specify is installed after you assign the profile, the device will not enter kiosk mode until after it is restarted.

## Bundle ID reference for built-in iOS apps

This list shows the bundle ID of some common built-in iOS apps. To find the bundle ID of other apps, contact your software vendor.

| Bundle ID                   | App Name     | Publisher |
|-----------------------------|--------------|-----------|
| com.apple.AppStore          | App Store    | Apple     |
| com.apple.calculator        | Calculator   | Apple     |
| com.apple.mobilecal         | Calendar     | Apple     |
| com.apple.camera            | Camera       | Apple     |
| com.apple.mobiletimer       | Clock        | Apple     |
| com.apple.compass           | Compass      | Apple     |
| com.apple.MobileAddressBook | Contacts     | Apple     |
| com.apple.facetime          | FaceTime     | Apple     |
| com.apple.mobileme.fmf1     | Find Friends | Apple     |
| com.apple.mobileme.fmip1    | Find iPhone  | Apple     |
| com.apple.gamecenter        | Game Center  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | Health       | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.MobileStore       | iTunes Store | Apple     |
| com.apple.itunesu           | iTunes U     | Apple     |
| com.apple.Keynote           | Keynote      | Apple     |
| com.apple.mobilemail        | Mail         | Apple     |
| com.apple.MapsMaps          |              | Apple     |
| com.apple.MobileSMS         | Messages     | Apple     |
| com.apple.Music             | Music        | Apple     |
| com.apple.news              | News         | Apple     |
| com.apple.mobilenotes       | Notes        | Apple     |
| com.apple.Numbers           | Numbers      | Apple     |
| com.apple.Pages             | Pages        | Apple     |
| com.apple.Photo-Booth       | Photo Booth  | Apple     |
| com.apple.mobileslideshow   | Photos       | Apple     |
| com.apple.podcasts          | Podcasts     | Apple     |
| com.apple.reminders         | Reminders    | Apple     |
| com.apple.MobileSafari      | Safari       | Apple     |
| com.apple.Preferences       | Settings     | Apple     |
| com.apple.stocks            | Stocks       | Apple     |
| com.apple.tips              | Tips         | Apple     |
| com.apple.videos            | Videos       | Apple     |
| com.apple.VoiceMemos        | VoiceMemos   | Apple     |
| com.apple.Passbook          | Wallet       | Apple     |
| com.apple.Bridge            | Watch        | Apple     |
| com.apple.weather           | Weather      | Apple     |

## Safari
-   **Safari (supervised only)** - Specify whether the Safari browser can be used on the device.
-   **Autofill** - Allow the user to change autocomplete settings in the browser.
-   **Cookies** - Allow the browser to use cookies.
-   **JavaScript** - Allow Java scripts to run in the browser.
-   **Fraud warnings** - Allow fraud warnings in the browser.
-   **Pop-ups** - Enable or disable the browser pop-up blocker.


## Domains

### Unmarked email domains

In the **Email Domain URL** field, add one or more URLs to the list. When end users receive an email from a domain other than those you configured, the email is marked as untrusted in the iOS Mail app.


### Managed web domains

In the **Web Domain URL** field, add one or more URLs to the list. When documents are downloaded from the domains you specify, they are considered managed. This setting applies only to documents downloaded using the Safari browser.


### Safari password autofill domains

In the **Domain URL** field, add one or more URLs to the list. Users can only save web passwords from URLs in this list. This setting applies only to the Safari browser, and to iOS 9.3 and later devices in supervised mode. If you don't specify any URLs, then passwords can be saved from all web sites.
