---
# required metadata

title: Remove company data on devices using Microsoft Intune - Azure | Microsoft Docs
description: Remove company data on a device or do a factory reset on an Android, Android for work, iOS, macOS, or Windows device using Microsoft Intune. Also delete a device from Azure Active Directory.
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/10/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Remove devices by using factory reset, removing company data, or manually unenrolling the device

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

By using the **Remove company data** or **Factory reset** actions, you can remove devices from Intune that are no longer needed, being repurposed, or missing. Users can also issue a remote command from the Intune Company Portal to personally owned devices that are enrolled in Intune.

> [!NOTE]
> Before you remove a user from Azure Active Directory (Azure AD), use the **Factory reset** or **Remove company data** actions for all devices that are associated with that user. If you remove users that have managed devices from Azure AD, Intune can no longer issue a factory reset or remove company data for those devices.

## Factory reset

The **Factory reset** action restores a device to its factory default settings. The user data is kept or wiped depending on whether or not you choose the **Retain enrollment state and user account** checkbox.

|Factory reset action|**Retain enrollment state and user account**|Removed from Intune management|Description|
|:-------------:|:------------:|:------------:|------------|
|**Factory Reset**| Not checked | Yes | Wipes all user accounts, data, MDM policies, and settings. Resets the operating system to its default state and settings.|
|**Factory Reset**| Checked | No | Wipes all MDM Policies. Keeps user accounts and data. Resets user settings back to default. Resets the operating system to its default state and settings.|

The **Retain enrollment state and user account** option is only available for Windows 10 version 1709 or later.

MDM policies will be reapplied the next time the device connects to Intune.

A factory reset is useful for resetting a device before you give the device to a new user, or when the device has been lost or stolen. Be careful about selecting **Factory reset**. Data on the device cannot be recovered.

### Factory reset a device

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Select **All services**, filter on **Intune**, and select **Microsoft Intune**.
3. Select **Devices** > **All devices**.
4. Select the name of the device that you want to factory reset.
5. In the pane that shows the device name, select **Factory reset**.
6. For Windows 10 version 1709 or later, you also have the **Retain enrollment state and user account** option. 
    
    |Retained during a factory reset|Not retained|
    | -------------|------------|
    |User accounts associated with the device|User files|
    |Machine state \(domain join, Azure AD-joined)| User-installed apps \(store and Win32 apps)|
    |Mobile device management (MDM) enrollment|Non-default device settings|
    |OEM-installed apps \(store and Win32 apps)||
    |User profile||
    |User data outside of the user profile||
    |User autologon|| 
    
         
7. To confirm the factory reset, select **Yes**.

If the device is on and connected, the **Factory reset** action propagates across all device types in less than 15 minutes.

## Remove company data

The **Remove company data** action removes managed app data (where applicable), settings, and email profiles that were assigned by using Intune. The device is removed from Intune management. This happens the next time the device checks in and receives the remote **Remove company data** action.

**Remove company data** leaves the user's personal data on the device.  

The following tables describe what data is removed, and the effect of the **Remove company data** action on data that remains on the device after company data is removed.

### iOS

|Data type|iOS|
|-------------|-------|
|Company apps and associated data installed by Intune|Apps are uninstalled. Company app data is removed.<br /><br />App data from Microsoft apps that use mobile app management is removed. The app is not removed.|
|Settings|Configurations that were set by Intune policy are no longer enforced. Users can change the settings.|
|Wi-Fi and VPN profile settings|Removed.|
|Certificate profile settings|Certificates are removed and revoked.|
|Management agent|The management profile is removed.|
|Email|Email profiles that are provisioned through Intune are removed. Cached email on the device is deleted.|
|Outlook|Email that's received by the Microsoft Outlook app for iOS is removed. This requires that the Outlook mobile app be deployed as a Required app to iOS users first.|
|Azure AD unjoin|The Azure AD record is removed.|
|Contacts |Contacts that are synced directly from the app to the native address book are removed. Any contacts that are synced from the native address book to another external source can't be removed. <br /> <br />Currently, only the Outlook app is supported.

### Android

|Data type|Android|Android Samsung Knox Standard|
|-------------|-----------|------------------------|
|Web links|Removed.|Removed.|
|Unmanaged Google Play apps|Apps and data remain installed.|Apps and data remain installed.|
|Unmanaged line-of-business apps|Apps and data remain installed.|Apps are uninstalled and data that's local to the app is removed. No data that's outside the app (for example, on an SD card) is removed.|
|Managed Google Play apps|App data is removed. The app isn't removed. Data that's protected by Mobile Application Management (MAM) encryption outside the app (for example, an SD card) remains encrypted and unusable, but isn't removed.|App data is removed. The app isn't removed. Data that's protected by MAM encryption outside the app (for example, an SD card) remains encrypted, but isn't removed.|
|Managed line-of-business apps|App data is removed. The app isn't removed. Data that's protected by MAM encryption outside the app (for example, an SD card) remains encrypted and unusable, but isn't removed.|App data is removed. The app isn't removed. Data that's protected by MAM encryption outside the app (for example, an SD card) remains encrypted and unusable, but isn't removed.|
|Settings|Configurations that were set by Intune policy are no longer enforced. Users can change the settings.|Configurations that were set by Intune policy are no longer enforced. Users can change the settings.|
|Wi-Fi and VPN profile settings|Removed.|Removed.|
|Certificate profile settings|Certificates are revoked but not removed.|Certificates are removed and revoked.|
|Management agent|Device Administrator privilege is revoked.|Device Administrator privilege is revoked.|
|Email|N/A (Email profiles aren't supported by Android devices)|Email profiles that are provisioned through Intune are removed. Cached email on the device is deleted.|
|Outlook|Email that's received by the Outlook app for Android is removed, but only if Outlook is protected by MAM policies. Otherwise, Outlook isn't wiped when the device is unenrolled.|Email that's received by the Outlook app for Android is removed, but only if Outlook is protected by MAM policies. Otherwise, Outlook isn't wiped when the device is unenrolled.|
|Azure AD unjoin|The Azure AD record is removed.|The Azure AD record is removed.|
|Contacts |Contacts that are synced directly from the app to the native address book are removed. Any contacts that are synced from the native address book to another external source can't be removed. <br /> <br />Currently, only the Outlook app is supported.|Contacts that are synced directly from the app to the native address book are removed. Any contacts that are synced from the native address book to another external source can't be removed. <br /> <br />Currently, only the Outlook app is supported.

### Android for Work

Removing company data from an Android for Work device removes all data, apps, and settings in the work profile on that device. The device is retired from management with Intune. Factory reset is not supported for Android for Work.


### macOS

|Data type|macOS|
|-------------|-------|
|Settings|Configurations that were set by Intune policy are no longer enforced. Users can change the settings.|
|Wi-Fi and VPN profile settings|Removed.|
|Certificate profile settings|Certificates that were deployed through MDM are removed and revoked.|
|Management agent|The management profile is removed.|
|Outlook|If conditional access is enabled, the device doesn't receive new mail.|
|Azure AD unjoin|The Azure AD record is removed.|

### Windows

|Data type|Windows 8.1 (MDM) and Windows RT 8.1|Windows RT|Windows Phone 8.1 and Windows Phone 8|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Company apps and associated data installed by Intune|Keys are revoked for files that are protected by EFS. The user can't open the files.|Company apps aren't removed.|Apps originally installed through the Company Portal are uninstalled. Company app data is removed.|Apps are uninstalled. Sideloading keys are removed.<br>For Windows 10 version 1703 (Creators Update) and later, Office 365 ProPlus apps aren't removed.|
|Settings|Configurations that were set by Intune policy are no longer enforced. Users can change the settings.|Configurations that were set by Intune policy are no longer enforced. Users can change the settings.|Configurations that were set by Intune policy are no longer enforced. Users can change the settings.|Configurations that were set by Intune policy are no longer enforced. Users can change the settings.|
|Wi-Fi and VPN profile settings|Removed.|Removed.|Not supported.|Removed.|
|Certificate profile settings|Certificates are removed and revoked.|Certificates are removed and revoked.|Not supported.|Certificates are removed and revoked.|
|Email|Removes email that's EFS-enabled. This includes emails and attachments in the Mail app for Windows.|Not supported.|Email profiles that are provisioned through Intune are removed. Cached email on the device is deleted.|Removes email that's EFS-enabled. This includes emails and attachments in the Mail app for Windows. Removes mail accounts that were provisioned by Intune.|
|Azure AD unjoin|No.|No.|The Azure AD record is removed.|Not applicable. On Windows 10, you can't remove company data for Azure AD-joined devices.|

### Remove company data

1. Sign in to the [Intune in the Azure portal](https://aka.ms/intuneportal).
2. In the **Devices** pane, select **All devices**.
3. Select the name of the device from which you want to remove company data.
4. In the pane that shows the device name, select **Remove company data**. To confirm, select **Yes**.

If the device is on and connected, the **Remove company data** action propagates across all device types in less than 15 minutes.

## Delete devices from the Intune portal

If you want to remove devices from the Intune portal, you can delete them from the specific device pane. The next time the device checks in, any company data on it will be removed.

1. Sign in to [Intune in the Azure portal](https://aka.ms/intuneportal).
2. Choose **Devices** > **All devices** > choose the devices you want to delete > **Delete**.

## Delete devices from the Azure Active Directory portal

You might need to delete devices from Azure AD due to communication issues or missing devices. You can use the **Delete** action to remove device records from the Azure portal for devices that you know are unreachable and unlikely to communicate with Azure again. The **Delete** action doesn't remove a device from management.

1.  Sign in to [Azure Active Directory in the Azure portal](http://aka.ms/accessaad) by using your admin credentials. You can also sign in to the [Office 365 portal](https://portal.office.com). From the menu, select **Admin centers** > **Azure AD**.
2.  Create an Azure subscription if you don’t have one. This shouldn't require a credit card or payment if you have a paid account (select the **Register your free Azure Active Directory** subscription link).
3.  Select **Azure Active Directory**, and then select your organization.
4.  Select the **Users** tab.
5. Select the user that's associated with the device that you want to delete.
6.  Select **Devices**.
7.  Remove devices as appropriate. For example, you might remove devices that are no longer in use, or devices that have inaccurate definitions.
