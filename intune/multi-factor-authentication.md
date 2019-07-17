---
# required metadata

title: Require multi-factor authentication for Intune device enrollment
titleSuffix: Microsoft Intune
description: How to require multi-factor authentication in Azure AD for Intune device enrollment.
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9

# optional metadata

ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: damionw
#ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Require multi-factor authentication for Intune device enrollments

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune can use Azure Active Directory (AD) multi-factor authentication (MFA) for device enrollment to help you secure your corporate resources.

MFA works by requiring any two or more of the following verification methods:

- Something you know (typically a password or PIN).
- Something you have (a trusted device that is not easily duplicated, like a phone).
- Something you are (biometrics, like a fingerprint).

MFA is supported for iOS, Android, Windows 8.1 or later, Windows Phone 8.1, or Windows 10 Mobile or later devices.

When you enable MFA, end users must supply two forms of credentials to enroll a device.

## Configure Intune to require multi-factor authentication at device enrollment

To require MFA when a device is enrolled, follow these steps:

>[!Important]
>You must have an Azure Active Directory Premium P1 or above assigned to your users to implement this policy.

>[!Important]
>Do not configure **Device based access rules** for Microsoft Intune enrollment.

1. Sign in to your [Microsoft Azure portal](https://portal.azure.com) with your credentials.
2. In the portal, go to **Intune** and choose **Conditional Access**. The Conditional Access node accessed from *Intune* is the same node as accessed from *Azure AD*.
4. Choose **New policy**.
5. In **New** policy, type a descriptive name for the policy.
6. In the **Assignments** section, choose **Users and groups**. 
7. In **Users and groups**, choose **Select users or groups**, and check **Users and groups**. Then select the users and /or groups that will receive this policy, then choose **Done**.
8. In the **Assignments** section, choose **Cloud apps**.
9. On the **Include** tab of **Cloud apps**, choose **Select apps**, then choose **Select** > **Microsoft Intune Enrollment**, and then choose **Done**.
10. In the **Assignments** section, for **Conditions** you do not need to configure any settings for MFA.
11. In the **Access controls** section, choose **Grant**.
12. In **Grant**, choose **Grant access**, and then select **Require multi-factor authentication**. Do not select **Require device to be marked as compliant** because a device cannot be evaluated for compliance until it is enrolled. Then choose **Select**.
13. In **New policy**, choose **Enable policy** > **On**, and then choose **Create**.

## Next steps

When end users enroll their device, they now must authenticate with a second form of identification, like a PIN, a phone, or biometrics.
