---
# required metadata
title: Mobile App Management (MAM)
titleSuffix: Microsoft Intune
description: Reference topic for the Mobile App Management category of entity collections in the Intune Data Warehouse API.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology:
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930

# optional metadata
#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-classic
ms.collection: M365-identity-device-management
---

# Reference for mobile app management (MAM) entities

The **Mobile App Management** category contains entities for mobile apps such as:

  - Apps
  - Instances
  - Check-in status
  - Health status
  - Policy status
  - Enrollment status
  - Platform types

## MamApplication

The **MamApplication** entity lists Line-of-Business (LOB) apps that are managed through Mobile Application Management (MAM) without enrollment in your enterprise.

| Property | Description | Example |
|---------|------------|--------|
| mamApplicationKey |Unique identifier of the MAM application. | 432 |
| mamApplicationName |Name of the MAM application. |MAM Application Example Name |
| mamApplicationId |Application Id of the MAM application. | 123 |
| IsDeleted |Indicates whether this MAM app record has been updated. <br>True- MAM app has a new record with updated fields in this table. <br>False- the latest record for this MAM app. |True/False |
| StartDateInclusiveUTC |Date and time in UTC when this MAM app was created in the data warehouse. |11/23/2016 12:00:00 AM |
| DeletedDateUTC |Date and time in UTC when IsDeleted changed to True. |11/23/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |Date and time in UTC when this MAM app was last modified in the data warehouse. |11/23/2016 12:00:00 AM |


## MamApplicationInstance

The **MamApplicationInstance** entity lists managed Mobile Application Management (MAM) apps as singular instances per user per device. All users and devices listed with in the entity are protected, as in, they have at least one MAM Policy assigned to them.


|          Property          |                                                                                                  Description                                                                                                  |               Example                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   ApplicationInstanceKey   |                                                               Unique identifier of the MAM app instance in the data warehouse - surrogate key.                                                                |                 123                  |
|           UserId           |                                                                              User ID of the user who has this MAM app installed.                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   ApplicationInstanceId    |                                              Unique identifier of the MAM app instance - similar to ApplicationInstanceKey, but the identifier is a natural key.                                              | b66bc706-ffff-7437-0340-032819502773 |
| mamApplicationId | Application Id of the Mam Application for which this Mam Application Instance was created.   | 11/23/2016 12:00:00 AM   |
|     ApplicationVersion     |                                                                                     Application version of this MAM app.                                                                                      |                  2                   |
|        CreatedDate         |                                                                 Date when this record of the MAM app instance was created. Value can be null.                                                                 |        11/23/2016 12:00:00 AM        |
|          Platform          |                                                                          Platform of the device on which this MAM app is installed.                                                                           |                  2                   |
|      PlatformVersion       |                                                                      Platform version of the device on which this MAM app is installed.                                                                       |                 2.2                  |
|         SdkVersion         |                                                                            The MAM SDK version that this MAM app was wrapped with.                                                                            |                 3.2                  |
| mamDeviceId | Device Id of the device with which MAM Application Instance is associated with.   | 11/23/2016 12:00:00 AM   |
| mamDeviceType | Device type of the device with which MAM Application Instance is associated with.   | 11/23/2016 12:00:00 AM   |
| mamDeviceName | Device name of the device with which MAM Application Instance is associated with.   | 11/23/2016 12:00:00 AM   |
|         IsDeleted          | Indicates whether this MAM app instance record has been updated. <br>True- this MAM app instance has a new record with updated fields in this table. <br>False - the latest record for this MAM app instance. |              True/False              |
|   StartDateInclusiveUtc    |                                                              Date and time in UTC when this MAM app instance was created in the data warehouse.                                                               |        11/23/2016 12:00:00 AM        |
|       DeletedDateUtc       |                                                                             Date and time in UTC when IsDeleted changed to True.                                                                              |        11/23/2016 12:00:00 AM        |
| RowLastModifiedDateTimeUtc |                                                           Date and time in UTC when this MAM app instance was last modified in the data warehouse.                                                            |        11/23/2016 12:00:00 AM        |


## MamCheckin

The **MamCheckin** entity represents data gathered when a Mobile Application Management (MAM) app instance has checked in with the Intune Service. 

> [!Note]  
> When an app instance checks in multiple times a day, the data warehouse stores it as single check-in.

| Property | Description | Example |
|---------|------------|--------|
| DateKey |Date Key when the MAM app check-in was recorded in the data warehouse. | 20160703 |
| ApplicationInstanceKey |Key of the app instance associated with this MAM app check-in. | 123 |
| UserKey |Key of the user associated with this MAM app check-in. | 4323 |
| mamApplicationKey |Application Key of Application associated with MAM Application check in. | 432 |
| DeviceHealthKey |Key of DeviceHealth associated with this MAM app check-in. | 321 |
| PlatformKey |Represents the platform of the device associated with this MAM app check-in. |123 |
| EffectiveAppliedPolicyKey |Represents the effective applied policy associated with the MAM app that has checked in. An effective applied policy results from merging all policies relevant to a particular app and user. | 322 |
| LastCheckInDate |Date and time when this MAM app last checked in. Value can be null. |11/23/2016 12:00:00 AM |


## MamDeviceHealth

The **MamDeviceHealth** entity represents devices that have Mobile Application Management (MAM) policies deployed to them even if they are jailbroken.

| Property | Description | Example |
|---------|------------|--------|
| DeviceHealthKey |Unique identifier of the device and its associated health in the data warehouse - surrogate key. |123 |
| DeviceHealth |Unique identifier of the device and its associated health - similar to DeviceHealthKey, but the identifier is a natural key. |b66bc706-ffff-7777-0340-032819502773 |
| DeviceHealthName |Represents the status of the device. <br>Not available - no information on this device. <br>Healthy - device is not jailbroken. <br>Unhealthy - device is jailbroken. |Not Available Healthy Unhealthy |
| RowLastModifiedDateTimeUtc |Date and time in UTC when this specific MAM Device Health was last modified in the data warehouse. |11/23/2016 12:00:00 AM |

## MamEffectivePolicy

The **MamEffectivePolicy** entity lists all Mobile Application Management (MAM) effective policies applied in your organization. An effective applied policy results from merging all policies relevant to a particular app and user.

| Property | Description | Example |
|---------|------------|--------|
| EffectivePolicyKey |Unique identifier of the MAM effective policy in the data warehouse. |2 |
| RealPolicyKey |Unique identifier of the MAM policy authored by the IT Pro. |1 |
| RowCreatedDateTimeUtc |Date and time in UTC when this MAM effective policy was created in the data warehouse. |11/23/2016 12:00:00 AM |

## MamGlobalApplication

The **MamGlobalApplication** entity lists store apps that are managed through Mobile Application Management (MAM) without enrollment in your enterprise.


|          Property          |                                               Description                                               |           Example            |
|----------------------------|---------------------------------------------------------------------------------------------------------|------------------------------|
|       ApplicationKey       |          Unique identifier of the store app in the data warehouse, known as the surrogate key.          |             123              |
|       ApplicationId        | Unique identifier of the store app. The identifier is similar to ApplicationKey, but is a natural key.  | com.microsoft.skydrive.<ios> |
|      ApplicationName       |                                      MAM Global Application Name.                                       |           Skydrive           |
| RowLastModifiedDateTimeUtc | Date and time in UTC when this specific MAM Global Application was last modified in the data warehouse. |    11/23/2016 12:00:00 AM    |

## MamPlatform

The **MamPlatform** entity lists platform names and types on which a Mobile Application Management (MAM) app was installed.


|          Property          |                                    Description                                    |                         Example                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        PlatformKey         |     Unique identifier of the platform in the data warehouse - surrogate key.      |                           123                           |
|          Platform          | Unique identifier of the platform - similar to PlatformKey, but is a natural key. |                           123                           |
|        PlatformName        |                                   Platform name                                   | Not Available <br>None <br>Windows <br>IOS <br>Android. |
| RowLastModifiedDateTimeUtc | Date and time in UTC when this platform was last modified in the data warehouse.  |                 11/23/2016 12:00:00 AM                  |
