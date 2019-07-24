---
# required metadata

title: Set up app based Conditional Access policy with Intune
titleSuffix: Microsoft Intune
description: Learn how to create an app-based Conditional Access policy with Intune.
keywords:
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Set up app-based Conditional Access policies with Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Set up app-based Conditional Access policies for apps that are part of the list of approved apps. The list of approved apps consists of apps that were tested by Microsoft.

> [!IMPORTANT]
> This article walks through the steps to add an app-based Conditional Access policy. You can use the same steps when add apps like SharePoint Online, Microsoft Teams, and Microsoft Exchange Online from the list of approved apps.

## Create app-based Conditional Access policies
Conditional Access is an Azure Active Directory (Azure AD) technology. The Conditional Access node accessed from *Intune* is the same node as accessed from *Azure AD*. This means you don't need to switch between Intune and Azure AD to configure policies.

> [!IMPORTANT]
> You need to have an Azure AD Premium license to create Conditional Access policies from the Intune portal.

### To create an app-based Conditional Access policy

> [!IMPORTANT]
> You need to have [Intune app protection policies](app-protection-policies.md) applied to your apps before using app-based Conditional Access policies.

1. In the **Intune Dashboard**, select **Conditional Access**.

2. In the **Policies** pane, choose **New policy** to create your new app-based Conditional Access policy.

4. Once you enter a policy name and configure the settings available in the **Assignments** section, then choose **Grant** under the **Access controls** section.

5. Choose **Require approved client app**, choose **Select**, then choose **Create** to save the new policy.

## Next steps
[Block apps that don't have modern authentication](app-modern-authentication-block.md)

## See also

[Protect app data with app protection policies](app-protection-policies.md)
[Conditional Access in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
