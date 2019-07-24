---
# required metadata

title: Add VPN settings to iOS devices in Microsoft Intune - Azure | Microsoft Docs
description: Add or create a VPN configuration profile using virtual private network (VPN) configuration settings, including the connection details, authentication methods, and split tunneling in the base settings; the custom VPN settings with the identifier, and the key and value pairs; the per-app VPN settings that include Safari URLs, and on-demand VPNs with SSIDs or DNS search domains; and the proxy settings to include a configuration script, IP or FQDN address, and TCP port in Microsoft Intune on devices running iOS.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology:

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

# Configure VPN settings on iOS devices in Microsoft Intune

Microsoft Intune includes many VPN settings that can be deployed to your iOS devices. These settings are used to create and configure VPN connections to your organization's network. This article describes these settings. Some settings are only available for some VPN clients, such as Citrix, Zscaler, and more.

## Connection type

Select the VPN connection type from the following list of vendors:

- **Check Point Capsule VPN**
- **Cisco Legacy AnyConnect**: Applicable to [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924) app version 4.0.5x and earlier.
- **Cisco AnyConnect**: Applicable to [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690) app version 4.0.7x and later.
- **SonicWall Mobile Connect**
- **F5 Access Legacy**: Applicable to F5 Access app version 2.1 and earlier.
- **F5 Access**: Applicable to F5 Access app version 3.0 and later.
- **Palo Alto Networks GlobalProtect (Legacy)**: Applicable to Palo Alto Networks GlobalProtect app version 4.1 and earlier.
- **Palo Alto Networks GlobalProtect**: Applicable to Palo Alto Networks GlobalProtect app version 5.0 and later.
- **Pulse Secure**
- **Cisco (IPSec)**
- **Citrix VPN**
- **Citrix SSO**
- **Zscaler**: To use Conditional Access, or allow users to bypass the Zscaler sign in screen, then you must integrate Zscaler Private Access (ZPA) with your Azure AD account. For detailed steps, see the [Zscaler documentation](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad). 
- **Custom VPN**

> [!NOTE]
> Cisco, Citrix, F5, and Palo Alto have announced that their legacy clients don't work on iOS 12. You should migrate to the new apps as soon as possible. For more information, see the [Microsoft Intune Support Team Blog](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409).

## Base VPN settings

The settings shown in the following list are determined by the VPN connection type you choose.  

- **Connection name**: End users see this name when they browse their device for a list of available VPN connections.
- **Custom domain name** (Zscaler only): Prepopulate the Zscaler app's sign in field with the domain your users belong to. For example, if a username is `Joe@contoso.net`, then the `contoso.net` domain statically appears in the field when the app opens. If you don't enter a domain name, then the domain portion of the UPN in Azure Active Directory (AD) is used.
- **IP address or FQDN**: The IP address or fully qualified domain name (FQDN) of the VPN server that devices connect with. For example, enter `192.168.1.1` or `vpn.contoso.com`.
- **Organization's cloud name** (Zscaler only): Enter the cloud name where your organization is provisioned. The URL you use to sign in to Zscaler has the name.  
- **Authentication method**: Choose how devices authenticate to the VPN server. 
  - **Certificates**: Under **Authentication certificate**, select an existing SCEP or PKCS certificate profile to authenticate the connection. [Configure certificates](certificates-configure.md) provides some guidance about certificate profiles.
  - **Username and password**: End users must enter a username and password to sign in to the VPN server.  

    > [!NOTE]
    > If username and password are used as the authentication method for Cisco IPsec VPN, they must deliver the SharedSecret through a custom Apple Configurator profile.

- **Excluded URLs** (Zscaler only): When connected to the Zscaler VPN, the listed URLs are accessible outside the Zscaler cloud. 

- **Split tunneling**: **Enable** or **Disable** to let devices decide which connection to use, depending on the traffic. For example, a user in a hotel uses the VPN connection to access work files, but uses the hotel's standard network for regular web browsing.

- **VPN identifier** (Custom VPN, Zscaler, and Citrix): An identifier for the VPN app you're using, and is supplied by your VPN provider.
  - **Enter key/value pairs for your organization's custom VPN attributes**: Add or import **Keys** and **Values** that customize your VPN connection. Remember, these values are typically supplied by your VPN provider.

- **Enable network access control (NAC)** (Citrix SSO, F5 Access): When you choose **I agree**, the device ID is included in the VPN profile. This ID can be used for authentication to the VPN to allow or prevent network access.

  **When using F5 Access**, be sure to:

  - Confirm you're using F5 BIG-IP 13.1.1.5. BIG-IP 14 isn't supported.
  - Integrate BIG-IP with Intune for NAC. See the [Overview: Configuring APM for device posture checks with endpoint management systems](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89) F5 guide.
  - Enable NAC in the VPN profile.

  **When using Citrix SSO with Gateway**, be sure to:

  - Confirm you're using Citrix Gateway 12.0.59 or higher.
  - Confirm your users have Citrix SSO 1.1.6 or later installed on their devices.
  - Integrate Citrix Gateway with Intune for NAC. See the [Integrating Microsoft Intune/Enterprise Mobility Suite with NetScaler (LDAP+OTP Scenario)](https://www.citrix.com/content/dam/citrix/en_us/documents/guide/integrating-microsoft-intune-enterprise-mobility-suite-with-netscaler.pdf) Citrix deployment guide.
  - Enable NAC in the VPN profile.

  **Important details**:  

  - When NAC is enabled, the VPN is disconnected every 24 hours. The VPN can immediately be reconnected.
  - The device ID is part of the profile, but it isn't shown in Intune. This ID isn't stored by Microsoft anywhere, and isn't shared by Microsoft.

  When the device ID is supported by VPN partners, the VPN client, such as Citrix SSO, can get the ID. Then, it can query Intune to confirm the device is enrolled, and if the VPN profile is compliant or not compliant.

  - To remove this setting, recreate the profile, and don't select **I agree**. Then, reassign the profile.

## Automatic VPN settings

- **Per-app VPN**: Enables per-app VPN. Allows the VPN connection to trigger automatically when certain apps are opened. Also associate the apps with this VPN profile. For more information, see [instructions for setting up per-app VPN for iOS](vpn-setting-configure-per-app.md).
  - **Provider Type**: Only available for Pulse Secure and Custom VPN.
  - When using iOS **per-app VPN** profiles with Pulse Secure or a Custom VPN, choose app-layer tunneling (app-proxy) or packet-level tunneling (packet-tunnel). Set the **ProviderType** value to **app-proxy** for app-layer tunneling, or **packet-tunnel** for packet-layer tunneling. If you're not sure which value to use, check your VPN provider's documentation.
  - **Safari URLs that will trigger this VPN**: Add one or more web site URLs. When these URLs are visited using the Safari browser on the device, the VPN connection is automatically established.

- **On-demand VPN**: Configure conditional rules that control when the VPN connection is started. For example, create a condition where the VPN connection is only used when a device isn't connected to a company Wi-Fi network. Or, create a condition. For example, if a device can't access a DNS search domain you enter, then the VPN connection isn't started.

  - **SSIDs or DNS search domains**: Select whether this condition uses wireless network **SSIDs**, or **DNS search domains**. Choose **Add** to configure one or more SSIDs or search domains.
  - **URL string probe**: Optional. Enter a URL that the rule uses as a test. If the device with this profile accesses this URL without redirection, then the VPN connection is started. And, the device connects to the target URL. The user doesn't see the URL string probe site. A URL string probe example is the address of an auditing Web server that checks device compliance before connecting the VPN. Another possibility is that the URL tests the ability of the VPN to connect to a site before connecting the device to the target URL through the VPN.
  - **Domain action**: Choose one of the following items:
    - Connect if needed
    - Never connect
  - **Action**: Choose one of the following items:
    - Connect
    - Evaluate connection
    - Ignore
    - Disconnect

## Proxy settings

If you're using a proxy, configure the following settings. Proxy settings aren't available for Zscaler VPN connections.  

- **Automatic configuration script**: Use a file to configure the proxy server. Enter the **Proxy server URL** (for example `http://proxy.contoso.com`) that includes the configuration file.
- **Address**: Enter the IP address of fully qualified host name of the proxy server.
- **Port number**: Enter the port number associated with the proxy server.

## Next step
[Create VPN profiles in Intune](vpn-settings-configure.md)  
