---
# required metadata

title: Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment
titlesuffix: Microsoft Intune
description: Learn how to enroll Android devices using Samsung KME
keywords:
author: ErikjeMS
ms.author: erikje
manager:
ms.date: 05/08/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 30df0f9e-6e9e-4d75-a722-3819e33d480d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: arnab
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment

This topic helps you set up Intune for enrolling supported Android devices using Samsung Knox Mobile Enrollment (KME). Using Intune with Samsung KME, you can enroll large numbers of company-owned Android devices when end users turn on their devices for the first time and connect to a WiFi or cellular network. Also, devices can be enrolled using Bluetooth or NFC when using the Knox Deployment App.

To enable Intune enrollment using Samsung KME, you use both the Intune and Samsung Knox portals in this order:

1. In the Knox portal:
    1. [Create an MDM profile](#create-mdm-profile)
    2. [Add devices](#add-devices)
    3. [Assign an MDM profile to the devices](#assign-an-mdm-profile-to-devices)
2. In the Azure portal, [identify devices as corporate-owned](#identify-devices-as-corporate-owned).
3. In the Knox portal, [configure end user sign in](#configure-how-end-users-sign-in).
4. [Distribute the devices](#distribute-devices).


A list of device identifiers (serial numbers and IMEIs) are automatically added to the Knox Portal when purchasing devices from authorized resellers participating in the Knox Deployment Program.


## Prerequisites

To enroll into Intune using KME, you must first register your company on the Samsung Knox portal by following these steps:
1.  [Make sure KME is available in your region](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries): KME is available in over 55 countries. Ensure that your country of deployment is supported.

2.  [Supported devices](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+): KME is available on all Samsung devices with a minimum of Knox 2.4.

3.  [Network requirements](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm): Make sure that the necessary firewall and network access rules are permitted on your network.

4.  [Register for a Samsung account](https://www2.samsungknox.com/en/user/register): A Samsung account is needed to register and enable KME and manage all Knox Enterprise entitlements in a single place.

5.  Registration Review: After your profile is completed and submitted, Samsung performs a review of your application and either approves it immediately or puts it in a pending review status for further follow-up. After your account is approved, you can proceed to further steps.

## Create MDM profile

When your company is successfully registered, you can create your MDM profile for Microsoft Intune in the Knox Portal using the information below. For step-by-step guidance, see the [ Samsung Knox Profile Setup Wizard](https://docs.samsungknox.com/KME-Getting-Started/Content/getting-started-wizard.htm) instructions.

| MDM Profile Fields| Required? | Values |
|-------------------|-----------|-------|
|MDM Server URI     | No        |Leave this blank.
|Profile Name       | Yes       |Enter a profile name of your choice.
|description        | No        |Enter text describing the Profile.
|MDM Agent APK      | Yes       |https://aka.ms/intune_kme
|Skip Setup wizard  | No        |Choose this option to skip standard device setup prompts on behalf of the end user.
|Allow End User to Cancel Enrollment | No | Choose this option to allow users to cancel KME.
|Custom JSON        | No        |Leave this blank.
| EULAs, Terms of Service & User Agreements| No | Choose this option to show Knox-related agreements for user acceptance.
Associate a Knox license with this profile | No | Leave this option unselected. Enrolling to Intune using KME does not require a Knox license.

## Add devices

To assign MDM Profiles to devices, supported Samsung Knox devices must be added to the Knox Portal using one of the following methods:
- **Using Samsung-Approved Reseller(s):** Use this method if you are purchasing devices from one of the Samsung-approved resellers. Resellers can auto-upload devices for you when approved. [Visit the Samsung Knox Enrollment User Guide to learn how to add resellers](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm).

- **Using the Knox Deployment App (KDA):** Use this method if you have existing devices that need to be enrolled using KME. You can either use Bluetooth or NFC to add devices to the Knox Portal using this method. [Visit the Samsung Knox Enrollment User Guide to learn about using the KDA](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm).

## Assign an MDM profile to devices
You must assign an MDM profile to added devices in the Knox Portal before they can be enrolled. [Visit the Samsung Knox Enrollment User Guide to learn about device configuration](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm).

## Identify devices as corporate-owned
You can identify devices enrolled using KME as corporate-owned. This must be done before enrolling the devices. This lets you perform additional management tasks and collect additional information such as the full phone number and an inventory of apps.

Follow these steps to identify devices as corporate-owned:

1. Export the list of devices from Knox Portal as a CSV file.

2. Format the CSV file using IMEI or serial number as indicated [here](https://docs.microsoft.com/en-us/intune/corporate-identifiers-add#identify-corporate-owned-devices-with-imei-or-serial-number).

3. In the Azure portal, upload the CSV file to **Device enrollment** > **Corporate device identifiers** > **Add**.

Now identified devices that enroll will be marked as corporate-owned.

> [!NOTE]
>Intune automatically assigns corporate-owned status to devices enrolled with [Device Enrollment Manager](https://docs.microsoft.com/en-us/intune/device-enrollment-manager-enroll) account.

## Configure how end users sign in

For devices enrolled in Intune using KME, you can configure how an end user signs in as follows:

- **Without user name association:** In the Knox Portal under **Device details**, leave the **User ID** and **Password** fields blank for the added devices. This requires the end user to enter both user name and password when enrolling to Intune.

- **With user name association:** In the Knox Portal under **Device details**, provide a **User ID** (such as a user name for the assigned user or a [Device Enrollment Manager](https://docs.microsoft.com/en-us/intune/device-enrollment-manager-enroll) account) for the added devices. This prepopulates the user name and requires the end user to enter a password when enrolling to Intune.

> [!NOTE]
>
>When user association is defined, only the associated user can enroll the device using KME. This is true even after a factory-reset of the device. When no user association is defined in the Knox Portal, any user with a valid Intune license can enroll the device using KME .
>

## Distribute devices

After creating and assigning an MDM profile, associating a user name, and identifying the devices as corporate-owned in Intune, you can distribute devices to users.

Still need help? Check out the complete [Knox Mobile Enrollment User Guide](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm).

## Frequently asked questions
- **Google Play Account:** Google Play account is not necessary for enrolling the device to Microsoft Intune. But future updates to the Intune Company Portal app may require a Google Play account on the device.

- **Google Device Owner mode:** Enrolling in Google Device Owner mode using KME is not supported in this Preview. This scenario is currently being investigated.

- **"Password" field is ignored:** If the **password** field is populated in **Device details** in the Knox Portal, it is ignored by the Intune Company Portal app. The end user must enter a password on the device to complete device enrollment.

- **"Android Enterprise Enrollment** KME does not support Android Enterprise Enrollment.

## Getting support
Learn more about [how to get support for Samsung KME](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm).


