---
# required metadata

title: Device management in Microsoft 365
description: Microsoft 365 Enterprise includes Microsoft Intune. See how Intune provides mobile device management and mobile application management for your organization. Read common scenarios, and use Intune to deploy Microsoft 365 in your environment. 
author: MandiOhlinger 
ms.author: mandia 
manager: dougeby 
ms.date: 07/22/2019
ms.topic: conceptual 
audience: microsoft-business
ms.service: microsoft-intune
ms.technology: 
ms.custom: microsoft-intune 
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
audience: ITPro

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune
ms.collection: M365-identity-device-management
---

# What is device management? 

A key task of any Administrator is to protect and secure an organization's resources and data. This task is *device management*. Users have many devices where they open and share personal files, visit websites, and install apps and games. These same users are also employees and students. They want to use their devices to access work and school resources, such as email and OneNote. Device management enables organizations to protect and secure their resources and data. 

Using a device management provider, organization can make sure that only authorized people and devices get access to proprietary information. Similarly, device users can feel at ease accessing work data from their phone, because they know their device meet their organization's security requirements. As an organization, you might ask - **What should we use to protect our resources?**

The answer is [Microsoft Intune](https://docs.microsoft.com/intune/introduction-intune). Intune offers mobile device management (MDM) and mobile application management (MAM). Some key tasks of any MDM or MAM solution are to:

- Support a diverse mobile environment and manage iOS, Android, Windows, and macOS devices securely.
- Make sure devices and apps are compliant with your organization's security requirements.
- Create policies that help keep your organization data safe on company-owned and personal devices.
- Use a single, unified mobile solution to enforce these policies, and help manage devices, apps, users, and groups.

Intune is included with Microsoft 365, and integrates with Azure Active Directory (Azure AD). Azure AD helps control who has access, and what they have access to.

## Hello Intune!
Many organizations, such as Microsoft, use Intune to secure proprietary data that users access from their company-owned and personal mobile devices. Intune includes device and app configuration policies, software update policies, and installation statuses (charts, tables, and reports) to help you secure and monitor data access.

It's common for people to have multiple devices that use different platforms. For example, an employee might use Surface Pro for work, and an Android mobile device in their personal life. And, it's common for a person to access organizational resources, such as Microsoft Outlook and SharePoint, from these multiple devices.

With Intune, you can manage multiple devices per person, and the different platforms that run on each device, including iOS, macOS, Android, and Windows. Intune separates policies and settings by device platform. So it's easy to manage and view devices of a specific platform.

**[Common scenarios](https://docs.microsoft.com/intune/common-scenarios)** is a great resource to see how Intune answers common questions when working with mobile devices. You'll find scenarios about:  
- Protecting email with on-premises Exchange
- Accessing Office 365 safely and securely
- Using personal devices to access organizational resources

## Integration with secure-and-protect services
A key task of any device management solution is to provide security and protection. Intune does a great job of integrating with other services to achieve this task. For example:

- **Microsoft 365** is a key component to simplifying common IT tasks. In the Microsoft 365 admin center, you create users, and manage groups. You also get access to other services, such as Intune, Azure AD, and more. 

  For example, create an iOS devices group in Microsoft 365. Then, use Intune to push policies to the iOS devices group that focus on iOS features, such as access to the app store, using AirDrop, backing up to iCloud, using Apple’s web filter, and more.

- **Windows Defender** includes many security features to help protect Windows 10 devices. For example, using Intune and Windows Defender together, you can: 

  - Enable [Windows Defender SmartScreen](https://docs.microsoft.com/intune/endpoint-protection-windows-10) to look for suspicious activity in files and apps on mobile devices. 
  - Use [Microsoft Defender Advanced Threat Protection (ATP)](https://docs.microsoft.com/intune/advanced-threat-protection) to help prevent security breaches on mobile devices. And, help limit the impact of a security breach by blocking a user from corporate resources.

- **Conditional Access** is a feature of Azure Active Directory, and integrates nicely with Intune. Using [Conditional Access](https://docs.microsoft.com/intune/conditional-access), make sure only compliant devices are allowed access to email, SharePoint, and other apps. 

## Choose the device management solution that's right for you

There are a couple of ways to approach device management. First, you can manage different aspects of devices using the features built in to Intune. This approach is called **Mobile device management (MDM)**. Users "enroll" their devices, and use certificates to communicate with Intune. As an IT administrator, you push apps on devices, restrict devices to a specific operating system, block personal devices, and more. If a device is ever lost or stolen, you can also remove all data from the device. 

In the second approach, you manage apps on devices. This approach is called **Mobile application management (MAM)**. Users can use their personal devices to access organizational resources. When opening an app, such as email or SharePoint, users are prompted for additional authentication. If a device is ever lost or stolen, you can remove all organization data from the device. 

You can also use a combination of [MDM and MAM](https://docs.microsoft.com/intune/byod-technology-decisions) together.

When you set up Intune, you also choose to work solely in the Azure portal to manage devices, or use Intune and Microsoft 365 together to manage devices. [Migrating mobile device management to Intune in the Azure portal](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal) is a Microsoft IT case study. In this case study, see how Microsoft IT chose a modern device management approach, and read the lessons learned.

## Simplify IT tasks using the Device Management admin center

The [Device Management admin center](https://devicemanagement.portal.azure.com/) is a one-stop shop to manage and complete tasks for your mobile devices. This workspace includes the services used for device management, including Intune and Azure Active Directory, and to also manage client apps. 

On the Device Management admin center, you can:

- [Enroll devices](https://docs.microsoft.com/intune/device-enrollment)
- [Set device compliance](https://docs.microsoft.com/intune/device-compliance-get-started)
- [Manage devices](https://docs.microsoft.com/intune/device-management)
- [Manage apps](https://docs.microsoft.com/intune/app-management)  
- [iOS eBooks](https://docs.microsoft.com/intune/vpp-ebooks-ios)  
- [Install Exchange on-premises connector](https://docs.microsoft.com/intune/exchange-connector-install)  
- [Manage roles](https://docs.microsoft.com/intune/role-based-access-control)  
- Manage software updates
  - [Manage Windows 10 updates](https://docs.microsoft.com/intune/windows-update-for-business-configure)  
  - [Manage iOS updates](https://docs.microsoft.com/intune/software-updates-ios)  
- [Azure active directory](https://docs.microsoft.com/azure/active-directory)  
- [Manage users](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [Manage groups and members](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [Troubleshoot](https://docs.microsoft.com/intune/help-desk-operators)

## Next step
When you're ready to get started with an MDM or MAM solution, walk through the different steps to set up Intune, enroll devices, and start creating policies. [Mobile device management for Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure) is also a great resource.
