---
# required metadata

title: Manage iOS volume-purchased apps 
titleSuffix: "Intune on Azure"
description: Learn about how you can sync apps you purchased in volume from the iOS store into Intune and then manage and track their usage."
keywords:
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/18/2017
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mghadial
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure
---

# How to manage iOS apps you purchased through a volume-purchase program with Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

The iOS app store lets you purchase multiple licenses for an app that you want to run in your company. This helps you reduce the administrative overhead of tracking multiple purchased copies of apps.

Microsoft Intune helps you manage apps that you purchased through this program by importing the license information from the app store, tracking how many of the licenses you have used, and preventing you from installing more copies of the app than you own.

Additionally, you can synchronize, manage, and assign books you purchased from the Apple volume-purchase program store with Intune, and assign these to users. Use the **Books** workload in the Intune portal to manage books. The procedures to manage books are the same as you use for managing apps.
You must have uploaded an Apple Volume Purchase Program token in order to do this. Currently, you can only assign books as a **Required** install.
When you assign a book to a device, that device must have the built-in iBooks app installed. If it is not, the end user must re-install the app in order to read the book. You cannot currently use Intune to restore removed built-in apps.


## Manage volume-purchased apps for iOS devices
You purchase multiple licenses for iOS apps through the [Apple Volume Purchase Program for Business](http://www.apple.com/business/vpp/) or the [Apple Volume Purchase Program for Education](http://volume.itunes.apple.com/us/store). This involves setting up an Apple VPP account from the Apple website and uploading the Apple VPP token to Intune.  You can then synchronize your volume purchase information with Intune and track your volume-purchased app use.

## Before you start
Before you start, you'll need to get a VPP token from Apple and upload this to your Intune account. Additionally, you should understand the following:

* You can associate multiple volume-purchase program tokens with your Intune account.
* If you previously used a VPP token with a different product, you must generate a new one to use with Intune.
* Each token is valid for one year.
* By default, Intune syncs with the Apple VPP service twice a day. You can start a manual sync at any time.
* Intune only syncs VPP app information from the VPP store with the country code associated with the Intune account. In other words, you will only be able to see and deploy VPP apps for the country code your Intune account is configured for. 
* After you have imported the VPP token to Intune, do not import the same token to any other device management solution. Doing so might result in the loss of license assignment and user records.
* Before you start to use iOS VPP with Intune, remove any existing VPP user accounts created with other mobile device management (MDM) vendors. Intune will not synchronize those user accounts into Intune as a security measure. Intune will only synchronize data from the Apple VPP service that Intune created.
* Intune supports adding up to 256 VPP tokens.

## To get and upload an Apple VPP token

1. Sign into the Azure portal.
2. Choose **More Services** > **Monitoring + Management** > **Intune**.
3. On the **Intune** blade, choose **Mobile apps**.
1.  In the **Mobile Apps** workload, choose **Setup** > **iOS VPP Tokens**.
2.  On the list of VPP tokens blade, click **Add**.
3.  On the New VPP Token blade, specify the following information:
	- **VPP token file** - If you haven't already, sign up for the Volume Purchase Program for Business or the Volume Purchase Program for Education. After you sign up, download the Apple VPP token for your account and select it here.
	- **Apple ID** - Enter the Apple ID of the account associated with the volume-purchase program.
	- **Type of VPP account** - Choose from **Business** or **Education**.
4. When you are done, click **Upload**.

The token is displayed in the list of tokens blade.


You can synchronize the data held by Apple with Intune at any time by choosing **Sync now**.

> [!NOTE]
> Microsoft Intune will only sync information of Apps which are publicly available through the iTunes Store. **Custom B2B Apps for iOS** are not yet supported. If your scenario targets such apps, the app information will not be synchronized.

## To assign a volume-purchased app

1. In the **Mobile Apps** workload, choose **Manage** > **Licensed Apps**.
2. On the list of apps blade, choose the app you want to assign, and then choose '**...**' > **Assign Groups**.
3. On the <*app name*> - **Groups Assigned** blade, choose **Manage** > **Groups Assigned**.
4. Choose **Assign Groups** then, on the **Select groups** blade, choose the Azure AD user or device groups to which you want to assign the app.
You must choose an assignment action of **Required**. Additionally, assignments to device groups are available to new tenants created after January 2017. If your tenant was created before then, and you do not have the option to assign VPP apps to device groups, contact Intune support.
5. Once you are done, choose **Save**.

See [How to monitor apps](apps-monitor.md) for information to help you monitor app assignments.

## Further information

When you assign the app as a **Required** installation, each user who installs the app uses a license.

To reclaim a license, you must change the assignment action to **Uninstall**. The license will be reclaimed after the app is uninstalled.

When a user with an eligible device first tries to install a VPP app, they will be asked to join the Apple Volume Purchase program. They must do this before the app installation proceeds. The invitation to join the Apple Volume Purchase program requires that the user can use the iTunes app on the iOS device. If you have set a custom configuration policy to disable the iTunes Store app, user-based licensing for VPP apps does not work. The solution is to either allow the iTunes app by removing the policy, or use device-based licensing.

When you assign a VPP app as Available, the app content and license are assigned directly from the app store.
