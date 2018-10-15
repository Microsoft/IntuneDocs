---
# required metadata

title: Android kiosk settings in Microsoft Intune - Azure | Microsoft Docs
description: Configure Android enterprsie kiosk devices. 
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 9/17/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Android enterprise kiosk settings in Intune

Android kiosk profiles support the following configuration settings. When creating a profile, these settings appear when you choose **Profile type** > **Device Owner Only** > **Device restrictions**. To see these settings, choose **Properties** from an Android enterprise device restriction profile and then choose **Configure**.

## General settings

- **Screen capture**: Choose **Block** to prevent users from capturing the device's screen.
- **Camera**: Choose **Block** to disable the device's camera.
- **Default permission policy**: This setting defines the default permission policy for requests for runtime permissions. The possible values include:
    - **Device default**: Use the device's default setting.
    - **Prompt**: The user is prompted to approve the permission.
    - **Auto grant**: Permissions are automatically granted.
    - **Auto deny**: Permissions are automatically denied.
- **Volume changes**: Choose **Block** to prevent users from changing the device's volume.
- **Wipe**: Choose **Block** to prevent users from wiping the device.
- **Safe boot**: Choose **Block** to prevent users from rebooting the device into safe mode.
- **Status bar**: Choose **Block** to prevent users from access the status bar, including notifications and quick settings.
- **Wi-Fi setting changes**: Choose **Block** to prevent users from changing wi-fi configurations created by the device owner. Users can create their own wi-fi configurations.
- **Wi-Fi access point configuration**: Choose **Block** to prevent users from creating or editing any wi-fi configurations.
- **Debugging features**: Choose **Allow** to let users use debugging features.
- **Microphone adjustment**: Choose **Block** to prevent users from adjusting the volume of or muting the microphone.
- **Wipe protection emails**: Choose **Google account email addresses** to define  email addresses (separate with semi colons) that can unlock the device after a wipe. If an email is not specified, anyone can unlock the device after a wipe.
- **Network escape hatch**: Choose **Enable** to let turn on the network escape hatch feature. If a network connection can't be made at boot time, the escape hatch prompts the user to temporarily connect to a network in order to refresh the device policy. After applying the policy, the temporary network is forgotten and the device continues booting. This prevents being unable to connect to a network if there is no suitable network in the last policy and the device boots into an app in lock task mode, or the user is unable to reach device settings.
- **Allow installation from unknown sources**: Choose **Allow** to let users install from unknown sources.
- **System update**: Choose an option to define how the device handles over the air updates:
    - **Device Default**: Use the device's default setting.
    - **Automatic**: Updates are automatically installed without user interaction. Setting this policy immediately installs any pending updates.
    - **Postponed**: Updates are postponed for 30 days. At the end of the 30 days, the user is prompted by Android to install the update. It's possible for device manufacturers or carriers to prevent (exempt) important security updates from being postponed. An exempted update shows a system notification to the user on the device. 
    - **Maintenance window**: Installs updates automatically during a daily maintenance window that you set in Intune. Installation is attempted daily for 30 days, and can fail due to insufficient space or battery levels. After 30 days, the user is prompted by Android to install. This window is also used to install updates for Play apps. This option is recommended for dedicated devices, such as kiosks, as single-app kiosk foreground apps can be updated. 

## Kiosk settings

- **Kiosk mode**: Defines whether the device can run only a single app or multiple apps. For more information, see [Kiosk settings for Android devices](android-kiosk-settings.md).
    - **Single app kiosk**: Users can only access a single app.
    - **Multi-app kiosk**: Users can access a limited set of apps.

## Device password settings

- **Keyguard**: Choose **Disable** to prevent uses from using Keyguard on the device.
- **Required password type**: Define the type of password required for the device.
- **Minimum password length**: Define the minimum password length required for the device.
- **Number of sign-in failures before wiping device**: Define the number of failed sign-ins that must occur before the device is wiped.

> [!Note] 
> If these settings are made, users are not prompted for a password on devices that are enrolled without user affinity. If a user enters a password or passcode directly on the device in the Security Lock screen settings of the device, the password or passcode must meet the parameters that are defined by the Intune Device Restriction Profile.

## Power settings

- **Time to lock screen**: Set the amount of idle time required before the device locks.
- **Screen on while device plugged in**: Choose which power sources cause the device's screen to stay on when plugged in.

## Users and Accounts settings

- **Add new users**: Choose **Block** to prevent users from adding new users.
- **User removal**: Choose **Block** to prevent users from removing users.
- **Account changes**: Choose **Block** to prevent users from modifying accounts.

## Next steps
[Assign the profile](device-profile-assign.md) and [monitor its status](device-profile-monitor.md).



