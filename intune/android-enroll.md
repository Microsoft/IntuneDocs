---
# required metadata

title: Enroll Android devices in Intune
titleSuffix: Microsoft Intune
description: Learn how to enroll Android devices in Intune.
keywords:
author: ErikjeMS 
ms.author: erikje
manager: dougeby
ms.date: 7/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: f276d98c-b077-452a-8835-41919d674db5

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.custom: seodec18
ms.collection: M365-identity-device-management
---

# Enroll Android devices

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

As an Intune administrator, you can enroll Android devices in the following ways:
- Android Enterprise, including:
    - **Android Enterprise work profile**: For personal devices granted permission to access corporate data. Admins can manage work accounts, apps, and data. Personal data on the device is kept separate from work data and admins don't control personal settings or data. 
    - **Android Enterprise dedicated**: For corporate-owned, single use devices, such as digital signage, ticket printing, or inventory management. Admins lock down the usage of a device for a limited set of apps and web links. It also prevents users from adding other apps or taking other actions on the device.
    - **Android Enterprise fully managed**: For corporate-owned, single user devices used exclusively for work and not personal use. Admins can manage the entire device and enforce policy controls unavailable to work profiles. 

## Prerequisites

To prepare to manage mobile devices, you must set the mobile device management (MDM) authority to **Microsoft Intune**. See [Set the MDM authority](mdm-authority-set.md) for instructions. You set this item only once, when you are first setting up Intune for mobile device management.

For devices manufactured by Zebra Technologies, you may need to grant the Company Portal additional permissions depending on the capabilities of the specific device. [Mobility Extensions on Zebra devices](android-zebra-mx-overview.md) has more details.

## Set up Android Enterprise enrollment

Android Enterprise offers a set of enrollment options that provide users with the most up-to-date and secure features. Android Enterprise enrollment options include work profile, fully managed and dedicated devices.

- [Set up Android Enterprise work profile enrollments](android-work-profile-enroll.md)
- [Set up Android Enterprise dedicated device enrollments](android-kiosk-enroll.md)
- [Set up Android Enterprise fully managed enrollments](android-fully-managed-enroll.md)

## End user experience when enrolling a Samsung Knox device

Samsung Knox Standard devices are supported for multi-user management by Intune. This means that users can sign in and out of a device with their Azure AD credentials. The device is centrally managed whether it’s in use or not. When users sign in, they have access to apps and additionally get any policies applied to them. When users sign out all app data is cleared.

There are several considerations when enrolling Samsung Knox devices:
- Even if no policies require a PIN, the device must have at least a four-digit PIN to enroll. If the device does not have a PIN, the user will be prompted to create one.
- There is no user interaction for Workplace Join Certificates (WPJ).
- The user is prompted with Service Enrollment info and what the app can do.
- The user is prompted with Knox Enrollment info and what Knox can do.
- If an Encryption Policy is enforced, users are required to set a six Character Complex password for the device passcode.
- There are no additional user prompts to install certificates pushed by a service for Company Resource Access.
- Some older Knox devices will prompt the user for additional certificates used for Company Resource Access.
- If a Samsung Mini device fails to install the WPJ with either the **Certificate Not Found** or **Unable to Register Device** errors, install the latest Samsung Firmware Updates.

## Next steps

- [Set up Android Enterprise work profile enrollments](android-work-profile-enroll.md)
- [Set up Android Enterprise dedicated device enrollments](android-kiosk-enroll.md)
- [Set up Android Enterprise fully managed enrollments](android-fully-managed-enroll.md)
