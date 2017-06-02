g---
# required metadata

title: App based conditional access with Intune
description: Understand the concepts of how app-based conditional access works with Intune.
keywords:
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/31/2017
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: b399fba0-5dd4-4777-bc9b-856af038ec41

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisgre
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# App-based conditional access with Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

[Intune app protection policies](app-protection-policy.md) help protect your company data on devices that are enrolled for management in Intune. You can also use app protection policies on employee owned devices that are not enrolled for management in Intune.  In this case, even though you don't manage the device, you still need to make sure that your company data and resources is protected. Using App-based conditional access with MAM, you can create a policy that allows only mobile apps that support Intune app protection policies to access O365 services like Exchange Online.

For example, by only allowing the **Microsoft Outlook app** to access Exchange Online, you can **block the built-in mail apps on iOS and Android**, which don't have the data protection being applied by Intune app protection policies to get email from **Exchange Online**. Additionally, you can block apps that don’t have Intune app protection policies applied from accessing **SharePoint Online**.

## Prerequisites
Before you create an App-based conditional access policy, you must have:

- **Enterprise Mobility + Security or an Azure Active Directory premium subscription**, and the users must be licensed for EMS or Azure AD.
	- For more details, see the [Enterprise Mobility pricing page](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) or the [Azure Active Directory pricing page](https://azure.microsoft.com/pricing/details/active-directory/).

## Supported apps

- **Exchange Online**:
	- **Microsoft Outlook** for Android and iOS.
<br></br>
- **SharePoint Online**
	- Microsoft Word for iOS and Android
	- Microsoft Excel for iOS and Android
	- Microsoft PowerPoint for iOS and Android
	- Microsoft OneDrive for Business for iOS and Android
	- Microsoft OneNote for iOS

> [!IMPORTANT]
> For Android devices, the initial device registration must be done by logging into either the OneDrive app, or the Outlook app. The OneNote app for Android does not yet support MAM without enrollment.

## How app-based conditional access works?

In this example, the admin has app protection policies applied to the Outlook app followed by a conditional access rule that adds the Outlook app to an approved list of apps that can be used when accessing corporate e-mail.

> [!NOTE] 
> The flowchart structure below can be used for other managed apps.

![App-based ca with Intune flow-chart](./media/ca-intune-common-ways-3.png)

1.  The user tries to authenticate to Azure AD from the Outlook app.

2.  The user gets redirected to the app store to install a broker app when trying to authenticate for the first time. The broker app can be either the Microsoft Authenticator for iOS, or the Microsoft Company portal for Android devices.

	> [!NOTE]
	> In this scenario, if users try to use a native e-mail app, they’ll be redirected to the app store to then install the Outlook app.

3.  The broker app gets installed on the device.

4.  The broker app starts the Azure AD registration process which creates a device record in Azure AD. This is not the same as the mobile device management (MDM) enrollment process, but this record is necessary so the conditional access policies can be enforced on the device.

5.  The broker app verifies the identity of the app. There’s a security layer so the broker app can validate if the app is authorized to be used by the user.

6.  The broker app requests the App Client ID to check if it’s in the policy approved list.

7.  Azure AD allows the user to authenticate and use the app. If the app is not in the policy approved list, Azure AD denies access to the app.

8.  Outlook app communicates with Outlook Cloud Service to initiate communication with Exchange Online.

9.  Outlook Cloud Service communicates with Azure AD to retrieve Exchange Online service access token for the user.

10.  Outlook app communicates with Exchange Online to retrieve user's corporate e-mail.

11.  Corporate e-mail is delivered to the user's mailbox.

## Next steps
[Create an Exchange Online Policy for MAM apps](app-based-conditional-access-intune-exchange-online-create.md)

[Create a SharePoint Online Policy for MAM apps](app-based-conditional-access-intune-sharepoint-online-create.md)

[Block apps that do not have modern authentication](app-modern-authentication-block.md)
