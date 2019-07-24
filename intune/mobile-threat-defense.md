---
# required metadata

title: Mobile Threat Defense with Microsoft Intune
titleSuffix: Microsoft Intune
description: Use Intune Mobile Threat Defense (MTD) with your Mobile Threat Defense partner to protect access to company resources based on device risk.
keywords:
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# What is Mobile Threat Defense integration with Intune?
Intune can integrate data from a Mobile Threat Defense vendor as an information source for compliance policies and Conditional Access rules. You can use this information to help protect corporate resources like Exchange and SharePoint, by blocking access from compromised mobile devices.  

## What problem does this solve?
Integrating information from a Mobile Threat Defense vendor can help you protect your corporate resources from threats that affect Mobile platforms.  

Typically, companies are proactive in protecting PCs from vulnerabilities and attack while mobile devices often go unmonitored and unprotected. Where mobile platforms have built-in protection such as app isolation and vetted consumer app stores, these platforms remain vulnerable to sophisticated attacks. As more employees use devices for work and to access sensitive information, the information from Mobile Threat Defense vendor can help you protect devices and your resources from increasingly sophisticated attacks.  

## How do the Intune Mobile Threat Defense connectors work?

Intune uses a Mobile Threat Defense connector to create a channel of communication between Intune and your chosen Mobile Threat Defense vendor. Intune Mobile Threat Defense partners offer intuitive, easy to deploy applications for mobile devices. These applications actively scan and analyze threat information to share with Intune. Intune can use the data for either reporting or enforcement purposes.  

For example: A connected Mobile Threat Defense app reports to the Mobile Threat Defense vendor that a phone on your network is currently connected to a network that is vulnerable to Man in the Middle attacks. This information is categorized to an appropriate risk level of low, medium, or high. This risk level is then compared with the risk level allowances you set in Intune. Based on this comparison, access to certain resources of your choice can be revoked while the device is compromised.

## What data does Intune collect for Mobile Threat Defense?

If enabled, Intune collects app inventory information from both personal and corporate-owned devices and makes it available for Mobile Threat Defense (MTD) providers to fetch, such as Lookout for Work. You can collect an app inventory from the users of iOS devices.

This service is opt-in; no app inventory information is shared by default. An Intune administrator must enable App Sync for iOS devices in the service settings before any app inventory information is shared.

**App inventory**  
If you enable App Sync for iOS devices, inventories from both corporate and personally owned iOS devices are sent to your MTD service provider. Data in the app inventory includes:

- App ID
- App Version
- App Short Version
- App Name
- App Bundle Size
- App Dynamic Size
- Whether the app is validated or not
- Whether the app is managed or not

## Sample scenarios

When a device is considered infected by the Mobile Threat Defense solution:

![Image showing a Mobile Threat Defense infected device](./media/MTD-image-1.png)

Access is granted when the device is remediated:

![Image showing a Mobile Threat Defense Access granted](./media/MTD-image-2.png)

> [!NOTE] 
> Using multiple Mobile Threat Defense vendors with Intune is not supported. Having multiple MTD tools enabled will force all MTD apps to be installed and scan across devices for threats.

## Mobile Threat Defense partners

Learn how to protect access to company resource based on device, network, and application risk with:

- [Lookout](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)
- [Sophos Mobile](sophos-mtd-connector.md)
- [Wandera Mobile Threat Defense](wandera-mtd-connector.md)
