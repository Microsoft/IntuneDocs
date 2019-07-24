---
# required metadata

title: Create and deploy app protection policies 
titleSuffix: Microsoft Intune
description: This topic describes how to create and assign Microsoft Intune app protection policies (APP).
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/01/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# How to create and assign app protection policies

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Learn how to create and assign Microsoft Intune app protection policies to your users. This topic also describes how to make changes to existing policies.

## Before you begin

App protection policies can apply to apps running on devices that may or may not be managed by Intune. For a more detailed description of how app protection policies work and the scenarios that are supported by Intune app protection policies, see [What are Microsoft Intune app protection policies?](app-protection-policy.md)

If you're looking for a list of MAM supported apps, see [MAM apps list](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

For information about adding your organization's line-of-business (LOB) apps to Microsoft Intune to prepare for app protection policies, see [Add apps to Microsoft Intune](apps-add.md).

## Create an app protection policy
1. In Intune portal, go to **Client apps** > **App protection policies**. This selection opens the **App protection policies** details, where you create new policies and edit existing policies.
2. Select **Create Policy**.

   ![Screenshot of the 'Add a policy' blade](./media/app-protection-add-policy.png)

3. Specify a name for the policy, add a brief description, and select the platform type for your policy. You can create more than one policy for each platform.

4. Select **Apps** to open the **Apps** blade, where a list of available apps is displayed. Select one or more apps from the list that you want to associate with the policy that you're creating. Select at least one app to create a policy.  

5. Once you've selected the apps, choose **Select** to save your selection.

6. On the **Add a policy** blade, select **Configure required settings** to open **Settings**.

   There are three categories of policy settings:
   - **Data protection** - This group includes the data loss prevention (DLP) controls, like cut, copy, paste, and save-as restrictions. These settings determine how users interact with data in the apps.
   - **Access requirements** - This group contains the per-app PIN options that determine how the end user accesses the apps in a work context.  
   - **Conditional launch** - This group holds settings like the minimum OS settings, jailbreak and rooted device detection, and offline grace periods.

   To get you started, the policy settings have default values. If the default values meet your requirements, you don't have to make any changes.

   > [!TIP]
   > These policy settings are enforced only when using apps in the work context. When end users use the app to do a personal task, they aren't affected by these policies. Note that when you create a new file it is considered a personal file. 

7. Select **OK** to save this configuration. You're now back in the **Add a policy** blade.
8. Select **Create** to create the policy and save your settings.

New policies you create aren't deployed to any users until you explicitly do so. To deploy a policy, see [Deploy a policy to users](app-protection-policies.md#deploy-a-policy-to-users).

## Deploy a policy to users

1. In the **App protection policies** pane, select a policy.

2. In the ***Intune App Protection** pane, select **Assignments** to open the **Intune App Protection - Assignments** pane. On the *Include* tab, select **Select groups to include**. 

   ![Screenshot of the Assignments pane with Select groups to include menu](./media/app-protection-policy-add-users.png)

3. A list of all the security groups in your **Azure Active Directory** is displayed. Select the user groups that you want this policy to apply to, and then choose **Select**. 

    ![Screenshot of the Add user group pane with list of Azure AD users](./media/azure-ad-user-group-list.png)

4. After you include and exclude groups, select **Save** to save the configuration and deploy the policy to users. If you select **Discard** before you save your configuration, you will discard all changes you've made to the *Include* and *Exclude* tabs.   
 
     ![Screenshot showing the save and discard options](./media/save-assignment.png)
  
You've now created a policy and deployed it to users.

Only users with assigned Microsoft Intune licenses are affected by the policy. Users in the selected security group that don’t have an assigned Intune license aren't affected.

>[!IMPORTANT]
> If you're using Intune with Configuration Manager to manage your devices, the policy is only applied to the users directly in the group that you selected. Members of child groups nested within the group you selected aren't affected.

End users can download the apps from the App store or Google Play. For more information, see:
* [What to expect when your Android app is managed by app protection policies](app-protection-enabled-apps-android.md)
* [What to expect when your iOS app is managed by app protection policies](app-protection-enabled-apps-ios.md)

## Change existing policies
You can edit an existing policy and apply it to the targeted users. However, when you change existing policies, users who are already signed in to the apps won’t see the changes for an eight-hour period.

To see the effect of the changes immediately, the end user must sign out of the app, and then sign back in.

### To change the list of apps associated with the policy

1. In the **App protection policies** pane, select the policy you want to change.

2. In the *Intune App Protection* pane, select **Targeted apps** to open the list of apps.

3. Remove or add apps from the list and then select the **Save** icon to save your changes.

### To change the list of user groups


1. In  the **App protection policies** pane, select the policy you want to change.

2. In the *Intune App Protection* pane, select **Assignments** to open the **Intune App Protection - Assignments** pane that shows the list of current user groups who have this policy.

3. To add a new user group to the policy, on the *Include* tab choose **Select groups to include**, and select the user group. Choose **Select** to add the group. 

4. To exclude a user group, on the *Exclude* tab choose **Select groups to exclude**, and select the user group. Choose **Select** to remove the user group.  

5. To delete groups that were added previously, on either the *Include* or *Exclude* tabs, select the ellipsis (...) and select **Delete**. 

5. After your changes to the assignments are ready, select **Save** to save the configuration and deploy the policy to the new set of users. If you select **Discard** before you save your configuration, you will discard all changes you've made to the *Include* and *Exclude* tabs.

### To change policy settings

1. In the **App protection policies** pane, choose the policy you want to change.

2. In the *Intune App Protection* pane, select **Properties** to open the list of settings areas you can edit. 

3. Select the settings area with the settings you want to change, like **Data relocation** or **Access requirements**. Then change the settings to new values.

4. Select the **Save** icon to save your changes. Repeat the process to select a settings area and modify and then save your changes, until all your changes are complete. You can then close the *Intune App Protection - Properties* pane. 

## Target app protection policies based on device management state
In many organizations, it’s common to allow end users to use both Intune Mobile Device Management (MDM) managed devices, such as corporate owned devices, and un-managed devices protected with only Intune app protection policies. Unmanaged devices are often known as Bring Your Own Devices (BYOD).

Because Intune app protection policies target a user’s identity, the protection settings for a user can apply to both enrolled (MDM managed) and non-enrolled devices (no MDM). Therefore, you can target an Intune app protection policy to either Intune enrolled or unenrolled iOS and Android devices. You can have one protection policy for unmanaged devices in which strict data loss prevention (DLP) controls are in place, and a separate protection policy for MDM managed devices, where the DLP controls may be a little more relaxed. For more information how this works on personal Android Enteprise devices, see [App protection policies and work profiles](android-deployment-scenarios-app-protection-work-profiles.md).

To create these policies, browse to **Client apps** > **App protection policies** in the Intune console, and then select **Create Policy**. You can also edit an existing app protection policy. To have the app protection policy apply to both managed and un-managed devices, confirm that **Target to all app types** is set to **Yes**, the default value. If you want to granularly assign base on management state, set **Target to all app types**  to **No**. 

![Screenshot of the Add a policy blade with Target to all app types](./media/app-protection-policies-target-all.png)

### App types

- **Apps on unmanaged devices**: Unmanaged devices are devices where Intune MDM management has not been detected. This includes 3rd party MDM vendors.
- **Apps on Intune managed devices**: Managed devices are managed by Intune MDM.
- **Apps in Android Work Profile**: Managed devices that have been enrolled as Android Enterprise work profile devices.

For iOS, additional app configuration settings are required to target app protection policy (APP) settings to apps on Intune enrolled devices:
- **IntuneMAMUPN** must be configured for all MDM managed applications. For more information, see [How to manage data transfer between iOS apps in Microsoft Intune](https://docs.microsoft.com/intune/data-transfer-between-apps-manage-ios#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).
- **IntuneMAMDeviceID** must be configured for all Third-party and LOB MDM managed applications. The **IntuneMAMDeviceID** should be configured to the device ID token. For example, `key=IntuneMAMDeviceID, value={{deviceID}}`. For more information, see [Add app configuration policies for managed iOS devices](https://docs.microsoft.com/intune/app-configuration-policies-use-ios).
- If only the **IntuneMAMDeviceID** is configured, the Intune APP will consider the device as unmanaged. 

> [!NOTE]
> For specific iOS support information about app protection policies based on device management state, see [MAM protection policies targeted based on management state](whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state-).


## Policy settings
To see a full list of the policy settings for iOS and Android, select one of the following links:

- [iOS policies](app-protection-policy-settings-ios.md)
- [Android policies](app-protection-policy-settings-android.md)

## Next steps
[Monitor compliance and user status](app-protection-policies-monitor.md)

## See also
* [What to expect when your Android app is managed by app protection policies](app-protection-enabled-apps-android.md)
* [What to expect when your iOS app is managed by app protection policies](app-protection-enabled-apps-ios.md)
