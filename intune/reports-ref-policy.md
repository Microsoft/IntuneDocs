---
# required metadata
title: Reference for Policy entities
titleSuffix: Microsoft Intune 
description: Reference topic for the Policy category of entity collections in the Intune Data Warehouse API.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology:

# optional metadata
#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: seodec18
ms.collection: M365-identity-device-management
---

# Reference for Policy entities

The **Policy** category contains entities for mobile devices that track information such as:

  - Inventory of device configuration profiles, app configuration profiles, and compliance policies  
  - Number of devices in the succeeded, pending, failed, or error state per day  
  - Number of users in the succeeded, pending, failed, or error state per day  
  - Cumulative number of devices in the succeeded, pending, failed, or error state  

## Policy

The **Policy** entity lists device configuration profiles, app configuration profiles, and compliance policies. You can assign the policies with Mobile Device Management (MDM) to a group in your enterprise.

| Property  | Description | Example |
|---------|------------|--------|
| PolicyKey |Unique Key to represent the policy in the data warehouse. |123 |
| PolicyId |Unique identifier of the Policy in the data warehouse. |b66bc706-ffff-7437-0340-032819502773 |
| PolicyName |Name of the Policy. |"Windows 10 Baseline" |
| PolicyVersion |Version of the Policy. When the policy is edited or changed, a newer version is created. |1, 2, 3 |
| IsDeleted |Indicates whether the Policy record has been updated.  <br>True- policy has a new record with updated fields. <br>False- the latest record for the policy. |True/False |
| StartDateInclusiveUTC |Date and time in UTC when the policy was created in the data warehouse. |11/23/2016 12:00:00 AM |
| DeletedDateUTC |Date and time in UTC when IsDeleted changed to True. |11/23/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |Date and time in UTC when the policy was last modified in the data warehouse. |11/23/2016 12:00:00 AM |

## PolicyType

The **PolicyType** entity lists types of device configuration profiles, app configuration profiles, and Compliance policies. You can assign the policies with Mobile Device Management (MDM) to a group in your enterprise.

| Property  | Description | Example |
|---------|------------|--------|
| PolicyTypeId |Unique identifier of the policy in the source system. |123 |
| PolicyTypeKey |Unique identifier of the policy in the data warehouse. |1 |
| PolicyTypeName |Name of the policy type. |Windows 10 Compliance policy. |

## DeviceConfiguration

The **DeviceConfigurationProfileDeviceActivity** entity lists the number of **devices** in the succeeded, pending, failed, or error state per day. The number reflects the Device configuration profiles assigned to the entity. For example, if a **device** is in the succeeded state for all its assigned policies, it increments the succeeded counter up one for that day. If a device has two profiles assigned to it, one in the succeeded state and another in an error state, the entity increments the Succeeded counter and place the device in the error state. The entity lists how many devices are in which state on a given day over the last 30 days.

| Property  | Description | Example |
|---------|------------|--------|
| DateKey |Date Key when the Device Configuration Profile check-in was recorded in the data warehouse. |20160703 |
| Pending |Number of unique Devices in pending state. |123 |
| Succeeded |Number of unique Devices in success state. |12 |
| Error |Number of unique Devices in error state. |10 |
| Failed |Number of unique Devices in failed state. |2 |

The **DeviceConfigurationProfileUserActivity** entity lists the number of **users** in the succeeded, pending, failed, or error state per day. The number reflects the Device configuration profiles assigned to the entity. For example, if a **user** is in the succeeded state for all their assigned policies, it moves up the succeeded counter by one for that day. If a user has two profiles assigned to them, one in the succeeded state and the other is in an error state, the user in the error state is counted.  The **DeviceConfigurationProfileUserActivity** entity lists how many users are in which state on a given day over the last 30 days.

| Property  | Description | Example |
|---------|------------|--------|
| DateKey |Date Key when the Device Configuration Profile check-in was recorded in the data warehouse. |20160703 |
| Pending |Number of unique Users in pending state. |123 |
| Succeeded |Number of unique Users in success state. |12 |
| Error |Number of unique Users in error state. |10 |
| Failed |Number of unique Users in failed state. |2 |

## PolicyTypeActivity

The **PolicyTypeActivity** entity lists the cumulative number of devices in the succeeded, pending, failed, or error state. It lists these states with respect to a device configuration profile, app configuration profile, or compliance policy per day.

| Property  | Description | Example |
|---------|------------|--------|
| DateKey |Date Key when the device Configuration profile check-in was recorded in the data warehouse. |20160703 |
| PolicyKey |Policy Key, can be joined with Policy to get the policyName. |Windows 10 baseline |
| PolicyTypeKey |Type of Policy Key,  can be joined with Policy Type to get the policy type name. |Windows10 Compliance Policy |
| Pending |Number of unique devices in pending state. |123 |
| Succeeded |Number of unique devices in success state. |12 |
| Error |Number of unique devices in error state. |10 |
| Failed |Number of unique devices in failed state. |2 |

## Compliance Policy

The Compliance Policy API Reference contains entities that provide status information about compliance policies assigned to devices.

### CompliancePolicyStatusDeviceActivities

The following table summarizes the assignment status of compliance policies to devices. It lists the count of devices found in each compliance state.


|Property     |Description  |Example  |
|---------|---------|---------|
|DateKey  |Date key when the summary was created for the compliance policy.|20161204 |
|Unknown  |Number of devices that are offline or failed to communicate with Intune or Azure AD for other reasons. |5|
|NotApplicable      |Number of devices where device compliance policies targeted by the admin are not applicable.|201 |
|Compliant      |Number of devices that successfully applied one or more device compliance policies targeted by the admin. |4083 |
|InGracePeriod      |Number of devices that are not compliant but that are in the grace-period defined by the admin. |57|
|NonCompliant      |Number of devices that failed to apply one or more device compliance policies targeted by the admin or where the user hasn't complied with the policies targeted by the admin.|43 |
|Error      |Number of devices that failed to communicate with Intune or Azure AD, and returned an error message. |3|

### CompliancePolicyStatusDevicePerPolicyActivities 

The following table summarizes the assignment status of compliance policies to devices on a per policy and a per policy type basis. It lists the count of devices found in each compliance state for each assigned compliance policy.



|Property  |Description  |Example  |
|---------|---------|---------|
|DateKey  |Date key when the summary was created for the compliance policy.|20161219|
|PolicyKey     |Key for the compliance policy for which the summary was created. |10178 |
|PolicyPlatformKey      |Key for the platform type of the compliance policy for which the summary was created.|5|
|Unknown     |Number of devices that are offline or failed to communicate with Intune or Azure AD for other reasons.|13|
|NotApplicable     |Number of devices where device compliance policies targeted by the admin are not applicable.|3|
|Compliant      |Number of devices that successfully applied one or more device compliance policies targeted by the admin. |45|
|InGracePeriod      |Number of devices that are not compliant but that are in the grace-period defined by the admin. |3|
|NonCompliant      |Number of devices that failed to apply one or more device compliance policies targeted by the admin or where the user hasn't complied with the policies targeted by the admin.|7|
|Error      |Number of devices that failed to communicate with Intune or Azure AD, and returned an error message. |3|

### PolicyPlatformTypes

The following table contains the platform types of all assigned policies. Policies platform types that have never been assigned to any devices are not present in this table.


|Property  |Description  |Example  |
|---------|---------|---------|
|PolicyPlatformTypeKey      |The unique key for the policy platform type. |20170519 |
|PolicyPlatformTypeId      |The unique identifier for the policy platform type.|1|
|PolicyPlatformTypeName      |The name for the policy platform type.|AndroidForWork |

### PolicyDeviceActivity

The following table lists the number of devices in the succeeded, pending, failed, or error state per day. The number reflects the data per Policy Type profiles. For example, if a device is in the succeeded state for all its assigned policies, it increments the succeeded counter up one for that day. If a device has two profiles assigned to it, one in the succeeded state and another in an error state, the entity increments the Succeeded counter and place the device in the error state. The PolicyDeviceActivity entity lists how many devices are in which state on a given day over the last 30 days.

|Property  |Description  |Example  |
|---------|---------|---------|
|DateKey|Date Key when the Device Configuration Profile check-in was recorded in the data warehouse.|20160703|
|Pending|Number of unique Devices in pending state.|123|
|Succeeded|Number of unique Devices in success state.|12|
PolicyKey|Policy Key, can be joined with Policy to get the policyName.|Windows 10 baseline|
|Error|Number of unique Devices in error state.|10|
|Failed|Number of unique Devices in failed state.|2|

### PolicyUserActivity 

The following table lists the number of users in the succeeded, pending, failed, or error state per day. The number reflects the data per Policy Type profiles. For example, if a user is in the succeeded state for all their assigned policies, it moves up the succeeded counter by one for that day. If a user has two profiles assigned to them, one in the succeeded state and the other is in an error state, the user in the error state is counted. The PolicyUserActivity entity lists how many users are in which state on a given day over the last 30 days.


| Property  |                                         Description                                         |       Example       |
|-----------|---------------------------------------------------------------------------------------------|---------------------|
|  DateKey  | Date Key when the Device Configuration Profile check-in was recorded in the data warehouse. |      20160703       |
|  Pending  |                         Number of unique Devices in pending state.                          |         123         |
| Succeeded |                         Number of unique Devices in success state.                          |         12          |
| PolicyKey |                Policy Key, can be joined with Policy to get the policyName.                 | Windows 10 baseline |
|   Error   |                          Number of unique Devices in error state.                           |         10          |
