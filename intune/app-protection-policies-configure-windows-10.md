---
# required metadata

title: Get ready to configure app protection policies for Windows 10 
titlesuffix: "Azure portal"
description: "Setup mobile application management (MAM) provider in Azure AD"
keywords:
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: joglocke
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Get ready to configure app protection policies for Windows 10

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Before creating a Windows 10 app protection policy using, you need to enable mobile application management (MAM) for Windows 10 by setting up the MAM provider in Azure AD. This configuration allows you to define the enrollment state when creating a new Windows Information Protection (WIP) policy with Intune.

> [!NOTE]
> The enrollment state can be either MAM or mobile device management (MDM).

## To configure the MAM provider

1.  Go to the [Azure portal](https://portal.azure.com/) and sign in with your Intune credentials.

2.  From the left menu, choose **Azure Active Directory**.

    ![MAM provider configuration](./media/mam-provider-sc-1.png)

3.  **Azure AD** blade opens, choose **Mobility (MDM and MAM)**, then click **Microsoft Intune**.

    ![Mobility MDM and MAM](NEW SCREENSHOT NEEDED)

4.  The configure blade opens, choose **Restore default MAM URLs** first, then configure the following:

    a.  MAM user scope: You can use MAM to protect corporate data on specific group of users that use Windows 10 devices or all users.

    b.  MAM terms of use URL: The URL of the terms of use endpoint of the MAM service. This is used to display the term of MAM service to end-users.

    c.  MAM discovery URL: This the URL devices seek when they need to apply app protection policies.

    d.  MAM compliance URL:

5.  Once you configure these settings, choose **Save**.

> [!NOTE]
> Devices with a MAM enrollment state are required to be Azure AD joined.

## Next steps

[Create a WIP app protection policy](windows-information-protection-policy-create.md)
