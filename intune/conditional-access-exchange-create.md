---
# required metadata

title: Create Exchange Conditional Access policy
titleSuffix: Microsoft Intune
description: Configure Conditional Access for Exchange on-premises and legacy Exchange Online Dedicated in Intune.
keywords:
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer:
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Create a Conditional Access policy for Exchange on-premises and legacy Exchange Online Dedicated

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

This article shows you how to configure Conditional Access for Exchange on-premises based on device compliance.

If you have an Exchange Online Dedicated environment and need to find out whether it is in the new or the legacy configuration, contact your account manager. To control email access to Exchange on-premises or to your legacy Exchange Online Dedicated environment, configure Conditional Access to Exchange on-premises in Intune.

## Before you begin

Before you can configure Conditional Access, verify the following configurations exist:

- Your Exchange version is **Exchange 2010 SP1 or later**. Exchange server Client Access Server (CAS) array is supported.

- You have installed and use the [Exchange Active Sync on-premises Exchange connector](exchange-connector-install.md), which connects Intune to on-premises Exchange.

    >[!IMPORTANT]  
    >Intune supports multiple on-premises Exchange connectors per subscription.  However, each on-premises Exchange connector is specific to a single Intune tenant and cannot be used with any other tenant.  If you have more than one on-premises Exchange organization, you can set up a separate connector for each Exchange organization.

- The connector for an on-premises Exchange organization can install on any machine as long as that machine can communicate with the Exchange server.

- The connector supports **Exchange CAS environment**. Intune supports installing the connector on the Exchange CAS server directly, but we recommend you install it on a separate computer due to the additional load the connector puts on the server. When configuring the connector, you must set it up to communicate to one of the Exchange CAS servers.

- **Exchange ActiveSync** must be configured with certificate-based authentication, or user credential entry.

- When Conditional Access policies are configured and targeted to a user, before a user can connect to their email, the **device** they use must be:
  - Either **enrolled** with Intune or is a domain joined PC.
  - **Registered in Azure Active Directory**. Additionally, the client Exchange ActiveSync ID must be registered with Azure Active Directory.

- Azure AD Device Registration Service (DRS) is activated automatically for Intune and Office 365 customers. Customers who have already deployed the ADFS Device Registration Service don't see registered devices in their on-premises Active Directory. **This does not apply to Windows PCs and Windows Phone devices**.

- **Compliant** with device compliance policies deployed to that device.

- If the device doesn't meet Conditional Access settings, the user is presented with one of the following messages when they sign in:
  - If the device isn't enrolled with Intune, or isn't registered in Azure Active Directory, a message is displayed with instructions about how to install the Company Portal app, enroll the device, and activate email. This process also associates the device's Exchange ActiveSync ID with the device record in Azure Active Directory.
  - If the device is not compliant, a message is displayed that directs the user to the Intune Company Portal website, or the Company Portal app where they can find information about the problem and how to remediate it.

### Support for mobile devices

- Windows Phone 8.1 and later
- Native email app on iOS.
- EAS mail clients such as Gmail on Android 4 or later.
- EAS mail clients **Android work profile devices:** Only **Gmail** and **Nine Work for Android Enterprise** in the **work profile** are supported on Android work profile devices. For Conditional Access to work with Android work profiles, you must deploy an email profile for the Gmail or Nine Work for Android Enterprise app, and also deploy those apps as a required installation.

> [!NOTE]
> Microsoft Outlook for Android and iOS is not supported via the Exchange on-premises connector. If you want to leverage Azure Active Directory Conditional Access policies and Intune App Protection Policies with Outlook for iOS and Android for your on-premises mailboxes, please see [Using hybrid Modern Authentication with Outlook for iOS and Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth). 

### Support for PCs

The native **Mail** application on Windows 8.1 and later (when enrolled into MDM with Intune)

## Configure Exchange on-premises access

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)

2. Go to **Exchange access**, and then select **Exchange On-premises access**. 

3. On the **Exchange on-premises access** pane, choose **Yes** to *Enable Exchange on-premises access control*.

4. Choose **On-premises access**. The **On-premises access** pane shows the status of the Exchange on-premises Connector.

5. Under **Manage**, choose **Exchange on-premises access**.

6. On the **Exchange on-premises access** pane, choose **Yes** to enable Exchange on-premises access control.

   > [!NOTE]
   > The option to enable access is disabled until after you [install and configure at least one Intune on-premises Exchange connector](exchange-connector-install.md) for Exchange on-premises.  

7. Under **Assignment**, choose **Groups Included**.  Use the security user group that should have Conditional Access applied to it. This action would require the users to enroll their devices in Intune and be compliant with the compliance profiles.

8. If you want to exclude certain groups of users, you can do so by choosing **Groups Excluded** and selecting a user group that you want to be exempt from requiring device enrollment and compliance.

9. Under **Settings**, choose **User notifications** to modify the default email message. This message is sent to users if their device isn't compliant and they want to access Exchange on-premises. The message template uses Markup language.  You can also see the preview of how the message looks as you type.
   > [!TIP]
   > To learn more about Markup language see this Wikipedia [article](https://en.wikipedia.org/wiki/Markup_language).

10. On the **Advanced Exchange Active Sync access settings** pane, set the global default rule for access from devices that are not managed by Intune, and for platform-level rules as described in the next two steps. To get to the advanced settings pane, on the *Exchange access - Exchange on-premises access* view, select *Exchange ActiveSync - on-premises connector*.

11. For a device that is not affected by Conditional Access or other rules, you can choose to allow it to access Exchange, or block it.

    - When you set this to allow access, all devices are able to access Exchange on-premises immediately.  Devices that belong to the users in the **Groups Included**, are blocked if they are subsequently evaluated as not compliant with the compliant policies or not enrolled in Intune.
    - When you set this to block access, all devices are immediately blocked from accessing Exchange on-premises initially.  Devices that belong to users in the **Groups Included** get access once the device is enrolled in Intune and is evaluated as compliant. On Android devices that do not run Samsung Knox standard is always blocked as they do not support this setting.

12. Under **Device platform exceptions**, choose **Add** to specify the platforms. If the **unmanaged device access** setting is set to **blocked**, devices that are enrolled and compliant are allowed even if there is a platform exception to block. Choose **Ok** to save the settings.

13. On the **On-premises** pane, click **Save** to save the Exchange Conditional Access policy.

Next step is to create a compliance policy and assign it to the users for Intune to evaluate their mobile devices, See [Get started with device compliance](device-compliance-get-started.md)

## See also

[Troubleshooting Intune On-Premises Exchange Connector in Microsoft Intune](https://support.microsoft.com/help/4471887)
