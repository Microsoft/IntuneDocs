---
# required metadata

title: Route audit logs in Azure monitor using Microsoft Intune - Azure | Microsoft Docs
description: Use Diagnostics Settings to send audit logs and operational logs in Microsoft Intune to Azure storage account, event hubs, or log analytics. Choose how long you want to keep the data, and see some estimated costs for different size tenants.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Send log data to storage, event hubs, or log analytics in Intune (preview)

Microsoft Intune includes built-in logs that provide information about your environment. **Audit Logs** show details on different events or tasks that happen in Intune. **Operational Logs (preview)** show details on users and devices that successfully (or failed) to enroll, as well as details on non-compliant devices.

These logs can also be sent to Azure Monitor services, including storage accounts, event hubs, and log analytics. Specifically, you can:

* Archive Intune logs to an Azure storage account to keep the data, or archive for a set time.
* Stream Intune logs to an Azure event hub for analytics using popular Security Information and Event Management (SIEM) tools, such as Splunk and QRadar.
* Integrate Intune logs with your own custom log solutions by streaming them to an event hub.
* Send Intune logs to Log Analytics to enable rich visualizations, monitoring, and alerting on the connected data.

These features are part of the **Diagnostics Settings** in Intune.

This article shows you how to use **Diagnostics Settings** to send log data to different services, gives examples and estimates of costs, and answers some common questions.

## Prerequisites

To use this feature, you need:

* An Azure subscription: If you don't have an Azure subscription, you can [sign up for a free trial](https://azure.microsoft.com/free/).
* A Microsoft Intune environment (tenant) in Azure
* A user who's a **Global Administrator** or **Intune Service Administrator** for the Intune tenant.

Depending on where you want to route the audit log data, you need one of the following services:

* An [Azure storage account](https://docs.microsoft.com/azure/storage/common/storage-account-overview) with *ListKeys* permissions. We recommend that you use a general storage account, and not a blob storage account. For storage pricing information, see the [Azure Storage pricing calculator](https://azure.microsoft.com/pricing/calculator/?service=storage). 
* An [Azure event hubs namespace](https://docs.microsoft.com/azure/event-hubs/event-hubs-create#create-an-event-hubs-namespace) to integrate with third-party solutions.
* An [Azure log analytics workspace](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) to send logs to Log Analytics.

## Send logs to Azure monitor

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Under **Monitoring**, select **Diagnostics settings**. The first time you open it, turn it on:

    ![Turn on Diagnostics settings in Intune to send logs to Azure Monitor](media/diagnostics-settings-turn-on.png)

3. Enter the following properties:

    - **Name**: Enter a name for the diagnostic settings. This setting includes all the properties you enter. For example, enter `Route audit logs to storage account`.
    - **Archive to a storage account**: Saves the log data to an Azure storage account. Use this option if you want to save or archive the data.

        1. Select this option > **Configure**. 
        2. Choose an existing storage account from the list > **OK**.

    - **Stream to an event hub**: Streams the logs to an Azure event hub. If you want analytics on your log data using SIEM tools, such as Splunk and QRadar, choose this option.

        1. Select this option > **Configure**. 
        2. Choose an existing event hub namespace and policy from the list > **OK**.

    - **Send to Log Analytics**: Sends the data to Azure log analytics. If you want to use visualizations, monitoring and alerting for your logs, choose this option.

        1. Select this option > **Configure**. 
        2. Create a new workspace, and enter the workspace details. Or, choose an existing workspace from the list > **OK**.

            [Azure log analytics workspace](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) provides more details on these settings.

    - **LOG** > **AuditLogs**: Choose this option to send the [Intune audit logs](monitor-audit-logs.md) to your storage account, event hub, or log analytics. The audit logs show the history of every task that generates a change in Intune, including who did it and when.

      If you choose to use a storage account, then also enter how many days you want to keep the data (retention). To keep data forever, set **Retention (days)** to `0` (zero).

    - **LOG** > **OperationalLogs**: Operational logs (preview) show the success or failure of users and devices that enroll in Intune, as well as details on non-compliant devices. Choose this option to send the enrollment logs to your storage account, event hub, or log analytics.

      If you choose to use a storage account, then also enter how many days you want to keep the data (retention). To keep data forever, set **Retention (days)** to `0` (zero).

      > [!NOTE]
      > Operational logs are in preview. To provide feedback, including information included in the operational logs, go to [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback) (opens a new website).

    When finished, your settings look similar to the following settings: 

    ![Sample image that sends Intune audit logs to an Azure storage account](media/diagnostics-settings-example.png)

4. **Save** your changes. Your setting is shown in the list. Once it's created, you can change the settings by selecting **Edit setting** > **Save**.

## Use audit logs throughout Intune

You can also export the audit logs in other parts of Intune, including enrollment, compliance, configuration, devices, client apps, and more.

For example, to export the audit logs when using device compliance:

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Select **Device compliance** > **Monitor** > **Audit logs**:

    ![Choose audit logs to route Intune data to Azure Monitor storage, events hubs, or analytics](media/audit-logs-under-monitor-in-compliance.png)

3. Select **Export Data Settings**. If it isn't enabled, you can turn on **Diagnostics settings**. You can also choose where to send the logs, as described in [send logs to Azure monitor](#send-logs-to-azure-monitor) (in this article).

## Cost considerations

If you already have a Microsoft Intune license, you need an Azure subscription to set up the storage account and event hub. The Azure subscription is typically free. But, you do pay to use Azure resources, including the storage account for archival and the event hub for streaming. The amount of data and the costs vary depending on the tenant size.

### Storage size for activity logs

Every audit log event uses about 2 KB of data storage. For a tenant with 100,000 users, you may have about 1.5 million events per day. You may need about 3 GB of data storage per day. Because writes typically happen in five-minute batches, you can expect approximately 9,000 write operations per month.

The following tables show a cost estimate depending on the size of the tenant. It also includes a general-purpose v2 storage account in West US for at least one year of data retention. To get an estimate for the data volume that you expect for your logs, use the [Azure storage pricing calculator](https://azure.microsoft.com/pricing/details/storage/blobs/).

**Audit log with 100,000 users**

| | |
|---|---|
|Events per day| 1.5 million|
|Estimated volume of data per month| 90 GB|
|Estimated cost per month (USD)| $1.93|
|Estimated cost per year (USD)| $23.12|

**Audit log with 1,000 users**

| | |
|---|---|
|Events per day| 15,000|
|Estimated volume of data per month| 900 MB|
|Estimated cost per month (USD)| $0.02|
|Estimated cost per year (USD)| $0.24|

### Event hub messages for activity logs

Events are typically batched in five-minute intervals, and sent as a single message with all the events within that timeframe. A message in the event hub has a maximum size of 256 KB. If the total size of all the messages within the timeframe exceed that volume, then multiple messages are sent.

For example, about 18 events per second typically happen for a large tenant of more than 100,000 users. This equates to 5,400 events every five minutes (300 seconds x 18 events). Audit logs are about 2 KB per event. This equates to 10.8 MB of data. So, 43 messages are sent to the event hub in that five-minute interval.

The following table contains estimated costs per month for a basic event hub in West US, depending on the volume of event data. To get an estimate of the data volume that you expect for your logs, use the [Event Hubs pricing calculator](https://azure.microsoft.com/pricing/details/event-hubs/).

**Audit log with 100,000 users**

| | |
|---|---|
|Events per second| 18|
|Events per five-minute interval| 5,400|
|Volume per interval| 10.8 MB|
|Messages per interval| 43|
|Messages per month| 371,520|
|Estimated cost per month (USD)| $10.83|

**Audit log with 1,000 users**

| | |
|---|---|
|Events per second|0.1 |
|Events per five-minute interval| 52|
|Volume per interval|104 KB |
|Messages per interval|1 |
|Messages per month|8,640 |
|Estimated cost per month (USD)|$10.80 |

### Log Analytics cost considerations

To review costs related to managing the Log Analytics workspace, see [Manage cost by controlling data volume and retention in Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-cost-storage).

## Frequently asked questions

Get answers to frequently asked questions, and read about any known issues with Intune logs in Azure Monitor.

### Which logs are included?

Audit logs and operational (preview) logs are both available for routing using this feature.

### After an action, when do the corresponding logs show up in the event hub?

The logs typically show up in your event hub within several minutes after the action is performed. [What is Azure Event Hubs?](https://docs.microsoft.com/azure/event-hubs/) provides more information.

### After an action, when do the corresponding logs show up in the storage account?

For Azure storage accounts, the latency is anywhere from 5 to 15 minutes after the action runs.

### What happens if an Administrator changes the retention period of a diagnostic setting?

The new retention policy is applied to logs collected after the change. Logs collected before the policy change are unaffected.

### How much does it cost to store my data?

The storage costs depend on the size of your logs and the retention period you choose. For a list of the estimated costs for tenants, which depend on the log volume generated, see the [Storage size for activity logs](#storage-size-for-activity-logs) (in this article).

### How much does it cost to stream my data to an event hub?

The streaming costs depend on the number of messages you receive per minute. For details on how costs are calculated and cost estimates based on the number of messages, see [Event hub messages for activity logs](#event-hub-messages-for-activity-logs) (in this article).

### How do I integrate Intune audit logs with my SIEM system?

Use Azure Monitor with Event Hubs to stream logs to your SIEM system. First, [stream the logs to an event hub](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub). Then, [set up your SIEM tool](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub#access-data-from-your-event-hub) with the configured event hub. 

### What SIEM tools are currently supported?

Currently, Azure Monitor is supported by [Splunk](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-integrate-activity-logs-with-splunk), QRadar, and [Sumo Logic](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory) (opens a new website). For more information about how the connectors work, see [Stream Azure monitoring data to an event hub for consumption by an external tool](https://docs.microsoft.com/azure/azure-monitor/platform/stream-monitoring-data-event-hubs).

### Can I access the data from an event hub without using an external SIEM tool?

Yes. To access the logs from your custom application, you can use the [Event Hubs API](https://docs.microsoft.com/azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph).

### What data is stored?

Intune doesn't store any data sent through the pipeline. Intune routes data to the Azure Monitor pipeline, at the authority of the tenant. For more information, see [Azure Monitor overview](https://docs.microsoft.com/azure/azure-monitor/overview).

## Next steps

* [Archive activity logs to a storage account](https://docs.microsoft.com/azure/active-directory/reports-monitoring/quickstart-azure-monitor-route-logs-to-storage-account)
* [Route activity logs to an event hub](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub)
* [Integrate activity logs with Log Analytics](https://docs.microsoft.com/azure/active-directory/reports-monitoring/howto-integrate-activity-logs-with-log-analytics)
