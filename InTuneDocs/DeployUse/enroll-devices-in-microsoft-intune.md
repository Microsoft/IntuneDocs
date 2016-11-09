---
# required metadata

title: Enroll devices | Microsoft Intune
description: Mobile device management (MDM) uses enrollment to bring devices into management and allow access to resources.
keywords:
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 09/15/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: damionw
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Enroll devices for management in Intune
You can enroll devices, including Windows PCs, to enable mobile device management (MDM) with Microsoft Intune. This topic describes different ways to enroll mobile devices in Intune management. The way you enroll your devices depends on the device type, ownership, and the level of management that's needed. "Bring your own device" (BYOD) enrollment lets users enroll their personal phones, tablets, or PCs. Corporate-owned device (COD) enrollment enables management scenarios like remote wipe, shared devices, or user affinity for a device.

You can enroll devices, including Windows PCs, to enable mobile device management (MDM) with Microsoft Intune. This topic describes different ways to enroll mobile devices in Intune management. The way you enroll your devices depends on the device type, ownership, and the level of management that's needed. "Bring your own device" (BYOD) enrollment lets users enroll their personal phones, tablets, or PCs. Corporate-owned device (COD) enrollment enables management scenarios like remote wipe, shared devices, or user affinity for a device.

You can enroll devices, including Windows PCs, to enable mobile device management (MDM) with Microsoft Intune. This topic describes different ways to enroll mobile devices in Intune management. The way you enroll your devices depends on the device type, ownership, and the level of management that's needed. "Bring your own device" (BYOD) enrollment lets users enroll their personal phones, tablets, or PCs. Corporate-owned device (COD) enrollment enables management scenarios like remote wipe, shared devices, or user affinity for a device.
If you use [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune), either on-premises or hosted in the cloud, you can enable simple Intune management without enrollment. Windows PCs can also be managed using [Intune client software](#manage-windows-pcs-with-intune).

## Overview of device enrollment methods

The following table shows Intune's enrollment methods with their supported capabilities. These capabilities include:
- **Wipe** - Factory reset the device, removing all data. For more information, see [Retire devices](retire-devices-from-microsoft-intune-management.md).
- **Affinity** - Associates devices with users. Required for mobile application management (MAM) and conditional access to company data. For more information, see [User affinity](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#using-company-portal-on-dep-or-apple-configurator-enrolled-devices).
- **Lock** - Prevents users from removing the device from management. iOS devices require Supervised mode for Lock. For more information, see [Remote lock](retire-devices-from-microsoft-intune-management.md#block-access-a-device).

**iOS enrollment methods**

| **Method** |	**Wipe** |	**Affinity**	|	**Lock** | **Details** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|	Yes |	No | [More information](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|	No |No |No	| [More information](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|
|**[DEP](#dep)**|	Yes |	Optional |	Optional|[More information](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB-SA](#usb-sa)**|	Yes |	Optional |	No| [More information](ios-setup-assistant-enrollment-in-microsoft-intune.md)|
|**[USB-Direct](#usb-direct)**|	No |	No	| No|[More information](ios-direct-enrollment-in-microsoft-intune.md)|

**Windows enrollment methods**

| **Method** |	**Wipe** |	**Affinity**	|	**Lock** | **Details**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Yes|	Yes |	No | [More information](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|	No |No |No	|[More information](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Android enrollment methods**

| **Method** |	**Wipe** |	**Affinity**	|	**Lock** | **Details**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|	Yes |	No | [More information](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|	No |No |No	|[More information](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

For a series of questions that help you find the right method, see [Choose how to enroll devices](/intune/get-started/choose-how-to-enroll-devices1).

## BYOD
"Bring your own device" users install the Company Portal app and enroll their device. This enables users to connect to the company network and join the domain or Azure Active Directory. For most platforms, you have to enable BYOD enrollment for many COD scenarios. For more information, see [Prerequisites for device enrollment](prerequisites-for-enrollment.md). ([Go back to the table](#overview-of-device-enrollment-methods))

## Corporate-owned devices
Corporate-owned devices (COD) can be managed by using the Intune console. iOS devices can be enrolled directly through the tools that are provided by Apple. All device types can be enrolled by an admin or manager using the device enrollment manager. Devices with an IMEI number can also be identified and tagged as company-owned to enable COD scenarios.

For more information, see [Enroll corporate-owned devices](manage-corporate-owned-devices.md).

### DEM
Device enrollment manager is a special Intune account that's used to enroll and manage multiple corporate-owned devices. Managers can install the Company Portal and enroll many user-less devices. Learn more about [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Go back to the table](#overview-of-device-enrollment-methods))

### DEP
Apple Device Enrollment Program (DEP) management lets you create and deploy policy “over the air” to iOS devices that are purchased and managed with DEP. The device is enrolled when users turn on the device for the first time and run iOS Setup Assistant. This method supports **iOS Supervised** mode, which in turn enables:
  -	Locked enrollment
  -	Conditional access
  -	Jailbreak detection
  -	Mobile application management

Learn more about [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Go back to the table](#overview-of-device-enrollment-methods))

### USB-SA
USB-connected, corporate-owned devices are prepared with Intune policy. For Setup Assistant enrollment, the admin creates this Intune policy and exports it to Apple Configurator. The admin must enroll each device manually. Users receive their devices and run Setup Assistant, enrolling their device. This method supports **iOS Supervised** mode, which in turn enables:
  -	Conditional access
  -	Jailbreak detection
  -	Mobile application management

Learn more about [Setup Assistant enrollment with Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Go back to the table](#overview-of-device-enrollment-methods))

### USB-Direct
For direct enrollment, the admin creates an Intune policy and exports it to Apple Configurator. USB-connected, corporate-owned devices are enrolled directly and don't require a factory reset. The admin must enroll each device manually. Devices are managed as user-less devices. They are not locked or supervised and cannot support conditional access, jailbreak detection, or mobile application management. Learn more about [direct enrollment with Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md). ([Go back to the table](#overview-of-device-enrollment-methods))

## Mobile device management with Exchange ActiveSync and Intune
Mobile devices that aren't enrolled but that connect to Exchange ActiveSync (EAS) can be managed by Intune using EAS MDM policy. Intune uses an Exchange Connector to communicate with EAS, either on-premises or cloud-hosted.

For more information, see [Mobile device management with Exchange ActiveSync and Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md).


## Windows PC management with Intune  
You can also use Microsoft Intune to manage Windows PCs with the Intune client software. PCs that are managed with the Intune client can:

 - Report software and hardware inventories
 - Install desktop applications (for example .exe and .msi files)
 - Firewall settings

PCs that are managed with the Intune client software cannot be fully wiped, although selective wipe is available. PCs managed with the Intune software client cannot take advantage of many Intune management features such as conditional access, VPN and Wi-Fi settings, or deployment of certificates and email configurations.

For more information, see [Manage Windows PCs with Intune](manage-windows-pcs-with-microsoft-intune.md).

## Supported device platforms

Intune can manage the following device platforms:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## Next steps
- [Prerequisites for device enrollment](prerequisites-for-enrollment.md)
- [Manage corporate-owned devices](manage-corporate-owned-devices.md)
- [Supported mobile  devices and computers](../get-started/supported-mobile-devices-and-computers.md)
