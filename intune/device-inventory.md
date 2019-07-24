---
# required metadata

title: View device details with Microsoft Intune - Azure | Microsoft Docs
description: View your device details, including operating systems, storage space, manufacturer, and model. Get a list of installed apps, check compliance policies, and set up TeamViewer with Microsoft Intune in Azure. Similar to viewing inventory of the devices you manage.
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# See device details in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

The **Devices** feature provides additional details into the devices you manage, including their hardware and the apps installed.

This article shows you how to view all your devices, and their properties in the Azure portal.

## View the device details

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Select **Devices** > **All devices** > select one of your listed devices to open its details:

   - **Overview** shows the device name, and lists some key properties of the device, like whether it's a bring-your-own-device (BYOD) device, check in time, and more. You can do the following on the device:
      - [Retire](devices-wipe.md#retire)
      - [Wipe](devices-wipe.md#wipe)
      - [Remote lock](device-remote-lock.md)
      - [Synchronize device](device-sync.md)
      - [Reset passcode](device-passcode-reset.md)
      - [Restart](device-restart.md) (Windows only)
      - [Fresh Start](device-fresh-start.md) (Windows only)
      - Start a remote assistance session
   - Use **Properties** to assign a [device category you create](device-group-mapping.md), and change ownership of the device to a personal device, or a corporate device.
   - **Hardware** includes many details about the device, like the device ID, operating system and version, storage space, and more details.
   - **Discovered apps** lists all the apps that Intune found installed on the device, and the app versions. For more information, see [Intune discovered apps](app-discovered-apps.md).
   - **Device compliance** lists all assigned compliance policies, and if the device is compliant or not compliant.
   - **Device configuration** shows all device configuration policies assigned to the device, and if the policy succeeded or failed.

Intune collects an app list only on corporate-owned devices. Apps aren't checked on personal devices. For Windows 10 PCs, only modern apps are listed for corporate-owned devices. Intune doesn't collect information about Win32 apps on the device unless you're using the [Intune Management Extension](https://docs.microsoft.com/intune/intune-management-extension). This only works on corporate owned devices. Depending on the carrier used by the devices, not all apps might be collected. There's no aggregated view and the data can only be viewed on a per-device basis currently.

|Platform|For Personal-owned Devices|For Company-owned devices|  
|--------------|---------------------------------|--------------------------------|  
|Windows 10 (without the Configuration Manager client)|Only managed modern apps|All modern apps installed on the device|
|Windows 8.1 (without the Configuration Manager client)|Only managed apps|Only managed apps|  
|Windows Phone 8|Only managed apps|Only managed apps|  
|Windows RT|Only managed apps|Only managed apps|  
|iOS|Only managed apps|All apps installed on the device|
|macOS|All apps installed on the device|All apps installed on the device|  
|Android|Only managed apps|All apps installed on the device|  
|Android Enterprise|Only managed apps|Only apps installed in the Work Profile|  

## Hardware device details
Depending on the carrier used by the devices, not all details might be collected

|Detail|Description|Platform| 
|--------------|----------------------|----|  
|Name|The name of the device.|Windows, iOS|
|Management name|The device name used only in the console. Changing this name won't change the name on the device.|Windows, iOS|
|UDID|The device's Unique Device identifier.|Windows, iOS|
|Intune Device ID|A GUID that uniquely identifies the device.|Windows, iOS|
|Serial number|The device's serial number from the manufacturer.|Windows, iOS|
|Shared device|If **Yes**, the device is shared by more than one user.|Windows, iOS|
|User approved enrollment|If **Yes**, then the device has user approved enrollment that lets admins manage certain security settings on the device.|Windows, iOS|
|Operating system|The operating system used on the device.|Windows, iOS|
|Operating system version|The version of the operating system on the device.|Windows, iOS|
|Operating system language|The language set for the operating system on the device.|Windows, iOS|
|Build number|The operating system's build number.|Android|
|Security patch level|The security patch level for the device.|Android|
|Total storage space|The total storage space on the device (in gigabytes).|Windows, iOS|
|Free storage space|The unused storage space on the device (in gigabytes).|Windows, iOS|
|IMEI|The device's International Mobile Equipment Identity.|Windows, iOS, Android|
|MEID|The device's mobile equipment identifier.|Windows, iOS, Android|
|Manufacturer|The manufacturer of the device.|Windows, iOS, Android|
|Model|The model of the device.|Windows, iOS, Android|
|Phone number|The phone number assigned to the device.|Windows, iOS, Android|
|Subscribe carrier|The device's wireless carrier.|Windows, iOS, Android|
|Cellular technology|The radio system used by the device.|Windows, iOS, Android|
|Wi-Fi MAC|The device's Media Access Control address.|Windows, iOS, Android|
|ICCID|The Integrated Circuit Card Identifier, which is a SIM card's unique identification number.|Windows, iOS, Android|
|Enrolled date|The date and time that the device was enrolled in Intune.|Windows, iOS, Android|
|Last contact|The date and time that the device last connected to Intune.|Windows, iOS, Android|
|Activation lock bypass code|The code that can be used to bypass the activation lock.|Windows, iOS, Android|
|Azure AD registered|If **Yes**, the device is registered with Azure Directory.|Windows, iOS, Android|
|Intune registered|If **Yes**, the device is registered with Intune|Windows, iOS, Android|
|Compliance|The device's compliance state.|Windows, iOS, Android|
|EAS activated|If **Yes**, then the device is synchronized with an Exchange mailbox.|Windows, iOS, Android|
|EAS activation ID|The device's Exchange ActiveSync identifier.|Windows, iOS, Android|
|Supervised|If **Yes**, administrators have enhanced control over the device.|Windows, iOS, Android|
|Encrypted|If **Yes**, the data stored on the device is encrypted.|Windows, iOS, Android|



## Next steps
See what else you can do to [manage your devices](device-management.md) with Intune.
