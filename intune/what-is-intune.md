---
# required metadata

title: What is Microsoft Intune
description: Learn how Microsoft Intune is the mobile device management (MDM) and mobile app management (MAM) component of the Enterprise Mobility + Security solution and how it helps you protect company data.
keywords: what is Intune
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 06/20/2019
ms.topic: overview
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: pmay
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: get-started
ms.collection: M365-identity-device-management
---

# What is Microsoft Intune?

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Microsoft Intune is a cloud-based service in the enterprise mobility management (EMM) space that helps enable your workforce to be productive while keeping your corporate data protected. Similar to other Azure services, Microsoft Intune is available in the Azure portal. With Intune, you can:
* Manage the mobile devices and PCs your workforce uses to access company data.
* Manage the mobile apps your workforce uses.
* Protect your company information by helping to control the way your workforce accesses and shares it.
* Ensure devices and apps are compliant with company security requirements.

## Common business problems that Intune helps solve

* [Protect your on-premises email and data so that it can be accessed by mobile devices](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Protect your Office 365 mail and data so that it can be safely accessed by mobile devices](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Issue corporate-owned phones to your workforce](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
* [Offer a bring-your-own-device (BYOD) or personal device program to all employees](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
* [Enable your employees to securely access Office 365 from an unmanaged public kiosk](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [Issue limited-use shared tablets to your task workers](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)

## How does Intune work?
Intune is the component of Microsoft's Enterprise Mobility + Security (EMS) suite that manages mobile devices and apps. It integrates closely with other EMS components like Azure Active Directory (Azure AD) for identity and access control and Azure Information Protection for data protection. When you use it with Office 365, you can enable your workforce to be productive on all their devices, while keeping your organization's information protected.

![Image of Intune architecture](./media/intunearch_sm.png)

View a [larger version](./media/intunearchitecture.svg) of the Intune architecture diagram.

How you use the device and app management features of Intune and EMS data protection depends on the [business problem you’re trying to solve](#common-business-problems-that-intune-helps-solve). For example:
* You’ll make strong use of device management if you're creating a pool of single-use devices to be shared by shift workers in a retail store.
* You’ll lean on app management and data protection if you allow your workforce to use their personal devices to access corporate data (BYOD).  
* If you are issuing corporate phones to information workers, you’ll rely on all of the technologies.

## Intune device management explained
Intune device management works by using the protocols or APIs that are available in the mobile operating systems. It includes tasks like:
* Enrolling devices into management so your IT department has an inventory of devices that are accessing corporate services
* Configuring devices to ensure they meet company security and health standards
* Providing certificates and Wi-Fi/VPN profiles to access corporate services
* Reporting on and measuring device compliance to corporate standards
* Removing corporate data from managed devices  

Sometimes, people think **access control to corporate data** is a device management feature. We don’t think of it that way because it isn’t something that the mobile operating system provides. Rather, it’s something the identity provider delivers. In our case, the identity provider is Azure Active Directory (Azure AD), Microsoft’s identity and access management system.  

Intune integrates with Azure AD to enable a broad set of access control scenarios. For example, you can require a mobile device to be compliant with corporate standards that you define in Intune before the device can access a corporate service like Exchange. Likewise, you can lock down the corporate service to a specific set of mobile apps. For example, you can lock down Exchange Online to only be accessed by Outlook or Outlook Mobile.

## Intune app management explained
When we talk about app management, we are talking about:
* Assigning mobile apps to employees
* Configuring apps with standard settings that are used when the app runs
* Controlling how corporate data is used and shared in mobile apps
* Removing corporate data from mobile apps   
* Updating apps
* Reporting on mobile app inventory
* Tracking mobile app usage

We have seen the term mobile app management (MAM) used to mean any one of those things individually or to mean specific combinations. In particular, it’s common for folks to combine the concept of app configuration with the concept of securing corporate data within mobile apps. That’s because some mobile apps expose settings that allow their data security features to be configured.

When we talk about app configuration and Intune, we are referring specifically to technologies like [managed app configuration on iOS](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html).

When you use Intune with the other services in EMS, you can provide your organization mobile app security over and above what is provided by the mobile operating system and the mobile apps themselves through app configuration. An app that is managed with EMS has access to a broader set of mobile app and data protection features that includes:

* [Single sign-on](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)  
* [Multi-factor authentication](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication)
* [App Conditional Access - allow access if the mobile app contains corporate data](app-based-conditional-access-intune.md)
* [Isolating corporate data from personal data inside the same app](app-protection-policy.md)
* [App protection policy (PIN, encryption, save-as, clipboard, etc.)](app-protection-policies.md)
* [Corporate data wipe from a mobile app](apps-selective-wipe.md)
* [Rights management support](https://docs.microsoft.com/information-protection/understand-explore/what-is-azure-rms)

![Image that shows the levels of app management data security](./media/managing-mobile-apps.png)

### Intune app security
Providing app security is a part of app management, and in Intune, when we talk about mobile app security, we mean:
* Keeping personal information isolated from corporate IT awareness
* Restricting the actions users can take with corporate information such as copy, cut/paste, save, and view
* Removing corporate data from mobile apps, also known as selective wipe or corporate wipe

One way Intune provides mobile app security is through its **app protection policy** feature. App protection policy uses Azure AD identity to isolate corporate data from personal data. Data that is accessed using corporate credentials will be given additional corporate protections.

For example, when a user logs on to their device with their corporate credentials, their corporate identity allows them to access data that is denied to their personal identity. As that corporate data is used, app protection policies control how it is saved and shared. Those same protections are not applied to data that is accessed when the user logs on to their device with their personal identity. In this way, IT has control of corporate data while the end user maintains control and privacy over their personal data.

## EMM with and without device enrollment
Most enterprise mobility management solutions support basic mobile device and mobile app technologies. These are usually tied to the device being enrolled in your organization’s mobile device management (MDM) solution. Intune supports these scenarios and additionally supports many “without enrollment” scenarios.  

Organizations differ to the extent they will adopt “without enrollment” scenarios. Some organizations standardize on it. Some allow it for companion devices such as a personal tablet. Others don’t support it at all. Even in this last case, where an organization requires all employee devices to be enrolled in MDM, they typically support "without enrollment" scenarios for contractors, vendors, and other devices that have a specific exemption.

You can even use Intune’s “without-enrollment” technology on enrolled devices. For example, a device enrolled in MDM may have "open-in" protections provided by the mobile operating system. "Open-in" protection is a feature of Apple's iOS that restricts you from opening a document from one app, like Outlook, into another app, like Word, unless both apps are managed by the same MDM provider. Also, IT may apply the app protection policy to EMS-managed mobile apps to control save-as, or to provide multi-factor authentication.

Whatever your organization’s position on enrolled and unenrolled mobile devices and apps, Intune, as a part of EMS, has tools that will help increase your workforce productivity while protecting your corporate data.

## Microsoft Intune in the Azure portal

The [Azure portal](https://portal.azure.com) is where you can find the Microsoft Intune service.

Highlights of the Microsoft Intune experience in the Azure portal include:

- An integrated console for all your Enterprise Mobility + Security (EMS) components
- An HTML-based console built on web standards
- Microsoft Graph API support to automate many actions
- Azure Active Directory (AD) groups to provide compatibility across all your Azure applications
- Support for most modern web browsers

For a quick guide to customize your portal experience, see [Getting started with Intune in the Azure portal](get-started-azure.md).

> [!NOTE]
> If you've used a previous version of Microsoft Intune, you may find the following information helpful:
> * [Where did my features go in Azure?](ui-changes.md) is a reference to show you the specific workflows and UIs that have changed with the move to Azure.
> * [Intune classic groups in the Azure portal](groups-get-started.md) explains the implications of the shift to Azure Active Directory security groups for group management.

### Before you start

To use Intune in the Azure portal, you must have an Intune admin and tenant account. [Sign up for an account](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) if you don't already have one.

### Supported web browsers for the Azure portal

The Azure portal runs on most modern PCs, Macs, and tablets. Mobile phones are not supported.
Currently, the following browsers are supported:

- Microsoft Edge (latest version)
- Microsoft Internet Explorer 11
- Safari (latest version, Mac only)
- Chrome (latest version)
- Firefox (latest version)

Check the [Azure portal](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices) for the latest information about supported browsers.

## Next steps
* Read about some of the [common ways to use Intune](common-scenarios.md).
* Get familiar with the product [with a 30-day trial of Intune](free-trial-sign-up.md).
* Dive into the [technical requirements and capabilities](supported-devices-browsers.md) of Intune.
