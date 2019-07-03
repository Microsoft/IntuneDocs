---
# required metadata

title: Your device is missing a required certificate | Microsoft Docs
titlesuffix: Microsoft Intune
description: What to do when your device is missing a required certificate.
keywords:
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
searchScope:
 - User help

# optional metadata

ROBOTS:  
#audience:
#ms.devlang:
ms.reviewer: esmich
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-enduser; seodec18
ms.collection: M365-identity-device-management
---


# Your device is missing a required certificate

## What's a certificate?

[Cryptography](https://technet.microsoft.com/library/cc962030.aspx) is the science of providing security for information. Traditionally, cryptography has been used to pass coded messages to [ensure that communication is kept secret](https://technet.microsoft.com/library/cc962019.aspx). In its simplist form, cryptography substitutes or transposes letters to create a coded message into an unreadable, scrambled, or hidden message. Only someone with a decoding key, or _certificate_, can convert the coded message back into its original, readable form. Your Android device uses certificates with Intune to make sure that communications between your device and your organizational resources, such as email and documents, are kept safe from one end, through the air, to the other.

## Fixing certificate issues

If your Android device isn’t enrolled in Intune, and it’s missing a certain certificate that is required by your company support, you won’t be able to sign in to the Company Portal app. When you try to sign in, you'll see the following message:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

The first step you should try is to see if your device is [missing a certificate that usually comes preinstalled on it](your-device-is-missing-a-preinstalled-certificate-android.md).

If resolving certificate issues doesn't work, your company support could [require you to install a second certificate for additional security](your-device-is-missing-an-IT-required-certificate-android.md).

Still need help? Contact your company support. For contact information, check the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980).

## Next steps  
Still need help? Contact your company support. For contact information, check the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980).  
