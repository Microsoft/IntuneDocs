---
# required metadata

title: iOS device feature settings in Microsoft Intune - Azure | Microsoft Docs
description: See all the settings to configure iOS devices for AirPrint, layout of the home screen, app notifications, shared device, single sign-in, and web content filter settings in Microsoft Intune. Use these settings in a device configuration profile to configure iOS devices to use these different Apple features in your organization.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/01/2019
ms.topic: reference
ms.prod:
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology:

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
search.appverid:
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# iOS device settings to use common iOS features in Intune

Intune includes some built-in settings to allow iOS users to use different Apple features on their devices. For example, administrators can control how iOS users use AirPrint printers, add apps and folders to the dock and pages on the home screen, show app notifications, show asset tag details on the lock screen, use single sign-on authentication, and authenticate users with certificates.

Use these features to control iOS devices as part of your mobile device management (MDM) solution.

This article lists these settings, and describes what each setting does.

## Before you begin

[Create an iOS device configuration profile](device-features-configure.md#create-a-device-profile).

## AirPrint settings

This feature allows iOS users to print to known AirPrint printers.

1. In **Settings**, select **AirPrint**. Enter the following properties of the AirPrint server:

    - **IP address**: Enter the IPv4 or IPv6 address of the printer. If you use hostnames to identify printers, you can get the IP address by pinging the printer in the terminal. Get the IP address and path (in this article) provides more details.
    - **Path**: The path is typically `ipp/print` for printers on your network. Get the IP address and path (in this article) provides more details.
    - **Port**: Enter the listening port of the AirPrint destination. If you leave this property blank, AirPrint uses the default port. Available on iOS 11.0 and later.
    - **TLS**: Choose **Enable** to secure AirPrint connections with Transport Layer Security (TLS). Available on iOS 11.0 and later.

2. Select **Add**. The AirPrint server is added to the list. You can add many AirPrint servers.

    You can also **Import** a comma-separated file (.csv) with this information. After you create the list, you can also **Export** your list of AirPrint servers.

3. When finished, select **OK** to save your list.

To add AirPrinter servers, you need the IP address of the printer, the resource path, and the port. The following steps show you how to get this information.

1. On a Mac that’s connected to the same local network (subnet) as the AirPrint printers, open **Terminal** (from **/Applications/Utilities**).
2. In the Terminal, type `ippfind`, and select enter.

    Note the printer information. For example, it may return something similar to `ipp://myprinter.local.:631/ipp/port1`. The first part is the name of the printer. The last part (`ipp/port1`) is the resource path.

3. In the Terminal, type `ping myprinter.local`, and select enter.

   Note the IP address. For example, it may return something similar to `PING myprinter.local (10.50.25.21)`.

4. Use the IP address and resource path values. In this example, the IP address is `10.50.25.21`, and the resource path is `/ipp/port1`.

## Home screen layout settings

These settings configure the app layout and folders on the dock and home screens of iOS devices. To use this feature, iOS devices must be in supervised mode and run iOS 9.3 or later.

### Dock

Use the **Dock** settings to add up to six items or folders to the dock of the iOS screen. Many devices support fewer items. For example, iPhone devices support up to four items. In this case, only the first four items you add are shown on the device.

1. In **Settings**, select **Home Screen Layout (supervised only)** > **Dock** > **Add**. You can add up to **six** items (apps and folders combined) for the device dock.
2. In **Type**, choose to add an **App** or a **Folder**.

    - **Add an app**: Choose this option to add apps to the dock on the screen. Enter:

      - **App Name**: Enter a name for the app. This name is used for your reference in the Azure portal. It *isn't* shown on the iOS device.
      - **App Bundle ID**: Enter the bundle ID of the app. See [Bundle IDs for built-in iOS apps](#bundle-ids-for-built-in-ios-apps) (in this article) for some examples.

      Select **OK** to save your changes.

    - **Add a folder**: Choose this option to add a folder to the dock on the screen. 

      Apps that you add to a page in a folder are arranged from left to right, and in the same order as the list. If you add more apps than can fit on a page, the apps are moved to another page.

      1. Enter a **Folder name**. This name is shown to users on their device.
      2. Choose **Add**, and enter the following properties:

          - **Page name**: Enter a name for the page. This name is used for your reference in the Azure portal. It *isn't* shown on the iOS device.
          - **App Name**: Enter a name for the app. This name is used for your reference in the Azure portal. It *isn't* shown on the iOS device.
          - **App Bundle ID**: Enter the bundle ID of the app. See [Bundle IDs for built-in iOS apps](#bundle-ids-for-built-in-ios-apps) (in this article) for some examples.

      3. Choose **Add**. You can add up to **20** pages for the device dock.
      4. Select **OK** to save your changes.

> [!NOTE]
> When you add icons using the Dock settings, the icons on the Home Screen and pages are locked, and can’t be moved. This may be by design with iOS and Apple’s MDM policies.

#### Example

In the following example, the dock screen shows only the Safari, Mail, and Stocks apps. The Mail app is selected to show its properties:

![Sample iOS dock settings](./media/FfFiUcP.png)

When you assign the policy to an iPhone, the dock looks similar to the following image:

![Sample iOS dock layout on iPhone](./media/bAgCe8F.png)

### Pages

Add the pages you want shown on the home screen, and the apps you want shown on each page. Apps that you add to a page are arranged from left to right, in the same order as the list. If you add more apps than can fit on a page, the apps are moved to another page.

> [!TIP]
> To reorder items in any Home screen and pages lists, you can drag and drop them.

1. In **Settings**, select **Home Screen Layout (supervised only)** > **Pages** > **Add**. You can add up to **40** pages on a device.
2. Enter a **Page name**. This name is used for your reference in the Azure portal, and *isn't* shown on the iOS device. 

    Select **Add**. You can add up to **60** items (apps and folder combined) on a device.

3. In **Type**, choose to add an **App** or a **Folder**.

    - **Add an app**: Choose this option to add apps to a page on the screen. Enter:

      - **App Name**: Enter a name for the app. This name is used for your reference in the Azure portal. It *isn't* shown on the iOS device.
      - **App Bundle ID**: Enter the bundle ID of the app. See [Bundle IDs for built-in iOS apps](#bundle-ids-for-built-in-ios-apps) (in this article) for some examples.

      Select **OK** to save your changes.

    - **Add a folder**: Choose this option to add a folder to the dock on the screen. 

      Apps that you add to a page in a folder are arranged from left to right, and in the same order as the list. If you add more apps than can fit on a page, the apps are moved to another page.

      1. Enter a **Folder name**. This name is shown to users on their device.
      2. Choose **Add**, and enter the following properties:

          - **Page name**: Enter a name for the page. This name is used for your reference in the Azure portal. It *isn't* shown on the iOS device.
          - **App Name**: Enter a name for the app. This name is used for your reference in the Azure portal. It *isn't* shown on the iOS device.
          - **App Bundle ID**: Enter the bundle ID of the app. See [Bundle IDs for built-in iOS apps](#bundle-ids-for-built-in-ios-apps) (in this article) for some examples.

      3. Choose **Add**.
      4. Select **OK** to save your changes.

#### Example

In the following example, a new page named **Contoso** is added. The page shows the Find Friends and Settings apps. The Settings app is selected to show its properties:

![iOS Home screen settings example](./media/Jc2OxyX.png)

When you assign the policy to an iPhone, the page looks similar to the following image:

![iOS device with modified home screen](./media/Bd37PHa.png)

## App notifications settings

Choose how installed apps on iOS devices send notifications. These settings support supervised devices running iOS 9.3 and later.

1. In **Settings**, select **App Notifications (supervised only)** > **Add**:

    ![Add app notification in iOS profile in Intune](./media/ios-macos-app-notifications.png)

2. Enter the following properties:

    - **App bundle ID**: Enter the **App Bundle ID** of the app you want to add. See [Bundle IDs for built-in iOS apps](#bundle-ids-for-built-in-ios-apps) (in this article) for some examples.
    - **App name**: Enter the name of the app you want to add. This name is used for your reference in the Azure portal. It *isn't* shown on the device.
    - **Publisher**: Enter the publisher of the app you're adding. This name is used for your reference in the Azure portal. It *isn't* shown on the device.
    - **Notifications**: **Enable** or **Disable** the app from sending notifications to the device.
       - **Show in Notification Center**: **Enable** allows the app to show notifications in the device Notification Center. **Disable** prevents the app from showing notifications in the Notification Center.
       - **Show in Lock Screen**: Select **Enable** to see notifications from the app on the device lock screen. **Disable** prevents the app from showing notifications on the lock screen.
       - **Alert type**: When the device is unlocked from, choose how the notification is shown. Your options:
         - **None**: No notification is shown.
         - **Banner**: A banner is briefly shown with the notification.
         - **Modal**: The notification is shown and the user must manually dismiss it before continuing to use the device.
       - **Badge on app icon**: Select **Enable** to add a badge to the app icon. The badge means the app sent a notification.
       - **Sounds**: Select **Enable** to play a sound when a notification is delivered.

3. Select **OK** to save your changes. Continue adding the apps you want. When finished, select **OK**.

## Lock screen message settings

Use these settings to show a custom message or text on the sign in window and lock screen. For example, you can enter an "If lost, return to ..." message and asset tag information. 

This feature supports supervised devices running:

- iOS 9.3 and later

1. In **Settings**, select **Lock Screen Message (supervised only)**.
2. Enter the following settings:

    - **Asset tag information**: Enter information about the asset tag of the device. For example, enter `Owned by Contoso Corp` or `Serial Number: {{serialnumber}}`. 

	  The text you enter is shown on the sign in window and lock screen on the device.

    - **Lock screen footnote**: If the device is lost or stolen, enter a note that might help get the device returned. You can enter any text you want. For example, enter something like `If found, call Contoso at ...`.

    Device tokens can also be used to add device-specific information to these fields. For example, to show the serial number, enter `Serial Number: {{serialnumber}}`. On the lock screen, the text shows similar to `Serial Number 123456789ABC`. When entering variables, be sure to use curly brackets `{{ }}`. [App configuration tokens](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) includes a list of variables that can be used. You can also use `deviceName` or any other device-specific value.

    > [!NOTE]
    > Variables aren't validated in the UI. As a result, you may see profiles saved with incorrect input. For example, if you enter `{{Devicename}}` instead of `{{devicename}}`, then the literal string is shown instead of the device’s unique name.

3. When finished, select **OK** to save your changes.

## Single sign-on settings

Most Line of Business (LOB) apps require some level of user authentication to support security. In many cases, the authentication requires the user to enter the same credentials repeatedly, which is frustrating for users. To improve the user experience, developers can create apps that use single sign-on (SSO). Using single sign-on reduces the number of times a user must enter credentials.

To use single sign-on, be sure you have:

- An app that's coded to look for the user credential store in single sign-on on the device.
- Intune configured for iOS device single sign-on.

1. In **Settings**, select **Single sign-on**:

   ![Single Sign On pane](./media/sso-blade.png)

2. Enter the following settings:

    - **Username attribute from AAD**: Intune looks for this attribute for each user in Azure AD. Intune then populates the respective field (such as UPN) before generating the XML that gets installed on the device. Your options:

      - **User principal name**: The UPN is parsed in the following way:

        ![Username attribute](media/User-name-attribute.png)

        You can also overwrite the realm with the text you enter in the **Realm** text box.

        For example, Contoso has several regions, including Europe, Asia, and North America. Contoso wants their Asia users to use SSO, and the app requires the UPN in the `username@asia.contoso.com` format. When you select **User Principal Name**, the realm for each user is taken from Azure AD, which is `contoso.com`. So for users in Asia, select **User Principal Name**, and enter `asia.contoso.com`. The end user's UPN becomes `username@asia.contoso.com`, instead of `username@contoso.com`.

      - **Intune device ID**: Intune automatically selects the Intune Device ID.

        By default, apps only need to use the device ID. But if your app uses the realm and the device ID, you can type the realm in the Realm text box.

        > [!NOTE]
        > By default, keep the realm empty if you use device ID.

      - **Azure AD device ID**

    - **Realm**: Enter the domain part of the URL. For example, enter `contoso.com`.
    - **URL prefixes that will use Single Sign On**: **Add** any URLs in your organization that require user single sign-on authentication.

        For example, when a user connects to any of these sites, the iOS device uses the single sign-on credentials. The user doesn't need to enter any additional credentials. If multi-factor authentication is enabled, then users are required to enter the second authentication.

        > [!NOTE]
        > These URLs must be properly formatted FQDN. Apple requires these to be in the `http://<yourURL.domain>` format.

        The URL matching patterns must begin with either `http://` or `https://`. A simple string match is run, so the `http://www.contoso.com/` URL prefix doesn't match `http://www.contoso.com:80/`. With iOS 10.0 or later, a single wildcard \* may be used to enter all matching values. For example, `http://*.contoso.com/` matches both `http://store.contoso.com/` and `http://www.contoso.com`.

        The `http://.com` and `https://.com` patterns match all HTTP and HTTPS URLs, respectively.

    - **Apps that will use Single Sign On**: **Add** apps on end users' devices that can use single sign-on.

        The `AppIdentifierMatches` array must include strings that match app bundle IDs. These strings may be exact matches, such as `com.contoso.myapp`, or enter a prefix match on the bundle ID using the \* wildcard character. The wildcard character must appear after a period character (.), and may appear only once, at the end of the string, such as `com.contoso.*`. When a wildcard is included, any app whose bundle ID begins with the prefix is granted access to the account.

        Use **App Name** to enter a user-friendly name to help you identify the bundle ID.

    - **Credential renewal certificate**: If using certificates for authentication (not passwords), select the existing SCEP or PFX certificate as the authentication certificate. Typically, this certificate is the same certificate that's deployed to the user for other profiles, such as VPN, Wi-Fi, or email.

3. When finished, select **OK** to save your changes.

## Web content filter settings

These settings control browser URL access on iOS devices.

1. In **Settings**, select **Web Content Filter (supervised only)**.
2. Choose the **Filter Type**. Your options:

    - **Configure URLs**: Use Apple’s built-in web filter that looks for adult terms, including profanity and sexually explicit language. This feature evaluates each web page as it's loaded, and identifies and blocks unsuitable content. You can also add URLs that you don't want checked by the filter. Or, block specific URLs, regardless of Apple's filter settings.

      - **Permitted URLs**: **Add** the URLs you want to allow. These URLs bypass Apple's web filter.

        > [!NOTE]
        > The URLs you enter are the URLs you don't want evauluated by the Apple web filter. These URLs aren't a list of allowed web sites. To create a list of allowed websites, set the **Filter Type** to **Specific websites only**.

        Select **OK** to save your changes.

      - **Blocked URLs**: **Add** the URLs you want to stop from opening, regardless of the Apple web filter settings.

        Select **OK** to save your changes.

    - **Specific websites only** (for the Safari web browser only): These URLs are added to the Safari browser’s bookmarks. The user is **only** allowed to visit these sites; no other sites can be opened. Use this option only if you know the exact list of URLs that users can access.

      - **URL**: Enter the URL of the website you want to allow. For example, enter `https://www.contoso.com`.
      - **Bookmark Path**: Enter the path to store the bookmark. For example, enter `/Contoso/Business Apps`. If you don't add a path, the bookmark is added to the default bookmark folder on the device.
      - **Title**: Enter a descriptive title for the bookmark.

      If you don't enter any URLs, then end users can't access any websites except for `microsoft.com`, `microsoft.net`, and `apple.com`. These URLs are automatically allowed by Intune.

      Select **OK** to save your changes.

## Wallpaper settings

Add a custom .png, .jpg, or .jpeg image to your supervised iOS devices. For example, use a company logo on the lock screen.

You may experience unexpected behavior when a profile with no image is assigned to devices with an existing image. For example, you create a profile without an image. This profile is assigned to devices that already have an image. In this scenario, the image may change to the device default, or the original image may stay on the device. This behavior is controlled and limited by Apple's MDM platform.

- **Wallpaper Display Location**: Choose a location on the device to show the image. Your options:
  - **Not configured**: A custom image isn't added to the device. The device uses the operating system default.
  - **Lock screen**: Adds the image to the lock screen.
  - **Home screen**: Adds the image to the home screen.
  - **Lock screen and Home screen**: Uses the same image on the lock screen and home screen.
- **Wallpaper Image**: Upload an existing .png, .jpg, or .jpeg image you want to use. Be sure the file size is less than 750 KB. You can also **remove** an image that you added.

> [!TIP]
> To display different images on the lock screen and home screen, create a profile with the lock screen image. Create another profile with the home screen image. Assign both profiles to your iOS user or device groups.

## Bundle IDs for built-in iOS apps

The following list shows the bundle ID of some common built-in iOS apps. To find the bundle ID of other apps, contact your software vendor.

| Bundle ID                   | App Name     | Publisher |
|-----------------------------|--------------|-----------|
| com.apple.AppStore          | App Store    | Apple     |
| com.apple.calculator        | Calculator   | Apple     |
| com.apple.mobilecal         | Calendar     | Apple     |
| com.apple.camera            | Camera       | Apple     |
| com.apple.mobiletimer       | Clock        | Apple     |
| com.apple.compass           | Compass      | Apple     |
| com.apple.MobileAddressBook | Contacts     | Apple     |
| com.apple.facetime          | FaceTime     | Apple     |
| com.apple.DocumentsApp      | Files        | Apple     |
| com.apple.mobileme.fmf1     | Find Friends | Apple     |
| com.apple.mobileme.fmip1    | Find iPhone  | Apple     |
| com.apple.gamecenter        | Game Center  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | Health       | Apple     |
| com.apple.Home              | Home         | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.iMovie            | iMovie       | Apple     |
| com.apple.itunesconnect.mobile | iTunes Connect | Apple |
| com.apple.MobileStore       | iTunes Store | Apple     |
| com.apple.itunesu           | iTunes U     | Apple     |
| com.apple.Keynote           | Keynote      | Apple     |
| com.apple.mobilemail        | Mail         | Apple     |
| com.apple.Maps              | Maps         | Apple     |
| com.apple.measure	      | Measure      | Apple     |
| com.apple.MobileSMS         | Messages     | Apple     |
| com.apple.Music             | Music        | Apple     |
| com.apple.news              | News         | Apple     |
| com.apple.mobilenotes       | Notes        | Apple     |
| com.apple.Numbers           | Numbers      | Apple     |
| com.apple.Pages             | Pages        | Apple     |
| com.apple.Photo-Booth       | Photo Booth  | Apple     |
| com.apple.mobileslideshow   | Photos       | Apple     |
| com.apple.podcasts          | Podcasts     | Apple     |
| com.apple.reminders         | Reminders    | Apple     |
| com.apple.mobilesafari      | Safari       | Apple     |
| com.apple.Preferences       | Settings     | Apple     |
| com.apple.SiriViewService   | Siri         | Apple     |
| com.apple.stocks            | Stocks       | Apple     |
| com.apple.tips              | Tips         | Apple     |
| com.apple.TV                | TV           | Apple     |
| com.apple.videos            | Videos       | Apple     |
| com.apple.VoiceMemos        | VoiceMemos   | Apple     |
| com.apple.Passbook          | Wallet       | Apple     |
| com.apple.Bridge            | Watch        | Apple     |
| com.apple.weather           | Weather      | Apple     |

## Next steps

[Assign the profile](device-profile-assign.md) and [monitor its status](device-profile-monitor.md).

You can also create device feature profiles for [macOS](macos-device-features-settings.md) devices.
