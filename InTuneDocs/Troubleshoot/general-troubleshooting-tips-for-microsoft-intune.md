---
# required metadata

title: General troubleshooting tips | Microsoft Intune
description: General resources to help resolve issues with Intune.
keywords:
author: nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c86a4e4a-6b9f-4835-a3d3-61a3f5f4c1ec

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: tscott
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# General troubleshooting tips for Microsoft Intune
After you deploy Microsoft Intune you may encounter problems with your configuration or with clients. The resources below may help you find out what could be causing the problem so that you can resolve it.

> [!NOTE]
> To create a support request, or to view an existing request, [visit the Office 365 admin center](https://portal.office.com/admin/default.aspx). For more information about support options, see [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

## Define the problem

-   What is the behavior?

-   Who experiences this behavior, and on what platforms and devices?

-   Did the device work properly previously?

-   What changes did you make to the Intune or device configuration?

-   Consider whether other changes were made to the environment in which you operate, other than configuration changes.

-   How frequently does this problem occur, and is it sporadic or consistent?

-   Could the user be experiencing an authentication issue? If this is a possiblity, check if the user can log in to other services that use Azure Active Directory. Also, see if the user can log in from a different device.

-   Have you checked the service status? You can monitor Intune service health in the [Office 365 management portal](https://portal.office.com/Admin/Default.aspx). Choose **Service Health** in the left pane.

## Collect available data

-   Device logs. Learn how to collect device logs in:
  - [Send Android diagnostic data logs to your IT administrator using a USB cable](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [Send Android diagnostic data logs to your IT administrator using email](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)
  - [Send Android enrollment errors to your IT administrator](/intune/enduser/send-enrollment-errors-to-your-it-administrator-android)
  - [Send iOS enrollment errors to your IT administrator](/intune/enduser/send-errors-to-your-it-admin-ios)

-   Admin console data, for example, for policy implementation issues you should examine the intended policy and the status of that policy, as described in [Use groups to manage users and devices with Microsoft Intune](/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).

## Research the solution

-   Search the Web for a solution. For example, if you receive the error 0x80073CF0, you can search for **technet intune 0x80073cf0** on the Web, and find the article [Troubleshoot app deployment problems in Microsoft Intune](troubleshoot-app-deployment-problems-in-microsoft-intune.md), which offers suggestions for addressing this issue.

-   You can search for an answer in the [Intune TechNet forum](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  If the issue has not been previously addressed you should post the question to see what suggestions the community might have.

-   You can open a support request. Intune Support will be better able to help you resolve an issue when you've defined the problem and have collected the available data.

    To create a support request [visit the Office 365 admin center](https://portal.office.com/admin/default.aspx). For more information about support options, see [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

## Community resources
You can find other helpful information in these community resources:

-   The [Microsoft Intune Survival Guide](http://social.technet.microsoft.com/wiki/contents/articles/23431.microsoft-intune-survival-guide.aspx) contains links to many resources that can help you configure, maintain, and troubleshoot Intune.

-   [The Intune blog](http://blogs.technet.com/b/windowsintune/)

-   [Follow Intune on Twitter](https://twitter.com/MSIntune)

-   [The Intune forums](https://social.technet.microsoft.com/Forums/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)

### Next steps
The topics listed below have troubleshooting help for specific issues. If that information doesn't help you, contact Microsoft Support as described in [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

[Troubleshoot Endpoint Protection in Microsoft Intune](troubleshoot-endpoint-protection-in-microsoft-intune.md)

[Troubleshoot company resource access problems with Microsoft Intune](troubleshoot-company-resource-access-problems-with-microsoft-intune.md)

[Troubleshoot app deployment problems in Microsoft Intune](troubleshoot-app-deployment-problems-in-microsoft-intune.md)

[Troubleshoot device enrollment in Intune](troubleshoot-device-enrollment-in-intune.md)

[Troubleshoot policies in Microsoft Intune](troubleshoot-policies-in-microsoft-intune.md)

[Troubleshoot client setup in Microsoft Intune](troubleshoot-client-setup-in-microsoft-intune.md)

[Troubleshoot software updates in Microsoft Intune](troubleshoot-software-updates-in-microsoft-intune.md)
