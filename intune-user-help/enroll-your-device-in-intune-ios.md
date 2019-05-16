---
# required metadata

title: Set up iOS device access to your company resources | Microsoft Docs
description: Describes how to get your iOS device managed by Intune
keywords:
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/05/2019
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
 - User help

# optional metadata

ROBOTS:  
#audience: 
#ms.devlang:
ms.reviewer: tisilv
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
---


# Set up iOS device access to your company resources  

Enroll your iOS device with the Intune Company Portal app to gain secure access to your organization's email, files, and apps.

After your device is enrolled, it becomes *managed*. Your organization can assign policies and apps to the device through a mobile device management (MDM) provider, such as Intune.  

To maintain access to work or school information from your device, you'll need to configure your device to match your organization's preferred settings. This article describes how to use Company Portal to enroll you device and maintain your organization's setting requirements. 

> [!NOTE]
> If you tried to access company email in the Mail app, and received a prompt to get your device managed, you're in the right place. Follow the instructions below to get access to your email and other company resources on your iOS device.  

## What to expect from the Company Portal app  

### Security  
During initial setup, the app requires that you authenticate yourself with your organization. It then informs you of any device settings you must update. For example, organizations often set minimum or maximum character password requirements that you'll be required to meet.     

### Protection  
After your device is enrolled, the Company Portal app will continue to make sure that your device is protected. If you install an app from an untrusted source, for example, the app will alert you and sometimes revoke access to company data. This kind of policy is common in organizations, and often requires you to uninstall the untrusted app before you can regain access.  

### Setting notifications  
If after enrollment your organization enforces a new security requirement, such as multi-factor authentication, the Company Portal app will notify you. You'll have the chance to adjust your settings so that you can continue to work from your device.  

To learn more about enrollment, see [What happens when I install the Company Portal app and enroll my device?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios).  

## Enroll your iOS device  

Go to the App store to download and install the [Intune Company Portal app](install-and-sign-in-to-the-intune-company-portal-app-ios.md) on your device. You'll also need to maintain a Wi-Fi connection and have access to Safari during enrollment. 

Pausing for more than a few minutes during enrollment might cause the app to close or end setup. If this happens, open the Company Portal app and try again.  

1. Open Company Portal and sign in with your work or school account. 

    ![Example screenshot of Company Portal app, Sign in.](./media/ios-01-cp-enroll-1903.PNG)  

2. When prompted to receive Company Portal notifications, tap **Allow.** Company Portal uses notifications to alert you if, for example, your device settings need to be updated. 

    ![Example screenshot of Company Portal home page, "Notifications" prompt.](./media/ios-04-cp-enroll-1903.PNG)  

3. On the **Set up access** screen, select **Begin.**  

     ![Example screenshot of Company Portal, "Set up access" screen.](./media/ios-05-cp-enroll-1903.PNG)  

4. Read through the list of device information your organization can and can't see. Then tap **Continue**.  

5. Read through the instructions on the **What's next?** screen. When you're ready to download and install the management profile, tap **Continue**.  

 > [!IMPORTANT]
> These next steps and screens will differ depending on your iOS version. Follow the steps for your iOS version. 

6. Safari opens the Company Portal website on your device. When prompted to download the configuration profile, tap **Allow**. If you're on a device running:  
    * iOS 12.2 and later: When the download is complete, tap **Done.** Continue to step 7 in this article.
    * iOS 12.1 and earlier: You'll be automatically redirected to the Settings app. Skip to step 8 in this article.  
 
    If you accidentally tap **Ignore**, refresh the page. You'll be prompted to open the Company Portal app. From the app, you can tap **Download again**.

  > [!NOTE]
  > You must install the management profile as described in the next steps within 8 minutes of downloading it. If you don't, the profile will be removed and you'll have to restart enrollment.  

7. iOS 12.2 and later only: When prompted to open Company Portal, tap **Open**. The **Installing Management Profile** screen lists the steps to install the profile.

    ![Example screenshot of Company Portal, Installing Management Profile screen.](./media/ios-1904-settings-icon.PNG)  

8. Go to the Settings app and tap **Profile Downloaded**.  

    If **Profile Downloaded** doesn't appear as an option, go to **General** > **Profiles**. If you still don't see the profile, you may need to download it again.  

    ![Example screenshot of the Settings app, Profile Downloaded setting.](./media/ios-1904-settings-badge.PNG)  

9. Tap **Install**.  
    
10. Enter your device password. Then tap **Install**.    

    ![Example screenshot of the Settings app, Installing Profile screen, with a cursor on the **Install** button.](./media/ios-1904-password-install.PNG)  


11. The next screen is a standard system warning for device management. To continue with installation, tap **Install**. If prompted to trust remote management, tap **Trust**.  

    ![Example screenshot of Settings app, standard system warning screen for root certificate and mobile device management.](./media/ios-15-cp-enroll-1903.PNG)  

12. After installation is complete, tap **Done**. To verify that the profile was installed, go to the **Profiles & Device Management** settings. You should see the profile listed under **Mobile Device Management**.   

    ![Example screenshot of Settings app, Profiles & Device Management settings, showing the management profile.](./media/ios-00-cp-enroll-1903.PNG)  

13. Return to the Company Portal app. Company Portal will begin to sync and set up your device. Company Portal might prompt you to update additional device settings. If it does, tap **Continue**.  

    ![Example screenshot of Company Portal, "Set up access" screen, with yellow triangle next to setting requirement.](./media/ios-12-cp-enroll-1903.PNG)  

14. You'll know that setup is complete when all items in the list show a green circle. Tap **Done**.   
    
    ![Example screenshot of Company Portal, "You're all set!" screen, showing all green circles.](./media/ios-13-cp-enroll-1903.PNG)  

> [!Note]
> If your organization monitors voice and data limits, or provides you with a company-owned device, you might have a few more steps to complete. If you're prompted to install the **Datalert** app, see [enrolling your device in telecom expense management](enroll-your-device-with-telecom-expense-management-ios.md). If your organization is part of Apple's Device Enrollment Program, find out [how to enroll your company-owned device](enroll-your-device-dep-ios.md).  

## Next steps  
Find apps that will help you at work or school. Learn [how apps are made available](use-managed-apps-on-your-device-ios.md) to you through Company Portal.  

Still need help? Check in with your company support. You can find their contact information on the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980).  

## See also

[Troubleshooting iOS device enrollment problems in Microsoft Intune](https://support.microsoft.com/en-us/help/4039809)
