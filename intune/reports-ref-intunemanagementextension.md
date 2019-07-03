---
# required metadata
title: IntuneManagementExtension Entity
titleSuffix: Microsoft Intune 
description: Reference topic for the IntuneManagementExtension Entity category of entity collections in the Intune Data Warehouse API.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology:
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421

# optional metadata
#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-classic
ms.collection: M365-identity-device-management
---

# Reference for Intune Management Extension

The **IntuneManagementExtension** category contains entities for mobile devices that track information such as:

  - Versions of an IntuneManagementExtension
  - Installation status of an IntuneManagementExtension

## IntuneManagementExtensionVersion

The **IntuneManagementExtensionVersion** entity lists all the versions used by IntuneManagementExtension.

| Property  | Description | Example |
|---------|------------|--------|
| ExtensionVersionKey |Unique identifier of the IntuneManagementExtension version. | 1 |
| ExtensionVersion |The 4 digit version number. |1.0.2.0 |

## IntuneManagementExtensionHealthState

The **IntuneManagementExtensionHealthState** lists all possible health states of the IntuneManagementExtension.

| Property  | Description | Example |
|---------|------------|--------|
| ExtensionStateKey |Unique identifier of health state. | 2 |
| ExtensionState |Health state of a IntuneManagementExtension. | Healthy |

## IntuneManagementExtension

The **IntuneManagementExtension** lists the IntuneManagementExtension health on each Windows 10 device per day.
The data is retained for the last 60 days. 


|      Property       |                         Description                         | Example |
|---------------------|-------------------------------------------------------------|---------|
|       DateKey       |               Unique identifier of the Date.                |   123   |
|      TenantKey      |              Unique identifier of the Tenant.               |   456   |
|      DeviceKey      |              Unique identifier of the Device.               |   789   |
| ExtensionVersionKey | Unique identifier of the IntuneManagementExtension version. |    1    |
|  ExtensionStateKey  |             Unique identifier of health state.              |    2    |
