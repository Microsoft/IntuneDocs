---
# required metadata

title: Set up enrollment for macOS devices
titleSuffix: Microsoft Intune
description: Learn how to set up enrollment for macOS devices in Intune.
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/13/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Set up enrollment for macOS devices in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune lets you manage macOS devices to give users access to company email and apps.

As an Intune admin, you can set up enrollment for company-owned macOS devices and personally owned macOS devices ("bring your own device" or BYOD). 

## Prerequisites

Complete the following prerequisites before setting up macOS device enrollment:

- [Make sure your device is eligible for Apple device enrollment](https://support.apple.com/en-us/HT204142#eligibility).
- [Configure domains](custom-domain-name-configure.md)
- [Set the MDM Authority](mdm-authority-set.md)
- [Create groups](groups-add.md)
- [Configure the Company Portal](company-portal-app.md)
- Assign user licenses in the [Microsoft 365 admin center](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Get an Apple MDM push certificate](apple-mdm-push-certificate-get.md)

## User-owned macOS devices (BYOD)

You can let users enroll their personal devices for Intune management, known as "bring your own device" or BYOD. After you've completed the prerequisites and assigned users licenses, your users can enroll their devices by:
- going to the [Company Portal website](https://portal.manage.microsoft.com) or
- downloading the Company Portal app.
You can also send them a link to online enrollment steps: [Enroll your macOS device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

For information about other end-user tasks, see these articles:

- [Resources about the end-user experience with Microsoft Intune](end-user-educate.md)
- [Using your macOS device with Intune](/intune-user-help/using-your-macos-device-with-intune)

## Company-owned macOS devices
For organizations that purchase devices for their users, Intune supports the following macOS company-owned device enrollment methods:
- [Apple's Device Enrollment Program (DEP)](device-enrollment-program-enroll-macos.md): Organizations can purchase macOS devices through Apple's Device Enrollment Program (DEP). DEP lets you deploy an enrollment profile “over the air” to bring devices into management.
- [Device enrollment manager (DEM)](device-enrollment-manager-enroll.md): You can use a DEM account to enroll up to 1,000 devices.

## Block macOS enrollment
By default, Intune lets macOS devices enroll. To block macOS devices from enrollment, see [Set device type restrictions](enrollment-restrictions-set.md).

## Enroll virtual macOS machines for testing

> [!NOTE]
> macOS virtual machines are only supported for testing. You should not use macOS virtual machines as production devices for your end users. 

You can enroll macOS virtual machines for testing using either Parallels Desktop or VMware Fusion. 

For Parallels Desktop, you need to set the hardware type and the serial number for the virtual machines so that Intune can recognize them. Follow Parallels' instructions for setting hardware type and [serial number](http://kb.parallels.com/123455) to set up the necessary settings for testing. We recommend that you match the hardware type of the device running the virtual machines to the hardware type of the virtual machines that you're creating. You can find this hardware type in **Apple menu** > **About this Mac** > **System Report** > **Model Identifier**. 

For VMware Fusion, you need to [edit the .vmx file](https://kb.vmware.com/s/article/1014782) to set the virtual machine's hardware model and serial number. We recommend that you match the hardware type of the device running the virtual machines to the hardware type of the virtual machines that you're creating. You can find this hardware type in **Apple menu** > **About this Mac** > **System Report** > **Model Identifier**. 

## User Approved enrollment

User Approved MDM enrollment is a type of macOS enrollment that you can use to manage certain security-sensitive settings. For more information, see [Apple's support documentation](https://support.apple.com/HT208019).

To be user approved, the end user must, after enrolling using the macOS Company Portal, manually provide approval by using System Preferences. Instructions to do this are provided by the macOS Company Portal for users on macOS 10.13.2 and later.

To find out if a device is User Approved, go to the Intune portal and then choose **Devices** > **All devices**> choose the device > **Hardware**. Check the **User Approved** field.

## Next steps

After macOS devices are enrolled, you can [create custom settings for macOS devices](custom-settings-macos.md).
