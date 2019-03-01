---
# required metadata

title: Set up Microsoft Intune on-premises Exchange connector | Microsoft Intune
description: Use the on-premises Exchange connector to manage device access to Exchange mailboxes based on Intune enrollment and Exchange Active Sync (EAS).
keywords:
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Set up the Intune on-premises Exchange connector in Microsoft Intune Azure

In an on-premises Exchange Server environment, Intune conditional access can be used to allow or block access to Exchange on-premises mailboxes. Use Exchange Active Sync on-premises connectors to connect Intune to your Exchange organizations, and set up Intune conditional access along with device compliance policies. Then, when a device tries to connect to Exchange, Intune determines if the device is enrolled in Intune and is compliant. To determine which devices are enrolled in Intune, the on-premises Exchange connector maps Exchange Active Sync (EAS) records in Exchange Server to Intune records. For more about how this works, see [What are common ways to use conditional access with Intune?](conditional-access-intune-common-ways-use.md)

> [!IMPORTANT]
> Intune now supports multiple on-premises Exchange connectors per subscription. If you have more than one on-premises Exchange organization, you can set up a separate connector for each Exchange organization.

To set up a connection that enables Microsoft Intune to communicate with the on-premises Exchange Server, here are the general steps:

1. Download the Intune on-premises Exchange connector from the Azure portal.
2. Install and configure the Exchange connector on a computer in the on-premises Exchange organization.
3. Validate the Exchange connection.
4. Repeat these steps for each Exchange organization you want to connect to Intune.

## Intune on-premises Exchange connector requirements
The following table lists the requirements for the computer on which you install the on-premises Exchange connector.


|            Requirement             |                                                                                                                                                                                                        More information                                                                                                                                                                                                        |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Operating systems          |                                                               Intune supports the on-premises Exchange connector on a computer that runs any edition of Windows Server 2008 SP2 64-bit, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2, or Windows Server 2016.<br /><br />The connector isn't supported on any Server Core installation.                                                                |
|         Microsoft Exchange         |                                                                           On-premises connectors require Microsoft Exchange 2010 SP3 or later or legacy Exchange Online Dedicated. To determine if your Exchange Online Dedicated environment is in the <strong>new</strong> or <strong>legacy</strong> configuration, contact your account manager.                                                                           |
| Mobile device management authority |                                                                                                                              [Set the mobile device management authority to Intune](mdm-authority-set.md).                                                                                                                               |
|              Hardware              |                                                                                                                                                     The computer on which you install the connector requires a 1.6 GHz CPU with 2 GB of RAM and 10 GB of free disk space.                                                                                                                                                      |
|  Active Directory synchronization  |                                                                                      Before you can use the connector to connect Intune to your Exchange Server, you must [set up Active Directory synchronization](users-add.md) so that your local users and security groups are synchronized with your instance of Azure Active Directory.                                                                                      |
|        Additional software         |                                                                                                                                           A full installation of Microsoft .NET Framework 4.5 and Windows PowerShell 2.0 must be installed on the computer that hosts the connector.                                                                                                                                           |
|              Network               | The computer on which you install the connector must be in a domain that has a trust relationship to the domain that hosts your Exchange Server.<br /><br />The computer requires configurations to enable it to access the Intune service through firewalls and proxy servers over Ports 80 and 443. Domains that are used by Intune include manage.microsoft.com, &#42;manage.microsoft.com, and &#42;.manage.microsoft.com. |

The account used to connect to Intune must have an assigned Intune license, e.g. EMS E3 or E5. 

### Exchange cmdlet requirements

You must create an Active Directory user account that is used by the on-premises Exchange connector. The account must have permission to run the following required Windows PowerShell Exchange cmdlets:


 -   Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 -   Get-CasMailbox, Set-CasMailbox
 -   Get-ActiveSyncMailboxPolicy, Set-ActiveSyncMailboxPolicy, New-ActiveSyncMailboxPolicy, Remove-ActiveSyncMailboxPolicy
 -   Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 -   Get-ActiveSyncDeviceStatistics
 -   Get-ActiveSyncDevice
 -   Get-ExchangeServer
 -   Get-ActiveSyncDeviceClass
 -   Get-Recipient
 -   Clear-ActiveSyncDevice, Remove-ActiveSyncDevice
 -   Set-ADServerSettings
 -   Get-Command

## Download the on-premises Exchange connector software installation package

1. On a supported Windows Server operating system for the on-premises Exchange connector, open the [Azure portal](https://portal.azure.com) and sign in with a user account that is an administrator in the on-premises Exchange server, and that has a license to use Exchange Server.

2. Go to **Intune** > **Exchange access**  

3. Under **Setup**, choose **Exchange ActiveSync on-premises connector**, and then select **Add**.

4. On the **Add Connector** page, select **Download the on-premises connector**. The on-premises Exchange connector is in a compressed (.zip) folder that can be opened or saved. In the **File Download** dialog box, choose **Save** to store the compressed folder to a secure location.

	> [!IMPORTANT]
	> Do not rename or move the files that are in the on-premises Exchange connector folder. Moving or renaming the folder's contents will cause the Exchange connector installation to fail.

## Install and configure the Intune on-premises Exchange connector
Perform the following steps to install the Intune on-premises Exchange connector. If you have multiple Exchange organizations, repeat these steps for each additional Exchange connector you want to set up.

1. On a supported operating system for the on-premises Exchange connector, extract the files in **Exchange_Connector_Setup.zip** to a secure location.

2. After the files are extracted, open the extracted folder and double-click **Exchange_Connector_Setup.exe** to install the on-premises Exchange connector.

   > [!IMPORTANT]
   > If the destination folder is not a secure location, you should delete the certificate file **MicrosoftIntune.accountcert** when you are finished installing your on-premises connectors.

3. In the **Microsoft Intune Exchange Connector** dialog box, select either **On-premises Microsoft Exchange Server** or **Hosted Microsoft Exchange Server**.

   ![Image showing where to choose your Exchange Server type](./media/intune-sa-exchange-connector-config.png)

   For an on-premises Exchange server, provide either the server name or the fully qualified domain name of the Exchange server that hosts the **Client Access Server** role.

   For a hosted Exchange server, provide the Exchange server address. To find the hosted Exchange server URL:

   1. Open Outlook on the web for Office 365.

   2. Choose the **?** icon at the upper left, and then select **About**.

   3. Locate the **POP External Server** value.

   4. Choose **Proxy Server** to specify proxy server settings for your hosted Exchange server.
       1. Select **Use a proxy server when synchronizing mobile device information**.

       2. Enter the **proxy server name** and the **port number** to be used to access the server.

       3. If it's necessary to provide user credentials to access the proxy server, select **Use credentials to connect to the proxy server**. Then enter the **domain\user** and the **password**.

       4. Choose **OK**.

4. In the **User (Domain\user)** and **Password** fields, enter the credentials that are necessary to connect to your Exchange server.

5. Provide the necessary credentials to send notifications to a user’s Exchange Server mailbox. This user can be dedicated to just notifications. The notifications user needs an Exchange mailbox to be able to send notifications by email. You can configure these notifications with conditional access policies in Intune.  

       Ensure that the Autodiscover service and Exchange Web Services are configured on the Exchange Client Access Server. For more information, see [Client Access server](https://technet.microsoft.com/library/dd298114.aspx).

6. In the **Password** field, provide the password for this account to enable Intune to access the Exchange Server.

7. Choose **Connect**.

   > [!NOTE]
   > It might take a few minutes for the connection to be configured.

During configuration, the Exchange connector stores your proxy settings to enable access to the Internet. If your proxy settings change, you'll have to reconfigure the Exchange connector to apply the updated proxy settings to the Exchange connector.

After the Exchange connector sets up the connection, mobile devices that are associated with users that are managed in Exchange are automatically synchronized and added to the Exchange connector. This synchronization might take some time to complete.

> [!NOTE]
> If you have installed the on-premises Exchange connector, and if at some point you delete the Exchange connection, you must uninstall the on-premises Exchange connector from the computer onto which it was installed.

## Install connectors for multiple Exchange organizations
Intune supports multiple on-premises Exchange connectors per subscription. For a tenant with multiple Exchange organizations, you can set up one connector for each Exchange organization. Download the .zip folder once, and then for each Exchange organization, follow the steps in the previous section to extract and run the setup program on a server in the organization.

The high availability, monitoring, and manual sync features described in the following sections are supported for each Exchange organization connected to Intune.

## On-premises Exchange connector high availability support 
After the Exchange connector creates a connection to Exchange using the specified CAS, the connector can discover other CASs. If the primary CAS becomes unavailable, the connector will failover to another CAS, if available, until the primary CAS becomes available. This feature is on by default. You can turn off this feature by using the following procedure:
1. On the server where the Exchange Connector is installed, go to %*ProgramData*%\Microsoft\Windows Intune Exchange Connector. 
2. Using a text editor, open **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Change &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; to &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt; to disable the feature.    


## Monitor the Exchange connector activity

After you have successfully configured Exchange connectors, you can view the status of the connections and the last successful synchronization attempt. To validate the Exchange connector connections:

1. On the Intune Dashboard, choose **Exchange access**.
2. Under **Setup**, select **Exchange online connector** to verify the connection status for each Exchange connector.

You can also check the time and date of the last successful synchronization attempt.

### System Center Operations Manager management pack

Beginning with the Intune 1710 release, you can use the [Operations Manager management pack for Exchange connector and Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True). This gives you different ways of monitoring the Exchange connector when you need to troubleshoot issues.

## Manually force a quick sync or full sync
An on-premises Exchange connector automatically synchronizes EAS and Intune device records regularly. If the compliance status of a device changes, the automatic sync process regularly updates records so that device access can be blocked or allowed accordingly.

   - **Quick sync** occurs regularly, several times a day. A quick sync retrieves device information for Intune-licensed and on-premises Exchange conditional access-targeted users that have changed since the last sync.

   - **Full sync** occurs once per day by default. A full sync retrieves device information for all Intune-licensed and on-premises Exchange conditional access-targeted users. A full sync also retrieves Exchange server information and ensures that the configuration specified by Intune in the Azure portal is updated on the Exchange server. 

You can force a connector to run a sync by using the **Quick Sync** or **Full Sync** options on the Intune dashboard with the following steps:

   1. On the Intune dashboard, choose **Exchange access**.
   2. Under **Setup**, choose **Exchange online connector**.
   3. Select the connector you want to sync, and then choose **Quick Sync** or **Full Sync**.

## Next steps
[Create a conditional access policy for Exchange on-premises](conditional-access-exchange-create.md)
