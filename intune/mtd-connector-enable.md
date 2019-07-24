---
# required metadata

title: Enable Mobile Threat Defense connector in Microsoft Intune
titleSuffix: Microsoft Intune
description: Enable the connector between your Mobile Threat Defense (MTD) partner and Microsoft Intune.
keywords:
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Enable the Mobile Threat Defense connector in Intune

> [!NOTE] 
> This topic applies to all Mobile Threat Defense partners.

During Mobile Threat Defense (MTD) setup, you've configured a policy for classifying threats in your MTD partner console and you've created the device compliance policy in Intune. If you've already configured the Intune connector in the MTD partner console, you can now enable the MTD connection for MTD partner applications.

When you integrate a new application to Intune Mobile Threat Defense and enable the connection, Intune creates a classic conditional access policy in Azure Active Directory. Each MTD app you integrate, like [Defender ATP](advanced-threat-protection.md) or any of our additional [MTD partners](mobile-threat-defense.md#mobile-threat-defense-partners), creates a new classic conditional access policy.  These policies can be ignored, but should not be edited, deleted, or disabled.

Classic conditional access policies for MTD apps: 

- Are used by Intune MTD to require that devices are registered in Azure AD so that they have a device ID. The ID is required so that devices and can successfully report their status to Intune.  
- Are distinct from conditional access policies you might create to help manage MTD.
- By default, don’t interact with other conditional access policies you use for evaluation.  

To view classic conditional access policies, in [Azure](https://portal.azure.com/#home), go to **Azure Active Directory** > **Conditional Access** > **Classic policies**.


## To enable the MTD connector

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

4. On the **Intune Dashboard**, choose **Device compliance**, then choose **Mobile Threat Defense** under the **Setup** section.

5. On the **Mobile Threat Defense** pane, choose **Add**.

6. Choose your MTD solution as the **Mobile Threat Defense connector to setup** from the drop-down list.

    ![MTD setup in Intune Azure portal](./media/enable-mtd-connector-1.png)

7. Enable the toggle options according to your organization's requirements. Toggle options visible will vary depending on the MTD partner.

## MTD toggle options

You can decide which MTD toggle options you need to enable according to your organization's requirements. Here are more details:

- **Connect Android 4.1+ devices to [MTD partner name] for Work MTD**: When you enable this option, you can have Android 4.1+ devices reporting security risk back to Intune.
  - **Mark as noncompliant if no data is received**: If Intune doesn't receive data about a device on this platform from the MTD partner, consider the device noncompliant.
<br></br>
- **Connect iOS 8.0+ devices to [MTD partner name] for Work MTD**: When you enable this option, you can have iOS 8.0+ devices reporting security risk back to Intune.
  - **Mark as noncompliant if no data is received**: If Intune doesn't receive data about a device on this platform from the MTD partner, consider the device noncompliant.
<br></br>
- **Enable App Sync for iOS Devices**: Allows this Mobile Threat Defense partner to request metadata of iOS applications from Intune to use for threat analysis purposes.

- **Block unsupported OS versions**: Block if the device is running an operating system less than the minimum supported version.

- **Number of days until partner is unresponsive**: Number of days of inactivity before Intune considers the partner to be unresponsive because the connection is lost. Intune ignores compliance state for unresponsive MTD partners.

> [!IMPORTANT] 
> When possible, we recommend that you add and assign the MTD apps before creating the device compliance and the Conditional Access policy rules. This helps ensures that the MTD app is ready and available for end users to install before they can get access to email or other company resources.

> [!TIP]
> You can see the **Connection status** and the **Last synchronized** time between Intune and the MTD partner from the Mobile Threat Defense pane.
