---
# required metadata
title: Reference for Application entities
titleSuffix: Microsoft Intune
description: Reference topic for the Application category of entity collections in the Intune Data Warehouse API.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology:
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68

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

# Reference for application entities

The **Application** category contains entities for mobile devices that track information such as:

- Versions of an app
- Installation source of an app
- Type of developers who created an app
- Managed software types for an app, for example **sidecar** or **desktop**
- Volume Purchasing Program (VPP) state of an app

## AppRevision

The **AppRevision** entity lists all the versions of apps.

| Property  | Description | Example |
|---------|------------|--------|
| AppKey |Unique identifier of the App. |123 |
| ApplicationId |Unique identifier of the App - similar to AppKey, but this key is a natural. |b66bc706-ffff-7437-0340-032819502773 |
| Revision |The version as mentioned by admin during uploading of the binary. |2 |
| Title |Title of the app. |Excel |
| Publisher |Publisher of the app. |Microsoft |
| UploadState |Upload state of the app. |1 |
| AppTypeKey |Reference to AppType described in the following section. | |
| VppProgramTypeKey |Reference to VppProgramType described below. | |
| CreationTime |The time when this revision was created. |11/23/2016 12:00:00 AM |
| ModifiedTime |Last time anything related to this revision was changed. |11/23/2016 12:00:00 AM |
| Size |Size of the binary. | |
| StartDateInclusiveUTC |Date and time in UTC when this App revision was created in the data warehouse. |11/23/2016 12:00:00 AM |
| EndDateExclusiveUTC |Date and time in UTC when this app revision became obsolete. |11/23/2016 12:00:00 AM |
| IsCurrent |Indicates whether this App version is current or not in the data warehouse. |True/False |
| RowLastModifiedDateTimeUTC |Date and time in UTC when this app version was last modified in the data warehouse. |11/23/2016 12:00:00 AM |

## AppTypes

The **AppTypes** entity lists the installation source of an app.

| Property  | Description |
|---------|------------|
| AppTypeID |ID for the type |
| AppTypeKey |Surrogate key for the key |
| AppTypeName |App type |

### Example

| AppTypeID  | Name | Description |
|---------|------------|--------|
| 0 |Android store app | An Android store app. |
| 1 |Android LOB app | An Android line-of-business app. |
| 2 |Managed Android store app (MAM) | An Android store app that has management enabled. |
| 3 |iOS store app | An iOS store app. |
| 4 |iOS LOB app | An iOS line-of-business app. |
| 5 |Managed iOS store app (MAM?) | An iOSstore app that is management enabled. |
| 6 |O365 Pro Plus Suite | The Office 365 Pro Plus Suite for Windows 10. |
| 7 |Web app | A web app. |
| 8 |Windows Phone 8.1 store app | A Windows phone 8.1 store app. |
| 9 |Windows store app | A Windows store app. |
| 10 |Windows LOB apps | A Windows AppX line-of-business app. |
| 11 |Windows Mobile MSI | An MSI line-of-business app. |
| 12 |Windows Phone LOB app | A Windows phone line-of-business app. |

## VppProgramTypes

The **VppProgramTypes** entity lists possible VPP program types for an app.

| Property  | Description |
|---------|------------|
| VppProgramTypeID | ID for the type. |
| VppProgramTypeKey | Surrogate key for the key. |
| VppProgramTypeName | VPP Program type. |

### Example

| VppProgramID  | Name | Description |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | Microsoft's VPP program. |
| 00000000-0000-0000-0000-000000000000 | Not Yet Available | Default value, No VPP. |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | Apple's VPP program. |

## ApplicationInventory

The **ApplicationInventory** entity lists the applications found on the device at the time of inventory collection.

| Property  | Description |
|---------|------------|
| DeviceKey | This is a reference to the Device table which contains the Intune device ID. |
| DateKey | Reference to date table indicating the day of inventory. |
| ApplicationName | The application name. |
| ApplicationVersion | Version of the application. |
| BundleSize | The size of the app in bytes. |

## MobileAppInstallState

The **MobileAppInstallState** entity represents the install state for a mobile application after it has been assigned to a group containing devices, users or both.

| Property | Description |
|---|---|
| AppInstallStateKey | The unique ID of the app install state for your account. |
| AppInstallState | Enum value of the app install state. |
| AppInstallStateName | Name of the app install state. |
