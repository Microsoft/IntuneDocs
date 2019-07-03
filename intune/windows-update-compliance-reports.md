---
# required metadata

title: Use Update Compliance reports for Windows Updates in Microsoft Intune | Microsoft Docs
description: Use OMS Update Compliance to view report data for Windows Updates you deploy with Intune.
keywords:
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
#ms.custom:
ms.collection: M365-identity-device-management
---

# Intune compliance reports for updates
When you use Intune to deploy Windows update to Windows 10 devices, view details about update compliance by using Intune or a free solution called *Update Compliance*, which is part of the Microsoft Operations Management Suite (OMS).

## Use Intune
To review a policy report on the deployment status for the Windows 10 update rings that you have configured: 
1. Sign in to the [Azure portal](https://portal.azure.com/).
2. Choose **All services**, filter on **Intune**, and select **Microsoft Intune**.
3. Select **Software updates** > **Overview**. You can see general information about the status of any update rings you assigned.
4. Open one of the following reports:  

   **For all deployment rings**:
   1. On the **Software updates** > **Windows 10 Update Rings**
   2. In the **Monitor section**, choose **Per update ring deployment state**.  

   **For specific deployment rings**:  

   1. In **Software updates** > **Windows 10 Update Rings**, choose the deployment ring to review.  
   2. In the **Monitor** section, choose from the following reports to view more detailed information about the update ring:  
      - **Device status**  
      - **User status**  

## Use Update Compliance
You can monitor Windows 10 update rollouts by using [Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor), a Windows Analytics solution. Update Compliance is offered through the Azure portal and is available free for devices that meet its [prerequisites](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started#update-compliance-prerequisites).  

When you use this solution, you deploy a commercial ID to any of your Intune managed Windows 10 devices for which you want to report update compliance.  

In the Intune console, you use the OMA-URI settings of a custom policy to configure the commercial ID. For details, see [Intune policy settings for Windows 10 devices in Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).  

The OMA-URI (case sensitive) path for configuring the commercial ID is: *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*  

For example, you can use the following values in **Add or edit OMA-URI Setting**:
- **Setting Name**: Windows Analytics Commercial ID
- **Setting Description**: Configuring commercial ID for Windows Analytics solutions
- **OMA-URI** (case sensitive): *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*
- **Data Type**: String
- **Value**: \<Use the GUID shown on the Windows Telemetry tab in your OMS workspace>
 
> [!NOTE]  
> For more information about MS DM Server, see [DMClient configuration service provider (CSP)]( https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp).

## Next steps
[Manage software updates in Intune](windows-update-for-business-configure.md)
