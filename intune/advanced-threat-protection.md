---
# required metadata

title: Use Windows Defender ATP in Microsoft Intune - Azure | Microsoft Docs
description: See how to enable Windows Defender Advanced Threat Protection (ATP) in an end-to-end scenario, including turning on ATP in Intune and Windows Defender Security Center (ATP portal), onboard devices using an ATP configuration profile, create an Intune device compliance policy, create an Azure AD conditional access policy, and monitor device compliance.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/24/2018

ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.reviewer: joglocke

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Enable Windows Defender ATP with conditional access in Intune

Windows Defender Advanced Threat Protection (ATP) and Microsoft Intune work together to help prevent security breaches, and help limit the impact of breaches within an organization.

This feature applies to: Windows 10 devices

For example, someone sends a Word attachment with embedded malicious code to a user within your organization. The user opens the attachment, and enables the content. An elevated privilege attack starts, and an attacker from a remote machine has admin rights to the victim’s device. The attacker then remotely accesses the user's other devices.

This security breach can impact the entire organization.

Windows Defender ATP can resolve security events like this scenario. The Windows Defender Security Center (ATP console) reports the devices as “high risk”, and includes a detailed report of suspicious activity. In our example, Windows Defender ATP detects that the device executed abnormal code, experienced a process privilege escalation, injected malicious code, and issued a suspicious remote shell. Windows Defender ATP then gives you options to mitigate the threat.

Using Intune, you can create a compliance policy that determines an acceptable level of risk. If a device exceeds this risk, then the device becomes non-compliant. When combined with Azure Active Directory (AD) Conditional Access, the user is blocked access from corporate resources.

This article shows you how to:

- Enable Intune in ATP, and enable ATP in Intune. These tasks create a service-to-service connection between Intune and Windows Defender ATP. This connection allows Windows Defender ATP to write the machine risk for your Intune devices.
- Create the compliance policy in Intune.
- Enable conditional access in Azure Active Directory (AD) on devices based on their threat level.

## Prerequisites

To use ATP with Intune, be sure you have the following configured, and ready to use:

- Licensed tenant for Enterprise Mobility + Security E5 and Windows E5 (or Microsoft 365 Enterprise E5)
- Microsoft Intune environment, with [Intune managed](windows-enroll.md) Windows 10 devices that are also Azure AD joined
- [Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) and access to the Windows Defender Security Center (ATP portal)

## Enable Windows Defender ATP in Intune

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Select **All services**, filter on **Intune**, and select **Microsoft Intune**.
3. Select **Device compliance** > **Windows Defender ATP** > **Open the Windows Defender Advanced Threat Protection admin console**.

    ![Alt text](./media/atp-device-compliance-open-windows-defender.png)

4. In the **Windows Defender Security Center**:
    1. Select **Settings** > **Advanced features**.
    2. For **Microsoft Intune connection**, choose **On**:

        ![Alt text](./media/atp-security-center-intune-toggle.png)

    3. Select **Save preferences**.

5. Go back to Intune, **Device compliance** > **Windows Defender ATP**. Set **Connect Windows 10.0.15063+ devices to Windows Defender Advanced Threat Protection** to **On**.
6. Select **Save**.

You typically do this task once. So if ATP is already enabled in your Intune resource, then you don't need to do it again.

## Onboard devices using a configuration profile

Windows Defender includes an onboard configuration package that is installed on devices. When installed, the package communicates with [Windows Defender ATP services](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) to scan files, detect threats, and report the risk to Windows Defender ATP. Using Intune, you can create a configuration profile that uses this configuration package. Then, assign this profile to devices you're onboarding for the first time.

Once you onboard a device using configuration package, then you don't need to do it again. This is typically a one-time task.

You can also onboard devices using a [group policy or System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-windows-defender-advanced-threat-protection).

The next steps show you how to onboard using Intune.

#### Download configuration package

1. In the [Windows Defender Security Center](https://securitycenter.windows.com), select **Settings** > **Onboarding**.
2. Enter the following settings:
  - **Operating system**: Windows 10
  - **Onboard a machine** > **Deployment method**: Mobile Device Management / Microsoft Intune
3. Select **Download package**, and save the **WindowsDefenderATPOnboardingPackage.zip** file. Extract the file.

This zip file includes **WindowsDefenderATP.onboarding**, which you need in the next steps.

#### Create the ATP configuration profile

This profile uses the onboarding package you downloaded in the previous steps.

1. In the [Azure portal](https://portal.azure.com), select **All services**, filter on **Intune**, and select **Microsoft Intune**.
2. Select **Device Configuration** > **Profiles** > **Create profile**.
3. Enter a **Name** and **Description**.
4. For **Platform**, select **Windows 10 and later**
5. For **Profile type**, select **Windows Defender ATP (Windows 10 Desktop)**.
6. Configure the settings:

  - **Onboard Configuration Package**: Browse and select the **WindowsDefenderATP.onboarding** file you downloaded. This file enables a setting so devices can report to the Windows Defender ATP service.
  - **Sample sharing for all files**: Allows samples to be collected, and shared with Windows Defender ATP. For example, if you see a suspicious file, you can submit it to Windows Defender ATP for deep analysis.
  - **Expedite telemetry reporting frequency**: For devices that are at high risk, enable this setting so it reports telemetry to the Windows Defender ATP service more frequently.
  - **Offboard Configuration Package**: If you want to remove, or "offload" Windows Defender ATP monitoring, you can download an Offload package in the [Windows Defender Security Center](https://securitycenter.windows.com), and add it. Otherwise, skip this property.

    [Onboard Windows 10 machines using System Center Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-sccm-windows-defender-advanced-threat-protection) has more details on these Windows Defender ATP settings.

7. Select **OK**, and **Create** to save your changes, which creates the profile.

## Create the compliance policy
The compliance policy determines an acceptable level of risk on a device.

1. In the [Azure portal](https://portal.azure.com), select **All services**, filter on **Intune**, and select **Microsoft Intune**.
2. Select **Device compliance** > **Policies** > **Create policy**.
3. Enter a **Name** and **Description**.
4. In **Platform**, select **Windows 10 and later**.
5. In the **Device Health** settings, set **Require the device to be at or under the Device Threat Level** to your preferred level:

  - **Secured**: This level is the most secure. The device cannot have any existing threats and still access company resources. If any threats are found, the device is evaluated as noncompliant.
  - **Low**: The device is compliant if only low-level threats exist. Devices with medium or high threat levels are not compliant.
  - **Medium**: The device is compliant if the threats found on the device are low or medium. If high-level threats are detected, the device is determined as noncompliant.
  - **High**: This level is the least secure, and allows all threat levels. So devices that with high, medium or low threat levels are considered compliant.

6. Select **OK**, and **Create** to save your changes (and create the policy).

## Assign the policy

1. In the [Azure portal](https://portal.azure.com), select **All services**, filter on **Intune**, and select **Microsoft Intune**.
2. Select **Device compliance** > **Policies**> select your Windows Defender ATP compliance policy.
3. Select **Assignments**.
4. Include or exclude your Azure AD groups to assign them the policy.
5. To deploy the policy to the groups, select **Save**. The user devices targeted by the policy are evaluated for compliance.

## Create an Azure AD conditional access policy
The conditional access policy blocks access to resources *if* the device is noncompliant. So if a device exceeds the threat level, you can block access to corporate resources, such as SharePoint or Exchange Online.

1. In the [Azure portal](https://portal.azure.com), open **Azure Active Directory** > **Conditional access** > **New policy**.
2. Enter a policy **Name**, and select **Users and groups**. Use the Include or Exclude options to add your groups for the policy, and select **Done**.
3. Select **Cloud apps**, and choose which apps to protect. For example, choose **Select apps**, and select **Office 365 SharePoint Online** and **Office 365 Exchange Online**.

    Select **Done** to save your changes.

4. Select **Conditions** > **Client apps** to apply the policy to apps and browsers. For example, select **Yes**, and then enable **Browser** and **Mobile apps and desktop clients**.

    Select **Done** to save your changes.

5. Select **Grant** to apply conditional access based on device compliance. For example, select **Grant access** > **Require device to be marked as compliant**.

    Choose **Select** to save your changes.

6. Select **Enable policy**, and then **Create** to save your changes.

[What's conditional access?](conditional-access.md) is a good resource.

## Monitor device compliance
Next, monitor the state of devices that have the Windows Defender ATP compliance policy.

1. In the [Azure portal](https://portal.azure.com), select **All services**, filter on **Intune**, and select **Microsoft Intune**.
2. Select **Device compliance** > **Policy compliance**.
3. Find your Windows Defender ATP policy in the list, and see which devices are compliant or noncompliant.

## More good stuff
[Windows Defender ATP conditional access](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/conditional-access-windows-defender-advanced-threat-protection)  
[Windows Defender ATP risk dashboard](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection)  
[Get started with device compliance policies](device-compliance-get-started.md)  
[Conditional access in Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)