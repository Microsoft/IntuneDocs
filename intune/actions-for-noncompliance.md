---
# required metadata

title: Noncompliant message and actions with Microsoft Intune - Azure | Microsoft Docs
description: Create a notification email to send to non-compliant devices. Add actions after a device is  marked as non-compliant, such as add a grace period to get compliant, or create a schedule to block access until the device is compliant. Do this using Microsoft Intune in Azure.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Automate email and add actions for noncompliant devices - Intune

There is an **Actions for noncompliance** feature that configures a time-ordered sequence of actions. These actions apply to devices that don't meet your compliance policy. 

## Overview
By default, when Intune detects a device that isn't compliant, Intune immediately marks the device as noncompliant. Azure Active Directory (AD) [conditional access](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) then blocks the device. When a device is not compliant, **actions for noncompliance** also gives you flexibility to decide what to do. For example, don't block the device immediately, and give the user a grace period to be compliant.

There are two types of actions:

- **Notify end users via email**: Customize an email notification before sending it to the end user. You can customize the recipients, subject, and message body, including company logo, and contact information.

    Additionally, Intune includes details about the noncompliant device in the email notification.

- **Mark device non-compliant**: Create a schedule (in number of days) after the device is marked not compliant. You can configure the action to take effect immediately, or give the user a grace period to be compliant.

## Before you begin

- To set up actions for non-compliance, you need at least one device compliance policy. To create a device compliance policy, see the following platforms:

  - [Android](compliance-policy-create-android.md)
  - [Android work profiles](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- When using device compliance policies to block devices from corporate resources, Azure AD conditional access must be set up. See [Conditional access in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) for guidance.

- A notification message template must be created. To send email to your users, this template is used to create actions for non-compliance.

## Create a notification message template

1. Sign in to the [Azure portal](https://portal.azure.com) with your Intune credentials. 
2. Select **All services**, filter on **Intune**, and select **Microsoft Intune**.
3. Select **Device compliance**, then select **Notifications**. 
4. Select **Create notification**, and then enter the following information:

   - Name
   - Subject
   - Message
   - Email header – Include company logo
   - Email footer – Include company name
   - Email footer – Include contact information

   ![Example of a compliant notification message in Intune](./media/actionsfornoncompliance-1.PNG)

Once you're done adding the information, choose **Create**. The Notification message template is ready to use.

> [!NOTE]
> You can also edit a Notification template previously created.

## Add actions for noncompliance

By default, Intune automatically creates an action for noncompliance. When a device is not meeting your compliance policy, this action marks the device as not compliant. You can customize how long the device is marked as not compliant. This action can't be removed.

You can add an action when you create a new compliance policy, or update an existing compliance policy. 

1. In the [Azure portal](https://portal.azure.com), open **Microsoft Intune**, and select **Device compliance**.
2. Select **Policies**, choose one of your policies, and then select **Properties**. 

  Don't have a policy yet? Create an [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md), or other platform policy.
  
  > [!NOTE]
  > JAMF devices and devices targeted with device groups cannot receive compliance actions at this time.

3. Select **Actions for noncompliance**, and then select **Add** to enter the action parameters. You can choose the message template previously created, add additional recipients, and update the grace period schedule. You can enter the number of days (0 to 365) on the schedule, then you can enforce the conditional access policies. If you enter **0** number of days, then conditional access **immediately** blocks access to corporate resources.

4. When finished, select **Add** > **OK** to save your changes.

## Next steps
Monitor the device compliance activity by running the reports. [How to monitor device compliance with Intune](device-compliance-monitor.md) provides some guidance.
