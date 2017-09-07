---
# required metadata

title: Enroll your macOS device in Intune with Company Portal | Microsoft Docs
description: Describes how to enroll a macOS device in Intune with Company Portal app
keywords: Mac OS X, macOS, OS X
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 09/07/2017
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
 - User help

# optional metadata

ROBOTS:  
#audience:
#ms.devlang:
ms.reviewer: elocholi
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-enduser

---

# Enroll your macOS device in Intune with the Company Portal app

[!INCLUDE[macos-preview-1708](./includes/macos-preview-1708.md)]

Getting access to your organization’s apps, data, and resources makes it easier for you to do your job. Your organization is using Intune to [manage access to those resources](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-ios.md), which requires you to download the Company Portal app for macOS. These instructions will work for macOS devices on OS X El Capitan 10.11+.

  > [!NOTE]
  > If you want to enroll an iOS device, such as an iPhone or iPad, [try these instructions instead](enroll-your-device-in-intune-ios.md).

1. On your __Dock__, find __Safari__ and go to [aka.ms/macoscompanyportal](https://aka.ms/macoscompanyportal).

2. Download the app. Your Mac will check to make sure that the download of **CompanyPortal.dmg** is safe to open. After you open it from your **Downloads** folder, drag the **CompanyPortal** app on the **Applications** folder.

3. Open your **Applications** folder or the **Launchpad**, then open **Company Portal**.

4. Your Mac will show you a message that says, **"CompanyPortal" is an application downloaded from the Internet. Are you sure you want to open it?** Click **Open**.

  > [!NOTE]
  > Intune needs access to your computer to make sure that your device is secure enough to access your organization's resources. If your computer refuses to open the Company Portal app, try [turning off Gatekeeper](https://support.apple.com/HT202491) and then opening the app.

6. The first screen you see in the Company Portal app prompts you to **Sign In** with the same work or school account you used to log in to the Company Portal website.

7. The Company Portal confirms your account information, then shows you your **Device Enrollment** and **Device Compliance** statuses. There will be yellow triangles letting you know that you have actions you'll need to take to make sure your Mac is safe for use at work. Click **Begin** to start [enrolling your device into management](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).

8. Your Mac will begin enrolling into management. You might be prompted to provide your computer's login information during this time. This may take a few minutes to enroll. During this time, you can do other things on your computer. A message appears once you've completed Company Access Setup to let you know you're done.

Still need help? Check in with your IT administrator. You can find their contact information on the [Company Portal website](http://portal.manage.microsoft.com).
