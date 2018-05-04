---
# required metadata

title: Data transfer policy exceptions for apps 
titleSuffix: Microsoft Intune
description: Create exceptions to the Intune Mobile Application Management (MAM) data transfer policy.
keywords:
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 03/28/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d

# optional metadata

#ROBOTS:

#audience:
#ms.devlang:
ms.reviewer: joglocke
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure
---

# How to create exceptions to the Intune Mobile Application Management (MAM) data transfer policy

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

As an administrator, you can create exceptions to the Intune Mobile Application Management (MAM) data transfer policy. An exception allows you to specifically choose which unmanaged apps can transfer data to and from managed apps. The unmanaged apps that you included in the exception list must be trusted by IT. 

>[!WARNING] 
> You are responsible for making changes to the data transfer exception policy. Additions to this policy allow unmanaged apps (apps that are not managed by Intune) to access data that is protected by managed apps. This access to protected data may cause data security leaks. You should add data transfer exceptions only for apps that your organization must use but that do not support Intune APP (Application Protection Policies). Additionally, add exceptions only for apps that you do not consider to be data leak risks.

This feature applies when you create an Intune Application Protection Policy by having data transfer set to **Policy Managed Apps**. Other than the exceptions that you create, when your data transfer policy is set to **Policy Managed Apps**, data transfer is still restricted to apps that are managed by Intune. You can create the restrictions by using protocols (iOS) or packages (Android).

You can configure this feature to enable exceptions to the Intune MAM App Protection policy **Allow app to transfer data to other apps**. This policy is required only if you want to allow data to be transferred to an app that does not support Intune APP. This policy allows applications managed by Intune, and that have data transfer set to **Policy Managed Apps**, to invoke unmanaged applications based on URL protocol (iOS) or package name (Android). Intune adds vital native applications to the default list of exceptions. 

## iOS data transfer exceptions
For a policy targeting iOS, you can configure data transfer exceptions by URL protocol. To add an exception, check the documentation provided by the developer of the app to find information about supported URL protocols. For additional information about iOS data transfer exceptions, see [iOS app protection policy settings - Data transfer exemptions](app-protection-policy-settings-ios.md#data-transfer-exemptions).

## Android data transfer exceptions
For a policy targeting Android, you can configure data transfer exceptions by app package name. You can check the **Google Play** store page for the app you would like to add an exception for to find the app package name. For additional information about Android data transfer exceptions, see [Android app protection policy settings - Data transfer exemptions](app-protection-policy-settings-android.md#data-transfer-exemptions).


>[!TIP]
> You can find the package ID of an app by browsing to the app on the Google Play store. The package ID is contained in the URL of the app's page. For example, the package ID of the Microsoft Word app is **com.microsoft.office.word**.

### Example
By adding the **Webex** package as an exception to the MAM data transfer policy, Webex links inside a managed Outlook email message are allowed to open directly in the Webex application. Data transfer is still restricted in other unmanaged apps.

- iOS **Webex** example:
    To exempt the **Webex** app so that it is allowed to be invoked by Intune managed apps, you must add a data transfer exception for the following string: <code>wbx</code>
    
 - iOS **Maps** example:
    To exempt the native **Maps** app so that it is allowed to be invoked by Intune managed apps, you must add a data transfer exception for the following string: <code>maps</code>

- Android **Webex** example:
    To exempt the **Webex** app so that it is allowed to be invoked by Intune managed apps, you must add a data transfer exception for the following string: <code>com.cisco.webex.meetings</code>
    
- Android **SMS** example:
    To exempt the native **SMS** app so that it is allowed to be invoked by Intune managed apps across different messaging apps and Android devices, you must add data transfer exceptions for the following strings: 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

## Next steps

- [Create and deploy app protection policies](app-protection-policies.md)
- [iOS app protection policy settings - Data transfer exemptions](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Android app protection policy settings - Data transfer exemptions](app-protection-policy-settings-android.md#data-transfer-exemptions)
