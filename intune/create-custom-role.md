---
# required metadata

title: Create a custom role in Intune
description: Learn how to create a custom role in Microsoft Intune.
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
---

# Create a custom role in Intune

You can create a custom Intune role that includes any permissions required for a specific job function. For example, if an IT department group manages applications, policies, and configuration profiles, you can add all those permissions together in one custom role. After creating a custom role, you can [assign](assign-role.md)
 it to any users that need those permissions.

To create, edit, or assign roles, your account must have one of the following permissions in Azure AD:
- **Global Administrator**
- **Intune Service Administrator**

## To create a custom role

1. Sign into the [Azure portal](https://portal.azure.com) with your Intune credentials.

2. Choose **All services** from the left menu, then type **Intune** in the text box filter.

3. Choose **Intune** > **Roles** > **All roles** > **Add**.

4. On the **Add Custom Role** blade, enter a name and description for the new role, then click **Permissions**.

5. On the **Permissions** blade, choose the permissions you want to use with this role.

6. On the **Scope (Tags)** blade, choose the tags for this role. This role can access resources that also have these tags.

7. When you're done, choose **OK**.

8. On the **Add Custom Role** blade, click **Create**. The new role is displayed in the list on the **Intune roles - All roles** blade.

## Next steps
- [Assign a role to a user](assign-role.md)
- [Learn more about role-based access control in Intune](role-based-access-control.md)
