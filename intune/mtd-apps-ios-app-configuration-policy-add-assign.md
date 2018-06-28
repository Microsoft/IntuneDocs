---
# required metadata

title: Add and assign MTD apps to Microsoft Intune
titleSuffix:
description: Use Intune to add Mobile Threat Defense (MTD) apps, Microsoft Authenticator app, and iOS configuration policy in the Azure portal.
keywords:
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 06/27/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: heenamac
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Add and assign Mobile Threat Defense (MTD) apps with Intune

> [!NOTE] 
> This topic applies to all Mobile Threat Defense partners.

You can use Intune to add and deploy MTD apps so end users can receive notifications when a threat is identified in their mobile devices, and to receive guidance to remediate the threats.


## Before you begin

The below steps need to be completed in the [Azure portal](https://portal.azure.com/). Make sure you’re familiar with the process of:

  -   [Adding an app into Intune](apps-add.md).
  -   [Adding an iOS app configuration policy into Intune](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).
  -   [Assigning an app with Intune](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune).
  -   [ Adding an iOS app configuration policy](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

> [!TIP]
> The Intune company portal works as the broker on Android devices so users can have their identities checked by Azure AD.

## Configure Microsoft Authenticator for iOS
For iOS devices, you need the [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) so users can have their identities checked by Azure AD. Additionally, you need the iOS app configuration policy which signals the MTD iOS app to use with Intune.

See the instructions for [adding iOS store apps to Microsoft Intune](store-apps-ios.md). Use this [Microsoft Authenticator app store URL](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) on **step 12** under the **Configure app information** section.

## Configure MTD applications

Choose the section that corresponds to your MTD provider:

  - [Lookout for Work](#configure-lookout-for-work-apps)
  - [Symantec Endpoint Protection Mobile (SEP Mobile)](#configure-symantec-endpoint-protection-mobile-apps)
  - [Check Point SandBlast Mobile](#configure-check-point-sandblast-mobile-apps)
  - [Zimperium](#configure-zimperium-apps)
  - [Pradeo](#configure-pradeo-apps)

### Configure Lookout for Work apps

- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](store-apps-android.md). Use this [Lookout for work Google app store URL](https://play.google.com/store/apps/details?id=com.lookout.enterprise) on **step 7**.

- **iOS**

  - See the instructions for [adding iOS store apps to Microsoft Intune](store-apps-ios.md). Use this [Lookout for Work iOS app store URL](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) on **step 12** under the **Configure app information** section.

-   **Lookout for Work app outside the Apple store**
    - You need to re-sign the Lookout for Work iOS app. Lookout distributes its Lookout for Work iOS app outside of the iOS App Store. Before distributing the app, you must re-sign the app with your iOS Enterprise Developer Certificate.
    - For detailed instructions to re-sign the Lookout for Work iOS apps, see [Lookout for Work iOS app re-signing process](https://personal.support.lookout.com/hc/articles/114094038714) on the Lookout website.

    - **Enable Azure AD authentication for Lookout for Work iOS app users.**

        1. Go to the [Azure portal](https://portal.azure.com), sign in with your credentials, then navigate to the application page.

        2. Add the **Lookout for Work iOS app** as a **native client application**.

        3. Replace the **com.lookout.enterprise.yourcompanyname** with the customer bundle ID you selected when you signed the IPA.

        4.  Add additional redirect URI: **&lt;companyportal://code/>** followed by a URL encoded version of your original redirect URI.

        5.  Add **Delegated Permissions** to your app.

        > [!NOTE] 
        > See [configure a native client application with Azure AD](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application) for more details.

     - **Add the Lookout for Work ipa file.**

        - Upload the re-signed .ipa file as described in the [Add iOS LOB apps with Intune](lob-apps-ios.md) topic. You also need to set the minimum OS version to iOS 8.0 or later.

### Configure Symantec Endpoint Protection Mobile apps

 - **Android**

    - See the instructions for [adding Android store apps to Microsoft Intune](store-apps-android.md). In **step 7**, use this [SEP Mobile app store URL](https://play.google.com/store/apps/details?id=com.skycure.skycure).  For **Minimum operating system**, select **Android 4.0 (Ice Cream Sandwich)**.

 - **iOS**

    - See the instructions for [adding iOS store apps to Microsoft Intune](store-apps-ios.md). In **step 12**, use this [SEP Mobile app store URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) under the **Configure app information** section.

### Configure Check Point SandBlast Mobile apps

 - **Android**

    - See the instructions for [adding Android store apps to Microsoft Intune](store-apps-android.md). Use this [Check Point SandBlast Mobile app store URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) on **step 7**.

 - **iOS**

    - Contact [Check Point SandBlast Mobile](https://www.checkpoint.com/products/sandblast-mobile/) to get the iOS app. See the instructions for [adding iOS store apps to Microsoft Intune](store-apps-ios.md), then use the Apple store URL in **step 12** under the **Configure app information** section.

### Configure Zimperium apps

 - **Android**

    - See the instructions for [adding Android store apps to Microsoft Intune](store-apps-android.md). Use this [Zimperium app store URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) on **step 7**.

 - **iOS**

    - See the instructions for [adding iOS store apps to Microsoft Intune](store-apps-ios.md). Use this [Zimperium app store URL](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) in **step 12** under the **Configure app information** section.

### Configure Pradeo apps

 - **Android**

    - See the instructions for [adding Android store apps to Microsoft Intune](store-apps-android.md). Use this [Pradeo app store URL](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) on **step 7**.

 - **iOS**

    - See the instructions for [adding iOS store apps to Microsoft Intune](store-apps-ios.md). Use this [Pradeo app store URL](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) in **step 12** under the **Configure app information** section.

## Configure your MTD apps with an iOS app configuration policy

### Lookout for Work app configuration policy

- Create the iOS app configuration policy as described in the [using iOS app configuration policy](app-configuration-policies-use-ios.md) topic.

### SEP Mobile app configuration policy

-   Use the same Azure AD account previously configured in the [Symantec Endpoint Protection Management console](https://aad.skycure.com), which should be the same account used to log in to the Intune classic portal.

-   You need to **download** the iOS app configuration policy file: 
    -   Go to [Symantec Endpoint Protection Management console](https://aad.skycure.com) and sign in with your admin credentials.

    -   Go to **Settings**, and under **Integrations**, choose **Intune**. Choose **EMM Integration Selection**. Choose **Microsoft**, and then save your selection.

    -   Click the **Integration setup files** link and save the generated \*.zip file. The .zip file contains the ***.plist** file that will be used to create the iOS app configuration policy in Intune.

    -   See the instructions for [using Microsoft Intune app configuration policies for iOS](app-configuration-policies-use-ios.md) to add the SEP Mobile iOS app configuration policy.

    - On **step 8**, use the option **Enter XML data**, copy the content from the ***.plist** file, and paste its content into the configuration policy body.

> [!NOTE]
> If you are unable to retrieve the files, contact [Symantec Endpoint Protection Mobile Enterprise Support](https://support.symantec.com/en_US/contact-support.html).

### Check Point SandBlast Mobile app configuration policy

- See the instructions for [using Microsoft Intune app configuration policies for iOS](app-configuration-policies-use-ios.md) to add the Check Point SandBlast Mobile iOS app configuration policy.
    - On **step 8**, use the option **Enter XML data**, copy the content below and paste it into the configuration policy body.

```
<dict><key>MDM</key><string>INTUNE</string></dict>
```

### Zimperium app configuration policy

- See the instructions for [using Microsoft Intune app configuration policies for iOS](app-configuration-policies-use-ios.md) to add the Zimperium iOS app configuration policy.
    - On **step 8**, use the option **Enter XML data**, copy the content below and paste it into the configuration policy body.

```
<dict>
<key>provider</key><string>Intune</string>
<key>userprincipalname</key><string>{{userprincipalname}}</string>
<key>deviceid</key>
<string>{{deviceid}}</string>
<key>serialnumber</key>
<string>{{serialnumber}}</string>
<key>udidlast4digits</key>
<string>{{udidlast4digits}}</string>
</dict>
```

## Assign apps to groups

- This step applies to all MTD partners. See instructions for [assigning apps to groups with Intune](apps-deploy.md).

## Next steps

- [Configure the device compliance policy for MTD](mtd-device-compliance-policy-create.md)
