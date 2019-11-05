---
# required metadata

title: Manage Apple volume-purchased apps
titleSuffix: Microsoft Intune
description: Learn about how you can sync apps you purchased in volume from iOS and macOS App Store into Microsoft Intune and then manage and track their usage.
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# How to manage iOS and macOS apps purchased through Apple Volume Purchase Program with Microsoft Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Apple lets you purchase multiple licenses for an app that you want to run in your company on iOS and macOS devices. Purchasing multiple copies helps you to efficiently manage apps in your company.

Microsoft Intune helps you manage multiple copies of apps purchased through this program by:

- Reporting license information from the app store.
- Tracking how many of the licenses you have used.
- Helping you to not install more copies of the app than you own.

There are two methods you can use to assign volume-purchased apps:

## Device licensing

When you assign an app to devices, one app license is used, and remains associated with the device to which you assigned it.

When you assign volume-purchased apps to a device, the end user of the device does not have to supply an Apple ID to access the store.

## User licensing

When you assign an app to a user, one app license is used for and is associated with the user. The app can be run on up to 5 devices that the user owns (the device limit is controlled by Apple).

When you assign a volume-purchased app to users, each end user must have a valid and unique Apple ID in order to access the app store.

Additionally, you can synchronize, manage, and assign books you purchased from the Apple volume-purchase program (VPP) store with Intune to iOS devices. For more information, see [How to manage iOS eBooks you purchased through a volume-purchase program](vpp-ebooks-ios.md).

## Manage volume-purchased apps for iOS and macOS devices

### Supports Apple Volume Purchase Program volume-purchased apps

Purchase multiple licenses for iOS and macOS apps through the [Apple Volume Purchase Program for Business](https://www.apple.com/business/vpp/) or the [Apple Volume Purchase Program for Education](https://volume.itunes.apple.com/us/store). This process involves setting up an Apple VPP account from the Apple website and uploading the Apple VPP token to Intune.  You can then synchronize your volume purchase information with Intune and track your volume-purchased app use.

### Supports Business-to-Business volume-purchased apps

In addition, third-party developers can also privately distribute apps to authorized Volume Purchase Program for Business members specified in App Store Connect. These VPP for Business members can sign in to the Volume Purchase Program App Store and purchase their apps. VPP for Business apps purchased by the end user will sync to their Intune tenants.

## Before you start
Before you start, you need to get a VPP token from Apple and upload it to your Intune account. Additionally, you should understand the following criteria:

* You can associate multiple VPP tokens with your Intune account.
* If you previously used a VPP token with a different product, you must generate a new one to use with Intune.
* Each token is valid for one year.
* By default, Intune syncs with the Apple VPP service twice a day. You can start a manual sync at any time.
* Before you start to use Apple VPP with Intune, remove any existing VPP user accounts created with other mobile device management (MDM) vendors. Intune does not synchronize those user accounts into Intune as a security measure. Intune only synchronizes data from the Apple VPP service that Intune created.
* Intune supports adding up to 256 VPP tokens.
* Apple's Device Enrollment Profile (DEP) program automates mobile device management (MDM) enrollment. Using DEP, you can configure enterprise devices without touching them. You can enroll in the DEP program using the same program agent account that you used with Apple's VPP. The Apple Deployment Program ID is unique to programs listed under the [Apple Deployment Programs](https://deploy.apple.com) website and cannot be used to log in to Apple services such as the iTunes store.
* When you assign VPP apps using the user licensing model to users or devices (with user affinity), each Intune user needs to be associated with a unique Apple ID or an email address when they accept the Apple terms and conditions on their device.
* Ensure that when you set up a device for a new Intune user, you configure it with that user's unique Apple ID or email address. The Apple ID or email address and Intune user form a unique pair and can be used on up to five devices.
* A VPP token is only supported for use on one Intune account at a time. Do not reuse the same VPP token for multiple Intune tenants.

>[!IMPORTANT]
>After you have imported the VPP token to Intune, do not import the same token to any other device management solution. Doing so might result in the loss of license assignment and user records.

## To get and upload an Apple VPP token

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. On the **Intune** pane, choose **Client apps** > **Apple VPP tokens** under **Setup**.
4. On the list of VPP tokens pane, select **Create**.
5. On the **Create VPP token** pane, specify the following information:
    - **VPP token file** - If you haven't already, sign up for the Volume Purchase Program for Business or the program for Education. After you sign up, download the Apple VPP token for your account and select it here.
    - **Apple ID** - Enter the Apple ID of the account associated with the volume-purchase program.
    - **Take control of token from another MDM** - Setting this option to yes will allow the token to be reassigned to Intune from another MDM.
    - **Token Name** - An administrative field for setting the token name.
    - **Country/Region** - Select the VPP country/region store.  Intune synchronizes VPP apps for all locales from the specified VPP country/region store.
        > [!WARNING]  
        > Changing the country/region will update the apps metadata and store URL on next sync with the Apple service for apps created with this token. The app will not be updated if it does not exist in the new country/region store.

    - **Type of VPP account** - Choose from **Business** or **Education**.
    - **Automatic app updates** - Choose from **On** or **Off** to enable automatic updates. When enabled, Intune detects the VPP app updates inside the app store and automatically pushes them to the device when the device checks in. Automatic app updates for Apple VPP apps will automatically update only apps deployed with **Required** install intent. For apps deployed with **Available** install intent, the automatic update generates a notification for the admin informing that a new version of the app is available. Additionally, the user will see that the app as not installed on Company Portal, even though an earlier version of the app is installed. In this case, the user can reinstall the app by clicking **Install** on the app details screen in the Company Portal app to install the newer version of the app.

        > [!NOTE]
        > Automatic app updates work for both device and user licensed apps for iOS Version 11.0 and above.
    - **I grant Microsoft permission to send both user and device information to Apple.** - You must select I agree to proceed. To review what data Microisoft sends to Apple use the following [link](https://docs.microsoft.com/intune/data-intune-sends-to-apple).

6. When you are done, select **Create**.

The token is displayed in the list of tokens pane.

You can synchronize the data held by Apple with Intune at any time by choosing **Sync now**.

## To assign a volume-purchased app

1. On the **Intune** pane, choose **Client apps** > **Apps** under **Manage**.
2. On the list of apps pane, choose the app you want to assign, and then choose **Assignments**.
3. On the ***App name*** - **Assignments** pane, choose **Add group** then, on the **Add group** pane, choose an **Assignment type** and choose the Azure AD user or device groups to which you want to assign the app.
5. For each group you selected, choose the following settings:
    - **Type** - Choose whether the app will be **Available** (end users can install the app from the Company Portal), or **Required** (end user devices will automatically get the app installed).
    - **License type** - Choose from **User licensing**, or **Device licensing**.
6. Once you are done, choose **Save**.


>[!NOTE]
>The Available deployment intent is not supported for device groups, only user groups are supported. The list of apps displayed is associated with a token. If you have an app that is associated with multiple VPP tokens, you see the same app being displayed multiple times; once for each token.

## End-User Prompts for VPP

The end-user will receive prompts for VPP app installation in a number of scenarios. The following table explains each condition:

| # | Scenario                                | Invite to Apple VPP program                              | App install prompt | Prompt for Apple ID |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD – user licensed                             | Y                                                                                               | Y                                           | Y                                 |
| 2 | Corp – user licensed (not supervised device)     | Y                                                                                               | Y                                           | Y                                 |
| 3 | Corp – user licensed (supervised device)         | Y                                                                                               | N                                           | Y                                 |
| 4 | BYOD – device licensed                           | N                                                                                               | Y                                           | N                                 |
| 5 | CORP – device licensed (not supervised device)                           | N                                                                                               | Y                                           | N                                 |
| 6 | CORP – device licensed (supervised device)                           | N                                                                                               | N                                           | N                                 |
| 7 | Kiosk mode (supervised device) – device licensed | N                                                                                               | N                                           | N                                 |
| 8 | Kiosk mode (supervised device) – user licensed   | --- | ---                                          | ---                                |

> [!Note]  
> It is not recommended to assign VPP apps to Kiosk-mode devices using the VPP user licensing.

## Revoking app licenses

You can revoke all associated iOS or macOS volume-purchase program (VPP) app licenses based on a given device, user, or app.  But there are some differences between iOS and macOS platforms. 

### Revoking app licenses on iOS
You can notify users when an app is no longer assigned to them. But revoking an app license will not uninstall the related VPP app from the device. To uninstall a VPP app and reclaim an app license assigned to a user or device, you must change the assignment action to **Uninstall**. When you remove an app that was assigned to a user, Intune reclaims the user or device license and uninstalls the app from the device. The reclaimed license count will be reflected in **Licensed Apps** node in the **App** workload​ of Intune. Once a VPP app has been uninstalled and the app license has been reclaimed, you can choose to assign the app license to another user or device.


### Revoking app licenses on macOS
Revoking an app license does not uninstall the VPP app from the device. When you revoke an app license that was assigned to a user, Intune reclaims the user or device license. The macOS app with revoked license remains usable on the device, but cannot be updated until a license is reassigned to the user or device. According to Apple, such apps are removed after a 30-day grace period. However, Apple does not provide a means for Intune to remove the app using **Uninstall** assignment action. But you can choose to assign the reclaimed app license to another user or device.

>[!NOTE]
>Intune will retrieve both iOS and macOS user licensed VPP app licenses when an employee leaves the company and is no longer part of the AAD groups.

## Deleting VPP tokens
<!-- 820879 -->  
You can delete an Apple Volume Purchasing Program (VPP) token using the console. This may be necessary when you have duplicate instances of a VPP token. Deleting a token will also delete any associated apps and assignment. However, deleting a token does not revoke app licenses or uninstall apps. 

>[!NOTE]
>Intune cannot revoke app licenses after a token has been deleted. 

<!-- 820870 -->  
To revoke the license of all VPP apps for a given VPP token, you must first revoke all app licenses associated with the token, then delete the token.

## Renewing app licenses

You can renew an Apple VPP token by downloading a new token from Apple Volume Purchase Program portal and updating the existing token in Intune.

## Deleting a VPP app

Currently, you cannot delete an iOS VPP app from Microsoft Intune.

## Assigning custom role permissions for VPP

Access to Apple VPP tokens and VPP apps can be controlled independently using permissions assigned to custom administrator roles in Intune.

* To allow an Intune custom role to manage Apple VPP tokens under **Client apps** > **Apple VPP tokens**, assign permissions for **Managed apps**.
* To allow an Intune custom role to manage apps purchased using iOS VPP tokens under **Client apps** > **Apps**, assign permissions for **Mobile apps**. 

## Additional information

When a user with an eligible device first tries to install a VPP app to a device, they are asked to join the Apple Volume Purchase program. They must join before the app installation proceeds. The invitation to join the Apple Volume Purchase program requires that the user can use the App Store app on the iOS or macOS device. If you have set a policy to disable the App Store app, user-based licensing for VPP apps does not work. The solution is to either allow the App Store app by removing the policy, or use device-based licensing.

Apple provides direct assistance to create and renew VPP tokens. For more information, see [Distribute content to your users with the Volume Purchase Program (VPP)](https://go.microsoft.com/fwlink/?linkid=2014661) as part of Apple's documentation. 

If **Assigned to external MDM** is indicated in the Intune portal, then you (the Admin) must remove the VPP token from the 3rd party MDM before using the VPP token in Intune.

## Frequently asked questions

### How long does the portal take to update the license count once an app is installed or removed from the device?
The license should be updated within a few hours after installing or uninstalling an app. Note that if the end user removes the app from the device, the license is still assigned to that user or device.

### Is it possible to oversubscribe an app and, if so, in what circumstance?
Yes. The Intune admin can oversubscribe an app. For example, if the admin purchases 100 licenses for app XYZ, and then targets the app to a group with 500 members in it. The first 100 members (users or devices) will get the license assigned to them, the rest of the members will fail on license assignment.

### How frequently does Intune sync VPP tokens with Apple?
Intune syncs VPP tokens and licenses twice a day with Apple. The Intune admin can initiate a manual sync under **Client apps** > **Apple VPP tokens**.

## Next steps

See [How to monitor apps](apps-monitor.md) for information to help you monitor app assignments.
