---
# required metadata

title: Configure Windows Update for Business in Microsoft Intune - Azure | Microsoft Docs
description: Update the Software Update settings in a profile to creating an update ring, review compliance, and pause updates in Windows Update for Business settings using Microsoft Intune on Windows 10 devices.
keywords:
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: coryfe
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
#ms.custom:
ms.collection: M365-identity-device-management
---

# Manage software updates in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Use Intune to define update rings that specify how and when Windows as a Service updates your Windows 10 devices. Update rings are policies you that you assign to groups of devices. By using update rings, you can create an update strategy that mirrors your business needs. For more information, see [Manage updates using Windows Update for Business](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

With Windows 10, new Feature Updates and Quality Updates include the contents of all previous updates. As long as you've installed the latest update, you know your Windows 10 devices are up-to-date. Unlike with previous versions of Windows, you now must install the entire update instead of part of an update.


By using Windows Update for Business, you simplify the update management experience. You don’t need to approve individual updates for groups of devices. You can manage risk in your environments by configuring an update rollout strategy. Intune provides the ability to [configure update settings](windows-update-settings.md) on devices and gives you the ability to defer update installation. Intune doesn’t store the updates, but only the update policy assignment. Devices access Windows Update directly for the updates. This collection of settings that configures when Windows 10 updates get installed is called a *Windows 10 update ring*.

Windows 10 update rings support [scope tags](scope-tags.md). You can use scope tags with update rings to help you filter and manage sets of configurations that you use.

## Prerequisites  

The following prerequisites must be met to use Windows updates for Windows 10 devices in Intune.  

- Windows 10 PCs must run at least Windows 10 Pro with the Windows Anniversary update or later (version 1607 or later)
- Windows Update supports the following Windows 10 editions:
  - Windows 10
  - Windows 10 Team (for Surface Hub devices)
  - Windows Holographic for Business  

    Windows Holographic for Business supports a subset of settings for Windows updates, including:
    - **Automatic update behavior**
    - **Microsoft product updates**
    - **Servicing channel**: Supports **Semi-annual channel** and **Semi-annual channel (Targeted)** options. For more information, see [Manage Windows Holographic](windows-holographic-for-business.md).  

    > [!NOTE]  
    > **Unsupported versions and editions**:
    > - Windows 10 Mobile  
    > - Windows 10 Enterprise LTSC. Windows Update for Business (WUfB) does not currently support *Long Term Service Channel* releases. Plan to use alternative patching methods, like WSUS or Configuration Manager.  

- On Windows devices, **Feedback & diagnostics** > **Diagnostic and usage data** must be set to **Basic**, **Enhanced**, or **Full**.  

  You can configure the *Diagnostic and usage data* setting for Windows 10 devices manually or use an Intune device restriction profile for Windows 10 and later. If you use a device restriction profile, set the [device restriction setting](device-restrictions-windows-10.md#reporting-and-telemetry) of **Share usage data** to at least **Basic**. This setting is found under the  **Reporting and Telemetry** category when you configure a device restriction policy for Windows 10 or later.

  For more information about device profiles, see [configure device restriction settings](device-restrictions-configure.md).  

- If you use the Azure classic portal, [migrate your settings to the Azure portal](#migrate-update-settings-to-the-azure-portal).  


## Create and assign update rings

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Select **Software updates** > **Windows 10 Update Rings** > **Create**.
4. Enter a name, a description (optional), and then choose **Configure**.
5. In **Settings**, configure settings for your business needs. For information about the available settings, see [Windows update settings](windows-update-settings.md).  
6. When done, select **OK**. In **Create Update Ring**, select **Create**. The new update ring is displayed in the list of update rings.
7. To assign the ring, in the list of update rings, select a ring, and then on the \<ring name> tab, choose **Assignments**.
8. Use the **Include** and **Exclude** tabs to define which groups this Ring is assigned to, and then select **Save** to complete the assignment.

## Manage your Windows 10 Update rings
In the portal, you can select a Windows 10 Update Ring to open its **Overview** pane. From this pane you can view the rings assignment status and take additional actions to manage the ring. 
### To view an updates rings Overview pane: 
1. Sign in to the Azure portal.
2. Navigate to **Intune** > **Software updates** > **Windows 10 Update Rings**.
3. Select the update ring you want to view or manage.  

In addition to viewing assignment status, you can select the following actions from the top of the Overview pane to manage the update ring:  
- [Delete](#delete)  
- [Pause](#pause)  
- [Resume](#resume)  
- [Extend](#extend)  
- [Uninstall](#uninstall)  

![Available actions](./media/windows-update-for-business-configure/overview-actions.png)

### Delete  
Select **Delete** to stop enforcing the settings of the selected Windows 10 update ring. Deleting a ring removes its configuration from Intune so that Intune no longer applies and enforces those settings.  

Deleting a ring from Intune doesn't modify the settings on devices that were assigned the update ring.  Instead, the device keeps its current settings. This is because devices don't maintain a historical record of what settings were previously in place, and because the device might receive settings from additional update rings that remain active.  

#### To delete a ring  
1. While viewing the overview page for an Update Ring, select **Delete**.  
2. Select **OK**.  

### Pause  
Select **Pause** to prevent assigned devices from receiving Feature Updates or Quality Updates for up to 35 days from the time you pause the ring. After the maximum days have passed, pause functionality automatically expires and the device scans Windows Updates for applicable updates. Following this scan, you can pause the updates again. 
If you resume a paused update ring, and then pause that ring again, the pause period resets to 35 days.  

#### To pause a ring  
1. While viewing the overview page for an Update Ring, select **Pause**.  
2. Select either **Feature** or **Quality** to pause that type of update, and then select **OK**.  
3. After pausing one update type, you can select Pause again to pause the other update type.  

When an update type is paused, the Overview pane for that ring displays how many days remain before that update type resumes.

> [!IMPORTANT]  
> After you issue a pause command, devices receive this command the next time they check into the service. It's possible that before they check in, they might install a scheduled update. Additionally, if a targeted device is turned off when you issue the pause command, when you turn it on, it might download and install scheduled updates before it checks in with Intune.

### Resume  
While an update ring is paused, you can select **Resume** to restore Feature and Quality updates for that ring to active operation. After you resume an update ring, you can pause that ring again.  

#### To resume a ring  
1. While viewing the overview page for a paused Update Ring, select **Resume**.  
2. Select from the available options to resume either **Feature** or **Quality** updates, and then select **OK**.  
3. After resuming one update type, you can select Resume again to resume the other update type.  

### Extend  
While an update ring is paused, you can select **Extend** to reset the pause period for both Feature and Quality updates for that update ring to 35 days.  

#### To Extend the pause period for a ring  
1. While viewing the overview page for a paused Update Ring, select **Extend**. 
2. Select from the available options to resume either **Feature** or **Quality** updates, and then select **OK**.  
3. After extending the pause for one update type, you can select Extend again to extend the other update type.  

### Uninstall  
An Intune administrator can use **Uninstall** to uninstall (roll back) the latest *feature* update or the latest *quality* update for an active or paused update ring. After uninstalling one type, you can then uninstall the other type. Intune doesn't support or manage the ability of users to uninstall updates.  

For Uninstall to be successful:  
- A device must run the Windows 10 April 2018 update (version 1803) or later.  

A device must have installed the latest update. Because updates are cumulative, devices that install the latest update will have the most recent feature and quality update. An example of when you might use this option is to roll back the last update should you discover a breaking issue on your Windows 10 machines.  

Consider the following when you use Uninstall:  
- Uninstalling a feature or quality update is only available for the servicing channel the device is on.  

- Using uninstall for Feature or Quality updates triggers a policy to restore the previous update on your Windows 10 machines.  

- On a Windows 10 device, after a quality update is successfully rolled back, end-users continue to see the update listed in **Windows settings** > **Updates** > **Update History**.  

- For Feature updates specifically, the time you can uninstall the feature update is limited from 2-60 days, as configured by the update rings Update setting **Set feature update uninstall period (2 – 60 days)**. You can't roll back a feature update that's been installed on a device after the feature update has been installed for longer than the configured uninstall period.  

  For example, consider an update ring with a feature update uninstall period of 20 days. After 25 days you decide to roll back the latest feature update and use the Uninstall option.  Devices that installed the feature update over 20 days ago can't uninstall it as they have removed the necessary bits as part of their maintenance. However, devices that only installed the feature update up to 19 days ago can uninstall the update if they successfully check in to receive the uninstall command prior to exceeding the 20-day uninstall period.  

For more information about Windows Update policies, see [Update CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp) in the Windows client management documentation.  

#### To uninstall the latest Windows 10 update  
1. While viewing the overview page for a paused Update Ring, select **Uninstall**.  
2. Select from the available options to uninstall either **Feature** or **Quality** updates, and then select **OK**.  
3. After triggering the uninstall for one update type, you can select Uninstall again to uninstall the remaining update type.  

## Migrate update settings to the Azure portal  
The Azure classic portal also has a limited number of other Windows 10 updates settings in the device configuration profile. If you have any of these settings configured when you migrate to the Azure portal, we strongly recommend that you do the following actions:  

1. Create Windows 10 update rings in the Azure portal with the settings that you need. The **Allow pre-release features** setting isn't supported in the Azure portal because it's no longer applicable to the latest Windows 10 builds. You can configure the other three settings, as well as other Windows 10 updates settings, when you create update rings.  

   > [!NOTE]  
   > Windows 10 updates settings created in the classic portal are not displayed in the Azure portal after migration. However, these settings are applied. If you migrate any of these settings, and edit the migrated policy from the Azure portal, these settings are removed from the policy.  

2. Delete the update settings in the classic portal. After you migrate to the Azure portal, and add the same settings to an update ring, you must delete the settings in the classic portal to avoid any potential policy conflicts. For example, when the same setting is configured with different values, there is a conflict. There isn't an easy way to know because the setting configured in the classic portal doesn't display in the Azure portal.  

## Next steps
[Windows update settings supported by Intune](windows-update-settings.md)  

[Intune compliance reports for updates](windows-update-compliance-reports.md)

[Troubleshooting Windows 10 update rings](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Windows-10-Update-Ring-Policies/ba-p/714046)

