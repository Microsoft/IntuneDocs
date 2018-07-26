---
# required metadata

title: Microsoft Intune VPN settings for devices running Android
titlesuffix:
description: Learn about the Intune settings you can use to configure VPN connections on devices running Android 
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Configure VPN settings in Microsoft Intune for devices running Android 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

This article shows you the Intune settings you can use to configure VPN connections on devices running Android.


You can configure VPN settings for the following platforms:

- [Android](#android-vpn-settings)
- [Android work profile devices](#android-for-work-vpn-settings)

Depending on the settings you choose, not all the following values are configurable.

## Android VPN settings
**Connection name** - Enter a name for this connection. End users see this name when they browse their device for the list of available VPN connections.
- **IP address or FQDN** - Provide the IP address or fully qualified domain name of the VPN server that devices connect to. Examples: **192.168.1.1**, **vpn.contoso.com**.
- **Authentication method** - Choose how devices authenticate to the VPN server from:
	- **Certificates** - Select a SCEP or PKCS certificate profile you previously created to authenticate the connection. For more details about certificate profiles, see [How to configure certificates](certificates-configure.md).
	- **Username and password** - End users must supply a user name and password to log into the VPN server.
- **Connection type** - Select the VPN connection type from the following list of vendors:
	- **Check Point Capsule VPN**
	- **Cisco AnyConnect**
	- **SonicWall Mobile Connect**
	- **F5 Edge Client**
	- **Pulse Secure**
	- **Citrix**

- **Fingerprint** (Check Point Capsule VPN only) - Specify a string (for example, "Contoso Fingerprint Code") that is used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it prompts the user to trust the VPN server that they are connecting to while showing the fingerprint (The user manually verifies the fingerprint and chooses trust to connect).
- **Enter key and value pairs for the Citrix VPN attributes** (Citrix only) - Enter key and value pairs, provided by Citrix, to configure the properties of the VPN connection.

## Android work profile device VPN settings

- **Connection name** - Enter a name for this connection. End users see this name when they browse their device for the list of available VPN connections.
- **IP address or FQDN** - Provide the IP address or fully qualified domain name of the VPN server that devices connect to. Examples: **192.168.1.1**, **vpn.contoso.com**.
	- **Authentication method** - Choose how devices authenticate to the VPN server from:
		- **Certificates** - Select a SCEP or PKCS certificate profile you previously created to authenticate the connection. For more details about certificate profiles, see [How to configure certificates](certificates-configure.md).
		- **Username and password** - End users must supply a user name and password to log into the VPN server.
- **Connection type** - Select the VPN connection type from the following list of vendors:
	- **Check Point Capsule VPN**
	- **Cisco AnyConnect**
	- **SonicWall Mobile Connect**
	- **F5 Edge Client**
	- **Pulse Secure**

