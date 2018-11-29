---
# required metadata
title:  Intune Date Warehouse Collections
titlesuffix: Microsoft Intune 
description: The Intune Data Warehouse collections provide details related to the Data Warehouse API.
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/19/2018
ms.topic: reference
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 29f09230-dc56-43db-b599-d961967bda49

# optional metadata
#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune
---

#  Intune Data Warehouse Collections

The following Intune Data Warehouse collections provides the properties, descriptions, and examples for v1.0 collections of the Data Warehouse API entities. 

## appRevisions
The **appRevision** entity lists all the versions of apps.

|          Property          |                                      Description                                      |                Example               |
|:--------------------------:|:-------------------------------------------------------------------------------------:|:------------------------------------:|
| AppKey                     | Unique identifier of the App.                                                         | 123                                  |
| ApplicationId              | Unique identifier of the App -   similar to AppKey, but this key is a natural.        | b66bc706-ffff-7437-0340-032819502773 |
| Revision                   | The version as mentioned by admin   during uploading of the binary.                   | 2                                    |
| Title                      | Title of the app.                                                                     | Excel                                |
| Publisher                  | Publisher of the app.                                                                 | Microsoft                            |
| UploadState                | Upload state of the app.                                                              | 1                                    |
| AppTypeKey                 | Reference to AppType described in   the following section.                            | 1                                    |
| VppProgramTypeKey          | Reference to VppProgramType   described below.                                        | 30876                                |
| CreationTime               | The time when this revision was   created.                                            | 11/23/2016 0:00                      |
| ModifiedTime               | Last time anything related to this   revision was changed.                            | 11/23/2016 0:00                      |
| Size                       | Size of the binary in bytes.                                                          | 120,392,000                          |
| StartDateInclusiveUTC      | Date and time in UTC when this App   revision was created in the data warehouse.      | 11/23/2016 0:00                      |
| EndDateExclusiveUTC        | Date and time in UTC when this app   revision became obsolete.                        | 11/23/2016 0:00                      |
| IsCurrent                  | Indicates whether this App version   is current or not in the data warehouse.         | True/False                           |
| RowLastModifiedDateTimeUTC | Date and time in UTC when this app   version was last modified in the data warehouse. | 11/23/2016 0:00                      |

## appTypes
The **appType** entity lists the installation source of an app.

|   Property  |        Description        |
|:-----------:|:-------------------------:|
| AppTypeID   | Id for the type           |
| AppTypeKey  | Surrogate key for the key |
| AppTypeName | App type                  |

### Example

| AppTypeID |                Name               |                     Description                     |
|:---------:|:---------------------------------:|:---------------------------------------------------:|
| 0         | Android   store app               | An   Android store app.                             |
| 1         | Android   LOB app                 | An   Android line-of-business app.                  |
| 2         | Managed   Android store app (MAM) | An   Android store app that has management enabled. |
| 3         | iOS   store app                   | An   iOS store app.                                 |
| 4         | iOS   LOB app                     | An   iOS line-of-business app.                      |
| 5         | Managed   iOS store app (MAM)     | An   iOSstore app that is management enabled.       |
| 6         | O365   Pro Plus Suite             | The   Office 365 Pro Plus Suite for Windows 10.     |
| 7         | Web   app                         | A   web app.                                        |
| 8         | Windows   Phone 8.1 store app     | A   Windows phone 8.1 store app.                    |
| 9         | Windows   store app               | A   Windows store app.                              |
| 10        | Windows   LOB apps                | A   Windows AppX line-of-business app.              |
| 11        | Windows   Mobile MSI              | An   MSI line-of-business app.                      |
| 12        | Windows   Phone LOB app           | A   Windows phone line-of-business app.             |

## compliancePolicyStatusDeviceActivities
The following table summarizes the assignment status of compliance policies to devices. It lists the count of devices found in each compliance state.

|    Property   |                                                                                      Description                                                                                     |  Example |
|:-------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey       | Date   key when the summary was created for the compliance policy.                                                                                                                   | 20161204 |
| Unknown       | Number   of devices that are offline or failed to communicate with Intune or Azure AD   for other reasons.                                                                           | 5        |
| NotApplicable | Number   of devices where device compliance policies targeted by the admin are not   applicable.                                                                                     | 201      |
| Compliant     | Number   of devices that successfully applied one or more device compliance policies   targeted by the admin.                                                                        | 4083     |
| InGracePeriod | Number   of devices that are not compliant but that are in the grace-period defined by   the admin.                                                                                  | 57       |
| NonCompliant  | Number   of devices that failed to apply one or more device compliance policies   targeted by the admin or where the user hasn't complied with the policies   targeted by the admin. | 43       |
|    Error      |    Number of   devices that failed to communicate with Intune or Azure AD, and returned an   error message.                                                                          |    3     |

## compliancePolicyStatusDevicePerPolicyActivities
The following table summarizes the assignment status of compliance policies to devices on a per policy and a per policy type basis. It lists the count of devices found in each compliance state for each assigned compliance policy.

|      Property     |                                                                                      Description                                                                                     |  Example |
|:-----------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey           | Date   key when the summary was created for the compliance policy.                                                                                                                   | 20161219 |
| PolicyKey         | Key   for the compliance policy for which the summary was created.                                                                                                                   | 10178    |
| PolicyPlatformKey | Key   for the platform type of the compliance policy for which the summary was   created.                                                                                            | 5        |
| Unknown           | Number   of devices that are offline or failed to communicate with Intune or Azure AD   for other reasons.                                                                           | 13       |
| NotApplicable     | Number   of devices where device compliance policies targeted by the admin are not   applicable.                                                                                     | 3        |
| Compliant         | Number   of devices that successfully applied one or more device compliance policies   targeted by the admin.                                                                        | 45       |
| InGracePeriod     | Number   of devices that are not compliant but that are in the grace-period defined by   the admin.                                                                                  | 3        |
| NonCompliant      | Number   of devices that failed to apply one or more device compliance policies   targeted by the admin or where the user hasn't complied with the policies   targeted by the admin. | 7        |
| Error             | Number   of devices that failed to communicate with Intune or Azure AD, and returned   an error message.                                                                             | 3        |
## complianceStates

|      Property      |                       Description                      |
|:------------------:|:------------------------------------------------------:|
| complianceStatus   | Compliance status of devices with   mdmStatusKey       |
| complianceStateKey | Compliance key to match device and   compliance status |
| complianceStateID  | The ID to match this compliance   state                |

### Example

|  complianceStatus  |                       Description                      |
|:------------------:|:------------------------------------------------------:|
|    Unknown         |    Unknown.                                                                        |
|    Compliant       |    Compliant.                                                                      |
|    Noncompliant    |       Device is non-compliant and is blocked from corporate resources.             |
|    Conflict        |    Conflict with other rules.                                                      |
|    Error           |       Error.                                                                       |
|    ConfigManager   |    Managed by Config Manager.                                                      |
|    InGracePeriod   |       Device is non-compliant but still has access to corporate resources          |

## dates
The **date** entity represents dates that are referenced across multiple data warehouse entities.

|     Property    |                       Description                      |    Example    |
|:---------------:|:------------------------------------------------------:|:-------------:|
| DateKey         | Unique identifier for this date in the data warehouse. | 20160703      |
| FullDate        | This date represented in full Date/Time format.        | 7/3/2016 0:00 |
| DayOfWeek       | Day of week                                            | 1             |
| DayOfMonth      | Day of month                                           | 3             |
| DayOfYear       | Day of year                                            | 185           |
| WeekOfYear      | Week of year                                           | 28            |
| MonthOfYear     | Month of the year                                      | 7             |
| CalendarQuarter | Calendar quarter                                       | 3             |
| CalendarYear    | Calendar year                                          | 2016          |
| DateKey         | Unique identifier for this date in the data warehouse. | 20160703      |
| FullDate        | This date represented in full Date/Time format.        | 7/3/2016 0:00 |
| DayOfWeek       | Day of week                                            | 1             |
| DayOfMonth      | Day of month                                           | 3             |
| DayOfYear       | Day of year                                            | 185           |
| WeekOfYear      | Week of year                                           | 28            |
| MonthOfYear     | Month of the year                                      | 7             |
| CalendarQuarter | Calendar quarter                                       | 3             |
| CalendarYear    | Calendar year                                          | 2016          |

## deviceCategories

|      Property      |                                    Description                                   |                Example               |
|:------------------:|:--------------------------------------------------------------------------------:|:------------------------------------:|
| deviceCategoryID   | Unique identifier for the device category.                                       | fb415ba2-7c08-41f6-a5e5-685b50da2c4c |
| deviceCategoryKey  | Unique identifier of the device category in the data   warehouse - surrogate key | 1                                    |
| deviceCategoryName | Display name for the device category.                                            | Smartphones                          |

## deviceConfigurationProfileDeviceActivities
The **DeviceConfigurationProfileDeviceActivity** entity lists the number of devices in the succeeded, pending, failed, or error state per day. The number reflects the Device configuration profiles assigned to the entity. For example, if a device is in the succeeded state for all its assigned policies, it increments the succeeded counter up one for that day. If a device has two profiles assigned to it, one in the succeeded state and another in an error state, the entity increments the Succeeded counter and place the device in the error state. The entity lists how many devices are in which state on a given day over the last 30 days.

|  Property |                                          Description                                          |  Example |
|:---------:|:---------------------------------------------------------------------------------------------:|:--------:|
| DateKey   | Date Key when the Device Configuration Profile check-in   was recorded in the data warehouse. | 20160703 |
| Pending   | Number of unique Devices in pending state.                                                    | 123      |
| Succeeded | Number of unique Devices in success state.                                                    | 12       |
| Error     | Number of unique Devices in error state.                                                      | 10       |
| Failed    | Number of unique Devices in failed state.                                                     | 2        |

## deviceConfigurationProfileUserActivities 
The **DeviceConfigurationProfileUserActivity** entity lists the number of users in the succeeded, pending, failed, or error state per day. The number reflects the Device configuration profiles assigned to the entity. For example, if a user is in the succeeded state for all their assigned policies, it moves up the succeeded counter by one for that day. If a user has two profiles assigned to them, one in the succeeded state and the other is in an error state, the user in the error state is counted. The **DeviceConfigurationProfileUserActivity** entity lists how many users are in which state on a given day over the last 30 days. 

| Property  | Description  | Example  |
|------------|----------------------------------------------------------------------------------------------|-----------|
| DateKey  | Date Key when the Device Configuration Profile check-in was recorded in the data warehouse.  | 20160703  |
| Pending  | Number of unique Users in pending state.  | 123  |
| Succeeded  | Number of unique Users in success state.  | 12  |
| Error  | Number of unique Users in error state.  | 10  |
| Failed  | Number of unique Users in failed state.  | 2  |

## devicePropertyHistories

|          Property          |                                                                                      Description                                                                                     |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DateKey                    | Reference to date table indicating the day.                                                                                                                                          |
| DeviceKey                  | Unique identifier of the device in the data warehouse -   surrogate key. This is a reference to the Device table that contains the   Intune device ID.                               |
| DeviceName                 | Name of the device on platforms that allow naming a   device. On other platforms, Intune creates a name from other properties. This   attribute cannot be available for all devices. |
| DeviceRegistrationStateKey | Key of the device registration state attribute for this   device.                                                                                                                    |
| OwnerTypeKey               | Key of the owner type attribute for this device:   corporate, personal, or unknown.                                                                                                  |
| ManagementStateKey         | Key of the management state associated with this device,   indicating latest state of a remote action or if it was jailbroken/rooted.                                                |
| AzureADRegistered          | Whether the device is Azure Active Directory registered.                                                                                                                             |
| ComplianceStateKey         | A key to ComplianceState.                                                                                                                                                            |
| OSVersion                  | OS version.                                                                                                                                                                          |
| JailBroken                 | Whether the device is jail broken or rooted.                                                                                                                                         |
| DeviceCategoryKey          | Key of device category attribute for this device.                                                                                                                                    |
## deviceRegistrationStates
The **DeviceRegistrationState** entity represents the registration type referenced by other data warehouse collections. 

|           Property          |                                     Description                                     |
|:---------------------------:|:-----------------------------------------------------------------------------------:|
| deviceRegistrationStateID   | Unique identifier for registration state                                            |
| deviceRegistrationStateKey  | Unique identifier of the registration state in the data   warehouse - surrogate key |
| deviceRegistrationStateName | Registration state                                                                  |
|    NotRegistered                     |    Not registered                                                                                                                                                                  |
|    Registered                        |       Registered                                                                                                                                                                   |
|    Revoked                           |       State means the IT administrator has blocked the client, and the client can   be unblocked. A device can also be in the Revoked state after it is wiped or   retired.        |
|    KeyConflict                       |    Key conflict                                                                                                                                                                    |
|    ApprovalPending                   |    Approval pending                                                                                                                                                                |
|    CertificateReset                  |    Reset certificate                                                                                                                                                               |
|    NotRegisteredPendingEnrollment    |    Not registered pending enrollment                                                                                                                                               |
|    Unknown                           |    Unknown state                                                                                                                                                                   |

## devices
The **device** entity lists all enrolled devices under management and their corresponding properties.

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
| EasDeviceId                | Exchange ActiveSync Id of the device.                                                                                                                                                  |
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


## deviceTypes
The **deviceType** entity represents the device type referenced by other data warehouse entities. The device type typically describes either the device model, manufacturer, or a combination of both.

|    Property    |                                  Description                                 |
|:--------------:|:----------------------------------------------------------------------------:|
| DeviceTypeID   | Unique   identifier of the device type                                       |
| DeviceTypeKey  | Unique   identifier of the device type in the data warehouse - surrogate key |
| DeviceTypeName | Device   type                                                                |

### Example

| deviceTypeID |        Name       |                      Description                      |
|:------------:|:-----------------:|:-----------------------------------------------------:|
| -1           | Not   Available   | The   device type is unavailable.                     |
| 0            | Desktop           | Windows   Desktop device                              |
| 1            | Windows           | Windows   device                                      |
| 2            | WinMO6            | Windows   Mobile 6.0 device                           |
| 3            | Nokia             | Nokia   device                                        |
| 4            | WindowsPhone      | Windows   Phone device                                |
| 5            | Mac               | Mac   device                                          |
| 6            | WinCE             | Windows   CE device                                   |
| 7            | WinEmbedded       | Windows   Embedded device                             |
| 8            | IPhone            | iPhone   device                                       |
| 9            | IPad              | iPad   device                                         |
| 10           | IPod              | iPod   device                                         |
| 11           | Android           | Android   device-managed using Device Administrator   |
| 12           | ISocConsumer      | iSoc   Consumer device                                |
| 13           | Unix              | Unix   Device                                         |
| 14           | MacMDM            | Mac   OS X device managed with the built-in MDM agent |
| 15           | HoloLens          | Holo   Lens device                                    |
| 16           | SurfaceHub        | Surface   Hub device                                  |
| 17           | AndroidForWork    | Android   device-managed using Android Profile Owner  |
| 18           | AndroidEnterprise | Android   enterprise device.                          |
| 100          | Blackberry        | Blackberry   Device                                   |
| 101          | Palm              | Palm   device                                         |
| 255          | Unknown           | Unknown   device type                                 |

## deviceEnrollmentTypes
The **deviceEnrollmentType** entity indicates how a device was enrolled. The enrollment type captures the method of enrollment. Examples list the different enrollment types and what they mean.

|         Property         |                                    Description                                    |
|:------------------------:|:---------------------------------------------------------------------------------:|
| deviceEnrollmentTypeID   | Unique   identifier of the enrollment type.                                       |
| deviceEnrollmentTypeKey  | Unique   identifier of the enrollment type in the data warehouse - surrogate key. |
| deviceEnrollmentTypeName | Enrollment   type name.                                                           |

### Example

| enrollmentTypeID |                Name                |                                        Description                                       |
|:----------------:|:----------------------------------:|:----------------------------------------------------------------------------------------:|
| 0                | Unknown                            | Enrollment   type was not collected                                                      |
| 1                | UserEnrollment                     | User driven enrollment through   BYOD channel.                                           |
| 2                | DeviceEnrollmentManager            | User enrollment with a device   enrollment manager account.                              |
| 3                | AppleBulkWithUser                  | Apple bulk enrollment with user   challenge. (DEP, Apple Configurator)                   |
| 4                | AppleBulkWithoutUser               | Apple bulk enrollment without user challenge.   (DEP, Apple Configurator, Mobile Config) |
| 5                | WindowsAzureADJoin                 | Windows 10 Azure AD Join.                                                                |
| 6                | WindowsBulkUserless                | Windows 10 Bulk enrollment through   ICD with certificate.                               |
| 7                | WindowsAutoEnrollment              | Windows 10 automatic enrollment.   (Add work account)                                    |
| 8                | WindowsBulkAzureDomainJoin         | Windows 10 bulk Azure AD Join.                                                           |
| 9                | WindowsCoManagement                | Windows 10 Co-Management triggered   by AutoPilot or Group Policy.                       |
| 10               | WindowsAzureADJoinsUsingDeviceAuth | Windows 10 Azure AD Join using   Device Auth.                                            |


## intuneManagementExtensions
The **intuneManagementExtension** lists the **intuneManagementExtension** health on each Windows 10 device per day. The data is retained for the last 60 days.

|       Property      |                          Description                          | Example |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| DateKey             | Unique identifier of the Date.                                | 123     |
| TenantKey           | Unique identifier of the Tenant.                              | 456     |
| DeviceKey           | Unique identifier of the Device.                              | 789     |
| ExtensionVersionKey | Unique identifier of the IntuneManagementExtension   version. | 1       |
| ExtensionStateKey   | Unique identifier of health state.                            | 2       |

## intuneManagementExtensionHealthStates
The **IntuneManagementExtensionHealthState** lists all possible health states of the **IntuneManagementExtension**.

|      Property     |                   Description                  | Example |
|:-----------------:|:----------------------------------------------:|:-------:|
| ExtensionStateKey | Unique   identifier of health state.           | 2       |
| ExtensionState    | Health   state of a IntuneManagementExtension. | Healthy |

## intuneManagementExtensionVersions
The **IntuneManagementExtensionVersion** entity lists all the versions used by **IntuneManagementExtension**.

|       Property      |                          Description                          | Example |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| ExtensionVersionKey | Unique identifier of the IntuneManagementExtension   version. | 1       |
| ExtensionVersion    | The 4 digit version number.                                   | 1.0.2.0 |

## managementAgentTypes
The **managementAgentType** entity represents the agents used to manage a device.

|         Property        |                                       Description                                       |
|:-----------------------:|:---------------------------------------------------------------------------------------:|
| ManagementAgentTypeID   | Unique identifier of the management agent type.                                         |
| ManagementAgentTypeKey  | Unique identifier of the management agent type in the data   warehouse - surrogate key. |
| ManagementAgentTypeName | Indicates what kind of agent is used to manage the device.                              |

### Example

| ManagementAgentTypeID |                Name               |                                  Description                                 |
|:---------------------:|:---------------------------------:|:----------------------------------------------------------------------------:|
| 1                     | EAS                               | The   device is managed through Exchange Active Sync                         |
| 2                     | MDM                               | The   device is managed using an MDM agent                                   |
| 3                     | EasMdm                            | The   device is managed by both Exchange Active Sync and an MDM agent        |
| 4                     | IntuneClient                      | The   device is managed by the Intune PC agent                               |
| 5                     | EasIntuneClient                   | The   device is managed by both Exchange Active Sync and the Intune PC agent |
| 8                     | ConfigManagerClient               | The   device is managed by the System Center Configuration Manager agent     |
| 10                    | ConfigurationManagerClientMdm     | The device is managed by   Configuration Manager and MDM.                    |
| 11                    | ConfigurationManagerCLientMdmEas  | The device is managed by   Configuration Manager, MDM and Eas.               |
| 16                    | Unknown                           | Unknown   management agent type                                              |
| 32                    | Jamf                              | The device attributes are fetched   from Jamf.                               |
| 64                    | GoogleCloudDevicePolicyController |  The device is managed by Google's CloudDPC.                                 |

## managementStates
The **ManagementState** entity provides details on the state of the device. Detail can be useful in the cases where remote actions are applied, the device is jailbroken, or rooted.

|       Property      |                                     Description                                    |
|:-------------------:|:----------------------------------------------------------------------------------:|
| managementStateID   | Unique   identifier of the management state.                                       |
| managementStateKey  | Unique   identifier of the management state in the data warehouse - surrogate key. |
| managementStateName | Indicates   the state of the remote action applied to this device.                 |

### Example

| managementStateID |      Name      |                                                   Description                                                   |
|:-----------------:|:--------------:|:---------------------------------------------------------------------------------------------------------------:|
| 0                 | Managed        | Managed   with no pending remote actions.                                                                       |
| 1                 | RetirePending  | There   is a retire command pending for the device.                                                             |
| 2                 | RetireFailed   | The   retire command failed on the device.                                                                      |
| 3                 | WipePending    | There   is a wipe command pending for the device.                                                               |
| 4                 | WipeFailed     | The   wipe command failed on the device.                                                                        |
| 5                 | Unhealthy      | Unhealthy   state.                                                                                              |
| 6                 | DeletePending  | There   is a delete command pending for the device.                                                             |
| 7                 | RetireIssued   | A   retire command has been issued to the device.                                                               |
| 8                 | WipeIssued     | A   wipe command has been issued.                                                                               |
| 9                 | WipeCanceled   | Wipe   command has been canceled.                                                                               |
| 10                | RetireCanceled | Retire   command has been canceled.                                                                             |
| 11                | Discovered     | The   device is newly discovered by Intune, once it checks in for the first time it   moves to -Managed- state. |

## mobileAppInstallStates
The MobileAppInstallState entity represents the install state for a mobile application after it has been assigned to a group containing devices, users or both.

|       Property      |                        Description                       |
|:-------------------:|:--------------------------------------------------------:|
| AppInstallStateKey  | The unique ID of the app install state for your account. |
| AppInstallState     | Enum value of the app install state.                     |
| AppInstallStateName | Name of the app install state.                           |

## mobileAppInstallStatusCounts
Represents a mobile app install status for a given target device type using Mobile Application Management through Microsoft Intune.

|      Property      |                                                          Description                                                          |
|:------------------:|:-----------------------------------------------------------------------------------------------------------------------------:|
| DateKey            | Key of the date when the app install status was recorded.                                                                     |
| AppKey             | Key of the mobile app used to identify an instance of   AppRevision.                                                          |
| DeviceTypeKey      | Key of the Device Type associated with the Mobile   Application.                                                              |
| AppInstallStateKey | Key of the app install state used to identify an instance   of MobileAppInstallState.                                         |
| ErrorCode          | The error code returned by the app installer, the mobile   platform or the service pertaining to the installation of the app. |
| Count              | Total count.                                                                                                                  |

## ownerTypes
The **ownerType** entity indicates whether a device is corporate, personally owned, or unknown.

|    Property   |                                                                                     Description                                                                                    |           Example          |
|:-------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------------------------:|
| ownerTypeID   | Unique identifier of the owner type.                                                                                                                                               |                            |
| ownerTypeKey  | Unique identifier of the owner type in the data warehouse   - surrogate key.                                                                                                       |                            |
| ownerTypeName | Represents the owner type of the devices:  Corporate  -   Device is enterprise owned.  Personal -   Device is personally owned (BYOD).   Unknown  -   No information on this device. | Corporate   Personal Unknown |

> [!Note]  
> For the `ownerTypeName` in AzureAD when creating Dynamic Groups for devices, you need to set the value `deviceOwnership` as `Company`. For more information, see [Rules for devices](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices). 

## policies
The **Policy** entity lists device configuration profiles, app configuration profiles, and compliance policies. You can assign the policies with Mobile Device Management (MDM) to a group in your enterprise.

|          Property          |                                                                       Description                                                                      |                Example               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| PolicyKey                  | Unique Key to represent the policy in the data warehouse.                                                                                              | 123                                  |
| PolicyId                   | Unique identifier of the Policy in the data warehouse.                                                                                                 | b66bc706-ffff-7437-0340-032819502773 |
| PolicyName                 | Name of the Policy.                                                                                                                                    | "Windows 10 Baseline"                |
| PolicyVersion              | Version of the Policy. When the policy is edited or   changed, a newer version is created.                                                             | 1, 2, 3                              |
| IsDeleted                  | Indicates whether the Policy record has been   updated.  True - Policy has a new record with updated fields.  False- The latest record for the policy. | True/False                           |
| StartDateInclusiveUTC      | Date and time in UTC when the policy was created in the   data warehouse.                                                                              | 11/23/2016 0:00                      |
| DeletedDateUTC             | Date and time in UTC when IsDeleted changed to True.                                                                                                   | 11/23/2016 0:00                      |
| RowLastModifiedDateTimeUTC | Date and time in UTC when the policy was last modified in   the data warehouse.                                                                        | 11/23/2016 0:00                      |

## policyDeviceActivities
The following table lists the number of devices in the succeeded, pending, failed, or error state per day. The number reflects the data per Policy Type profiles. For example, if a device is in the succeeded state for all its assigned policies, it increments the succeeded counter up one for that day. If a device has two profiles assigned to it, one in the succeeded state and another in an error state, the entity increments the Succeeded counter and place the device in the error state. The **policyDeviceActivity** entity lists how many devices are in which state on a given day over the last 30 days.

|  Property |                                           Description                                           |        Example        |
|:---------:|:-----------------------------------------------------------------------------------------------:|:---------------------:|
| DateKey   | Date   Key when the Device Configuration Profile check-in was recorded in the data   warehouse. | 20160703              |
| Pending   | Number   of unique Devices in pending state.                                                    | 123                   |
| Succeeded | Number   of unique Devices in success state.                                                    | 12                    |
| PolicyKey | Policy   Key, can be joined with Policy to get the policyName.                                  | Windows   10 baseline |
| Error     | Number   of unique Devices in error state.                                                      | 10                    |
| Failed    | Number   of unique Devices in failed state.                                                     | 2                     |

## policyPlatformTypes

|        Property        |                      Description                      |     Example    |
|:----------------------:|:-----------------------------------------------------:|:--------------:|
| PolicyPlatformTypeKey  | The unique key for the policy   platform type.        | 20170519       |
| PolicyPlatformTypeId   | The unique identifier for the   policy platform type. | 1              |
| PolicyPlatformTypeName | The name for the policy platform   type.              | AndroidForWork |

## policyTypeActivities
The **PolicyTypeActivity** entity lists the cumulative number of devices in the succeeded, pending, failed, or error state. It lists these states with respect to a device configuration profile, app configuration profile, or compliance policy per day.

|    Property   |                                          Description                                          |           Example           |
|:-------------:|:---------------------------------------------------------------------------------------------:|:---------------------------:|
| DateKey       | Date Key when the device Configuration profile check-in   was recorded in the data warehouse. | 20160703                    |
| PolicyKey     | Policy Key, can be joined with Policy to get the   policyName.                                | Windows 10 baseline         |
| PolicyTypeKey | Type of Policy Key, can be joined with Policy Type to get   the policy type name.             | Windows10 Compliance Policy |
| Pending       | Number of unique devices in pending state.                                                    | 123                         |
| Succeeded     | Number of unique devices in success state.                                                    | 12                          |
| Error         | Number of unique devices in error state.                                                      | 10                          |
| Failed        | Number of unique devices in failed state.                                                     | 2                           |

## policyTypes
The **PolicyType** entity lists types of device configuration profiles, app configuration profiles, and Compliance policies. You can assign the policies with Mobile Device Management (MDM) to a group in your enterprise.

|    Property    |                       Description                      |            Example            |
|:--------------:|:------------------------------------------------------:|:-----------------------------:|
| PolicyTypeId   | Unique identifier of the policy in the source system.  | 123                           |
| PolicyTypeKey  | Unique identifier of the policy in the data warehouse. | 1                             |
| PolicyTypeName | Name of the policy type.                               | Windows 10 Compliance policy. |

## policyUserActivities
The following table lists the number of users in the succeeded, pending, failed, or error state per day. The number reflects the data per Policy Type profiles. For example, if a user is in the succeeded state for all their assigned policies, it moves up the succeeded counter by one for that day. If a user has two profiles assigned to them, one in the succeeded state and the other is in an error state, the user in the error state is counted. The **PolicyUserActivity** entity lists how many users are in which state on a given day over the last 30 days.

|  Property |                                          Description                                          |       Example       |
|:---------:|:---------------------------------------------------------------------------------------------:|:-------------------:|
| DateKey   | Date Key when the Device Configuration Profile check-in   was recorded in the data warehouse. | 20160703            |
| Pending   | Number of unique Devices in pending state.                                                    | 123                 |
| Succeeded | Number of unique Devices in success state.                                                    | 12                  |
| PolicyKey | Policy Key, can be joined with Policy to get the   policyName.                                | Windows 10 baseline |
| Error     | Number of unique Devices in error state.                                                      | 10                  |

## termsAndConditions
A **termsAndConditions** entity represents the metadata and contents of a given Terms and Conditions (T&C) policy. The contents of  T&C policies are presented to users upon their first attempt to enroll into Intune and subsequently upon edits where an administrator has required re-acceptance. They enable administrators to communicate the provisions to which a user must agree in order to have devices enrolled into Intune.

|    Property        |    Description    |    Example        |
|----------------------------------|-----------------------------------------------------------------------------------------------|-----------------------------------------------------------|
|    termsAndConditionsKey    |    A key corresponding to an entry in the   ‘userTermsAndConditionsAcceptances’ collection    |    123    |
|    termsAndCondidionsId    |    The ID for this termsAndConditions entry    |    276edcb7-7440-4339-b6c5-8b6fc556fee6    |
|    termsAndConditionsVersion    |    The version of this terms and conditions entry    |    1    |
|    name    |    The name of this termsAndConditions entry.        |    Intune terms of use     |
|    description    |    The description for these terms and conditions.     |         |
|    title    |    The title for these terms and conditions.     |    Device management corporate policy        |
|    summaryOfTerms    |    The summary of terms given to the user.     |    I agree to the terms and conditions.    |
|    termsAndConditionsBodyText    |    The body of text for these terms and conditions.       |    *Device encryption* Enforcement of 6 digits PIN    |
|    isDeleted    |    True or false value for whether this value is   deleted.     |    False    |
|    startDateInclusiveUTC    |    The start date of these terms and conditions.     |    8/23/2018 4:01:34 AM    |
|    endDateEclusiveUTC    |    The end date of these terms and conditions.     |    12/31/9999 12:00:00 AM    |

## userDeviceAssociations
The **UserDeviceAssociation** entity contains user device associations in your organization.

|        Name        |                                             Description                                            |     Example     |
|:------------------:|:--------------------------------------------------------------------------------------------------:|:---------------:|
| UserKey            | Unique identifier of the user in the data warehouse.   (Surrogate key).                            | 123             |
| DeviceKey          | Unique identifier of the device in the data warehouse.                                             | 123             |
| CreatedDateTimeUTC | Date and time when the user device association was   created. Uses UTC format.                     | 11/23/2016 0:00 |
| IsDeleted          | Indicates that the user unenrolled that device, and that   the association is not current anymore. | True/False      |
| EndedDateTimeUTC   | Date and time in UTC when IsDeleted changed to True.                                               | 6/23/2017 0:00  |

## users
The **user** entity lists all the Azure Active Directory (Azure AD) users with assigned licenses in your enterprise.

The **user** entity collection contains user data. These records include user states during the data collection period, even if the user has been removed. For example, a user may be added to Intune and then removed during the course of the last month. While this user is not present at the time of the report, the user and state are present in the data from the prior month. You could create a report that would show the duration of the user's historic presence in your data.

|          Property          |                                                                                                           Description                                                                                                          |                Example               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| UserKey                    | Unique identifier of the user in the data warehouse -   surrogate key.                                                                                                                                                         | 123                                  |
| UserId                     | Unique identifier of the user - similar to UserKey, but is   a natural key.                                                                                                                                                    | b66bc706-ffff-7437-0340-032819502773 |
| UserEmail                  | Email address of the user.                                                                                                                                                                                                     | John@constoso.com                    |
| UPN                        | User principal name of the user.                                                                                                                                                                                               | John@constoso.com                    |
| DisplayName                | Display name of the user.                                                                                                                                                                                                      | John                                 |
| IntuneLicensed             | Specifies if this user is Intune licensed or not.                                                                                                                                                                              | True/False                           |
| IsDeleted                  | Indicates whether all of the user's licenses have expired   and whether the user was therefore removed from Intune. For a single record,   this flag does not change. Instead, a new record is created for a new user   state. | True/False                           |
| RowLastModifiedDateTimeUTC | Date and time in UTC when the record was last modified in   the data warehouse                                                                                                                                                 | 11/23/2016 0:00                      |

## userTermsAndConditionsAcceptances
A **userTermsAndConditionsAcceptance** entity represents the acceptance status of a given Terms and Conditions (T&C) policy by a given user. Users must accept the most up-to-date version of the terms in order to retain access to the Company Portal.

|    Property    |    Description    |    Example    |
|-------------------------------|--------------------------------------------------------------------------------|----------------------------|
|    dateKey    |    A key corresponding to a date values in the   ‘dates’ collection.     |    20180823    |
|    userKey    |    A user key mapping to a user in the ‘users’   collection.     |    20000    |
|    termsAndConditionsKey    |    A key corresponding to an entry in the   ‘termsAndConditions’ collection    |    1    |
|    acceptedDateTimeUTC    |    The time that the user accepted these terms and   conditions    |    8/23/2018 4:01:34 AM    |
|    lastModifiedDateTimeUTC    |    The last time that this entry was modified.     |    8/23/2018 4:01:34 AM    |

## vppProgramTypes 
The **vppProgramType** entity lists possible VPP program types for an app.

|      Property      |          Description         |
|:------------------:|:----------------------------:|
| VppProgramTypeID   | ID   for the type.           |
| VppProgramTypeKey  | Surrogate   key for the key. |
| VppProgramTypeName | VPP   Program type.          |

### Example

|             VppProgramID             |         Name        | Description                |
|:------------------------------------:|:-------------------:|----------------------------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft           | Microsoft's   VPP program. |
| 00000000-0000-0000-0000-000000000000 | Not   Yet Available | Default   value, No VPP.   |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple               | Apple's   VPP program.     |

## Next steps

For more about the Intune Data Warehouse, see [Data Warehouse data model](https://docs.microsoft.com/intune/reports-ref-data-model).

