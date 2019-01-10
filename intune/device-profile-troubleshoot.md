---
# required metadata

title: Troubleshoot device profiles in Microsoft Intune - Azure | Microsoft Docs
description: Common issues with device profiles, including profile changes not applied to some users or devices, how long does it take for a new policy to be pushed to devices, which settings are applied when there are multiple policies, what happens when a profile is deleted or removed, and more with Microsoft InTune in the Azure portal
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 1/17/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Common issues and resolutions with device profiles in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Troubleshoot common issues using Intune device profiles.

## Why doesn't a user get a new profile when changing a password or passphrase on an existing Wi-Fi profile? 
You create a corporate Wi-Fi profile, deploy the profile to a group, change the password, and save the profile. When the profile changes, some users may not get the new profile.

To mitigate this issue, set up guest Wi-Fi. If the corporate Wi-Fi fails, users can connect to the guest Wi-Fi. Be sure to enable any automatically connect settings. Deploy the guest Wi-Fi profile to all users.

Some additional recommendations:  

- Since the Wi-Fi network you're connecting to uses a password or passphrase, make sure you can connect to the Wi-Fi router directly. You can test with an iOS device.
- After you successfully connect to the Wi-Fi endpoint (Wi-Fi router), note the SSID and the credential used (this value is the password or passphrase).
- Enter the SSID and credential (password or passphrase) in the Pre-Shared Key field. 
- Deploy to a test group that has limited number of users, preferably only the IT team. 
- Sync your iOS device to Intune. Enroll if you haven’t already enrolled. 
- Test connecting to the same Wi-Fi endpoint (as mentioned in the first step) again.
- Roll out to larger groups and eventually to all expected users in your organization. 

## How long does it take for mobile devices to get a policy or apps after they have been assigned?
When a policy or an app is assigned, Intune immediately begins notifying the device to check in with the Intune service. The notification typically takes less than five minutes.

If a device doesn't check in to get the policy after the first notification is sent, Intune makes three more attempts. If the device is offline (for example, it is turned off, or not connected to a network), it might not receive the notifications. In this case, the device gets the policy on its next scheduled check-in with the Intune service as follows:

- iOS and macOS: Every six hours
- Android: Every eight hours
- Windows Phone: Every eight hours
- Windows 8.1 and Windows 10 PCs enrolled as devices: Every eight hours

If the device is recently enrolled, the check-in frequency is more frequent, as follows:

- iOS and macOS: Every 15 minutes for six hours, and then every six hours
- Android: Every three minutes for 15 minutes, then every 15 minutes for two hours, and then every eight hours
- Windows Phone: Every five minutes for 15 minutes, then every 15 minutes for two hours, and then every eight hours
- Windows PCs enrolled as devices: Every three minutes for 30 minutes, and then every eight hours

To immediately check for the policy anytime, users can open the Company Portal app, and sync the device.

For devices without user affinity, the sync frequency immediately following enrollment can vary from hours to a day or more. Intune sends requests at various intervals for a device to check in with the service. However it is still up to the device to check in. After initial enrollment, depending on the type of device enrollment and the policies and profiles assigned to a device, the time it takes a device to complete the check-in is unpredictable. However, once the device is enrolled, and all initial policies are applied, the device typically checks for new policies about every six hours.

## What actions cause Intune to immediately send a notification to a device?
Devices check in with Intune when they receive a notification to check in, or during their regularly scheduled check-in. When you target a device or user with an action, such as wipe, lock, passcode reset, app assignment, profile assignment, or policy assignment, then Intune immediately notifies the device to check in with the Intune service to receive these updates.

Other changes, such as revising the contact information in the company portal, do not cause an immediate notification to devices.

## If multiple policies are assigned to the same user or device, how do I know which settings gets applied?
If two or more policies are assigned to the same user or device, then which settings apply occur at the individual setting level:

-   Compliance policy settings always have precedence over configuration policy settings

-   If a compliance policy is evaluated against the same setting in a different compliance policy, then the most restrictive compliance policy setting applies.

-   If a configuration policy setting conflicts with a setting in a different configuration policy, this conflict displays in the Azure portal. In this scenario, manually resolve these conflicts.

## What happens when app protection policies conflict with each other? Which one is applied to the app?
Conflict values are the most restrictive settings available in an app protection policy, except for the number entry fields (like PIN attempts before reset). The number entry fields are set the same as the values, as if you created a MAM policy in the console by using the recommended settings option.

Conflicts occur when two profile settings are the same. For example, you configured two MAM policies that are identical except for the copy/paste setting. In this scenario, the copy/paste setting is set to the most restrictive value, but the rest of the settings is applied as configured.

If one profile is assigned to the app and takes effect, and then a second one is assigned, the first one takes precedence and stays applied, while the second shows in conflict. If they are both applied at the same time, meaning that there is no preceding profile, then they are both in conflict. Any conflicting settings are set to the most restrictive values.

## What happens when iOS custom policies conflict?
Intune does not evaluate the payload of Apple Configuration files or a custom Open Mobile Alliance Uniform Resource Identifier (OMA-URI) profile. It merely serves as the delivery mechanism.

When you assign a custom profile, ensure that the configured settings do not conflict with compliance, configuration, or other custom policies. If a custom profile and its settings conflicts, then the settings are applied randomly.

## What happens when a profile is deleted or no longer applicable?
When you delete a profile, or you remove a device from a group that has the profile, the profile and settings are removed from the device according to the following lists:

- Wi-Fi, VPN, certificate, and email profiles: These profiles are removed from all supported enrolled devices.
- All other profile types:  
	- **Windows and Android devices**: Settings are not removed from the device
	- **Windows Phone 8.1 devices**: The following settings are removed:  
		- Require a password to unlock mobile devices
		- Allow simple passwords
		- Minimum password length
		- Required password type
		- Password expiration (days)
		- Remember password history
		- Number of repeated sign-in failures to allow before the device is wiped
		- Minutes of inactivity before password is required
		- Required password type – minimum number of character sets
		- Allow camera
		- Require encryption on mobile device
		- Allow removable storage
		- Allow web browser
		- Allow application store
		- Allow screen capture
		- Allow geolocation
		- Allow Microsoft account
		- Allow copy and paste
		- Allow Wi-Fi tethering
		- Allow automatic connection to free Wi-Fi hotspots
		- Allow Wi-Fi hotspot reporting
		- Allow wipe
		- Allow Bluetooth
		- Allow NFC
		- Allow Wi-Fi

	- **iOS**: All settings are removed, except:
		- Allow voice roaming
		- Allow data roaming
		- Allow automatic synchronization while roaming

## I changed a device restriction profile, but the changes haven't taken effect
Windows Phone devices do not allow security policies set using MDM or EAS to be reduced in security once you've set them. For example, you set a **Minimum number of character password** to 8 then try to reduce it to 4. The more restrictive profile has already been applied to the device.

If you want to change the profile to a less secure value, then reset security policies. For example, in Windows 8.1, on the desktop, swipe in from right, and select **Settings** > **Control Panel**. Select the **User Accounts** applet. In the left-hand navigation menu, there is a **Reset Security Policies** link (toward the bottom). Select it, and then choose **Reset Policies**.

Other MDM devices, such as Android, Windows Phone 8.1 and later, and iOS, and Windows 10, may need to be retired, and re-enrolled back into the service to apply a less restrictive profile.

## Some settings in my Windows 10 profile are returning "Not Applicable"
When Windows 10 settings return "Not Applicable", it means that specific setting is not supported on that particular version/edition of Windows. This can occur for two reasons:

	- The setting is only available for newer versions of Windows than the current OS on the client
	- The setting is only available for specific Windows Editions/SKUs (Home, Pro, Enterprise, Education)

To understand a settings version and SKU requirements, visit the Configuration Service Provider (CSP) reference https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference 

## Next steps
Need extra help? See [How to get support for Microsoft Intune](get-support.md).
