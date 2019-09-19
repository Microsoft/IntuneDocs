---
# required metadata

title: Use role-based access control (RBAC) and scope tags for distributed IT in Intune | Microsoft Docs
description: Use scope tags to filter configuration profiles to specific roles.
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/06/2019
ms.topic: article
ms.service: microsoft-intune
ms.technology:
ms.assetid: 

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Use role-based access control (RBAC) and scope tags for distributed IT

You can use role-based access control and scope tags to make sure that the right admins have the right access and visibility to the right Intune objects. Roles determine what access admins have to which objects. Scope tags determine which objects admins can see.

For example, let’s say a Seattle regional office admin has the Policy and Profile Manager role. You want this admin to see and manage only the profiles and policies that only apply to Seattle devices. To set up this access, you would:

1. Create a scope tag called Seattle.
2. Create a role assignment for the Policy and Profile Manager role with: 
    - Members (Groups) = A security group named Seattle IT admins. All admins in this group will have  permission to manage policies and profiles for users/devices in the Scope (Groups).
    - Scope (Groups) = A security group named Seattle users. All users/devices in this group can have their profiles and policies managed by the admins in the Members (Groups). 
    - Scope (Tags) = Seattle. Admins in the Member (Groups) can see Intune objects that also have the Seattle scope tag.
3. Add the Seattle scope tag to policies and profiles that you want admins in Members (Groups) to have access to.
4. Add the Seattle scope tag to devices that you want visible to admins in the Members (Groups). 

## Default scope tag
The default scope tag is automatically added to all untagged objects that support scope tags.

The default scope tag feature is similar to the security scopes feature in System Center Configuration Manager. 

## To create a scope tag

1. In Intune, choose **Roles** > **Scope (Tags)** > **Create**.

    ![Screenshot of create a scope tag.](./media/scope-tags/create-scope-tag.png)

3. If you want all devices in specific groups, choose **Assign scope tag to all devices in selected groups**.
    1. In the **Select groups to include** page, choose the groups containing the devices that you want to assign this scope tag to.
    2. Choose **Select**.
4. Choose **Create**.

## To assign a scope tag to a role

1. In Intune, choose **Roles** > **All roles** > choose a role > **Assignments** > **Assign**.

    ![Screenshot of assign scope to a role.](./media/scope-tags/assign-scope-to-role.png)

2. Provide an **Assignment name** and **Description**.
3. Choose **Members (Groups)** > **Add** > choose the groups that you want as part of this assignment > **Select** > **OK**. Users in this group will have permissions to manage users/devices in the Scope (Groups).

    ![Screenshot of select member groups.](./media/scope-tags/select-member-groups.png)

4. If you want to manage users/devices in a specific set of groups, choose **Scope (Groups)** > **Selected Groups** > **Select groups to include** > choose the groups > **Select** > **OK**. All users/devices in this group will be managed by the admins in the Members (Group).

    ![Screenshot of select scope groups.](./media/scope-tags/select-scope-groups.png)

    Alternately, you can choose **All Devices**, **All Users**, or **All Users & All Devices**.

    ![Screenshot of other options for select scope groups.](./media/scope-tags/scope-group-other-options.png)
    
5. Choose **Scope (Tags)** > **Add** > choose the tags that you want to add to this role > **Select** > **OK**. Users in Members (Groups) will have access to Intune objects that also have the same scope tag.

    ![Screenshot of select scope tags.](./media/scope-tags/select-scope-tags.png)

6. Choose **OK**. 

## Assign scope tags to other objects

For objects that support scope tags, scope tags usually appear under **Properties**. For example, to assign a scope tag to a configuration profile, follow these steps:

1. In Intune, choose **Device configuration** > **Profiles** > choose a profile.

    ![Screenshot of select profile.](./media/scope-tags/choose-profile.png)

2. Choose **Properties** > **Scope (Tags)** > **Add**.

    ![Screenshot of add scope tags.](./media/scope-tags/add-scope-tags.png)

3. Under **Select Tags**, choose the tags that you want to add to the profile.
4. Choose **Select** > **OK** > **Save**.


## Scope tag details
When working with scope tags, remember these details: 

- You can assign scope tags to an Intune object type if the tenant can have multiple versions of that object (such as role assignments or apps).
  The following Intune objects are exceptions to this rule and don't currently support scope tags:
    - Windows ESP profiles
    - Device Categories
    - Enrollment Restrictions
    - Corp Device Identifiers
    - Terms and Conditions
    - Autopilot Devices
    - Device compliance locations
    - Jamf devices
- VPP apps and ebooks associated with the VPP token inherit the scope tags assigned to the associated VPP token.
- Device Enrollment Program (DEP) devices and DEP profiles associated with the DEP token inherit the scope tags assigned to the associated DEP token.
- When an admin creates an object in Intune, all scope tags assigned to that admin will be automatically assigned to the new object.
- Intune RBAC doesn't apply to Azure Active Directory roles. So, the Intune Service Admins and Global Admins roles have full admin access to Intune no matter what scope tags they have.
- If a role assignment has no scope tag, that IT admin can see all objects based on the IT admins permissions. Admins that have no scope tags essentially have all scope tags.
- You can only assign a scope tag that you have in your role assignments.
- You can only target groups that are listed in the Scope (Groups) of your role assignment.
- If you have a scope tag assigned to your role, you can't delete all scope tags on an Intune object. At least one scope tag is required.

## Next steps

Learn how scope tags behave when there are [multiple role assignments](role-based-access-control.md#multiple-role-assignments).
Manage your [roles](role-based-access-control.md) and [profiles](device-profile-assign.md).
