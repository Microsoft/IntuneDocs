---
# required metadata

title: Enroll iOS devices in Intune
titleSuffix: Microsoft Intune
description: Set up enrollment of iOS devices in Microsoft Intune.
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.custom: seodec18
ms.collection: M365-identity-device-management
---

# Enroll iOS devices in Intune

Intune enables mobile device management (MDM) of iPads and iPhones to give users access to company email and apps.

As an Intune admin, you can enable enrollment for iOS devices. You can let users enroll personally owned devices, known as "bring your own device" (BYOD) enrollment. You can also enable enrollment of company-owned devices.

## Prerequisites for iOS enrollment
Before you can enable iOS devices, complete the following steps:
- [Make sure your device is eligible for Apple device enrollment](https://support.apple.com/en-us/HT204142#eligibility).
- [Set up Intune](setup-steps.md) - These steps set up your Intune infrastructure. In particular, device enrollment requires that you [set your MDM authority](mdm-authority-set.md).
- [Get an Apple MDM Push certificate](apple-mdm-push-certificate-get.md) - Apple requires a certificate to enable management of iOS and macOS devices.


## User-owned iOS devices (BYOD)

You can let users enroll their personal devices for Intune management, know as "bring your own device" or BYOD. Once you've completed the prerequisites and assigned users licenses, they can download the Intune Company Portal app from the App Store, and follow enrollment instructions in the app. You can customize the Company Portal privacy statement on iOS devices as explained in [privacy statement customization](company-portal-app.md#privacy-statement-customization).

## Company-owned iOS devices
For organizations that buy devices for their users, Intune supports the following iOS company-owned device enrollment methods:

- Apple's Device Enrollment Program (DEP)
- Apple School Manager
- Apple Configurator Setup Assistant enrollment
- Apple Configurator direct enrollment

You can also enroll company-owned iOS devices with a [device enrollment manager](device-enrollment-manager-enroll.md) account.

## Device Enrollment Program
Organizations can purchase iOS devices through Apple's Device Enrollment Program (DEP). DEP lets you deploy an enrollment profile “over the air” to bring devices into management. Learn more about [Device Enrollment Program](device-enrollment-program-enroll-ios.md).

## Apple School Manager
Apple School Manager is a device purchase and enrollment program for schools. Like DEP, you can deploy a profile to enroll devices in management. Learn more about [Apple School Manager](apple-school-manager-set-up-ios.md).

## Apple Configurator
You can enroll iOS devices with Apple Configurator running on a Mac computer. To prepare devices, you USB-connect them and install an enrollment profile. You can enroll devices with Apple Configurator in two ways:
- Setup Assistant enrollment - Wipes the device, prepares it to run Setup Assistant, and installs the company's policies for the device’s new user.
- Direct enrollment - Doesn't wipe the device and enrolls the device with a predefined policy. This method is for devices with no user affinity.

Learn more about [Apple Configurator enrollment](apple-configurator-setup-assistant-enroll-ios.md).

## Use the Company Portal on DEP-enrolled or Apple Configurator-enrolled devices

Devices configured with user affinity can install and run the Company Portal app to download apps and manage devices. After users receive their devices, they must complete a number of additional steps to complete the Setup Assistant and install the Company Portal app.

User affinity is required to support the following:
- Mobile application management (MAM) apps
- Conditional Access to email and company data
- Company Portal app

**How users enroll corporate-owned iOS devices with user affinity**
1. When users turn on their device, they are prompted to complete the Setup Assistant. 
2. After completing setup, users are prompted for an Apple ID. They must provide an Apple ID to allow the device to install Company Portal. 
3. The iOS device automatically installs the Company Portal app from the App Store.
4. Users should launch the Company Portal app and sign in using the credentials (like the unique personal name or UPN) that are associated with their subscription in Intune. 
5. After logging in, enrollment is complete. Users can now use this device with the full set of capabilities.

### About corporate-owned managed devices with no user affinity

Devices that are configured with no user affinity do not support the Company Portal and should not have the app installed. The Company Portal is designed for users who have corporate credentials and require access to personalized corporate resources (like email). Devices that are enrolled with no user affinity aren't intended to have a dedicated user sign in. Kiosk, point of sale (POS), or shared-utility devices are typical use cases for devices that are enrolled with no user affinity.

If user affinity is required, be sure that the device’s enrollment profile has **User Affinity** selected before enrolling the device. To change the affinity status on a device, you must retire the device and reenroll it.

## See also

[Troubleshooting iOS device enrollment problems in Microsoft Intune](https://support.microsoft.com/help/4039809)
