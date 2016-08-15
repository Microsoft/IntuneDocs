---
# required metadata

experiment_id: kgremban_images_080416
title: Introduction to Microsoft Intune | Microsoft Intune
description: Learn how Intune is the mobile device management component of the Enterprise Mobility + Security solution.
keywords:
author: Lindavr
manager: angrobe
ms.date: 08/10/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Introduction to Intune
Microsoft Intune is the "management arm" of Microsoft Enterprise Mobility + Security (EMS, formerly Enterprise Mobility Suite). Enterprise mobility is about enabling your employees to be productive on all of their devices while keeping your organization's information protected.  

EMS is a complete, integrated suite for enterprise mobility inclusive of productivity, identity, access control, management, and data protection. It gives you an effective way to deploy and operate a mobility solution in your organization.  

Intune helps you manage mobile devices and mobile apps. It integrates closely with Azure Active Directory (Azure AD) for identity and access control, and Azure Rights Management (Azure RMS) for data protection.  

Intune helps solve the following common business problems:

* Securing your on-premises email and collaboration infrastructure so that it can be accessed by mobile devices and apps on the Internet.
* Securing your Office 365 infrastructure so that it can be safely accessed by mobile devices and apps on the Internet.
* Enabling your organization to issue mobile phones to its employees.
* Enabling your organization to provide limited-use “shared devices” for task workers.
* Enabling your organization to implement a secure “bring your own device (BYOD)” or personal device strategy.
* Enabling your organization to support employees accessing Office 365 from devices and apps that you don’t control, such as a kiosk in the lobby of a trade show.

![Image of enterprise mobility vision](..\media\em-vision.png)

The primary tools that Intune offers include:
* **Mobile device management (MDM)**: The ability to enroll devices in Intune so that you can provision, configure, monitor, and take actions on those devices, such as wiping them.
* **Mobile application management (MAM)**: The ability to publish, push, configure, secure, monitor, and update mobile apps for your users.
* **Mobile application security**: As a part of managing mobile apps, the ability to help secure mobile data by isolating personal data from corporate data and allowing the corporate data to be selectively wiped.

These tools are used in different combinations to enable the common business scenarios above. For example, shared device scenarios make heavy use of MDM. BYOD scenarios typically rely on MAM. And the corporate phone scenarios build upon both. Almost all scenarios make use of mobile application security.

Throughout this documentation, we’ll explain how to use the tools that Intune provides to support your business scenarios.  We’ll also explain how to use these tools with Office 365, Azure AD, Azure RMS, and other parts of the Microsoft mobility suite. We will give you a broad overview of the ways in which the technology is commonly used and how it might be useful in your environment, as well as procedures to implement them. The technology itself is flexible and can be adapted to all sorts of scenarios beyond the ones that we describe here.

### Next steps
* Read about some of the [common ways to use Intune](common-ways-to-use-intune.md).
* Get familiar with the product [with a 30-day trial of Intune](get-started-with-a-30-day-trial-of-microsoft-intune.md).
* Dive into the [technical requirements and capabilities](/intune/get-started/what-to-know-before-you-start-microsoft-intune) of Intune.
