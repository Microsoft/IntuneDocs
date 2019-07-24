---
# required metadata

title: Microsoft Intune VPN settings for macOS devices 
titleSuffix:
description: Learn about the Intune settings you can use to configure VPN connections on macOS devices.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
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

# Configure VPN settings in Microsoft Intune for devices running macOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

This article shows you the Intune settings you can use to configure VPN connections on devices running macOS.

Depending on the settings you choose, not all values in the following list are configurable.

## Base VPN settings

**Connection name** - Enter a name for this connection. End users see this name when they browse their device for the list of available VPN connections.
- **IP address or FQDN** - Provide the IP address or fully qualified domain name of the VPN server that devices connect to. Examples: **192.168.1.1**, **vpn.contoso.com**.
- **Authentication method** - Choose how devices authenticate to the VPN server from:
  - **Certificates** - Under **Authentication certificate**, Choose a SCEP or PKCS certificate profile you previously created to authenticate the connection. For more details about certificate profiles, see [How to configure certificates](certificates-configure.md).
  - **Username and password** - End users must supply a username and password to log into the VPN server.
- **Connection type** - Select the VPN connection type from the following list of vendors:
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Custom VPN**
- **Split tunneling** - **Enable** or **Disable** this option that lets devices decide which connection to use depending on the traffic. For example, a user in a hotel uses the VPN connection to access work files, but use the hotel's standard network for regular web browsing.

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](apps-deploy.md). --->

## Custom VPN settings

If you selected **Custom VPN**, configure these further settings:

- **VPN identifier** This is an identifier for the VPN app you are using, and is supplied by your VPN provider.
- **Enter key and value pairs for the custom VPN attributes** Add or import **Keys** and **Values** that customize your VPN connection. Again, these values are typically supplied by your VPN provider.


## Proxy settings

- **Automatic configuration script** - Use a file to configure the proxy server. Enter the **Proxy server URL** that contains the configuration file. For example, enter `http://proxy.contoso.com`.
- **Address** - Enter the proxy server address (as an IP address).
- **Port number** - Enter the port number associated with the proxy server.
