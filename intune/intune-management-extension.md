---
# required metadata

title: Add PowerShell scripts in Microsoft Intune for Windows 10 devices - Azure | Microsoft Docs
description: Add PowerShell scripts, assign the script policy to Azure Active Directory groups, use reports to monitor the scripts, and see the steps to delete scripts you add on Windows 10 devices in Microsoft Intune. 
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/30/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Manage PowerShell scripts in Intune for Windows 10 devices
The Intune management extension lets you upload PowerShell scripts in Intune to run on Windows 10 devices. The management extension supplements Windows 10 mobile device management (MDM) capabilities and makes it easier for you to move to modern management.

## Moving to modern management
End-user computing is going through a digital transformation. Classic, traditional IT focuses on a single device platform, business-owned devices, users that work from the office, and a variety of manual, reactive IT processes. The modern workplace, however, enables multiple device platforms that are both user and business owned, allow users to work from anywhere, and provide automated and proactive IT processes. 

MDM services, such as Microsoft Intune, can manage Windows 10 devices by using the MDM protocol. The built-in Windows 10 management client is able to communicate with Intune to perform enterprise management tasks. It helps you drive toward modern management on Windows 10 devices. However, there are certain capabilities that you might need, such as advanced device configuration, troubleshooting, and legacy Win32 app management that currently isn't available in Windows 10 MDM. For these capabilities, you might run the Intune software client on your Windows 10 devices. As a result, you are not able to use the new capabilities that Windows 10 MDM provides. [Compare the differences between the Intune software client and Windows 10 MDM](https://docs.microsoft.com/intune-classic/deploy-use/pc-management-comparison).

The Intune management extension supplements the in-box Windows 10 MDM capabilities. You can create PowerShell scripts to run on the Windows 10 devices that provide the capabilities you need. For example, you can create a PowerShell script that installs a legacy Win32 app on your Windows 10 devices, upload the script to Intune, assign the script to an Azure Active Directory (AD) group, and run the script on Windows 10 devices. You can then monitor the run status of the script on Windows 10 devices from start to finish.

## Prerequisites
The Intune management extension has the following prerequisites:
- Devices must be joined to Azure AD. This includes Hybrid AD joined devices.
- Devices must run Windows 10, version 1607 or later.
- Automatic MDM enrollment must be [enabled in Azure AD](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment), and devices must be auto-enrolled to Intune.

## Create a PowerShell script policy 
1. Sign in to the [Azure portal](https://portal.azure.com).
2. Select **All services**, filter on **Intune**, and select **Microsoft Intune**.
3. Select **Device configuration** > **PowerShell scripts** > **Add**.
4. Enter a **Name** and **Description** for the PowerShell script. For **Script location**, browse to the PowerShell script. The script must be less than 200KB (ASCII) or 100KB (Unicode) in size.
5. Choose **Configure**. Then choose to run the script with the user's credentials on the device (**Yes**), or system context (**No**). By default, the script runs in the system context. Select **Yes** unless the script is required to run in the system context. 
  ![Add PowerShell script pane](./media/mgmt-extension-add-script.png)
6. Choose if the script must be signed by a trusted publisher (**Yes**). By default, there is no requirement for the script to be signed. 
7. Select **OK**, and then **Create** to save the script.

## Assign a PowerShell script policy
1. In **PowerShell scripts**, select the script to assign, and then choose **Manage** > **Assignments**.
  ![Add PowerShell script pane](./media/mgmt-extension-assignments.png)
 
2. Choose **Select Groups** to list available Azure AD groups. 
3. Select one or more groups that contain the users whose devices receive the script. **Select** to assign the policy to the selected groups.

> [!NOTE]
> - PowerShell scripts can't be applied to computer groups.
> - PowerShell scripts are executed on devices only when an Azure Active Directory (AD) user is signed in to the device.

The Intune management extension synchronizes to Intune once every hour. After you assign the policy to the Azure AD groups, the PowerShell script runs, and the run results are reported. 
 
## Monitor run status for PowerShell scripts
You can monitor the run status of PowerShell scripts for users and devices in the Azure portal.

In **PowerShell scripts**, select the script to monitor, choose **Monitor**, and then choose one of the following reports:
   - **Device status**
   - **User status**

## Delete a PowerShell script
In **PowerShell scripts**, right-click the script, and select **Delete**.
