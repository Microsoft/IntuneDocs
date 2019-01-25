---
# required metadata

title: Kiosk settings for Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Configure your Windows 10 (and later) devices as single-app and multi-app kiosks, customize the start menu, add apps, show the task bar, and configure a web browser in Microsoft Intune. 
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure; seodec18

---

# Windows 10 and later device settings to run as a kiosk in Intune

On Windows 10 and later devices, you can configure these devices to run in single-app kiosk mode, or multi-app kiosk mode.

This article lists and describes the different settings you can control on Windows 10 and later devices. As part of your mobile device management (MDM) solution, use these settings to configure your Windows 10 and later devices to run in kiosk mode.

As an Intune administrator, you can create and assign these settings to your devices.

To learn more about the Windows kiosk feature in Intune, see [configure kiosk settings](kiosk-settings.md).

## Before you begin

[Create the profile](kiosk-settings.md#create-the-profile).

## Single full-screen app kiosks

When you choose single app kiosk mode, enter the following settings:

- **User logon type**: The apps you add run as the user account you enter. Your options:

  - **Auto logon (Windows 10 version 1803 and later)**: For kiosks in public-facing environments that don't require the user to sign in, similar to a guest account. This setting uses the [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Local user account**: Enter the local (to the device) user account. The account you enter is used to sign in to the kiosk.

- **Application type**: Select **Store app**.

- **App to run in kiosk mode**: Choose **Add a store app**, and select an app from the list.

    Don't have any apps listed? Add some using the steps at [Client Apps](apps-add.md).

    Select **OK** to save your changes.

- **Kiosk browser settings**: These settings control a web browser app on the kiosk. Be sure you get the [Kiosk browser app](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) from the Store, add it to Intune as a [Client App](apps-add.md), and then assign the app to the kiosk devices.

  Enter the following settings:

  - **Default home page URL**: Enter the default URL shown when the kiosk browser opens or when the browser restarts. For example, enter `http://bing.com` or `http://www.contoso.com`.

  - **Home button**: **Show** or **hide** the kiosk browser's home button. By default, the button isn't shown.

  - **Navigation buttons**: **Show** or **hide** the forward and back buttons. By default, the navigation buttons aren't shown.

  - **End session button**: **Show** or **hide** the end session button. When shown, the user selects the button, and the app prompts to end the session. When confirmed, the browser clears all browsing data (cookies, cache, and so on), and then opens the default URL. By default, the button isn't shown.

  - **Refresh browser after idle time**: Enter the amount of idle time (1-1440 minutes) until the kiosk browser restarts in a fresh state. Idle time is the number of minutes since the user’s last interaction. By default, the value is empty or blank, which means there isn't any idle timeout.

  - **Allowed websites**: Use this setting to allow specific websites to open. In other words, use this feature to restrict or prevent websites on the device. For example, you can allow all websites at `http://contoso.com*` to open. By default, all websites are allowed.
 
      To allow specific websites, upload a file that includes a list of the allowed websites on separate lines. If you don't add a file, all websites are allowed. Intune supports * (asterisk) as a wild card.

      Your sample file should look similar to the following list:

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com/*`  
      `https://contoso.com/*`  

  Select **OK** to save your changes.

## Multi-app kiosks

Apps in this mode are available on the start menu. These apps are the only apps the user can open.

When you choose multi app kiosk mode, enter the following settings:

- **Target Windows 10 in S mode devices**: Choose **Yes** to allow store apps and AUMID apps (excludes Win32 apps) in the kiosk profile. Choose **No** to allow store apps, Win32 apps, and AUMID apps in the kiosk profile. When you choose **No**, this kiosk profile isn't deployed to S-mode devices.

- **User logon type**: The apps you add run as the user account you enter. Your options:

  - **Auto logon (Windows 10 version 1803 and later)**: For kiosks in public-facing environments that don't require the user to sign in, similar to a guest account. This setting uses the [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Local user account**: **Add** the local (to the device) user account. The account you enter is used to sign in to the kiosk.
  - **Azure AD user or group (Windows 10 version 1803 and later)**: Select **Add** to choose Azure AD users or groups from the list. You can select multiple users and groups. Choose **Select** to save your changes.
  - **HoloLens visitor**: The visitor account is a guest account that doesn't require any user credentials or authentication, as described in [shared PC mode concepts](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Applications**: Add the apps to run on the kiosk device. Remember, you can add several apps.

  - **Add store app**: Add an app from the Microsoft Store for Business. If you don't have any apps listed, then you can get apps, and [add them to Intune](store-apps-windows.md). For example, you can add Kiosk Browser, Excel, OneNote, and more.

  - **Add Win32 App**: A Win32 app is a traditional desktop app, such as Visual Studio Code or Google Chrome. Enter the following properties:

    - **Application name**: Required. Enter a name for the application.
    - **Local path**: Required. Enter the path to the executable, such as `C:\Program Files (x86)\Microsoft VS Code\Code.exe` or `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
    - **Application user model ID (AUMID)**: Enter the Application user model ID (AUMID) of the Win32 app. This setting determines the start layout of the tile on the desktop. To get this ID, see [find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).
    - **Tile size**: Required. Choose a Small, Medium, Wide, or Large app tile size.
  
  - **Add by AUMID**: Use this option to add inbox Windows apps, such as Notepad or Calculator. Enter the following properties: 

    - **Application name**: Required. Enter a name for the application.
    - **Application user model ID (AUMID)**: Required. Enter the Application user model ID (AUMID) of the Windows app. To get this ID, see [find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).
    - **Tile size**: Required. Choose a Small, Medium, Wide, or Large app tile size.

  > [!TIP]
  > After you add all the apps, you can change the display order by clicking-and-dragging the apps in the list.  

  Select **OK** to save your changes.

- **Kiosk browser settings**: These settings control a web browser app on the kiosk. Be sure you deploy a web browser app to the kiosk devices using [Client Apps](apps-add.md).

  Enter the following settings:

  - **Default home page URL**: Enter the default URL shown when the kiosk browser opens or when the browser restarts. For example, enter `http://bing.com` or `http://www.contoso.com`.

  - **Home button**: **Show** or **hide** the kiosk browser's home button. By default, the button isn't shown.

  - **Navigation buttons**: **Show** or **hide** the forward and back buttons. By default, the navigation buttons aren't shown.

  - **End session button**: **Show** or **hide** the end session button. When shown, the user selects the button, and the app prompts to end the session. When confirmed, the browser clears all browsing data (cookies, cache, and so on), and then opens the default URL. By default, the button isn't shown.

  - **Refresh browser after idle time**: Enter the amount of idle time (1-1440 minutes) until the kiosk browser restarts in a fresh state. Idle time is the number of minutes since the user’s last interaction. By default, the value is empty or blank, which means there isn't any idle timeout.

  - **Allowed websites**: Use this setting to allow specific websites to open. In other words, use this feature to restrict or prevent websites on the device. For example, you can allow all websites at `contoso.com*` to open. By default, all websites are allowed.

    To allow specific websites, upload a .csv file that includes a list of the allowed websites. If you don't add a .csv file, all websites are allowed.

  Select **OK** to save your changes.

- **Use alternative Start layout**: Choose **Yes** to enter an XML file that describes how the apps appear on the start menu, including the order of the apps. Use this option if you require more customization in your start menu. [Customize and export Start layout](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) provides some guidance, and sample XML.

- **Windows Taskbar**: Choose to **Show** or **hide** the taskbar. By default, the taskbar isn't shown.

## Next steps

[Assign the profile](device-profile-assign.md) and [monitor its status](device-profile-monitor.md).

You can also create kiosk profiles for [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#kiosk-settings), and [Windows Holographic for Business](kiosk-settings-holographic.md) devices.
