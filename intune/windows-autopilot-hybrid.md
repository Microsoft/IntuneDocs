---
# required metadata

title: Enrollment for hybrid Azure AD-joined devices - Windows Autopilot
titleSuffix: 
description: Use Windows Autopilot to enroll hybrid Azure AD-joined devices in Microsoft Intune.
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod:
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
 
# optional metadata
 
#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: seodec18
ms.collection: M365-identity-device-management
---
 

# Deploy hybrid Azure AD-joined devices by using Intune and Windows Autopilot (Preview)
You can use Intune and Windows Autopilot to set up hybrid Azure Active Directory (Azure AD)-joined devices. To do so, follow the steps in this article.

## Prerequisites

Successfully configure your [hybrid Azure AD-joined devices](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan). Be sure to [verify your device registration]( https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration) by using the Get-MsolDevice cmdlet.

The devices to be enrolled must also:
- Be running Windows 10 with the [October 2018 update](https://blogs.windows.com/windowsexperience/2018/10/02/how-to-get-the-windows-10-october-2018-update/).
- Have access to the internet.
- Have access to your Active Directory (VPN connection not supported).
- Undergo the out-of-box experience (OOBE).
- Be able to ping the domain controller of the domain you are trying to join.

## Set up Windows 10 automatic enrollment

1. Sign in to the [Azure portal](https://portal.azure.com) and, in the left pane, select **Azure Active Directory**.

   ![The Azure portal](./media/auto-enroll-azure-main.png)

1. Select **Mobility (MDM and MAM)**.

   ![The Azure Active Directory pane](./media/auto-enroll-mdm.png)

1. Select **Microsoft Intune**.

   ![The Mobility (MDM and MAM) pane](./media/auto-enroll-intune.png)

1. Make sure that the users who deploy Azure AD-joined devices by using Intune and Windows are members of a group that's included in your **MDM User scope**.

   ![The Mobility (MDM and MAM) Configure pane](./media/auto-enroll-scope.png)

1. Use the default values in the **MDM Terms of use URL**, **MDM Discovery URL**, and **MDM Compliance URL** boxes, and then select **Save**.

## Increase the computer account limit in the Organizational Unit

The Intune Connector for your Active Directory creates autopilot-enrolled computers in the on-premises Active Directory domain. The computer that hosts the Intune Connector must have the rights to create the computer objects within the domain. 

In some domains, computers are not granted the rights to create computers. Additionally, domains have a built-in limit (default of 10) that applies to all users and computers that aren't delegated rights to create computer objects. Therefore, the rights need to be delegated to computers that host the Intune Connector on the organizational unit where hybrid Azure AD-joined devices are created.

The organizational unit that's granted the rights to create computers must match:
- The organizational unit that's entered in the Domain Join profile.
- If no profile is selected, the computer's domain name for your domain.

1. Open **Active Directory Users and Computers (DSA.msc)**.

1. Right-click the organizational unit that you'll use to create hybrid Azure AD-joined computers, and then select **Delegate Control**.

    ![The Delegate Control command](media/windows-autopilot-hybrid/delegate-control.png)

1. In the **Delegation of Control** wizard, select **Next** > **Add** > **Object Types**.

1. In the **Object Types** pane, select the **Computers** check box, and then select **OK**.

    ![The Object Types pane](media/windows-autopilot-hybrid/object-types-computers.png)

1. In the **Select Users, Computers, or Groups** pane, in the **Enter the object names to select** box, enter the name of the computer where the Connector is installed.

    ![The Select Users, Computers, or Groups pane](media/windows-autopilot-hybrid/enter-object-names.png)

1. Select **Check Names** to validate your entry, select **OK**, and then select **Next**.

1. Select **Create a custom task to delegate** > **Next**.

1. Select the **Only the following objects in the folder** check box, and then select the **Computer objects**, **Create selected objects in this folder**, and **Delete selected objects in this folder** check boxes.

    ![The Active Directory Object Type pane](media/windows-autopilot-hybrid/only-following-objects.png)
    
1. Select **Next**.

1. Under **Permissions**, select the **Full Control** check box.  
    This action selects all the other options.

    ![The Permissions pane](media/windows-autopilot-hybrid/full-control.png)

1. Select **Next**, and then select **Finish**.

## Install the Intune Connector

The Intune Connector for Active Directory must be installed on a computer that's running Windows Server 2016 or later. The computer must also have access to the internet and your Active Directory. To increase scale and availability or to support multiple Active Directory domains, you can install multiple connectors in your environment. We recommend installing the Connector on a server that's not running any other Intune connectors.

1. Make sure that you have a language pack installed and configured as described in [Intune Connector (Preview) language requirements](https://docs.microsoft.com/windows/deployment/windows-autopilot/intune-connector).
2. In [Intune](https://aka.ms/intuneportal), select **Device enrollment** > **Windows enrollment** > **Intune Connector for Active Directory (Preview)** > **Add connector**. 
3. Follow the instructions to download the Connector.
4. Open the downloaded Connector setup file, *ODJConnectorBootstrapper.exe*, to install the Connector.
5. At the end of the setup, select **Configure**.
6. Select **Sign In**.
7. Enter the user Global Administrator or Intune Administrator role credentials.  
   The user account must have an assigned Intune license.
8. Go to **Device enrollment** > **Windows enrollment** > **Intune Connector for Active Directory (Preview)**, and then confirm that the connection status is **Active**.

> [!NOTE]
> After you sign in to the Connector, it might take a couple of minutes to appear in [Intune](https://aka.ms/intuneportal). It appears only if it can successfully communicate with the Intune service.

### Configure web proxy settings

If you have a web proxy in your networking environment, ensure that the Intune Connector for Active Directory works properly by referring to [Work with existing on-premises proxy servers](https://docs.microsoft.com/en-us/intune/windows-autopilot-hybrid-connector-proxy).


## Create a device group
1. In [Intune](https://aka.ms/intuneportal), select **Groups** > **New group**.

1. In the **Group** pane, do the following:

    a. For **Group type**, select **Security**.

    b. Enter a **Group name** and **Group description**.

    c. Select a **Membership type**.

1. If you selected **Dynamic Devices** for the membership type, in the **Group** pane, select **Dynamic device members** and then, in the **Advanced rule** box, do one of the following:
    - To create a group that includes all your Autopilot devices, enter `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`.
    - To create a group that includes all your Autopilot devices with a specific order ID, enter `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`.
    - To create a group that includes all your Autopilot devices with a specific Purchase Order ID, enter `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`.
    
1. Select **Save**.

1. Select **Create**.  

## Register your Autopilot devices

Select one of the following ways to enroll your Autopilot devices.

### Register Autopilot devices that are already enrolled

1. Create an Autopilot deployment profile with **Convert all targeted devices to Autopilot** set to **Yes**. 
2. Assign the profile to a group that contains the members that you want to automatically register with Autopilot.

For more information, see [Create an Autopilot deployment profile](enrollment-autopilot.md#create-an-autopilot-deployment-profile).

### Register Autopilot devices that aren't enrolled

If your devices aren't yet enrolled, you can register them yourself. For more information, see [Add devices](enrollment-autopilot.md#add-devices).

### Register devices from an OEM

If you're buying new devices, some OEMs can register the devices for you. For more information, see the [Windows Autopilot page](http://aka.ms/WindowsAutopilot).

When your Autopilot devices are *registered*, before they're enrolled into Intune, they're displayed in three places (with names set to their serial numbers):
- The **Autopilot Devices** pane in the Intune in the Azure portal. Select **Device enrollment** > **Windows enrollment** > **Devices**.
- The **Azure AD devices** pane in the Intune in the Azure portal. Select **Devices** > **Azure AD Devices**.
- The **Azure AD All Devices** pane in Azure Active Directory in the Azure portal by selecting **Devices** > **All Devices**.

After your Autopilot devices are *enrolled*, they're displayed in four places:
- The **Autopilot Devices** pane in the Intune in the Azure portal. Select **Device enrollment** > **Windows enrollment** > **Devices**.
- The **Azure AD devices** pane in the Intune in the Azure portal. Select **Devices** > **Azure AD Devices**.
- The **Azure AD All Devices** pane in Azure Active Directory in the Azure portal. Select **Devices** > **All Devices**.
- The **All Devices** pane in the Intune in the Azure portal. Select **Devices** > **All Devices**.

After your Autopilot devices are enrolled, their names become the hostname of the device. By default, the hostname begins with *DESKTOP-*.


## Create and assign an Autopilot deployment profile
Autopilot deployment profiles are used to configure the Autopilot devices.

1. In [Intune](https://aka.ms/intuneportal), select **Device enrollment** > **Windows enrollment** > **Deployment Profiles** > **Create Profile**.
1. Type a **Name** and, optionally, a **Description**.
1. For **Deployment mode**, select **User-driven**.
1. In the **Join to Azure AD as** box, select **Hybrid Azure AD joined (Preview)**.
1. Select **Out-of-box experience (OOBE)**, configure the options as needed, and then select **Save**.
1. Select **Create** to create the profile. 
1. In the profile pane, select **Assignments**.
1. Select **Select groups**.
1. In the **Select groups** pane, select the device group, and then click **Select**.

It takes about 15 minutes for the device profile status to change from *Not assigned* to *Assigning* and, finally, to *Assigned*.

## (Optional) Turn on the enrollment status page

1. In [Intune](https://aka.ms/intuneportal), select **Device enrollment** > **Windows enrollment** > **Enrollment Status Page (Preview)**.
1. In the **Enrollment Status Page** pane, select **Default** > **Settings**.
1. In the **Show app and profile installation progress** box, select **Yes**.
1. Configure the other options as needed.
1. Select **Save**.

## Create and assign a Domain Join profile

1. In [Intune](https://aka.ms/intuneportal), select **Device configuration** > **Profiles** > **Create Profile**.
1. Enter the following properties:
   - **Name**: Enter a descriptive name for the new profile.
   - **Description**: Enter a description for the profile.
   - **Platform**: Select **Windows 10 and later**.
   - **Profile type**: Select **Domain Join (Preview)**.
1. Select **Settings**, and then provide a **Computer name prefix**, **Domain name**, and (optional) **Organizational unit** in [DN format](https://docs.microsoft.com/windows/desktop/ad/object-names-and-identities#distinguished-name). 
1. Select **OK** > **Create**.  
    The profile is created and displayed in the list.
1. To assign the profile, follow the steps under [Assign a device profile](device-profile-assign.md#assign-a-device-profile). 

## Next steps

After you configure Windows Autopilot, learn how to manage those devices. For more information, see [What is Microsoft Intune device management?](device-management.md).
