---
# required metadata

title: Compare Windows PC management options
titleSuffix: Microsoft Intune
description: Enrollment of corporate-owned iOS devices by using the Apple Device Enrollment Program (DEP) or Apple Configurator.
keywords:
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology:
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3

# optional metadata

#audience:
#ms.devlang:
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
---

# Compare managing Windows PCs as computers or mobile devices

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Organizations can use Microsoft Intune to manage Windows PCs either as mobile devices with mobile device management (MDM) or as computers with the Intune software client.  Microsoft recommends that customers use the MDM management solution whenever possible. To help you better understand the differences between these options, however, the following chart compares the two management options.

|**Capability / Scenario** |**Windows as Computer**<br>Intune software client | **Windows as Mobile Device**<br>MDM |
|--------------|-------------------------------|-------------------------------|
|**Operating systems** |Windows 10, Windows 8+, Windows 7, Windows Vista | Windows 10+ |
|**Intune Portal support** |[Silverlight console](https://manage.microsoft.com)|[Azure portal](https://portal.azure.com) |
|**Conditional Access**|Not available|Available <br>[What is Conditional Access?](conditional-access.md)|
|**Bulk enrollment**|Not available|Available <br>[Bulk enrollment for Windows devices](windows-bulk-enroll.md)|
|**Device profiles**|Not available|Available <br>[What are Microsoft Intune device profiles?](device-profiles.md)|
|**Agentless enrollment**|Not available |Available<br>[Enroll Windows devices](windows-enroll.md)|
|**Software update management**| Windows Updates and Microsoft app updates<br>[Keep Windows PCs up-to-date with software updates](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)|Microsoft Store for Business for both Windows 10 and Microsoft apps updates<br> [Configure Windows Update for Business settings](windows-update-for-business-configure.md) |
|**Software license management**|Available <br>[Manage license agreements for Windows PC software](manage-license-agreements-for-windows-pc-software-in-microsoft-intune.md)|Microsoft Store for Business (.appx apps only)<br>[Manage apps purchased from the Microsoft Store for Business](windows-store-for-business.md)|
|**Inventory**|Available <br>[View hardware and software inventory for Windows PCs](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md)|Available <br>[How to monitor app information](apps-monitor.md)<br>[What is device management](device-management.md)|
|**Windows Firewall policy**|Available <br>[Help protect Windows PCs using Windows Firewall policies](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) |Available <br>[Windows Defender Firewall](endpoint-protection-windows-10.md#windows-defender-firewall)|
|**Anti-malware protection**|Endpoint Protection<br>[Help secure Windows PCs with Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)|Windows Defender<br>[Enable Windows Defender](advanced-threat-protection.md)|
|**Remote assistance** |TeamViewer<br>[Request and provide remote assistance for Windows PCs](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md)|TeamViewer<br> [Use TeamViewer to remotely administer Intune devices](teamviewer-support.md) |
|**App deployment** | Not available for Microsoft Store for Business,<br>.exe, .appx, and multi-file .msi only<br>[Add apps for Windows PCs that run the Intune software client](add-apps-for-windows-pcs-in-microsoft-intune.md)|Available for Microsoft Store apps and line-of-business apps<br>[How to add Windows store apps](store-apps-windows.md)<br>[How to add Windows line-of-business (LOB) apps](lob-apps-windows.md)|
|**App protection**|Not available|Available <br>[What are app protection policies?](app-protection-policy.md)|
|**Health attestation**|Not available|Available|


## Advantages of MDM Windows PC management
Windows PC management with modern mobile device management has the following advantages:
- **Scalability** - MDM management scales with Intune cloud management. The Intune software client is limited to 7000 PCs.
- **Simplicity** - Uses modern management capabilities included in the operating system without relying on a downloaded software client
- **Consistency** - Your Windows PCs are managed like all other mobile devices in your organization
<!-- - **Cloud optimization** - -->
