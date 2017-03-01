---
# required metadata

title: What's new | Microsoft Docs
description: Find out what’s new in this month’s and past releases of Microsoft Intune
keywords:
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/27/2017
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: priyar
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-classic

---
# What's new in Microsoft Intune - February 2017
Learn what’s new in this release of Microsoft Intune. You can also find out about upcoming changes that you should be planning for, as well as information about past releases.

> [!Note]
> All of these features will eventually be supported for hybrid customers' deployments (Configuration Manager with Intune). For more information about new hybrid features, check out our [hybrid What’s New page](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## New Capabilities

### Modernizing the Company Portal website <!--753980-->
The Company Portal website will support apps that are targeted to users who do not have managed devices. The website will align with other Microsoft products and services by using a new contrasting color scheme, dynamic illustrations, and a "hamburger menu," ![Small image of the hamburger menu that is now added at the top left corner of the Company Portal website](./media/CP_hamburger_menu.png) which will contain helpdesk contact details and information on existing managed devices. The landing page will be rearranged to emphasize apps that are available to users, with carousels for Featured and Recently Updated apps. You can find before and after images available on the [UI updates page](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### New guided experience for Windows 10 Company Portal <!--713927-->
Beginning in March, the Company Portal for Windows 10 will include a guided Intune walkthrough experience for devices that have not been identified or enrolled. The new experience provides step-by-step instructions, customized for the user’s build of Windows 10, that guide users through performing AAD registration (required for identification for Conditional Access features) and MDM enrollment (required for device management features). The guided experience will be accessible from the Company Portal home page and is optional; users can continue to use the app if they do not complete registration and enrollment, but may experience limited functionality.

## Notices

### Group migration will not require any updates to groups or policies for iOS devices <!--898837-->
For every Intune device group pre-assigned by a Corporate Device Enrollment profile, a corresponding dynamic device group will be created in AAD based on the Corporate Device Enrollment profile’s name, during the migration to Azure Active Directory device groups. This will ensure the as devices enroll, they will be automatically grouped and receive the same policies and apps as the original Intune group.

Once a tenant enters the migration process for grouping and targeting, Intune will automatically create a dynamic AAD group to correspond to an Intune group targeted by a Corporate Device Enrollment profile. If the Intune Admin deletes the targeted Intune group, the corresponding dynamic AAD group will not be deleted. The group's members and the dynamic query will be cleared, but the group itself will remain until the IT Admin removes it via the AAD portal.

Similarly, if the IT Admin changes which Intune group is targeted by a Corporate Device Enrollment profile, Intune will create new dynamic group reflecting the new profile assignment, but will not remove the dynamic group created for the old assignment.

### Defaulting to managing Windows desktop devices through Windows settings <!--663050-->
The default behavior for enrolling Windows 10 desktops is changing. New enrollments will follow the typical MDM agent enrollment flow rather than through the PC agent. The Company Portal website will provide Windows 10 desktop users with enrollment instructions that guide them through the process of adding Windows 10 desktop computers as mobile devices. This will not impact currently enrolled PCs, and your organization can still manage Windows 10 desktops using the PC agent [if you prefer](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

### Improving mobile app management support for selective wipe <!--581242-->
End users will be given additional guidance on how to regain access to work or school data if that data is automatically removed due to the "Offline interval before app data is wiped" policy.<!--, or the removal of the Intune Company Portal on Android.-->

### Company Portal for iOS links open inside the app <!--665954-->
Links inside of the Company Portal app for iOS, including those to documentation and apps, will open directly in the Company Portal app using an in-app view of Safari. This update will ship separately from the service update in January.

### New MDM server address for Windows devices <!--893007-->
Windows and Windows Phone users attempting to enroll a device will fail if they enter __manage.microsoft.com__ as the MDM server address (if prompted). The MDM server address is changing from __manage.microsoft.com__ to __enrollment.manage.microsoft.com__. Notify your user to use __enrollment.manage.microsoft.com__ as the MDM server address if prompted for it while enrolling a Windows or and Windows Phone device. No changes are needed to your CNAME setup. For additional information about this change, visit [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange).

### New user experience for the Company Portal app for Android <!--621622-->
Beginning in March, the Company Portal app for Android will follow [material design guidelines](https://material.io/guidelines/material-design/introduction.html) to create a more modern look and feel. This improved user experience includes:

* __Colors__: tab headers can be colored according to your custom color palette.
* __Interface__: Featured Apps and All Apps buttons have been updated in the Apps tab. The Search button is now a floating action button.
* __Navigation__: All Apps shows a tabbed view of Featured, All and Categories for easier navigation.
* __Service__: My Devices and Contact IT tabs have improved readability.

You can find before and after images on the [UI updates page](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### Associate multiple management tools with the Windows Store for Business <!--926135-->
If you are using more than one management tool to deploy Windows Store for Business apps, previously, you could only associate one of these with the Windows Store for Business. You can now associate multiple management tools with the store, for example, Intune and Configuration Manager. For details, see [Manage apps you purchased from the Windows Store for Business with Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune).

## What's new in the public preview of the Intune admin experience on Azure <!--736542-->

In early calendar year 2017 we will be migrating our full admin experience onto Azure, allowing for powerful and integrated management of core EMS workflows on a modern service platform that’s extensible using Graph APIs.

New trial tenants will start to see the public preview of the new admin experience in the Azure portal this month. While in preview state, capabilities and parity with the existing Intune console will be delivered iteratively.

The admin experience in the Azure portal will use the already announced new grouping and targeting functionality; when your existing tenant is migrated to the new grouping experience you will also be migrated to preview the new admin experience on your tenant. In the meantime, if you want to test or look at any of the new functionality until your tenant is migrated, sign up for a new Intune trial account or take a look at the [new documentation](https://docs.microsoft.com/intune-azure/introduction/whats-new).

If you have any questions about the timeline for your tenant’s migration, contact our migration team at [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

You can find what's new in the Intune preview in Azure [here](https://docs.microsoft.com/intune-azure/introduction/whats-new).

## What's coming

### Apple to require updates for Application Transport Security <!--748318-->

Beginning in Spring 2017, Apple has announced that they will enforce specific requirements for Application Transport Security (ATS). ATS is used to enforce stricter security on all app communications over HTTPS. This change impacts Intune customers using the iOS/macOS Company Portal apps. Review our [Intune support blog](https://aka.ms/compportalats) for more details. 

### See also
* [Microsoft Intune Blog](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Cloud Platform roadmap](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [What's new in the Azure preview](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [What's new in the Company Portal UI](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)
* [What's new archive](whats-new-archive.md)
