---
# required metadata
title: Devices - Intune Data Warehouse
titleSuffix: Microsoft Intune
description: Reference topic for the Devices category of entity collections in the Intune Data Warehouse API.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology:
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F

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

# Reference for devices entities

The **Devices** category contains entities for mobile devices that track information such as:

  - Device type
  - Device enrollment and registration status
  - Device ownership
  - Device management state
  - Device membership to Azure AD status
  - Enrollment status
  - Historic information about the device
  - Inventory of apps on the device

## DeviceTypes

The **DeviceTypes** entity represents the device type referenced by other data warehouse entities. The device type typically describes either the device model, manufacturer, or a combination of both.

| Property  | Description |
|---------|------------|
| DeviceTypeID |Unique identifier of the device type |
| DeviceTypeKey |Unique identifier of the device type in the data warehouse - surrogate key |
| DeviceTypeName |Device type |

### Example

| deviceTypeID  | Name | Description |
|---------|------------|--------|
| 0 |Desktop |Windows Desktop device |
| 1 |WindowsRT |WindowsRT device |
| 2 |WinMO6 |Windows Mobile 6.0 device |
| 3 |Nokia |Nokia device |
| 4 |WindowsPhone |Windows Phone device |
| 5 |Mac |Mac device |
| 6 |WinCE |Windows CE device |
| 7 |WinEmbedded |Windows Embedded device |
| 8 |IPhone |iPhone device |
| 9 |IPad |iPad device |
| 10 |IPod |iPod device |
| 11 |Android |Android device-managed using Device Administrator |
| 12 |ISocConsumer |iSoc Consumer device |
| 14 |MacMDM |Mac OS X device managed with the built-in MDM agent |
| 15 |HoloLens |HoloLens device |
| 16 |SurfaceHub |Surface Hub device |
| 17 |AndroidForWork |Android device-managed using Android Profile Owner |
| 100 |Blackberry |Blackberry Device |
| 101 |Palm |Palm device |
| 255 |Unknown |Unknown device type |

## enrollmentActivities 
The **EnrollmentActivity** entity indicates the activity of a device enrollment.

| Property                      | Description                                                               |
|-------------------------------|---------------------------------------------------------------------------|
| dateKey                       | Key of the date when this enrollment activity was recorded.               |
| deviceEnrollmentTypeKey       | Key of the type of the enrollment.                                        |
| deviceTypeKey                 | Key of the type of device.                                                |
| enrollmentEventStatusKey      | Key of the status indicating the success or failure of the enrollment.    |
| enrollmentFailureCategoryKey  | Key of the enrollment failure category (if the enrollment failed).        |
| enrollmentFailureReasonKey    | Key of the enrollment failure reason (if the enrollment failed).          |
| osVersion                     | The operating system version of the device.                               |
| count                         | Total count of enrollment activities matching the classifications above.  |

## enrollmentEventStatuses 
The **EnrollmentEventStatus** entity indicates the result of a device enrollment.

| Property                   | Description                                                                       |
|----------------------------|-----------------------------------------------------------------------------------|
| enrollmentEventStatusKey   | Unique identifier of the enrollment status in the data warehouse (surrogate key)  |
| enrollmentEventStatusName  | The name of the enrollment status. See examples below.                            |

### Example

| enrollmentEventStatusName  | Description                            |
|----------------------------|----------------------------------------|
| Success                    | A successful device enrollment         |
| Failed                     | A failed device enrollment             |
| Not Available              | The enrollment status is unavailable.  |

## enrollmentFailureCategories 
The **EnrollmentFailureCategory** entity indicates why a device enrollment failed. 

| Property                       | Description                                                                                 |
|--------------------------------|---------------------------------------------------------------------------------------------|
| enrollmentFailureCategoryKey   | Unique identifier of the enrollment failure category in the data warehouse (surrogate key)  |
| enrollmentFailureCategoryName  | The name of the enrollment failure category. See examples below.                            |

### Example

| enrollmentFailureCategoryName   | Description                                                                                                   |
|---------------------------------|---------------------------------------------------------------------------------------------------------------|
| Not Applicable                  | The enrollment failure category is not applicable.                                                            |
| Not Available                   | The enrollment failure category is not available.                                                             |
| Unknown                         | Unknown error.                                                                                                |
| Authentication                  | Authentication failed.                                                                                        |
| Authorization                   | Call was authenticated, but not authorized to enroll.                                                         |
| AccountValidation               | Failed to validate the account for enrollment. (Account blocked, enrollment not enabled)                      |
| UserValidation                  | User could not be validated. (User does not exist, missing license)                                           |
| DeviceNotSupported              | Device is not supported for mobile device management.                                                         |
| InMaintenance                   | Account is in maintenance.                                                                                    |
| BadRequest                      | Client sent a request that is not understood/supported by the service.                                        |
| FeatureNotSupported             | Feature(s) used by this enrollment are not supported for this account.                                        |
| EnrollmentRestrictionsEnforced  | Enrollment restrictions configured by admin blocked this enrollment.                                          |
| ClientDisconnected              | Client timed out or enrollment was aborted by end user.                                                        |
| UserAbandonment                 | Enrollment was abandoned by end user. (End user started onboarding but failed to complete it in timely manner)  |

## enrollmentFailureReasons  
The **EnrollmentFailureReason** entity indicates a more detailed reason for a device enrollment failure within a given failure category.  

| Property                     | Description                                                                               |
|------------------------------|-------------------------------------------------------------------------------------------|
| enrollmentFailureReasonKey   | Unique identifier of the enrollment failure reason in the data warehouse (surrogate key)  |
| enrollmentFailureReasonName  | The name of the enrollment failure reason. See examples below.                            |

### Example

| enrollmentFailureReasonName      | Description                                                                                                                                                                                            |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Not Applicable                   | The enrollment failure reason is not applicable.                                                                                                                                                       |
| Not Available                    | The enrollment failure reason is not available.                                                                                                                                                        |
| Unknown                          | Unknown Error.                                                                                                                                                                                         |
| UserNotLicensed                  | The user was not found in Intune or does not have a valid license.                                                                                                                                     |
| UserUnknown                      | User is not known to Intune.                                                                                                                                                                           |
| BulkAlreadyEnrolledDevice        | Only one user can enroll a device. This device was previously enrolled by another user.                                                                                                                |
| EnrollmentOnboardingIssue        | Intune mobile device management (MDM) authority is not configured yet.                                                                                                                                 |
| AppleChallengeIssue              | The iOS management profile installation was delayed or failed.                                                                                                                                         |
| AppleOnboardingIssue             | An Apple MDM push certificate is required to enroll into Intune.                                                                                                                                       |
| DeviceCap                        | The user attempted to enroll more devices than maximum allowed.                                                                                                                                        |
| AuthenticationRequirementNotMet  | Intune enrollment service failed to authorize this request.                                                                                                                                            |
| UnsupportedDeviceType            | This device does not meet minimum requirements for Intune enrollment.                                                                                                                                  |
| EnrollmentCriteriaNotMet         | This device failed to enroll due to a configured enrollment restriction rule.                                                                                                                          |
| BulkDeviceNotPreregistered       | This device’s international mobile equipment identifier (IMEI) or serial number wasn’t found.  Without this identifier, devices are recognized as personal-owned devices which are currently blocked.  |
| FeatureNotSupported              | The user was attempting to access a feature that is not yet released for all customers or is not compatible with your Intune configuration.                                                            |
| UserAbandonment                  | Enrollment was abandoned by end user. (End user started onboarding but failed to complete it in timely manner)                                                                                           |
| APNSCertificateExpired           | Apple devices cannot be managed with an expired Apple MDM push certificate.                                                                                                                            |
## OwnerTypes

The **EnrollmentTypes** entity indicates whether a device is corporate, personally owned, or unknown.

| Property  | Description | Example |
|---------|------------|--------|
| ownerTypeID |Unique identifier of the owner type. | |
| ownerTypeKey |Unique identifier of the owner type in the data warehouse - surrogate key. | |
| ownerTypeName |Represents the owner type of the devices:  <br>Corporate - device is enterprise owned. <br>Personal - device is personally owned (BYOD).  <br>Unknown - no information on this device. |Corporate Personal Unknown |

> [!Note]  
> For the `ownerTypeName` in AzureAD when creating Dynamic Groups for devices, you need to set the filter value `deviceOwnership` as `Company`. For more information, see [Rules for devices](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices). 

## ManagementStates

The **ManagementStates** entity provides details on the state of the device. Detail can be useful in the cases where remote actions are applied, the device is jailbroken, or rooted.

| Property  | Description |
|---------|------------|
| managementStateID | Unique identifier of the management state. |
| managementStateKey | Unique identifier of the management state in the data warehouse - surrogate key. |
| managementStateName | Indicates the state of the remote action applied to this device. |

### Example

| managementStateID  | Name | Description |
|---------|------------|--------|
| 0 |Managed | Managed with no pending remote actions. |
| 1 |RetirePending | There is a retire command pending for the device. |
| 2 |RetireFailed | The retire command failed on the device. |
| 3 |WipePending | There is a wipe command pending for the device. |
| 4 |WipeFailed | The wipe command failed on the device. |
| 5 |Unhealthy | Unhealthy state. |
| 6 |DeletePending | There is a delete command pending for the device. |
| 7 |RetireIssued | A retire command has been issued to the device. |
| 8 |WipeIssued | A wipe command has been issued. |
| 9 |WipeCanceled | Wipe command has been canceled. |
| 10 |RetireCanceled | Retire command has been canceled. |
| 11 |Discovered | The device is newly discovered by Intune, once it checks in for the first time it moves to -Managed- state. |

## ManagementAgentTypes

The **ManagementAgentTypes** entity represents the agents used to manage a device.

| Property  | Description |
|---------|------------|
| ManagementAgentTypeID | Unique identifier of the management agent type. |
| ManagementAgentTypeKey | Unique identifier of the management agent type in the data warehouse - surrogate key. |
| ManagementAgentTypeName |Indicates what kind of agent is used to manage the device. |

### Example

| ManagementAgentTypeID  | Name | Description |
|---------|------------|--------|
| 1 |EAS | The device is managed through Exchange Active Sync |
| 2 |MDM | The device is managed using an MDM agent |
| 3 |EasMdm | The device is managed by both Exchange Active Sync and an MDM agent |
| 4 |IntuneClient | The device is managed by the Intune PC agent |
| 5 |EasIntuneClient | The device is managed by both Exchange Active Sync and the Intune PC agent |
| 8 |ConfigManagerClient | The device is managed by the System Center Configuration Manager agent |
| 16 |Unknown | Unknown management agent type |

## Devices

The **Devices** entity lists all enrolled devices under management and their corresponding properties.

|          Property          |                                                                                       Description                                                                                      |
|:--------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DeviceKey                  | Unique   identifier of the device in the data warehouse - surrogate key.                                                                                                               |
| DeviceId                   | Unique   identifier of the device.                                                                                                                                                     |
| DeviceName                 | Name   of the device on platforms that allow naming a device. On other platforms,   Intune creates a name from other properties. This attribute cannot be   available for all devices. |
| DeviceTypeKey              | Key   of the device type attribute for this device.                                                                                                                                    |
| DeviceRegistrationState    | Key   of the client registration state attribute for this device.                                                                                                                      |
| OwnerTypeKey               | Key   of the owner type attribute for this device: corporate, personal, or unknown.                                                                                                    |
| EnrolledDateTime           | Date   and time that this device was enrolled.                                                                                                                                         |
| LastSyncDateTime           | Last known device check-in with   Intune.                                                                                                                                              |
| ManagementAgentKey         | Key of the management agent   associated with this device.                                                                                                                             |
| ManagementStateKey         | Key of the management state   associated with this device, indicating latest state of a remote action or if   it was jailbroken/rooted.                                                |
| AzureADDeviceId            | The   Azure deviceID for this device.                                                                                                                                                  |
| AzureADRegistered          | Whether the device is Azure Active   Directory registered.                                                                                                                             |
| DeviceCategoryKey          | Key of the category associated   with this device.                                                                                                                                     |
| DeviceEnrollmentType       | Key of the enrollment type   associated with this device, indicating method of enrollment.                                                                                             |
| ComplianceStateKey         | Key of the Compliance state   associated with this device.                                                                                                                             |
| OSVersion                  | Operating system version of the device.                                                                                                                                                |
| EasDeviceId                | Exchange ActiveSync ID of the device.                                                                                                                                                  |
| SerialNumber               | SerialNumber                                                                                                                                                                           |
| UserId                     | Unique Identifier for the user   associated with the device.                                                                                                                           |
| RowLastModifiedDateTimeUTC | Date and time in UTC when this   device was last modified in the data warehouse.                                                                                                       |
| Manufacturer               | Manufacturer of the device                                                                                                                                                             |
| Model                      | Model of the device                                                                                                                                                                    |
| OperatingSystem            | Operating system of the device. Windows, iOS,   etc.                                                                                                                                   |
| IsDeleted                  | Binary   to show whether the device is deleted or not.                                                                                                                                 |
| AndroidSecurityPatchLevel  | Android security patch level                                                                                                                                                           |
| MEID                       | MEID                                                                                                                                                                                   |
| isSupervised               | Device supervised status                                                                                                                                                               |
| FreeStorageSpaceInBytes    | Free Storage in Bytes.                                                                                                                                                                 |
| TotalStorageSpaceInBytes   | Total Storage in Bytes.                                                                                                                                                                |
| EncryptionState            | Encryption state on the   device.                                                                                                                                                      |
| SubscriberCarrier          | Subscriber carrier of the device                                                                                                                                                       |
| PhoneNumber                | Phone number of the device                                                                                                                                                             |
| IMEI                       | IMEI                                                                                                                                                                                   |
| CellularTechnology         | Cellular technology of the   device                                                                                                                                                    |
| WiFiMacAddress             | Wi-Fi MAC                                                                                                                                                                              |

## DevicePropertyHistory

The **DevicePropertyHistory** entity has the same properties as the devices table and daily snapshots of each device record per day for the past 90 days. The DateKey column indicates the day for each row.

|          Property          |                                                                                      Description                                                                                     |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DateKey                    | Reference to date table indicating the day.                                                                                                                                          |
| DeviceKey                  | Unique identifier of the device in the data warehouse -  surrogate key. This is a reference to the Device table that contains the   Intune device ID.                               |
| DeviceName                 | Name of the device on platforms that allow naming a   device. On other platforms, Intune creates a name from other properties. This   attribute cannot be available for all devices. |
| DeviceRegistrationStateKey | Key of the device registration state attribute for this   device.                                                                                                                    |
| OwnerTypeKey               | Key of the owner type attribute for this device:   corporate, personal, or unknown.                                                                                                  |
| ManagementStateKey         | Key of the management state associated with this device,   indicating latest state of a remote action or if it was jailbroken/rooted.                                                |
| AzureADRegistered          | Whether the device is Azure Active Directory registered.                                                                                                                             |
| ComplianceStateKey         | A key to ComplianceState.                                                                                                                                                            |
| OSVersion                  | OS version.                                                                                                                                                                          |
| JailBroken                 | Whether the device is jail broken or rooted.                                                                                                                                         |
| DeviceCategoryKey          | Key of device category attribute for this device. 

## ApplicationInventory

The **ApplicationInventory** entity lists the apps found on the device at the time of inventory collection.


|      Property      |                       Description                        |
|--------------------|----------------------------------------------------------|
|     DeviceKey      |              A reference to devices table.               |
|   ApplicationKey   | ? (copied from ExchangeDeviceService\DeviceApplication). |
|  ApplicationName   | ? (copied from ExchangeDeviceService\DeviceApplication). |
| ApplicationVersion | ? (copied from ExchangeDeviceService\DeviceApplication). |
|     BundleSize     | ? (copied from ExchangeDeviceService\DeviceApplication). |
