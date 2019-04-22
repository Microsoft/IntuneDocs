---
# required metadata

title: Android Enterprise device settings in Microsoft Intune - Azure | Microsoft Docs
description: On Android Enterprise or Android for Work devices, restrict settings on the device, including copy and paste, show notifications, app permissions, data sharing, password length, sign-in failures, use fingerprint to unlock, reuse passwords, and enable bluetooth sharing of work contacts. Configure devices as a dedicated device kiosk to run one app, or multiple apps.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/10/2019
ms.topic: reference
ms.prod:
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
ms.custom: intune-azure, seodec18
ms.collection: M365-identity-device-management
---

# Android Enterprise device settings to allow or restrict features using Intune

This article lists and describes the different settings you can control on Android Enterprise devices. As part of your mobile device management (MDM) solution, use these settings to allow or disable features, run apps on dedicated devices, control security, and more.

## Before you begin

[Create a device configuration profile](device-restrictions-configure.md).

## Device owner only

### General settings

- **Screen capture**: Choose **Block** to prevent screenshots or screen captures on the device. It also prevents the content from being shown on display devices that don't have a secure video output. **Not configured** lets the user capture the screen contents as an image.
- **Camera**: Choose **Block** to prevent access to the camera on the device. **Not required** allows access to the device's camera.
- **Default permission policy**: This setting defines the default permission policy for requests for runtime permissions. The possible values include:
  - **Device default**: Use the device's default setting.
  - **Prompt**: The user is prompted to approve the permission.
  - **Auto grant**: Permissions are automatically granted.
  - **Auto deny**: Permissions are automatically denied.
- **Date and Time changes**: Choose **Block** to prevent users from manually setting the date and time. **Not configured** allows users to the set date and time on the device.
- **Volume changes**: Choose **Block** to prevent users from changing the device's volume. **Not configured** allows using the volume settings on the device.
- **Factory reset**: Choose **Block** to prevent users from using the factory reset option in the device's settings. **Not configured** allows users to use this setting on the device.
- **Safe boot**: Choose **Block** to prevent users from rebooting the device into safe mode. **Not configured** allows users to reboot the device in safe mode.
- **Status bar**: Choose **Block** to prevent access to the status bar, including notifications and quick settings. **Not configured** allows users access to the status bar.
- **Roaming data services**: Choose **Block** to prevent data roaming over the cellular network. **Not configured** allows data roaming when the device is on a cellular network.
- **Wi-Fi setting changes**: Choose **Block** to prevent users from changing Wi-Fi settings created by the device owner. Users can create their own Wi-Fi configurations. **Not configured** allows users to change the Wi-Fi settings on the device.
- **Wi-Fi access point configuration**: Choose **Block** to prevent users from creating or changing any Wi-Fi configurations. **Not configured** allows users to change the Wi-Fi settings on the device.
- **Bluetooth configuration**: Choose **Block** to prevent users from configuring Bluetooth on the device. **Not configured** allows using Bluetooth on the device.
- **Tethering and access to hotspots**: Choose **Block** to prevent tethering and access to portable hotspots. **Not configured** allows tethering and access to portable hotspots.
- **USB storage**: Choose **Allow** to access USB storage on the device. **Not configured** prevents access to USB storage.
- **USB file transfer**: Choose **Block** to prevent transferring files over USB. **Not configured** allows transferring files.
- **External media**: Choose **Block** to prevent using or connecting any external media on the device. **Not configured** allows external media on the device.
- **Beam data using NFC**: Choose **Block** to prevent using the Near Field Communication (NFC) technology to beam data from apps. **Not configured** allows using NFC to share data between devices.
- **Debugging features**: Choose **Allow** to let users use debugging features on the device. **Not configured** prevents users from using the debugging features on the device.
- **Microphone adjustment**: Choose **Block** to prevent users from unmuting the microphone and adjusting the microphone volume. **Not configured** allows the user to use and adjust the volume of the microphone on the device.
- **Factory reset protection emails**: Choose **Google account email addresses**. Enter the email addresses of device administrators that can unlock the device after it's wiped. Be sure to separate the email addresses with a semi-colon, such as `admin1@gmail.com;admin2@gmail.com`. If an email isn't entered, anyone can unlock the device after it's restored to the factory settings.
- **Network escape hatch**: Choose **Enable** to allow users to turn on the network escape hatch feature. If a network connection isn't made when the device boots, then the escape hatch asks to temporarily connect to a network and refresh the device policy. After applying the policy, the temporary network is forgotten and the device continues booting. This feature connects devices to a network if:
  - There isn't a suitable network in the last policy.
  - The device boots into an app in lock task mode.
  - The user is unable to reach the device settings.

  **Not configured** prevents users from turning on the network escape hatch feature on the device.

- **System update**: Choose an option to define how the device handles over-the-air updates:
  - **Device Default**: Use the device's default setting.
  - **Automatic**: Updates are automatically installed without user interaction. Setting this policy immediately installs any pending updates.
  - **Postponed**: Updates are postponed for 30 days. At the end of the 30 days, Android prompts the user to install the update. It's possible for device manufacturers or carriers to prevent (exempt) important security updates from being postponed. An exempted update shows a system notification to the user on the device. 
  - **Maintenance window**: Installs updates automatically during a daily maintenance window that you set in Intune. Installation tries daily for 30 days, and can fail if there's insufficient space or battery levels. After 30 days, Android prompts the user to install. This window is also used to install updates for Play apps. Use this option for dedicated devices, such as kiosks, as single-app dedicated device foreground apps can be updated.

- **Notification windows**: When set to **Disable**, window notifications, including toasts, incoming calls, outgoing calls, system alerts, and system errors are not shown on the device. When set to **Not configured**, the operating system default is used, which may be to show notifications.
- **Skip first use hints**: Choose **Enable** to hide or skip suggestions from apps to step through tutorials or read any introductory hints when the app starts. When set to **Not configured**, the operating system default is used, which may be to show these suggestions when the app starts.

### System security settings

- **Threat scan on apps**: **Require** (default) enables Google Play Protect to scan apps before and after they’re installed. If it detects a threat, it may warn the user to remove the app from the device. **Not configured** doesn't enable or run Google Play Protect to scan apps.

### Dedicated device settings

Use these settings to configure a kiosk-style experience on your dedicated devices. You can configure a device to run one app, or run many apps. When a device is set with kiosk mode, only the apps you add are available. These settings apply to Android Enterprise dedicated devices. They don't apply to Android Enterprise fully managed devices.

**Kiosk mode**: Choose if the device runs one app or runs multiple apps.

- **Single app**: Users can only access a single app on the device. When the device starts, only the specific app starts. Users are restricted from opening new apps or from changing the running app.

  **Steps**
  1. Choose **Select a managed app**, and select the managed Google Play app from the list. 

      If you don't have any apps listed, then [add some Android apps](apps-add-android-for-work.md) to the device. Be sure to [assign the app to the device group created for your dedicated devices](apps-deploy.md).

  2. Choose **OK** > **OK** to add the app.

- **Multi-app**: Users can access a limited set of apps on the device. When the device starts, only the apps you add start. You can also add some web links that users can open. When the policy is applied, users see icons for the allowed apps on the home screen.

  > [!IMPORTANT]
  > For multi-app dedicated devices, the [Managed Home Screen app](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) from Google Play **must be**:
  >   - [Added as a client app](apps-add-android-for-work.md) in Intune
  >   - [Assigned to the device group](apps-deploy.md) created for your dedicated devices
  > 
  > The **Managed Home Screen** app isn't required to be in the configuration profile, but it is required to be added as a client app. When the **Managed Home Screen** app is added as a client app, any other apps you add in the configuration profile are shown as icons on the **Managed Home Screen** app. 

  - Choose **Add**, and select your apps from the list.

    If the **Managed Home Screen** app isn't listed, then [add it from Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise). Be sure to [assign the app](apps-deploy.md) to the device group created for your dedicated devices.

    You can also add other [Android apps](apps-add-android-for-work.md) and [web apps](web-app.md) created by your organization to the device. Be sure to [assign the app to the device group created for your dedicated devices](apps-deploy.md).

  - **Virtual home button**: Choose **Enable** to show a home button on the dedicated device. When selected, it returns the user to the device's home screen so users can easily switch between apps. On some Android devices, users may need to swipe up on the screen to show the home button. **Disable** doesn't show a home button, so users must use the back button to switch between apps.
  - **Leave kiosk mode**: Choose **Enable** to allow Administrators to temporarily pause kiosk mode to update the device. To use this feature, the administrator: 
  
    1. Continues to select the back button until the "Exit kiosk" button is shown. 
    2. Selects the button, and enters the **Leave kiosk mode code** PIN.
    3. When done making changes, select the **Managed Home Screen** app. This step relocks the device into multi-app kiosk mode. 

    **Disable** doesn't give the ability to pause kiosk mode. If the administrator continues to select the back button, and selects the "Exit kiosk" button, then a message states that a passcode is required.

    - **Leave kiosk mode code**: Enter a 4-6 digit numeric PIN. The administrator uses this PIN to temporarily pause kiosk mode.

  - **Set custom URL background**: Enter a URL to customize the background screen on the dedicated device.
  
  > [!NOTE]
  > For most cases, we recommend starting with images of at least the following sizes: 
  >    -Phone:  1080x1920 px.
  >    -Tablet: 1920x1080 px. 
  >    
  >   For the best experience and crisp details, it’s suggested that per device image assets be created to the display specifications. 
  >   Modern displays have higher pixel densities and can display equivalent 2K/4K definition images.
      
  - **Wi-Fi configuration**: Choose **Enable** to allow end users to connect the device to different WiFi networks. Enabling this feature also turns on device location. **Not configured** (default) prevents users from connecting to WiFi networks while in the Managed Home Screen (lock task mode).

    More on [lock task mode](https://developer.android.com/work/dpc/dedicated-devices/lock-task-mode) (opens Android's web site).

  - **Bluetooth configuration**: Choose **Enable** to allow Bluetooth on the device, and allow end users to pair devices over Bluetooth. Enabling this feature also turns on device location. **Not configured** (default) prevents users from configuring Bluetooth and pairing devices while in the Managed Home Screen (lock task mode). 

    More on [lock task mode](https://developer.android.com/work/dpc/dedicated-devices/lock-task-mode) (opens Android's web site).

### Device password settings

- **Disable lock screen**: Choose **Disable** to prevent users from using Keyguard lock screen feature on the device. **Not configured** allows the user to use the Keyguard features.
- **Disabled lock screen features**: When keyguard is enabled on the device, choose which features to disable. For example, when **Secure camera** is checked, the camera feature is disabled on the device. Any features not checked are enabled on the device.

  These features are available to users when the device is locked. Users won't see or access features that are checked.

- **Required password type**: Define the type of password required for the device. Your options:
  - **Device default**
  - **Password required, no restrictions**
  - **Weak biometric**: [Strong vs. weak biometrics](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (opens Android's web site)
  - **Numeric**: Password must only be numbers, such as `123456789`. Enter the **minimum password length** a user must enter, between 4 and 16 characters.
  - **Numeric complex**: Repeated or consecutive numbers, such as "1111" or "1234", aren't allowed. Enter the **minimum password length** a user must enter, between 4 and 16 characters.
  - **Alphabetic**: Letters in the alphabet are required. Numbers and symbols aren't required. Enter the **minimum password length** a user must enter, between 4 and 16 characters.
  - **Alphanumeric**: Includes uppercase letters, lowercase letters, and numeric characters. Enter the **minimum password length** a user must enter, between 4 and 16 characters.
  - **Alphanumeric with symbols**: Includes uppercase letters, lowercase letters, numeric characters, punctuation marks, and symbols. Also enter:

    - **Minimum password length**: Enter the minimum length the password must have, between 4 and 16 characters.
    - **Number of characters required**: Enter the number of characters the password must have, between 0 and 16 characters.
    - **Number of lowercase characters required**: Enter the number of lowercase characters the password must have, between 0 and 16 characters.
    - **Number of uppercase characters required**: Enter the number of uppercase characters the password must have, between 0 and 16 characters.
    - **Number of non-letter characters required**: Enter the number of non-letters (anything other than letters in the alphabet) the password must have, between 0 and 16 characters.
    - **Number of numeric characters required**: Enter the number of numeric characters (`1`, `2`, `3`, and so on) the password must have, between 0 and 16 characters.
    - **Number of symbol characters required**: Enter the number of symbol characters (`&`, `#`, `%`, and so on) the password must have, between 0 and 16 characters.

- **Number of days until password expires**: Enter the number of days, between 1-365, until the device password must be changed. For example, to change the password after 60 days, enter `60`. When the password expires, users are prompted to create a new password.
- **Number of passwords required before user can resuse a password**: Enter the number of recent passwords that can't be reused, between 1-24. Use this setting to restrict the user from creating previously used passwords.
- **Number of sign-in failures before wiping device**: Enter the number, between 4-11, of failed sign-ins to allow before the device is wiped.

### Power settings

- **Time to lock screen**: Set the amount of idle time required before the device locks.
- **Screen on while device plugged in**: Choose which power sources cause the device's screen to stay on when plugged in.

### Users and Accounts settings

- **Add new users**: Choose **Block** to prevent users from adding new users. Each user has a personal space on the device for custom Home screens, accounts, apps, and settings. **Not configured** allows users to add other users to the device.
- **User removal**: Choose **Block** to prevent users from removing users. **Not configured** allows users to remove other users from the device.
- **Account changes**: Choose **Block** to prevent users from modifying accounts. **Not configured** allows users to update user accounts on the device.

### Applications

- **Allow installation from unknown sources**: Choose **Allow** so users can turn on **Unknown sources**. This setting allows apps to install from unknown sources, including sources other than the Google Play Store. **Not configured** prevents users from turning on **Unknown sources**.
- **Allow access to all apps in Google Play store**: When set to **Allow**, users get access to all apps in Google Play store. They don't get access to the apps the administrator blocks in [Client Apps](apps-add-android-for-work.md). **Not configured** forces users to only access the apps the administrator makes available Google Play store, or apps required in [Client Apps](apps-add-android-for-work.md).
- **App auto-updates**: Choose when automatic updates are installed. Your options:
  - **Not configured**
  - **User choice**
  - **Never**
  - **Wi-Fi only**
  - **Always**

### Connectivity

- **Always-on VPN**: Choose **Enable** to set a VPN client to automatically connect and reconnect to the VPN. Always-on VPN connections stay connected or immediately connect when the user locks their device, the device restarts, or the wireless network changes. 

  Choose **Not configured** to disable always-on VPN for all VPN clients.

  > [!IMPORTANT]
  > Be sure to deploy only one Always On VPN policy to a single device. Deploying multiple Always VPN policies to a single device isn't supported.

- **VPN client**: Choose a VPN client that supports Always On. Your options:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Custom
    - **Package ID**: Enter the package ID of the app in the Google Play store. For example, if the URL for the app in the Play store is `https://play.google.com/store/details?id=com.contosovpn.android.prod`, then the package ID is `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  >  - The VPN client you choose must be installed on the device, and it must support per-app VPN in work profiles. Otherwise, an error occurs. 
  >  - You do need to approve the VPN client app in the **Managed Google Play Store**, sync the app to Intune, and deploy the app to the device. After you do this, then the app is installed in the user's work profile.
  >  - There may be known issues when using per-app VPN with F5 Access for Android 3.0.4. See [F5's release notes for F5 Access for Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) for more information.

- **Lockdown mode**: Choose **Enable** to force all network traffic to use the VPN tunnel. If a connection to the VPN isn't established, then the device won't have network access.

  Choose **Not configured** to allow traffic to flow through the VPN tunnel or through the mobile network.

## Work profile only 

### Work profile settings

#### General

- **Copy and paste between work and personal profiles**: Choose **Block** to prevent copy-and-paste between work and personal apps. **Not configured** allows users to share data using copy-and-paste with apps in the personal profile 
- **Data sharing between work and personal profiles**: Choose if apps in the work profile can share with apps in the personal profile. For example, you can control sharing actions within applications, such as the **Share…** option in the Chrome browser app. This setting doesn't apply to copy/paste clipboard behavior. Your sharing options:
  - **Default sharing restrictions**: The default sharing behavior of the device, which varies depending on the Android version. By default, sharing from the personal profile to the work profile is allowed. Also by default, sharing from the work profile to the personal profile is blocked. This setting prevents sharing of data from the work to the personal profile. On devices running versions 6.0 and later, Google doesn't block sharing from the personal profile to the work profile.
  - **Apps in work profile can handle sharing request from personal profile**: Enables the built-in Android feature that allows sharing from the personal to work profile. When enabled, a sharing request from an app in the personal profile can share with apps in the work profile. This setting is the default behavior for Android devices running versions earlier than 6.0.
  - **Allow sharing across boundaries**: Enables sharing across the work profile boundary in both directions. When you select this setting, apps in the work profile can share data with unbadged apps in the personal profile. This setting allows managed apps in the work profile to share with apps on the unmanaged side of the device. So, use this setting carefully.

- **Work profile notifications while device locked**: Controls whether apps in the work profile can show data in notifications when the device is locked. **Block** doesn't show the data. **Not configured** shows the data.
- **Default app permissions**: Sets the default permission policy for all apps in the work profile. Starting with Android 6, the user is prompted to grant certain permissions required by apps when the app is launched. This policy setting lets you decide if users are prompted to grant permissions for all apps in the work profile. For example, you assign an app to the work profile that requires location access. Normally that app prompts the user to approve or deny location access to the app. Use this policy to automatically grant permissions without a prompt, automatically deny permissions without a prompt, or let the end user decide. Choose from:
  - **Device default**
  - **Prompt**
  - **Auto grant**
  - **Auto deny**

  You can also use an App Configuration policy to grant permissions for individual apps (**Client Apps** > **App configuration policies**).

- **Add and remove accounts**: Choose **Block** to prevent end users from manually adding or removing accounts in the work profile. For example, when you deploy the Gmail app into an Android work profile, you can prevent end users from adding or removing accounts in this work profile. **Not configured** allows adding accounts in the work profile.  

- **Contact sharing via Bluetooth**: Enables access to work contacts from another device, such as a car, that is paired using Bluetooth. By default, this setting isn't configured, and work profile contacts aren't shown. Select **Enable** to allow this sharing, and show work profile contacts. This setting applies to Android work profile devices on Android OS v6.0 and newer. Enabling this setting may allow certain Bluetooth devices to cache work contacts upon first connection. Disabling this policy after an initial pairing/sync may not remove work contacts from a Bluetooth device.

- **Screen capture**: Choose **Block** to prevent screenshots or screen captures on the device in the work profile. It also prevents the content from being shown on display devices that don't have a secure video output. **Not configured** allows getting screenshots.

- **Display work contact caller-id in personal profile**: When enabled (**Not configured**), the work contact caller details are displayed in the personal profile. When set to **Block**, the work contact caller number isn't displayed in the personal profile. Applies to Android OS v6.0 and newer versions.

- **Search work contacts from personal profile**: Choose **Block** to prevent users from searching for work contacts in apps in the personal profile. **Not required** allows searching for work contacts in the personal profile.

- **Camera**: Choose **Block** to prevent access to the camera on the device in the work profile. The camera on the personal side is not affected by the setting. **Not required** allows access to the camera in the work profile.

#### Work Profile Password

- **Require Work Profile Password**: Applies to Android 7.0 and above with work profile enabled. Choose **Require** to enter a passcode policy that applies only to the apps in the work profile. By default, the end user can use the two separately defined PINs, or users can choose to combine the PINs into the stronger of the two PINs. **Not configured** allows the user to use work apps, without entering a password.
- **Minimum password length**: Enter the minimum number of characters the user's password must have, from **4**-**16**.
- **Maximum minutes of inactivity until work profile locks**: Select the amount of time before the work profile locks. The user must then enter their credentials to regain access.
- **Number of sign-in failures before wiping device**: Enter the number of times an incorrect password can be entered before the work profile is wiped from the device.
- **Password expiration (days)**: Enter the number of days until an end user's password must be changed (from **1**-**255**).
- **Required password type**: Select the type of password that must be set on the device. Choose from:
  - **Device default**
  - **Low security biometric**
  - **Required**
  - **At least numeric**
  - **Numeric complex**: Repeating, or consecutive numbers like '1111' or '1234' aren't allowed
  - **At least alphabetic**
  - **At least alphanumeric**
  - **At least alphanumeric with symbols**
- **Prevent reuse of previous passwords**: Enter the number of new passwords that must be used before an old password can be reused (from **1**-**24**).
- **Fingerprint unlock**: Choose **Block** to prevent end users from using the device fingerprint scanner to unlock the device. **Not configured** allows users to unlock devices with a fingerprint in the work profile.
- **Smart Lock and other trust agents**: Choose **Block** to prevent Smart Lock or other trust agents from adjusting lock screen settings on compatible devices. This feature, sometimes known as a trust agent, lets you disable or bypass the device lock screen password if the device is in a trusted location. For example, bypass the work profile password when the device is connected to a specific Bluetooth device, or when it's close to an NFC tag. Use this setting to prevent users from configuring Smart Lock.

### Device password

These password settings apply to personal profiles on devices that use a work profile.

- **Minimum password length**: Enter the minimum number of characters the user's password must have, from **4**-**14**.
- **Maximum minutes of inactivity until screen locks**: Select the amount of time before an inactive device automatically locks
- **Number of sign-in failures before wiping device**: Enter the number of times an incorrect password can be entered before all data is wiped from the device
- **Password expiration (days)**: Enter the number of days until an end user's password must be changed (from **1**-**255**)
- **Required password type**: Select the type of password that must be set on the device. Choose from:
  - **Device default**
  - **Low security biometric**
  - **Required**
  - **At least numeric**
  - **Numeric complex**: Repeating, or consecutive numbers like '1111' or '1234' are not allowed
  - **At least alphabetic**
  - **At least alphanumeric**
  - **At least alphanumeric with symbols**
- **Prevent reuse of previous passwords**: Enter the number of new passwords that must be used before an old password can be reused (from **1**-**24**).
- **Fingerprint unlock**: Choose **Block** to prevent end user from using the device fingerprint scanner to unlock the device. **Not configured** allows the user to unlock the device using a fingerprint.
- **Smart Lock and other trust agents**: Choose **Block** to prevent Smart Lock or other trust agents from adjusting lock screen settings on compatible devices. This feature, sometimes known as a trust agent, lets you disable or bypass the device lock screen password if the device is in a trusted location. For example, bypass the work profile password when the device is connected to a specific Bluetooth device, or when it's close to an NFC tag. Use this setting to prevent users from configuring Smart Lock.

### System security

- **Threat scan on apps**: **Require** enforces that the **Verify Apps** setting is enabled for work and personal profiles.

   > [!Note]
   > This setting only works for devices that are Android O and above.

### Connectivity

- **Always-on VPN**: Choose **Enable** to set a VPN client to automatically connect and reconnect to the VPN. Always-on VPN connections stay connected or immediately connect when the user locks their device, the device restarts, or the wireless network changes. 

  Choose **Not configured** to disable always-on VPN for all VPN clients.

  > [!IMPORTANT]
  > Be sure to deploy only one Always On VPN policy to a single device. Deploying multiple Always VPN policies to a single device isn't supported.

- **VPN client**: Choose a VPN client that supports Always On. Your options:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Custom
    - **Package ID**: Enter the package ID of the app in the Google Play store. For example, if the URL for the app in the Play store is `https://play.google.com/store/details?id=com.contosovpn.android.prod`, then the package ID is `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  >  - The VPN client you choose must be installed on the device, and it must support per-app VPN in work profiles. Otherwise, an error occurs. 
  >  - You do need to approve the VPN client app in the **Managed Google Play Store**, sync the app to Intune, and deploy the app to the device. After you do this, then the app is installed in the user's work profile.
  >  - There may be known issues when using per-app VPN with F5 Access for Android 3.0.4. See [F5's release notes for F5 Access for Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) for more information.

- **Lockdown mode**: Choose **Enable** to force all network traffic to use the VPN tunnel. If a connection to the VPN isn't established, then the device won't have network access.

  Choose **Not configured** to allow traffic to flow through the VPN tunnel or through the mobile network.

## Next steps

[Assign the profile](device-profile-assign.md) and [monitor its status](device-profile-monitor.md).

You can also create dedicated device kiosk profiles for [Android](device-restrictions-android.md#kiosk) and [Windows 10](kiosk-settings.md) devices.
