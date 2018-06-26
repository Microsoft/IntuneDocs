---
# required metadata

title: Pradeo MTD connector with Intune
titleSuffix: Intune on Azure
description: Learn about integrating Intune with Pradeo Mobile Threat Defense to control mobile device access to your corporate resources.
keywords:
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/29/2017
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 975d8d84-792a-41ad-925a-4a7f1ae4dcaf

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: hacha
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Pradeo Mobile Threat Defense connector with Intune

You can control mobile device access to corporate resources using conditional access based on risk assessment conducted by Pradeo, a Mobile Threat Defense (MTD) solution that integrates with Microsoft Intune. Risk is assessed based on telemetry collected from devices running the Pradeo app.

You can configure conditional access policies based on Pradeo risk assessment enabled through Intune device compliance policies, which you can use to allow or block noncompliant devices to access corporate resources based on detected threats.

## How do Intune and Pradeo help protect your company resources?

Pradeo app for Android and iOS captures file system, network stack, device, and application telemetry where available, then sends the telemetry data to the Pradeo cloud service to assess the device's risk for mobile threats.

The Intune device compliance policy includes a rule for Pradeo Mobile Threat Defense, which is based on the Pradeo risk assessment. When this rule is enabled, Intune evaluates device compliance with the policy that you enabled. If the device is found noncompliant, users are blocked access to corporate resources like Exchange Online and SharePoint Online. Users also receive guidance from the Pradeo app installed in their devices to resolve the issue and regain access to corporate resources.

## Sample scenarios

See below a few scenarios when integrating Pradeo with Intune:

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices until the threat is resolved:

-   Connecting to corporate e-mail

-   Syncing corporate files with the OneDrive for Work app

-   Accessing company apps

**Block when malicious apps are detected:**

![Malicious apps detected](./media/Maliciousapps_blocked_Pradeo.png)

**Access granted on remediation:**

![Malicious apps detected access granted](./media/maliciousapps_unblocked_Pradeo.png)

### Control access based on threat to network

Detect threats like **Man-in-the-middle** in network, and protect access to Wi-Fi networks based on the device risk.

**Block network access through Wi-Fi:**

![Block network access through Wi-Fi](./media/network_wifi_blocked_Pradeo.png)

**Access granted on remediation:**

![Access granted on remediation](./media/network_wifi_unblocked_Pradeo.png)

### Control access to SharePoint Online based on threat to network

Detect threats like **Man-in-the-middle** in network, and prevent synchronization of corporate files based on the device risk.

**Block SharePoint Online when network threats are detected:**

![Block SharePoint Online when network threats are detected](./media/network_spo_blocked_Pradeo.png)

**Access granted on remediation:**

![Access granted on remediation for Sharepoint example](./media/network_spo_unblocked_Pradeo.png)

## Supported platforms

-   **Android 4.0.3 and later**

-   **iOS 7 and later**

## Prerequisites

-   Azure Active Directory Premium

-   Microsoft Intune subscription

-   Pradeo Mobile Threat Defense subscription

    -   For more information, see [Pradeo's website](https://apps-security.com/).

## Next steps

- [Integrate Pradeo with Intune](Pradeo-mtd-connector-integration.md)

- [Set up Pradeo apps](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Create Pradeo device compliance policy](mtd-device-compliance-policy-create.md)

- [Enable Pradeo MTD connector](mtd-connector-enable.md)
