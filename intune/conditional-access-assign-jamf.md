---
# required metadata

title: Device compliance policy for Jamf devices
titlesuffix: Microsoft Intune
description: Use Microsoft Intune compliance policies with Azure Active Directory conditional access to help secure Jamf-managed devices.
keywords:
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/16/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc

# optional metadata

#ROBOTS: 
#audience:
#ms.devlang:
ms.reviewer: elocholi
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure
---

# Enforce compliance on Macs managed with Jamf Pro

|Applies to: Intune in the Azure portal |
|--|
|Looking for documentation about Intune in the classic portal? [Go here](/intune/introduction-intune?toc=/intune-classic/toc.json).|
| |

You can use Azure Active Directory and Microsoft Intune's conditional access policies ensure that your end users are compliant with organizational requirements. You can apply these policies to Macs that are [managed with Jamf Pro](conditional-access-integrate-jamf.md). This requires access to both the Intune and Jamf Pro consoles.

## Set up device compliance policies in Intune

1. Open Microsoft Azure, then navigate to **Intune** > **Device Compliance** > **Policies**. You can create policies for macOS, including choosing a series of actions (e.g., sending warning emails) to noncompliant users and groups.
2. Search for your desired groups, then apply the policies to them.

> [!Note]
> Intune requires full disk encryption to be compliant.

## Deploy the Company Portal app for macOS in Jamf Pro

You should deploy the Company Portal app for macOS in Jamf Pro as a background installation following the procedure below:

1. On a macOS device, download the current version of the [Company Portal app for macOS](https://go.microsoft.com/fwlink/?linkid=862280). Do not install it; you need a copy of the app to upload to Jamf Pro.
2. Open Jamf Pro, then navigate to **Computer management** > **Packages**.
3. Create a new package with the Company Portal app for macOS, then click **Save**.
4. Open **Computers** > **Policies**, then select **New**.
5. Use the **General** payload to configure settings for the policy. These settings should be:
   - Trigger: select **Enrollment Complete** and **Recurring Check-in**
   - Execution Frequency: select **Once per computer**
6. Select the **Packages** payload and click **Configure**.
7. Click **Add** to select the package with the Company Portal app.
8. Choose **Install** from the **Action** pop-up menu.
9. Configure the settings for the package.
10. Click the **Scope** tab to specify on which computers the Company Portal app should be installed. Click **Save**. The policy will run scoped devices the next time the selected trigger occurs on the computer and meets the criteria in the **General** payload.

## Create a policy in Jamf Pro to have users register their devices with Azure Active Directory

> [!NOTE]
> You need to [deploy the Company Portal](conditional-access-assign-jamf.md#require-the-company-portal-app-for-macos) for macOS before going through the next steps.  

End users need to launch the Company Portal app through Jamf Self Service to register the device with Azure AD as a device managed by Jamf Pro. This will require your end users to take action. We recommend that you [contact your end user](end-user-educate.md) through email, Jamf Pro notifications, or any other methods of notifying your end users to click the button in Jamf Self Service.

> [!WARNING]
> The Company Portal app must be launched from Jamf Self Service to begin device registration. <br><br>Launching the Company Portal app manually (e.g., from the Applications or Downloads folders) will not register the device. If an end user launches the Company Portal manually, they will see a warning, 'AccountNotOnboarded'.

1. In Jamf Pro, navigate to **Computers** > **Policies**, and create a new policy for device registration.
2. Configure the **Microsoft Intune Integration** payload, including the trigger and execution frequency.
3. Click the **Scope** tab, and scope the policy to all targeted devices.
4. Click the **Self Service** tab to make the policy available in Jamf Self Service. Include the policy in the **Device Compliance** category. Click **Save**.

## Removing a Jamf-managed device from Intune

You can remove a Jamf-managed device from the Intune console, by selecting "Delete" in the "All devices" view. Bulk device deletion can be enabled by selecting multiple devices and clicking "Delete."

Get information on how to [remove a Jamf-managed device in the Jamf Pro docs](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). You can also file a support ticket with [Jamf support](https://www.jamf.com/support/) for additional help. 

## Next steps

- [Conditional access in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Get started with conditional access in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
