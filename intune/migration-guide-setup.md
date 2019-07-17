---
# required metadata

title: Microsoft Intune basic setup
description: This article provides the necessary steps to set up Microsoft Intune.
keywords:
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
#ms.custom:
ms.collection: M365-identity-device-management
---

# Basic setup

After you assess your environment, it’s time to set up Microsoft Intune.

## External dependencies for an Intune deployment

### Identity

Intune requires Azure Active Directory (AAD) as the identity and user grouping provider. Learn more about:

- [Identity requirements](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)

- [Directory synchronization requirements](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)

- [Multi-factor authentication (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks)

- [Planning your user and device groups](users-add.md)

- [How to create user and device groups](groups-get-started.md)

If your organization is already using Office 365, Intune must use the same Azure Active Directory environment.

### PKI (optional)

If you're planning to use certificate-based authentication for VPN, Wi-Fi, or e-mail profiles with Intune, you’ll need to make sure that you have a supported [PKI infrastructure in place](certificates-configure.md), ready to create and deploy certificate profiles. Learn more about configuring certificates in Intune:

- [How to configure the certificate infrastructure for SCEP](/intune/certificates-scep-configure)

- [How to configure the certificate infrastructure for PFX](/intune/certficates-pfx-configure).

## Task list for an Intune setup

### Task 1: Intune subscription

Before you can migrate to Intune, you first need an Intune subscription.

- You can visit [this page](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0), which gives you instructions on how to:

  - Create a new Intune subscription linked to a new AAD tenant.

  - Link the Intune subscription by signing into an existing AAD tenant.

### Task 2: Assign Intune user licenses

- Learn [how to assign Intune user licenses](licenses-assign.md).

- If you have created a new Azure Active Directory tenant, learn [how to create new users or sync user from your on-premises Active Directory (AD).](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)

### Task 3: Set your MDM authority to Intune

Intune can be managed through the Azure portal or the Configuration Manager Current Branch console. Unless you need to integrate Intune with a Configuration Manager Current Branch deployment, we recommend that you manage Intune from the [Azure portal](https://portal.azure.com).

Set your MDM authority to **Intune** to enable the Intune Azure portal. Using a different MDM authority allows Intune to transfer MDM management to alternate Microsoft management consoles. These cases are uncommon.

> [!IMPORTANT]
> If you are transferring your mobile device management to Intune for the first time, you should set the MDM authority to Intune.

Learn [how to set the mobile management authority](mdm-authority-set.md).

## Next step

Configure [device and app management policies](migration-guide-configure-policies.md).
