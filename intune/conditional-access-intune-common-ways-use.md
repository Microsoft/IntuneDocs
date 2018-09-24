---
# required metadata

title: Conditional access with Microsoft Intune
titlesuffix:
description: Learn how Intune conditional access is commonly used for device-based and app-based conditional access.
keywords:
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure; get-started

---

# What are common ways to use conditional access with Intune?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

There are two types of conditional access with Intune: device-based conditional access and app-based conditional access. You need to configure the related compliance policies to drive conditional access compliance at your organization. Conditional access is commonly used to do things like allow or block access to Exchange on-premises, control access to the network, or integrate with a Mobile Threat Defense solution.

The below information helps you understand how to use the Intune mobile *device* compliance capabilities and the Intune mobile *application* management (MAM) capabilities. 

> [!NOTE]
> Conditional access is an Azure Active Directory capability that is included with an Azure Active Directory Premium license. Intune enhances this capability by adding mobile device compliance and mobile app management to the solution.

## Device-based conditional access

Intune and Azure Active Directory work together to make sure only managed and compliant devices are allowed access to email, Office 365 services, Software as a service (SaaS) apps, and [on-premises apps](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started). Additionally, you can set a policy in Azure Active Directory to only enable computers that are domain-joined, or mobile devices that are enrolled in Intune to access Office 365 services.

Intune provides device compliance policy capabilities that evaluate the compliance status of the devices. The compliance status is reported to Azure Active Directory that uses it to enforce the conditional access policy created in Azure Active Directory when the user tries to access company resources.

Device-based conditional access policies for Exchange online and other Office 365 products are configured through the [Azure portal](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

-   Learn more about [conditional access in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

-   Learn more about [Intune device compliance](device-compliance.md).

-   Learn more about [protecting e-mail, Office 365, and other services using conditional access with Intune](https://docs.microsoft.com/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).

[!NOTE]
On Android devices, when you enable Device Based Access for Sharepoint Online, users must enable the **Enable Browser Access** option on the enrolled device as follows:
1. Launch the **Company Portal app**.
2. Go to the **Settings** page from the triple dots (...) or the hardware menu button.
3. Press the **Enable Browser Access** button.
4. In the Chrome browser, sign out of Office 365 and restart Chrome.

### Conditional access for Exchange on-premises

Conditional access can be used to allow or block access to **Exchange on-premises** based on the device compliance policies and enrollment state. When conditional access is used in combination with a device compliance policy, only compliant devices are allowed access to Exchange on-premises.

You can configure advanced settings in conditional access for more granular control such as:

-   Allow or block certain platforms.

-   Immediately block devices that are not managed by Intune.

Any device used to access Exchange on-premises is checked for compliance when device compliance and conditional access policies are applied.

When devices do not meet the conditions set, the end user is guided through the process of enrolling the device to fix the issue that is making the device noncompliant.

#### How conditional access for Exchange on-premises works

The Intune Exchange connector pulls in all the Exchange Active Sync (EAS) records that exist at the Exchange server so Intune can take these EAS records and map them to Intune device records. These records are devices enrolled and recognized by Intune. This process allows or blocks e-mail access.

If the EAS record is brand new, and Intune is not aware of it, Intune issues a command-let that blocks access to e-mail. Here are more details on how this process works:

![Exchange on-premises with CA flow-chart](./media/ca-intune-common-ways-1.png)

1.  User tries to access corporate email, which is hosted on Exchange on-premises 2010 SP1 or later.

2.  If the device is not managed by Intune, it will be blocked access to email. Intune sends block notification to the EAS client.

3.  EAS receives block notification, moves the device to quarantine, and sends the quarantine email with remediation steps that contain links so the users can enroll their devices.

4.  The Workplace join process happens, which is the first step to have the device managed by Intune.

5.  The device gets enrolled into Intune.

6.  Intune maps the EAS record to a device record, and saves the device compliance state.

7.  The EAS client ID gets registered by the Azure AD Device Registration process, which creates a relationship between the Intune device record, and the EAS client ID.

8.  The Azure AD Device Registration saves the device state information.

9.  If the user meets the conditional access policies, Intune issues a command-let through the Intune Exchange connector that allows the mailbox to sync.

10. Exchange server sends the notification to EAS client so the user can access e-mail.

#### What’s the Intune role?

Intune evaluates and manages the device state.

#### What’s the Exchange server role?

Exchange server provides API and infrastructure to move devices to its quarantine.

> [!IMPORTANT]
> Keep in mind that the user who’s using the device must have a compliance profile assigned to them so the device to be evaluated for compliance. If no compliance policy is deployed to the user, the device is treated as compliant and no access restrictions are applied.

### Conditional access based on network access control

Intune integrated with partners like Cisco ISE, Aruba Clear Pass, and Citrix NetScaler to provide access controls based on the Intune enrollment and the device compliance state.

Users can be allowed or denied access when trying to access corporate Wi-Fi or VPN resources based on whether the device is managed and compliant with Intune device compliance policies.

-   Learn more about the [NAC integration with Intune](network-access-control-integrate.md).

### Conditional access based on device risk

Intune partners with Mobile Threat Defense vendors that provide a security solution to detect malware, Trojans, and other threats on mobile devices.

#### How the Intune and Mobile Threat Defense integration works

When mobile devices have the Mobile Threat Defense agent installed, the agent can send compliance state messages back to Intune reporting if a threat has been found in the mobile device itself.

The Intune and mobile threat defense integration plays a factor at the conditional access decisions based on device risk.

-   Learn more about [Intune mobile threat defense](https://docs.microsoft.com/intune-classic/deploy-use/mobile-threat-defense).

### Conditional access for Windows PCs

Conditional access for PCs provides capabilities similar to those available for mobile devices. Let’s talk about the ways you can use conditional access when managing PCs with Intune.

#### Corporate-owned

-   **On premises AD domain joined:** This option is commonly used by organizations who are reasonably comfortable with how they’re already managing their PCs through AD group policies and/or System Center Configuration Manager.

-   **Azure AD domain joined and Intune management:** This scenario is typically geared to Choose Your Own Device (CYOD), and roaming laptop scenarios where these devices are rarely connected to the corporate network. The device joins to the Azure AD and gets enrolled to Intune, which removes any dependency on on-premises AD, and domain controllers. This can be used as a conditional access criteria when accessing corporate resources.

-   **AD domain joined and System Center Configuration Manager:** As of current branch, System Center Configuration Manager provides conditional access capabilities that can evaluate specific compliance criteria, in addition to be a domain-joined PC:

    -   Is the PC encrypted?

    -   Is malware installed? Is it up-to-date?

    -   Is the device jailbroken or rooted?

#### Bring your own device (BYOD)

-   **Workplace join and Intune management:** Here the user can join their personal devices to access corporate resources and services. You can use Workplace join and enroll devices into Intune to receive device-level policies, which is also another option to evaluate conditional access criteria.

## App-based conditional access

Intune and Azure Active Directory work together to make sure only managed apps can access corporate e-mail or other Office 365 services.

-   Learn more about [app-based conditional access with Intune](app-based-conditional-access-intune.md).

## Next steps

[How to configure conditional access in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[How to install on-premises Exchange connector with Intune](https://docs.microsoft.com/intune/exchange-connector-install).

[How to create a conditional access policy for Exchange on-premises](conditional-access-exchange-create.md)
