---
# required metadata

title: Create WiFi profile with pre-shared key - Microsoft Intune - Azure | Microsoft Docs
description: Use a custom profile to create a Wi-Fi profile with a pre-shared key, and get sample XML code for Android, Windows, and EAP-based Wi-Fi profiles in Microsoft Intune
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure

ms.collection: M365-identity-device-management
---
# Use a custom device profile to create a WiFi profile with a pre-shared key - Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Pre-shared keys (PSK) are typically used to authenticates users in WiFi networks, or wireless LANs. With Intune, you can create a WiFi profile using a pre-shared key. To create the profile, use the **Custom device profiles** feature within Intune. This article also includes some examples of how to create an EAP-based Wi-Fi profile.

> [!IMPORTANT]
>- Using a pre-shared key with Windows 10 causes a remediation error to appear in Intune. When this happens, the Wi-Fi profile is properly assigned to the device, and the profile works as expected.
>- If you export a Wi-Fi profile that includes a pre-shared key, be sure the file is protected. The key is in plain text, so it's your responsibility to protect the key.

## Before you begin

- It may be easier to copy the code from a computer that connects to that network, as described later in this article.
- You can add multiple networks and keys by adding more OMA-URI settings.
- For iOS, use Apple Configurator on a Mac station to set up the profile.
- PSK requires a string of 64 hexadecimal digits, or a passphrase of 8 to 63 printable ASCII characters. Some characters, such as asterisk ( * ), aren't supported.

## Create a custom profile
You can create a custom profile with a pre-shared key for Android, Windows, or an EAP-based Wi-Fi profile. To create the profile using the Azure portal, see [Create custom device settings](custom-settings-configure.md). When you create the device profile, choose **Custom** for your device platform. Don't select the Wi-Fi profile. When you choose custom, be sure to: 

1. Enter a name and description of the profile.
2. Add a new OMA-URI setting with the following properties: 

   a. Enter a name for this Wi-Fi network setting.

   b. (Optional) Enter a description of the OMA-URI setting, or leave it blank.

   c. Set the **Data Type** to **String**.

   d. **OMA-URI**:

   - **For Android**: ./Vendor/MSFT/WiFi/Profile/SSID/Settings
   - **For Windows**: ./Vendor/MSFT/WiFi/Profile/SSID/WlanXml

     > [!NOTE]
     > Be sure to include the dot character at the beginning.

     SSID is the SSID for which you’re creating the policy. For example, if the Wi-Fi is named `Hotspot-1`, enter `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`.

   e. **Value Field** is where you paste your XML code. See the examples within this article. Update each value to match your network settings. The comments section of the code includes some pointers.
3. Select **OK**, save, and then assign the policy.

    > [!NOTE]
    > This policy can only be assigned to user groups.

The next time each device checks in, the policy is applied, and a Wi-Fi profile is created on the device. The device can then connect to the network automatically.

## Android or Windows Wi-Fi profile example

The following example includes the XML code for an Android or Windows Wi-Fi profile. The example is provided to show proper format and provide more details. It's only an example, and isn't intended as a recommended configuration for your environment.

### Important considerations

- `<protected>false</protected>` must be set to **false**. When **true**, it could cause the device to expect an encrypted password, and then try to decrypt it; which may result in a failed connection.

- `<hex>53534944</hex>` should be set to the hexadecimal value of `<name><SSID of wifi profile></name>`. Windows 10 devices may return a false `x87D1FDE8 Remediation failed` error, but the device still contains the profile.

- XML has special characters, such as the `&` (ampersand). Using special characters may prevent the XML from working as expected. 

### Example

``` xml
<!--
<hex>53534944</hex> = The hexadecimal value of <name><SSID of wifi profile></name>
<Name of wifi profile> = Name of profile shown to users. It could be <name>Your Company's Network</name>.
<SSID of wifi profile> = Plain text of SSID. Does not need to be escaped. It could be <name>Your Company's Network</name>.
<nonBroadcast><true/false></nonBroadcast>
<Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
<Type of encryption> = Type of encryption used by the network, such as AES.
<protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
<password> = Plain text of the password to connect to the network
-->

<WLANProfile
xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
  <name><Name of wifi profile></name>
  <SSIDConfig>
    <SSID>
      <hex>53534944</hex>
 <name><SSID of wifi profile></name>
    </SSID>
    <nonBroadcast>false</nonBroadcast>
  </SSIDConfig>
  <connectionType>ESS</connectionType>
  <connectionMode>auto</connectionMode>
  <autoSwitch>false</autoSwitch>
  <MSM>
    <security>
      <authEncryption>
        <authentication><Type of authentication></authentication>
        <encryption><Type of encryption></encryption>
        <useOneX>false</useOneX>
      </authEncryption>
      <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial>password</keyMaterial>
      </sharedKey>
      <keyIndex>0</keyIndex>
    </security>
  </MSM>
</WLANProfile>
```

## EAP-based Wi-Fi profile example
The following example includes the XML code for an EAP-based Wi-Fi profile: The example is provided to show proper format and provide more details. It's only an example, and isn't intended as a recommended configuration for your environment.

```xml
    <WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name>testcert</name>
      <SSIDConfig>
        <SSID>
          <hex>7465737463657274</hex>
          <name>testcert</name>
        </SSID>
        <nonBroadcast>true</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication>WPA2</authentication>
            <encryption>AES</encryption>
            <useOneX>true</useOneX>
            <FIPSMode     xmlns="http://www.microsoft.com/networking/WLAN/profile/v2">false</FIPSMode>
          </authEncryption>
          <PMKCacheMode>disabled</PMKCacheMode>
          <OneX xmlns="http://www.microsoft.com/networking/OneX/v1">
            <cacheUserData>false</cacheUserData>
            <authMode>user</authMode>
            <EAPConfig>
              <EapHostConfig     xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                <EapMethod>
                  <Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type>
                  <VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
                  <VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
                  <AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
                </EapMethod>
                <Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                  <Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
                    <Type>13</Type>
                    <EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
                      <CredentialsSource>
                        <CertificateStore>
                          <SimpleCertSelection>true</SimpleCertSelection>
                        </CertificateStore>
                      </CredentialsSource>
                      <ServerValidation>
                        <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
                        <ServerNames></ServerNames>
                      </ServerValidation>
                      <DifferentUsername>false</DifferentUsername>
                      <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</PerformServerValidation>
                      <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName>
                      <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
                        <FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3">
                          <AllPurposeEnabled>true</AllPurposeEnabled>
                          <CAHashList Enabled="true">
                            <IssuerHash>75 f5 06 9c a4 12 0e 9b db bc a1 d9 9d d0 f0 75 fa 3b b8 78 </IssuerHash>
                          </CAHashList>
                          <EKUMapping>
                            <EKUMap>
                              <EKUName>Client Authentication</EKUName>
                              <EKUOID>1.3.6.1.5.5.7.3.2</EKUOID>
                            </EKUMap>
                          </EKUMapping>
                          <ClientAuthEKUList Enabled="true"/>
                          <AnyPurposeEKUList Enabled="false">
                            <EKUMapInList>
                              <EKUName>Client Authentication</EKUName>
                            </EKUMapInList>
                          </AnyPurposeEKUList>
                        </FilteringInfo>
                      </TLSExtensions>
                    </EapType>
                  </Eap>
                </Config>
              </EapHostConfig>
            </EAPConfig>
          </OneX>
        </security>
      </MSM>
    </WLANProfile>
```

## Create the XML file from an existing Wi-Fi connection

You can also create an XML file from an existing Wi-Fi connection. On a Windows computer, use the following steps:

1. Create a local folder for the exported W-Fi- profiles, such as c:\WiFi.
2. Open up a command prompt as an administrator (right-click `cmd` > **Run as administrator**)
3. Run `netsh wlan show profiles`. The names of all the profiles are listed.
4. Run `netsh wlan export profile name="YourProfileName" folder=c:\Wifi`. This command creates a file named `Wi-Fi-YourProfileName.xml` in c:\Wifi.

    - If you're exporting a Wi-Fi profile that includes a pre-shared key, add `key=clear` to the command:
  
      `netsh wlan export profile name="YourProfileName" key=clear folder=c:\Wifi`

      `key=clear` exports the key in plain text, which is required to successfully use the profile.

After you have the XML file, copy and paste the XML syntax into OMA-URI settings > **Data type**. [Create a custom profile](#create-a-custom-profile) (in this article) lists the steps.

> [!TIP]
> `\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}` also includes all the profiles in XML format.

## Best practices

- Before you deploy a Wi-Fi profile with PSK, confirm that the device can connect to the endpoint directly.

- When rotating keys (passwords or passphrases), expect downtime and plan your deployments. Consider pushing new Wi-Fi profiles during non-working hours. Also, warn users that connectivity may be affected.

- For a smooth transition, be sure the end user’s device has an alternate connection to the Internet. For example, the end user can switch back to Guest WiFi (or some other WiFi network) or have cellular connectivity to communicate with Intune. The extra connection allows the user to receive policy updates when the corporate WiFi Profile is updated on the device.
