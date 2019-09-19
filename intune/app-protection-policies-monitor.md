---
# required metadata

title: How to monitor app protection policies 
titleSuffix: Microsoft Intune
description: This topic describes how to monitor the compliance status of mobile app management policies in Intune.
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02

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

# How to monitor app protection policies
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

You can monitor the compliance status of the mobile app management (MAM) policies that you've applied to users from the Intune app protection pane in the [Azure portal](https://portal.azure.com). Additionally, you can find information about the users affected by MAM policies, MAM policy compliance status, and any issues that your users might be experiencing.

There are three different places to monitor the compliance status of MAM policies:
- Summary view
- Detailed view
- Reporting view

> [!NOTE]
> For information about creating app protection policies, see [How to create and assign app protection policies](app-protection-policies.md).

The retention period for app protection data is 90 days. Any app instances that have checked in to the MAM service within the past 90 days will be included in the App Protection Status report. An app instance is a unique user + app + device. 

## Summary view

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. On the **Intune** pane, choose **Client apps**.
4. In the **Client apps** workload, choose **App protection status** from the **Monitor** section, to see the summary view:

![Summary tile on the Intune mobile application management pane](./media/app-protection-user-status-summary.png)

- **Assigned users**: The total number of assigned users in your company who are using an app that is associated with a policy in a work context and are protected and licensed, as well as the assigned users that are unprotected and unlicensed.
- **Flagged users**: The number of users who are experiencing issues. Jailbroken (iOS) and rooted (Android) devices are reported under **Flagged users**. Users with devices that are flagged by the Google SafetyNet device attestation check (if turned on by the IT admin) are reported here. 
- **Users with potentially harmful apps**: The number of users who may have a harmful app on their Android device detected by Google Play Protect. 
- **User status for iOS** and **User status for Android**: The number of users who have used an app who have a policy assigned to them in a work context for the related platform. This information shows the number of users managed by the policy, as well as the number of users who are using an app that is not targeted by any policy in a work context. You might consider adding these users to the policy.
- **Top Protected iOS Apps**: Based on the most used iOS apps, this information shows the number of protected and unprotected iOS apps.
- **Top Protected Android Apps**: Based on the most used Android apps, this information shows the number of protected and unprotected Android apps.
- **Top Configured iOS Apps Without Enrollment**: Based on the most used iOS apps for unenrolled devices, this information shows the number of configured iOS apps.
- **Top Configured Android Apps Without Enrollment**: Based on the most used Android apps for unenrolled devices, this information shows the number of configured Android apps.

    > [!NOTE]
    > If you have multiple policies per platform, a user is considered managed by policy when they have at least one policy is assigned to them.

## Detailed view
You can get to the detailed view of the summary by choosing the **User status** tile (based on device OS platform), and the **Flagged users** tile.

### User status
You can search for a single user and check the compliance status for that user. The **App reporting** pane shows the following information for a selected user:
- **Icon**: Displays whether the app status is up to date.
- **App Name**: The name of the app.
- **Device Name**: Devices that are associated with the user's account.
- **Device Type**: The type of device or operating system the device is running.
- **Policies**: The policies associated with the app.
- **Status**:
  - **Checked in**: The policy was deployed to the user, and the app was used in the work context at least once.
  - **Not checked in**: The policy was deployed to the user, but the app has not been used in the work context since then.
- **Last Sync**: When the device was last synced.

>[!NOTE]
> If the users you searched for do not have the MAM policy deployed to them, you see a message informing you that the user is not targeted by any MAM policies.

To see the reporting for a user, follow these steps:

1. To select a user, choose the **User status** summary tile.

    ![Screenshot of the Summary tile of Intune mobile application management](./media/MAM-reporting-6.png)

2. On the **App reporting** pane that opens, choose **Select user** to search for an Azure Active Directory user.

    ![Screenshot of the Select user option on the App reporting pane](./media/MAM-reporting-2.png)

3. Select the user from the list. You can see the details of the compliance status for that user.

### Flagged users
The detailed view shows the error message, the app that was accessed when the error happened, the device OS platform affected, and a time stamp. Users with devices that are flagged by the Google SafetyNet device attestation check are reported here with the reason as reported by Google.

## Reporting view

You can find the same reports at the top of the **App protection status** blade.

> [!NOTE]
> Intune provides additional device reporting fields, including App Registration Id, Android manufacturer, model, and security patch version, as well as iOS model. In Intune, these fields are available by selecting **Client apps** > **App protection status** and choosing **App Protection Report: iOS, Android**. In addition, these parameters will help you configure the **Allow** list for device manufacturer (Android), the **Allow** list for device model (Android and iOS), and the minimum Android security patch version setting. 

Additional reports are available to help you with the MAM policy compliance status. To view these reports, select **Client apps** > **App protection status** > **Reports**. 

The **Reports** blade provides several reports based on user and app, including the following:


- **User report**: This report outlines the same information you can find at the **User status** report under the [Detailed view](app-protection-policies-monitor.md#detailed-view) section above.

- **App report**: In addition to selecting the platform and app, this report provides two different app protection statuses that you can select before generating the report. The statuses can be **Protected** or **Unprotected**.

  - User status for managed MAM activity (**Protected**): This report outlines the activity of each managed MAM app, on a per user basis. It shows all apps targeted by MAM policies for each user, and break down the status of each app as checked in with MAM policies, or that was targeted with a MAM policy but the app was never checked in.
  - User status for unmanaged MAM activity (**Unprotected**): This report outlines the activity of MAM-enabled apps that are currently unmanaged, on a per user basis. This might happen according to the following reasons:
    - These apps are either being used by a user or an app that is not currently targeted by a MAM policy.
    - All apps are checked in, but aren't getting any MAM policies.

    ![Screenshot of a user's App reporting blade with details for 3 apps](./media/MAM-reporting-4.png)

- **User configuration report**: Based on a selected user, this report provides details about any app configurations the user has received.
- **App configuration report**: Base on the selected platform and app, this report provides details about which users have received configurations for the selected app.
- **App learning report for Windows Information Protection**: This report shows which apps are attempting to cross policy boundaries.
- **Website learning for Windows Information Protection**: This report shows which websites are attempting to cross policy boundaries.

## Table grouping

Once the **App protection user report** data is displayed, you can aggregate data by the following:

- **Validation result:** The data shows up grouped by app protection status, which can be failure, warning or success.
- **App name:** The data shows up grouped by apps (the actual app name) with failure, warning, or success.

## Export app protection activities to CSV

You can export all your app protection policy activities to a single *.csv* file. This can be helpful to analyze all the app protection statuses reported from the users.

Follow these steps to generate the App protection report:

1. On the Intune mobile application management pane, choose **App protection report**.

    ![Screenshot of the App protection download link](./media/app-protection-report-csv-2.png)

2. Choose **Yes** to save your report, then choose **Save As** and select the folder you want to save the report in.

    ![Screenshot of the Save report confirmation box](./media/app-protection-report-csv-1.png)

## See also
- [Manage data transfer between iOS apps](data-transfer-between-apps-manage-ios.md)
- [What to expect when your Android app is managed by app protection policies](app-protection-enabled-apps-android.md)
- [What to expect when your iOS app is managed by app protection policies](app-protection-enabled-apps-ios.md)
