---
# required metadata

title: Troubleshoot Exchange connectors
titleSuffix: Microsoft Intune
description: Troubleshoot issues related to the Intune on-premises Exchange connector.
keywords:
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/18/2018
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology:
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500

# optional metadata

#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Troubleshoot the Intune on-premises Exchange connector

This article describes how to troubleshoot issues related to the Intune on-premises Exchange connector.

## Steps for checking the connector configuration 

Check the [Intune on-premises Exchange connector setup](exchange-connector-install.md) to make sure the connector is configured correctly. Below are some common issues. After making any corrections, see if the problem is resolved.

- In the Microsoft Intune Exchange Connector dialog box, make sure you've specified a user account that has the appropriate permissions to execute the [required Windows PowerShell Exchange cmdlets](exchange-connector-install.md#exchange-cmdlet-requirements).
- Enable notifications and specify a notification account.
- When configuring the Exchange Connector, specify a Client Access Server (CAS) that is as close as possible to the server hosting the Exchange connector. Communication latency between the CAS and the Exchange connector could delay device discovery, particularly when using Exchange Online Dedicated.
- A user with a newly enrolled device could be delayed in getting access until the Exchange connector synchronizes with the Exchange CAS. A full sync takes place once a day, and a delta (quick) sync occurs several times a day.  You can [manually force a quick sync or full sync](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync) to minimize delays.
 
## Exchange ActiveSync device not discovered from Exchange
[Monitor the Exchange connector activity](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support) to see if the Exchange connector is syncing with the Exchange server. If a full sync or quick sync has completed successfully since the device joined, you can check for other possible issues, listed below. If no sync has taken place, collect the sync logs and attach them to a support request.

- Make sure users have an Intune license, otherwise the Exchange connector won’t discover their devices.
- If a user’s primary SMTP address is different from their UPN in Azure Active Directory (Azure AD), the Exchange Connector will not discover any devices for that user. Fix the primary SMTP address to resolve the issue.
- If you have both Exchange 2010 and Exchange 2013 mailbox servers in your environment, we recommend pointing the Exchange connector to an Exchange 2013 CAS. Otherwise, if the Exchange connector is set up to communicate with an Exchange 2010 CAS, the Exchange connector will not discover any Exchange 2013 users’ devices. 
- For Exchange Online Dedicated environments, you must point the Exchange connector to an Exchange 2013 CAS (not an Exchange 2010 CAS) in the dedicated environment during the initial setup, as the connector will only communicate with this CAS when executing Powershell cmdlets.


## Using Powershell to get more data on Exchange Connector issues
- To get a list of all mobile devices for a mailbox, use `Get-ActiveSyncDeviceStatistics -mailbox mbx`
- To get a list of SMTP addresses for a mailbox, use `Get-Mailbox -Identity user | select emailaddresses | fl`
- To get detailed information about a device's access state, use `Get-CASMailbox <upn> | fl`

## Next steps
If this information doesn't help you, you can also [get support for Microsoft Intune](get-support.md).
