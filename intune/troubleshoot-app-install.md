---
title: Troubleshoot app installation issues
titleSuffix: Microsoft Intune
description: Use the Microsoft Intune troubleshooting pane to help you troubleshoot app installation issues.
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/04/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology:
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mghadial
#ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Troubleshoot app installation issues

On Microsoft Intune MDM-managed devices, sometimes app installations can fail. When these app installs fail, it can be challenging to understand the failure reason or troubleshoot the issue. Microsoft Intune provides app installation failure details that allow help desk operators and Intune administrators to view app information to address user help requests. The troubleshooting pane within Intune provides failure details, including details about managed apps on a user's device. Details about the end-to-end lifecycle of an app are provided under each individual device in the **Managed Apps** pane. You can view installation issues, such as when the app was created, modified, targeted, and delivered to a device. 

## App troubleshooting details

Intune provides app troubleshooting details based on the apps installed on a specific user's device.

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. On the **Intune** pane, choose **Troubleshoot**.
4. Click **Select user** to select a user to troubleshoot. The **Select users** pane will be displayed.
5. Select a user by typing the name or email address. Click **Select** at the bottom of the pane. The troubleshooting information for the user is displayed in the **Troubleshoot** pane. 
6. Select the device that you want to troubleshoot from the **Devices** list.
    ![The Intune Troubleshooting pane.](media/troubleshoot-app-install-01.png)
7. Select **Managed Apps** from selected device pane. A list of managed apps is displayed.
    ![Details of a specific device managed by Intune.](media/troubleshoot-app-install-02.png)
8. Select an app from the list where **Installation Status** indicates a failure.
    ![A selected app that shows installation failure details.](media/troubleshoot-app-install-03.png)

    > [!Note]  
    > The same app could be assigned to multiple groups but with different intended actions (intents) for the app. For instance, a resolved intent for an app will show **excluded** if the app is excluded for a user during app assignment. For more information, see [How conflicts between app intents are resolved](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > If an installation failure occurs for a required app, either you or your helpdesk will be able to sync the device and retry the app install.

The app installation error details will indicate the problem. You can use these details to determine the best action to take to resolve the problem. For more information about troubleshooting app installation issues, see [App installation errors](troubleshoot-app-install.md#app-installation-errors).

> [!Note]  
> You can also access the **troubleshooting** pane by pointing your browser to: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## User Group targeted app installation does not reach device
The following actions should be considered when you have problems installing apps:
- If the app does not display in the Company Portal, ensure the app is deployed with **Available** intent and that the user is accessing the Company Portal with the device type supported by the app.
- For Windows BYOD devices, the user needs to add a Work account to the device.
- Check if the user is over the AAD device limit:
  1. Navigate to [Azure Active Directory Device Settings](https://portal.azure.com/#blade/Microsoft_AAD_IAM/DevicesMenuBlade/DeviceSettings/menuId).
  2. Make note of the value set for **Maximum devices per user**.
  3. Navigate to [Azure Active Directory Users](https://portal.azure.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade/AllUsers).
  4. Select the affected user and click **Devices**.
  5. If user is over the set limit then delete any stale records that are no longer needed.
- For iOS DEP devices, ensure that the user is listed as **Enrolled by User** in Intune Device Overview blade. If it shows NA, then deploy a config policy for the Intune Company Portal. For more information, see [Configure the Company Portal app](https://docs.microsoft.com/intune/app-configuration-policies-use-ios#configure-the-company-portal-app-to-support-ios-dep-devices).

## Win32 app installation troubleshooting

Select the Win32 app that was deployed using the Intune management extension. You can select the **Collect logs** option when your Win32 app installation fails. 

> [!IMPORTANT]
> The **Collect logs** option will not be enabled when the Win32 app has been successfully installed on the device.<p>Before you can collect Win32 app log information, the Intune management extension must be installed on the Windows client. The Intune management extension is installed when a PowerShell script or a Win32 app is deployed to a user or device security group. For more information, see [Intune Management extension - Prerequisites](intune-management-extension.md#prerequisites).

### Collect log file

To collect your Win32 app installation logs, first follow the steps provided in the section [App troubleshooting details](troubleshoot-app-install.md#app-troubleshooting-details). Then, continue with the following steps:

1. Click the **Collect logs** option on the **Installation details** blade.

    <image alt="Win32 app installation details - Collect log option" src="media/troubleshoot-app-install-04.png" width="500" />

2. Provide file paths with log file names to begin the log file collection process and click **OK**.
    
    > [!NOTE]
    > Log collection will take less than two hours. Supported file types: *.log, .txt, .dmp, .cab, .zip, .xml, .evtx, and .evtl*. A maximum of 25 file paths are allowed.

3. Once the log files have been collected, you can select the **logs** link to download the log files.

    <image alt="Win32 app log details - Download logs" src="media/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > A notification will be displayed indicating the success of the app log collection.

#### Win32 log collection requirements

There are specific requirements that must be followed to collect log files:

- You must specify the complete log file path. ​
- You can specify environment variables for log collection, such as the following:<br>
  *%PROGRAMFILES%, %PROGRAMDATA% %PUBLIC%, %WINDIR%, %TEMP%, %TMP%*
- Only exact file extensions are allowed, such as:<br>
  *.log, .txt, .dmp, .cab, .zip, .xml*
- The maximum log file to upload is 60 MB or 25 files, whichever occurs first. 
- Win32 app install log collection is enabled for apps that meet the required, available, and uninstall app assignment intent.
- Stored logs are encrypted to protect any personal identifiable information contained in the logs​.
- While opening support tickets for Win32 app failures, attach the related failure logs using the steps provided above.

## App installation errors

The following error messages and descriptions provide details about both Android and iOS installation errors. 

### Android errors

This section mentions both Device Administrator (DA) and Samsung Knox enrollment. For more information, see [Android device administrator enrollment](android-enroll-device-administrator.md) and [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md). 

| Error message/code | Description |
|---------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| The app failed to install. (0xC7D14FB5) | This error message is displayed when Intune cannot determine the root cause of the Android app installation error. No information was provided by Android during the failure. This error is returned when the APK download succeeded, but the app installation failed. This error may occur more commonly due to a bad APK file that cannot be installed onto the device. A possible cause can be when Google Play Protect blocks the install of the app due to security concerns. Another possible cause of this error is when a device does not support the app. For example, if the app requires API version 21+ and the device currently has API version 19. Intune returns this error for both DA and KNOX devices and although there may be a notification that users can click to retry, if there is an issue with the APK, it will never continue to fail. If the app is an available app, the notification can be dismissed. However, if the app is required, it cannot be dismissed. |
| The app installation was canceled because the installation (APK) file was deleted after download, but before installation. (0xC7D14FBA) | The download of the APK succeeded, but before the user installed the app the file was removed from the device. This could happen if there was a large time difference between download and install. For example, the user canceled the original install, waited, and then clicked the notification to try again. This error message is returned this for only DA scenarios. KNOX scenarios can be done silently. We do present a notification to retry so the user can accept instead of cancel. If the app is an available app, the notification can be dismissed. However, if the app is required, it cannot be dismissed. |
| The app installation was canceled because the process was restarted during installation. (0xC7D14FBB) | The device was rebooted during the APK installation process, resulting in a canceled installation. This error message is returned for both DA and KNOX devices. Intune presents a notification that users can click to retry. If the app is an available app, the notification can be dismissed. However, if the app is required, it cannot be dismissed. |
| The application was not detected after installation completed successfully. (0x87D1041C) | The user explicitly uninstalled the app. This error is not returned from the client. It is an error produced when the app was installed at one point, but then the user uninstalled it. This error should only occur for required applications. Users can uninstall non-required apps. This error can only happen in DA. KNOX blocks the uninstall of managed apps. The next sync will repost the notification on the device for the user to install. The user can ignore the notification. This error will continue to be reported until the user installs the app. |
| The download failed because of an unknown error. (0xC7D14FB2) | This error occurs when the download fails. This error can commonly occur due to Wi-Fi issues or slow connections. This error is returned for only DA scenarios. For KNOX scenarios, the user is not prompted to install, this can be done silently. Intune presents a notification that users can click to retry. If the app is an available app, the notification can be dismissed. However, if the app is required, it cannot be dismissed. |
| The download failed because of an unknown error. The policy will be retried the next time the device syncs. (0xC7D15078) | This error occurs when the download fails. This error can commonly occur due to Wi-Fi issues or slow connections. This error is returned for only DA scenarios. For KNOX scenarios, the user is not prompted to install, this can be done silently. |
| The end user canceled the app installation. (0xC7D14FB1) | The user explicitly uninstalled the app. This error is returned when the Android OS install activity was canceled by the user. The user pressed the cancel button when the OS install prompt was presented or clicked away from the prompt. This error is returned for only DA scenarios. For KNOX scenarios, the user is not prompted to install, this can be done silently. Intune presents a notification that users can click to retry. If the app is an available app, the notification can be dismissed. However, if the app is required, it cannot be dismissed. Ask the user not to cancel the install. |
| The file download process was unexpectedly stopped. (0xC7D15015) | The OS stopped the download process before it was complete. This error can occur when the device has low battery or the download is taking too long. This error is returned for only DA scenarios. For KNOX scenarios, the user is not prompted to install, this can be done silently. Intune presents a notification that users can click to retry. If the app is an available app, the notification can be dismissed. However, if the app is required, it cannot be dismissed. Ensure the device has a reliable network connection.  |
| The file download service was unexpectedly stopped. The policy will be retried the next time the device syncs. (0xC7D1507C) | The OS ended the download process before it was completed. This error can occur when the device has low battery or the download is taking too long. This error is returned for only DA scenarios. For KNOX scenarios, the user is not prompted to install, this can be done silently. Manually sync the device or wait for 24 hours and check the status. |
| The app failed to uninstall. (0xc7d14fb8) | This error is a generic uninstall failure. The OS did not specify why the app failed to uninstall. Some admin apps cannot simply be uninstalled. Check to ensure the app can be uninstalled manually and collect the Company Portal logs if the uninstall fails. |
| The app installation APK file used for the upgrade does not match the signature for the current app on the device. (0xc7d14fb7) | Android OS has the limitation of requiring the signing cert for the upgrade version to be exactly the same as the cert used to sign the existing version. If the developer cannot use the same cert to sign the new version, you will need to uninstall the existing app and re-deploy the new app rather than upgrade the existing app. |
| The end user canceled the app installation. (0xc7d14fb9) | Educate the user to accept the Intune deployed app and install the app when prompted. |
| Uninstall of the app was canceled because the process was restarted during installation. (0xc7d14fbc) | The app install process was terminated by the OS or the device was restarted. Retry the install and collect Company Portal logs if this error occurs again. |
| The app installation APK file cannot be installed because it was not signed. (0xc7d14fb6) | By default, Android OS requires apps to be signed. Ensure the app is signed before deployment. |

### iOS errors

| Error message/code | Description/Troubleshooting tips |
|------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (0x87D12906) | Apple MDM Agent returned that the installation command failed. |
| (0x87D1313C) | The network connection was lost while the updated download service URL was sent to the device. Specifically, a server with the specified hostname could not be found. |
| iOS device is currently busy. (0x87D11388) | The iOS device was busy, which resulted in an error. The device was locked. The user needs to unlock the device to install the app. |
| The app installation has failed. (0x87D13B64) | An app installation failure occurred. iOS Console logs are needed to troubleshoot this error. |
| The app is managed, but has expired or been removed by the user. (0x87D13B66) | Either the user explicitly uninstalled the app, or the app is expired but failed to download, or the app detection does not match the response from the device. Additionally, this error could occur based on an iOS 9.2.2 platform bug. |
| The app is scheduled for installation, but needs a redemption code to complete the transaction. (0x87D13B60) | This error typically occurs with iOS Store apps which are paid apps. |
| The application was not detected after installation completed successfully. (0x87D1041C) | The app detection process did not match with the response from the device. |
| The user rejected the offer to install the app. (0x87D13B62) | During initial app install, the user clicked cancel. Ask the user to accept the install request the next time. |
| The user rejected the offer to update the app. (0x87D13B63) | The end user clicked cancel during the update process. Deploy as required or educate the user to accept the upgrade prompt. |
| Unknown error (0x87D103E8) | An unknown app installation error occurred. This is the resulting error when other errors have not occurred. |
| Can only install VPP apps on Shared iPad (-2016330861). | The apps must be obtained using Apple Volume Purchase Program to install on a Shared iPad. |
| Can't install apps when App Store is disabled (-2016330860). | The App Store must be enabled for the user to install the app. |
| Can't find VPP license for app (-2016330859). | Try revoking and reassigning the app license. |
| Can't install system apps with your MDM provider (-2016330858). | Installing apps that are pre-installed by the iOS operating system is not a supported scenario. |
| Can't install apps when device is in Lost Mode (-2016330857). | All use of the device is blocked in Lost Mode. Disable Lost Mode to install apps. |
| Can't install apps when device is in kiosk mode (-2016330856). | Try adding this device to an exclude group for kiosk mode configuration policy to install apps. |
| Can't install 32-bit apps on this device (-2016330852). | The device doesn't support installing 32-bit apps. Try deploying the 64-bit version of the app. |
| User must sign in to the App Store (-2016330855). | The user needs to sign in to the App Store before the app can be installed. |
| Unknown problem. Please try again (-2016330854). | The app installation failed due to an unknown reason. Try again later. |
| The app installation failed. Intune will try again the next time the device syncs (-2016330853). | The app installation encountered a device error. Sync the device to try installing the app again. |
| License Assignment failed with Apple error 'No VPP licenses remaining' (0x87d13b7e) | This behavior is by design. To resolve this, purchase additional VPP licenses or reclaim licenses from users no longer targeted. |
| App Install Failure 12024: Unknown cause. (0x87d13b6e) | Apple hasn't given us sufficient information to determine why the install failed. Nothing to report. |
| Needed app configuration policy not present, ensure policy is targeted to same groups. (0x87d13b7f) | App requires app config but no app config is targeted. Admin should make sure the groups the app is targeted to also has the required app config targeted to to the groups. |
| Device VPP licensing is only applicable for iOS 9.0+ devices. (0x87d13b69) | Upgrade affected iOS devices to iOS 9.0+. |
| The application is installed on the device but is unmanaged. (0x87d13b8f) | This error only happens to LOB apps. The app was installed outside of Intune. To address this error, uninstall the app from the device. The next time the device sync happens, the device should install the app from Intune. |
| User declined app management (0x87d13b68) | Ask the user to accept app management. |
| Unknown error. (0x87d1279d) | This error happens to iOS store apps, but the error scenario is unknown. |
| The latest version of the app failed to update from an earlier version. (0x87D13B9D) | This error message is displayed if the app is installed and managed but with the incorrect version on the device. This situation includes when a device has received a command to update an app but the new version has not yet been installed and reported back. This error will be reported for the first check-in of a device after the upgrade has been deployed, and will occur until the device reports that the new version is installed, or fails due to a different error.  |


### Other installation errors

|  Error message/code  |  Description  |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  0x80073CFF, 0x80CF201C (client error)  |  To install this app, you must have a sideloading-enabled system. Make sure that the app package is signed with a trusted signature and installed on a domain-joined device that has the **AllowAllTrustedApps** policy enabled, or a device that has a Windows Sideloading license with the **AllowAllTrustedApps** policy enabled. For more information, see [Troubleshooting packaging, deployment, and query of Windows Store apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).   |
|  0x80073CF0  |  The package could not be opened. Possible causes:<ul><li> The package is unsigned.</li><li> The publisher name does not match the signing certificate subject.</li></ul> Check the **AppxPackagingOM** event log for information. For more information, see [Troubleshooting packaging, deployment, and query of Windows Store apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).  |
|  0x80073CF3  |  The package failed update, dependency, or conflict validation. Possible causes:<ul><li> The incoming package conflicts with an installed package.</li><li> A specified package dependency is not found.</li><li> The package does not support the correct processor architecture.</li></ul> Check the **AppXDeployment-Server** event log for information. For more information, see [Troubleshooting packaging, deployment, and query of Windows Store apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).  |
|  0x80073CFB  |  The provided package is already installed, and reinstallation of the package is blocked. You could receive this error if you are installing a package that is not identical to the package that is already installed. Confirm the digital signature is also part of the package. When a package is rebuilt or re-signed, that package is no longer bitwise identical to the previously installed package. Two possible options to fix this error are as follows:<ul><li> Increment the version number of the app, then rebuild and re-sign the package.</li><li> Remove the old package for every user on the system before you install the new package.</li></ul> For more information, see [Troubleshooting packaging, deployment, and query of Windows Store apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).  |
|  0x87D1041C  |  Application installation succeeded but application is not detected. The app was deployed successfully by Intune, then subsequently uninstalled. Reasons for the app being uninstalled include:<ul><li> The end user uninstalled the app.</li><li> The identity information in the package does not match what device reports for bad apps.</li><li>For self-updating MSIs, the product version does not match the information of the app after it is updated outside of Intune.</li></ul> Instruct the user to reinstall the app from the company portal. Note that required apps will be reinstalled automatically when the device next checks in.  |
|  0x8000FFFF  |  An unexpected error occurred during installation. Check the installation logs for additional information.  |

## Troubleshooting apps from the Microsoft Store

The information in the topic [Troubleshooting packaging, deployment, and query of Microsoft Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) helps you troubleshoot common problems you might encounter when installing apps from the Microsoft Store, whether by using Intune, or by any other means.

## App troubleshooting resources
- [Deploying Visio and Project as part of your Office Pro Plus Deployment](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [Take Action to Ensure MSfB Apps deployed through Intune install on Windows 10 1903](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [Troubleshooting MSI app deployments in Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [Best practices for software distribution to Intune classic Windows PC agent](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## Next steps

- For additional Intune troubleshooting information, see [Use the troubleshooting portal to help users at your company](help-desk-operators.md). 
- Learn about any known issues in Microsoft Intune. For more information, see [Intune Customer Success](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess).
- Need extra help? See [How to get support for Microsoft Intune](get-support.md).
