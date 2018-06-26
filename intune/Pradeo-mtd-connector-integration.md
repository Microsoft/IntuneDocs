---
# required metadata

title: Integrate Pradeo MTD with Microsoft Intune
titleSuffix:
description: How to set up the Pradeo Mobile Threat Defense (MTD) solution with Microsoft Intune to control mobile device access to your corporate resources.
keywords:
author: hacha
ms.author: hacha
manager: benyim
ms.date: 12/29/2017
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: hacha
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Integrate Pradeo with Intune

Complete the following steps to integrate the Pradeo Mobile Threat Defense solution with Intune.

## Before you begin

> [!NOTE]
> The following steps are to be completed in the [Pradeo MTD console](https://apps-security.com/).

Before starting the process of integrating Pradeo with Intune, make sure you have the following subscription and credentials:

-   Microsoft Intune subscription

-   Azure Active Directory admin credentials to grant the following permissions:

    -   Sign in and read user profile

    -   Access the directory as the signed-in user

    -   Read directory data

    -   Send device information to Intune

-   Admin credentials to access Pradeo MTD console.

### Pradeo app authorization

The Pradeo app authorization process follows:

-   Allow the Pradeo service to communicate information related to device health state back to Intune.

-   Pradeo syncs with Azure Active Directory (AD) Enrollment Group membership to populate its device’s database.

-   Allow Pradeo admin console to use Azure AD Single Sign On (SSO).

-   Allow the Pradeo app to sign in using Azure AD SSO.

## To set up Pradeo integration

1.  Go to [Pradeo MTD console](https://apps-security.com/) and sign in with your credentials.

2.  Choose **Mobile Threat Defense** from the menu.

3.  Choose the **Administration** tab, then select Intune

4.  Choose **Add MDM,** then select **Microsoft Intune** from the **MDM provider** list.

5.  Follow the wizard steps provided to Add Pradeo Connector, Add Pradeo Device Health and Connect with Microsoft.

## Next steps

-   [Set up Pradeo apps](mtd-apps-ios-app-configuration-policy-add-assign.md)
