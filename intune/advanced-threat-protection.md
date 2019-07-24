---
# required metadata

title: Use Microsoft Defender ATP in Microsoft Intune - Azure | Microsoft Docs
description: See how to enable Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) in an end-to-end scenario, including turning on Microsoft Defender ATP in Intune and Microsoft Defender Security Center, onboard devices using a Microsoft Defender ATP configuration profile, create an Intune device compliance policy, create an Azure AD Conditional Access policy, and monitor device compliance.
keywords:
author: brenduns 
ms.author: brenduns
manager: dougeby
ms.date: 07/22/2019

ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.reviewer: joglocke


# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Enforce compliance for Microsoft Defender ATP with Conditional Access in Intune  

Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) and Microsoft Intune work together to help prevent security breaches, and help limit the impact of breaches within an organization.

This feature applies to: Windows 10 devices

For example, someone sends a Word attachment with embedded malicious code to a user within your organization. The user opens the attachment, and enables the content. An elevated privilege attack starts, and an attacker from a remote machine has admin rights to the victim’s device. The attacker then remotely accesses the user's other devices.

This security breach can impact the entire organization.

Microsoft Defender ATP can resolve security events like this scenario. The Microsoft Defender Security Center reports the devices as “high risk”, and includes a detailed report of suspicious activity. In our example, Microsoft Defender ATP detects that the device executed abnormal code, experienced a process privilege escalation, injected malicious code, and issued a suspicious remote shell. Microsoft Defender ATP then gives you options to mitigate the threat.

Using Intune, you can create a compliance policy that determines an acceptable level of risk. If a device exceeds this risk, then the device becomes non-compliant. When combined with Azure Active Directory (AD) Conditional Access, the user is blocked access from corporate resources.

This article shows you how to:

- Enable Intune in Microsoft Defender Security Center, and enable Microsoft Defender ATP in Intune. These tasks create a service-to-service connection between Intune and Microsoft Defender ATP. This connection allows Microsoft Defender ATP to write the machine risk for your Intune devices.
- Create the compliance policy in Intune.
- Enable Conditional Access in Azure Active Directory (AD) on devices based on their threat level.

## Prerequisites

To use Microsoft Defender ATP with Intune, be sure you have the following configured, and ready to use:

- Licensed tenant for Enterprise Mobility + Security E3 and Windows E5 (or Microsoft 365 Enterprise E5)
- Microsoft Intune environment, with [Intune managed](windows-enroll.md) Windows 10 devices that are also Azure AD joined
- [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) and access to the Microsoft Defender Security Center (ATP portal)

## Enable Microsoft Defender ATP in Intune

When you integrate a new application to Intune Mobile Threat Defense and enable the connection, Intune creates a classic conditional access policy in Azure Active Directory. Each MTD app you integrate, like [Defender ATP](advanced-threat-protection.md) or any of our additional [MTD partners](mobile-threat-defense.md#mobile-threat-defense-partners), creates a new classic conditional access policy.  These policies can be ignored, but should not be edited, deleted, or disabled.

Classic conditional access policies for MTD apps: 

- Are used by Intune MTD to require that devices are registered in Azure AD so that they have a device ID. The ID is required so that devices and can successfully report their status to Intune.  
- Are distinct from conditional access policies you might create to help manage MTD.
- By default, don’t interact with other conditional access policies you use for evaluation.  

To view classic conditional access policies, in [Azure](https://portal.azure.com/#home), go to **Azure Active Directory** > **Conditional Access** > **Classic policies**.

### To enable Defender ATP
1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Select **Device compliance** > **Microsoft Defender ATP**, and then below *Connector Settings*, select **Open the Microsoft Defender Security Center**.

    ![Select to open the Microsoft Defender Security Center](./media/advanced-threat-protection/atp-device-compliance-open-microsoft-defender.png)

4. In **Microsoft Defender Security Center**:
    1. Select **Settings** > **Advanced features**.
    2. For **Microsoft Intune connection**, choose **On**:

        ![Enable the connection to Intune](./media/advanced-threat-protection/atp-security-center-intune-toggle.png)

    3. Select **Save preferences**.

4. Go back to Intune, **Device compliance** > **Microsoft Defender ATP**. Set **Connect Windows devices version 10.0.15063 and above to Microsoft Defender ATP** to **On**.
5. Select **Save**.

You typically do this task once. So if Microsoft Defender ATP is already enabled in your Intune resource, then you don't need to do it again.

## Onboard devices using a configuration profile

When an end-user enrolls in Intune, you can push different settings to the device using a configuration profile. This also applies to Microsoft Defender ATP.

Microsoft Defender ATP includes an onboarding configuration package that communicates with [Microsoft Defender ATP services](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) to scan files, detect threats, and report the risk to Microsoft Defender ATP.

When you onboard, Intune gets an auto-generated configuration package from Microsoft Defender ATP. Intune pushes the configuration package to the device when it sends the configuration profile to the device, which allows Microsoft Defender ATP to monitor the device for the threats.

Once you onboard a device using configuration package, then you don't need to do it again. You can also onboard devices using a [group policy or System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

### Create the configuration profile

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Select **Device Configuration** > **Profiles** > **Create profile**.
3. Enter a **Name** and **Description**.
4. For **Platform**, select **Windows 10 and later**
5. For **Profile type**, select **Microsoft Defender ATP (Windows 10 Desktop)**.
6. Configure the settings:

    - **Microsoft Defender ATP client configuration package type**: Select **Onboard** to add the configuration package to the profile. Select **Offboard** to remove the configuration package from the profile.
  
    > [!NOTE]  
    > If you've properly established a connection with Microsoft Defender ATP, Intune will automatically **Onboard** the configuration profile for you, and the **Microsoft Defender ATP client configuration package type** setting will not be available.
  
    - **Sample sharing for all files**: **Enable** allows samples to be collected, and shared with Microsoft Defender ATP. For example, if you see a suspicious file, you can submit it to Microsoft Defender ATP for deep analysis. **Not configured** doesn't share any samples to Microsoft Defender ATP.
    - **Expedite telemetry reporting frequency**: For devices that are at high risk, **Enable** this setting so it reports telemetry to the Microsoft Defender ATP service more frequently.

    [Onboard Windows 10 machines using System Center Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-sccm) has more details on these Microsoft Defender ATP settings.

7. Select **OK**, and **Create** to save your changes, which creates the profile.

## Create the compliance policy
The compliance policy determines an acceptable level of risk on a device.

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Select **Device compliance** > **Policies** > **Create policy**.
3. Enter a **Name** and **Description**.
4. In **Platform**, select **Windows 10 and later**.
5. In the **Microsoft Defender ATP** settings, set **Require the device to be at or under the machine risk score** to your preferred level. Threat level classifications are [determined by Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue).

   - **Clear**: This level is the most secure. The device can't have any existing threats and still access company resources. If any threats are found, the device is evaluated as noncompliant. (Microsoft Defender ATP users the value *Secure*.)
   - **Low**: The device is compliant if only low-level threats exist. Devices with medium or high threat levels aren't compliant.
   - **Medium**: The device is compliant if the threats found on the device are low or medium. If high-level threats are detected, the device is determined as noncompliant.
   - **High**: This level is the least secure, and allows all threat levels. So devices that with high, medium, or low threat levels are considered compliant.

6. Select **OK**, and **Create** to save your changes (and create the policy).

## Assign the policy

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Select **Device compliance** > **Policies**> select your Microsoft Defender ATP compliance policy.
3. Select **Assignments**.
4. Include or exclude your Azure AD groups to assign them the policy.
5. To deploy the policy to the groups, select **Save**. The user devices targeted by the policy are evaluated for compliance.

## Create a Conditional Access policy
The Conditional Access policy blocks access to resources *if* the device is noncompliant. So if a device exceeds the threat level, you can block access to corporate resources, such as SharePoint or Exchange Online.  

> [!TIP]  
> Conditional Access is an Azure Active Directory (Azure AD) technology. The Conditional Access node accessed from *Intune* is the same node as accessed from *Azure AD*.  

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) and select **Conditional Access** > **New policy**.
2. Enter a policy **Name**, and select **Users and groups**. Use the Include or Exclude options to add your groups for the policy, and select **Done**.
3. Select **Cloud apps**, and choose which apps to protect. For example, choose **Select apps**, and select **Office 365 SharePoint Online** and **Office 365 Exchange Online**.

    Select **Done** to save your changes.

4. Select **Conditions** > **Client apps** to apply the policy to apps and browsers. For example, select **Yes**, and then enable **Browser** and **Mobile apps and desktop clients**.

    Select **Done** to save your changes.

5. Select **Grant** to apply Conditional Access based on device compliance. For example, select **Grant access** > **Require device to be marked as compliant**.

    Choose **Select** to save your changes.

6. Select **Enable policy**, and then **Create** to save your changes.

[What's Conditional Access?](conditional-access.md) is a good resource.

## Monitor device compliance
Next, monitor the state of devices that have the Microsoft Defender ATP compliance policy.

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Select **Device compliance** > **Policy compliance**.
3. Find your Microsoft Defender ATP policy in the list, and see which devices are compliant or noncompliant.

## More good stuff
[Microsoft Defender ATP Conditional Access](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/conditional-access)  
[Microsoft Defender ATP risk dashboard](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)  

[Get started with device compliance policies](device-compliance-get-started.md)  
[Conditional Access in Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)