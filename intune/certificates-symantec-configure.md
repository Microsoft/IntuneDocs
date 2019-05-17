---
title: Issue DigiCert PKCS certificates with Microsoft Intune
titleSuffix: 
description: Install and configure Intune Certificate Connector to issue PKCS Certificates from DigiCert PKI Manager Web Service to Intune-managed devices.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.prod:
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure

ms.collection: M365-identity-device-management
---
# Set up Intune Certificate Connector for DigiCert PKI Manager Web Service

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

This article show you how to install and configure Intune Certificate Connector to issue PKCS Certificates from a DigiCert PKI Manager Web Service to Intune managed devices.

The DigiCert PKI Manager Web Service is referred as DigiCert CA throughout this article. If you already configured Intune Certificate Connector to issue PKCS Certificates and SCEP Certificates from Microsoft Certification Authority (CA), the same Connector can be used to configure and issue PKCS Certificates from a DigiCert CA. In this case, Intune Certificate Connector can issue the following cetificates:

* PKCS Certificates from a Microsoft CA
* SCEP Certificates from a Microsoft CA
* PKCS Certificates from a DigiCert CA

If you want to use Intune Certificate Connector for Microsoft CA and DigiCert CA, you must complete the Intune Certificate Connector configuration for the Microsoft CA first then follow these steps to configure it for the DigiCert CA.  For more details about configuring Intune Certificate Connector for a Microsoft CA, see [How to configure certificates in Microsoft Intune](certificates-configure.md).

## Prepare to install Intune Certificate Connector

If you are already using Intune Certificate Connector for an existing Microsoft CA, and you want to add DigiCert CA support, skip this step and continue the remaining steps after you install the latest Intune Certificate Connector from the Intune Admin portal. This step is required only when you want to use Intune Certificate Connector for a DigiCert CA standalone.

1. Choose one of the Windows Operating System versions from the following list and install it on a computer:
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. Create a user with administrative privileges and use it to complete the following steps.

3. Update for latest Windows Updates and install them if available.

   > [!IMPORTANT]
   > After installing Windows Updates, restart the computer.

4. Install .NET Framework 3.5:

    a. Open **Control Panel** > **Programs and Features** > **Turn Windows features on or off**

    b. Select **.NET Framework 3.5** and install it.

## Install the DigiCert Registration Authorization Certificate

Use the following steps to get the Registration Authorization (RA) certificate from the DigiCert CA. You must have an active subscription at the DigiCert CA to get the RA Certificate.

1. Save the following code snippet as in a file named **certreq.ini** and update as required (For example: *Subject name in CN format*).

   ```
    [Version] 
    Signature="$Windows NT$" 

    [NewRequest] 
    ;Change to your,country code, company name and common name 
    Subject = "Subject Name in CN format"

    KeySpec = 1 
    KeyLength = 2048 
    Exportable = TRUE 
    MachineKeySet = TRUE 
    SMIME = False 
    PrivateKeyArchive = FALSE 
    UserProtected = FALSE 
    UseExistingKeySet = FALSE 
    ProviderName = "Microsoft RSA SChannel Cryptographic Provider" 
    ProviderType = 12 
    RequestType = PKCS10 
    KeyUsage = 0xa0 

    [EnhancedKeyUsageExtension] 
    OID=1.3.6.1.5.5.7.3.2 ; Client Authentication  // Uncomment if you need a mutual TLS authentication

    ;----------------------------------------------- 
   ```

2. Open an elevated command prompt and generate CSR content using the following command:

   `Certreq.exe -new certreq.ini request.csr`

3. Open the request.csr file in Notepad and copy the CSR content which is to the following format:

    ```
    -----BEGIN NEW CERTIFICATE REQUEST-----
    MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
    …
    …
    fzpeAWo=
    -----END NEW CERTIFICATE REQUEST-----
    ```

4. Logon to the DigiCert CA and navigate to **Get an RA Cert** from the tasks.

   a. Provide the CSR content from Step 3 in the designated text box.

   b. Provide the Certificate Friendly Name in the designated text box.

   c. Click **Continue**.

      This shows you a downloadable link for the RA Certificate.

   d. Download the RA certificate to the local computer.

5. Import the RA Certificate into the Windows Certificate store:

    a. Open an MMC console.

    b. Click **File** > **Add or Remove Snap-ins** > **Certificate** > then click **Add**.

    c. Select **Computer Account** > then click **Next**.

    d. Select **Local Computer** > and then click **Finish**.

    e. Click **OK** on the **Add or Remove Snap-ins** window.Expand **Certificates (Local Computer)** > **Personal** > **Certificates**.

    f. Right-click the **Certificates** node and select **All Tasks** > **Import**.

    g. Select the location of the RA Certificate that you downloaded from the DigiCert CA and click **Next**.

    h. Select **Personal Certificate Store** and click then **Next**.

    i. Click **Finish**. This imports the RA Certificate into the Local Machine-Personal store along with its private key.  

6. Export and import the private key certificate:

    a. Expand **Certificates (Local Machine)** > **Personal** > **Certificates**.

    b. Select the certificate that was imported in the previous step.

    c. Right-click the certificate and choose **All Tasks** > **Export**.

    d. Click **Next** and type the password.

    e. Select the location to export to and click **Finish**.

    f. Follow the same procedure in Step 5 to import the private key certificate into the Local Computer-Personal store.

7. Copy the RA Certificate thumbprint without any spaces.  The following is an example thumbprint:

   ```
   RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”
   ```


   > [!NOTE]
   > If there are any issues getting the RA Certificate from the DigiCert CA, contact DigiCert Customer support.

## Install Intune Certificate Connector

If you are already using the latest Intune Certificate Connector for an existing Microsoft CA and want to add DigiCert CA support, skip this step. Otherwise, download the latest Intune Certificate Connector from the Intune admininstration portal and follow these instructions.

1. Sign into the [Azure portal](https://portal.azure.com).
2. Choose **All services** > **Intune**. Intune is located in the **Monitoring + Management** section.
3. On the **Intune** pane, select **Device configuration**.
4. On the **Device configuration** pane, select **Certification Authority**.
5. Click **Add** and select **Download the connector file**. Save the download to a location where you can access it from the server where you are going to install it. 
3. Run NDESConnectorSetup.exe with elevated privileges.

    a. On the **Installation Options** screen, select **PFX Distribution** as shown in the following screen shot.  Complete the remaining setup with the default selections.

   > [!IMPORTANT]
   > If you want to configure Intune Certificate Connector to issue certificates from a Microsoft CA and a DigiCert CA, select **SCEP and PFX Profile Distribution**. Complete the remaining setup with the default selections.

   ![InstallConnector][InstallConnector]
 
## Configure Intune Certificate Connector

Intune Certificate Connector is installed at `%ProgramFiles%\Microsoft Intune` by default.

1. Open %ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config file in Notepad.

    a. Update the RACertThumbprint key value with the cert thumbprint value you copied in the previous section.  The following is an example:

   ```
   <add key="RACertThumbprint"
   value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>
   ```

    b. Save and close the file.

2. Open services.msc.

    a. Select **Intune Connector Service**.

    b. Stop the service and then start the service.

    c. Close the Services window.

## Setup the Intune administrator account

If you are already using Intune Certificate Connector for an existing Microsoft CA and want to add DigiCert CA support, skip this step and continue with the remaining steps. 

1. Start the NDES Connector user interface from ` %ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe `

    a. Click the **Enrollment** tab and then click **Sign In**.

    b. Provide your Intune tenant admin credentials in the designated text boxes.

    c. Click **Sign In**.  It will display a confirmation dialog with a **Successfully enrolled** message as shown in the following screen shot.
2. Close the NDES Connector user interface.

![ConfigureConnector][ConfigureConnector]
 
## Create a Trusted Certificate Profile

The PKCS Certificates deployed for Intune managed devices must be chained with a Trusted Root Certificate. This requires you to create an Intune Trusted Certificate Profile with the root certificate obtained from the DigiCert CA.

1. Get a Trusted Root Certificate from the DigiCert CA:

    a. Logon to DigiCert CA Admin portal.

    b. Click Manage CAs from Tasks:

    c. Select the appropriate CA from CAs list.

    d. Click Download root certificate to download the Trusted Root Certificate.

2. Create a Trusted Certificate Profile in the Intune administration portal:

    a. Sign in to the [Azure portal](https://portal.azure.com) using Intune tenant admin credentials and search for Intune resources.

    b. Create a Trusted Certificate profile from **Microsoft Intune** > **Device configuration** > **Profiles** > **Create profile**.

    c. Provide the required information in **Name** and **Description** fields then select the target platform. 

    d. Select the Trusted certificate profile from the Profile type drop down list.

    e. Upload the Trusted Root Certificate that you obtained from DigiCert CA in the previous step.

    f. Complete the remaining steps in the profile creation. 

    g. Click **Assignments** and select the appropriate group.  At least one user or device must be part of the assigned group.

## Get the Certificate Profile OID

The Certificate Profile OID is associated with a Certificate Profile template in the DigiCert CA.  To create a PKCS Certificate profile in the Intune administration portal, the certificate template name must be provided in the form of a Certificate Profile OID which is associated with a Certificate template in the DigiCert CA.

1. Login to the DigiCert CA Admin portal.
2. Click Manage Certificate Profiles.
3. Select the Certificate Profile that you want to use.
4. Copy the Certificate Profile OID. It looks similar to the following example:

   ```
   Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 
   ```

   > [!NOTE]
   > If there are any issues obtaining the Certificate Profile OID, contact DigiCert Customer Support.

## Create a PKCS Certificate Profile

1. Sign in to the [Azure portal](https://portal.azure.com) using your Intune tenant administrator credentials and search for Intune resources.
2. Create a PKCS Certificate profile from **Microsoft Intune** > **Device configuration > Profiles** > **Create profile**.

    a. Provide the required information in the **Name** and **Description** fields then select the target platform.

    b. Select the **PKCS certificate profile** from the **Profile type** drop down list.  

    c. Complete the remaining steps to create the profile.

   ![ConfigureProfile][ConfigureProfile]

   > [!IMPORTANT]
   > The following parameters of the PKCS Certificate Profile must be configured with specified values in the following table as shown in screen shot to issue PKCS Certificates through Intune Certificate Connector from DigiCert CA. 

    |PKCS Certificate Parameter | Value | Description |
    | --- | --- | --- |
    | Certificate authority | pki-ws.symauth.com | This value must be DigiCert CA base service FQDN without trailing slashes.  If you are not sure whether this is the correct base service FQDN for your DigiCert CA subscription, contact DigiCert Customer support. <br><br> If this FQDN is incorrect, Intune Certificate Connector won't issue PKCS Certificates from the Symantec CA.| 
    | Certificate authority name | DigiCert | This value must be the string **DigiCert**. <br><br> If there is any change to this value, Intune Certificate Connector won't issue PKCS Certificates from the DigiCert CA.|
    | Certificate template name | Certificate Profile OID from DigiCert CA. <br><br> Ex: `2.16.840.1.113733.1.16.1.2.3.1.1.61904612`| This value must be a Certificate Profile OID obtained in the previous section from the DigiCert CA Certificate Profile template. <br><br> If Intune Certificate Connector cannot find a certificate template associated with this Certificate Profile OID in the DigiCert CA, it won't issue PKCS certificates from the DigiCert CA.|

   > [!NOTE]
   > The PKCS Certificate profiles for Windows platforms doesn’t need to associate with a Trusted Certificate profile. But it is required for non-Windows platform profiles such as Android.

3. Click **Assignments** and select the appropriate group.  At least one user or device must be part of the assigned group.
 
After completing the previous steps, Intune Certificate Connector will issue PKCS Certificates from the DigiCert CA to Intune managed devices in the assigned group. These certificates will be available in the Personal store of the Current User certificate store on the Intune managed device.

### PKCS Certificate Profile supported attributes

|Attribute | Intune Supported formats | DigiCert Cloud CA Supported formats | Result |
| --- | --- | --- | --- |
| Subject Name |Intune supports the subject name in following three formats only: <br><br> 1. Common Name <br> 2. Common Name includes email <br> 3. Common Name as email <br><br> The following is an example: <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | DigiCert CA supports additional attributes.  If you want to select additional attributes, they must be defined with fixed values in the DigiCert Certificate Profile template.| We use Common Name or email from the PKCS Certificate request. <br><br> Any mismatch in attributes selection between the Intune Certificate Profile and the DigiCert Certificate Profile template results in no certificates issued from the DigiCert CA.|
| SAN | Intune supports only the following SAN field values: <br><br> AltNameTypeEmail <br><br> AltNameTypeUpn <br><br> AltNameTypeOtherName (encoded value) | The DigiCert Cloud CA also supports these parameters. If you want to select additional attributes, they must be defined with fixed values in the DigiCert Certificate Profile template. <br><br> AltNameTypeEmail: If this type is not found in SAN, it uses the value from AltNameTypeUpn.  If AltNameTypeUpn is also not found in SAN then it uses the value from Subject Name if it’s in email format.  If still not found, Intune Certificate Connector fails to issue the certificates. <br><br> Ex: `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> AltNameTypeUpn: If this type is not found in SAN, it uses the value from AltNameTypeEmail. If AltNameTypeEmail is also not found in SAN then uses the value from Subject Name if it’s in email format.  If still not found, Intune Certificate Connector fails to issue the certificates.  <br><br> Ex: `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> AltNameTypeOtherName: If this type is not found in SAN, Intune Certificate Connector fails to issue the certificates. <br><br> Ex: `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  **Important Note:** The value of this field is supported only in encoded format (hexadecimal value) by the DigiCert CA. So, for any value in this field, Intune Certificate Connector converts it to base 64 encoded before it submits the certificate request. **Intune Certificate Connector doesn’t validate whether this value is already encoded or not.** | None |

## Troubleshooting

Intune Certificate Connector Service logs are available in `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs` on the NDES Connector machine. Open the logs in the [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) and search for exception or error messages.

| Issue/Error Message | Resolution steps |
| --- | --- |
| Unable to Sign-In with Intune tenant admin account on NDES Connector UI | This can happen when the on-premises Certificate Connector is not enabled in the Intune administration portal. To resolve this issue, use the following steps: <br><br> From Silver Light UI: <br> 1. Logon to the [Intune admin portal](https://admin.manage.microsoft.com) <br> 2. Click ADMIN <br> 3. Select Mobile Device Management > Certificate Connector <br> 4. Click **Configure On-premises Certificate Connector** <br> 5. Select the **Enable Certificate Connector** checkbox <br> 6. Click **OK**. <br><br>Or <br><br> From the Azure portal UI: <br> 1. Sign in to the [Azure portal](https://portal.azure.com) <br> 2. Go to Microsoft Intune <br> 3. Select **Device Configuration** > **Certificate Authority** <br> 4. Click **Enable**. <br><br> After completing the previous steps from either the Silver Light UI or the Azure portal, try to sign in with the same Intune tenant admin account in the NDES Connector UI. |
| NDES Connector certificate could not be found. <br><br> System.ArgumentNullException: Value cannot be null. | Intune Certificate Connector shows this error if the Intune tenant administrator account has never signed in to the NDES Connector UI. <br><br> If this error persists, restart the Intune Service Connector. <br><br> 1. Open services.msc <br> 2. Select **Intune Connector Service**. <br> 3. Right click and select **Restart**.|
| NDES Connector - IssuePfx -Generic Exception: <br> System.NullReferenceException: Object reference not set to an instance of an object. | This error is transient. Restart the Intune Service Connector. <br><br> 1. Open services.msc <br> 2. Select **Intune Connector Service** <br> 3. Right-click and select **Restart**. |
| DigiCert Provider - Failed to get DigiCert policy “The operation has timed out” | Intune Certificate Connector received operation time-out error while communicating with the DigiCert CA. If this error continues to occur, increase the connection timeout value and try again. <br><br> To increase the connection timeout: <br> 1. Goto the NDES Connector computer. <br>2. Open the `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config` file in Notepad. <br> 3. Increase the timeout value for the following parameter: <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4. Restart the Intune Connector Service. <br><br> If the issue persists, contact DigiCert customer support. |
| DigiCert Provider - Failed to get client certificate | Intune Certificate Connector failed to retrieve the Resource Authorization Certificate from Local Machine-Personal certificate store. To resolve this issue, make sure to install the Resource Authorization Certificate in the Local Machine-Personal certificate store along with its private key. <br><br> **Note:** The Resource Authorization certificate must be obtained from the DigiCert CA. For more details, contact DigiCert customer support. | 
| DigiCert Provider - Failed to get DigiCert policy “The request was aborted: Could not create SSL/TLS secure channel.” | This error occurs under the following scenarios: <br><br> 1. Intune Certificate Connector service doesn’t have enough permissions to read the Resource Authorization certificate along with its private key from the Local Machine-Personal certificate store. To resolve this issue, check the Connector service running context account in services.msc. The Connector service must run under NT AUTHORITY\SYSTEM context. <br><br> 2. The PKCS Certificate profile in the Intune admin portal may be configured with an invalid DigiCert CA base service FQDN. The FQDN is similar to `pki-ws.symauth.com`. To resolve this issue, check with DigiCert customer support whether the URL is correct for your subscription. <br><br> 3. Intune Certificate Connector fails to authenticate with DigiCert CA using the Resource Authorization certificate because it is to unable to retrieve its private key. To resolve this issue, make sure to install the Resource Authorization certificate along with its private key in the Local Machine-Personal certificate store. <br><br> If the issue persists, contact DigiCert customer support. |
| DigiCert Provider - Failed to get DigiCert policy “A request element is not understood.” | Intune Certificate Connector failed to get the DigiCert Certificate Profile template, because the Client Profile OID does not match the Intune Certificate Profile. In another case, Intune Certificate Connector is unable to find the certificate profile template that is associated with the given Client Profile OID in DigiCert CA. <br><br> To resolve this issue, make sure to obtain the correct Client Profile OID from the DigiCert Certificate template in the DigiCert CA. Then update the PKCS Certificate profile in the Intune admin portal. <br><br> Obtain Client Profile OID from DigiCert CA: <br> 1. Log on to DigiCert CA admin portal. <br> 2. Click on Manage Certificate Profiles <br> 3. Select the Certificate Profile that you intend to use. <br> 4. Obtain the Certificate Profile OID. It looks similar to the following example: <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> Update the PKCS Certificate profile with correct Certificate Profile OID: <br>1. Log on to Intune admin portal <br> 2. Go to the PKCS Certificate Profile and click **Edit**. <br> 3. Update the Certificate Profile OID in update in Certificate Template name field. <br> 4. Save the PKCS Certificate Profile. |
| DigiCert Provider - Policy Verification failed. <br><br> Attribute does not fall under DigiCert supported Certificate template attributes list | The DigiCert CA shows this message when there is discrepancy between the DigiCert Certificate Profile template and the Intune Certificate Profile. This issue likely happened due to attribute mismatch in SubjectName or SubjectAltName. <br><br> To resolve this issue, make sure to select Intune supported attributes for SubjectName and SubjectAltName in the DigiCert Certificate Profile template. For more information, see the Intune Supported attributes in the Certificate Parameters section. |
| Some User devices are not receiving PKCS certificates from DigiCert CA. | This issue happens when User UPN contains special characters like underscore (Example: `global_admin@intune.onmicrosoft.com`). <br><br> The DigiCert CA doesn’t support special characters in mail_firstname and mail_lastname. <br><br> The following steps help resolve this issue: <br><br> 1.	Log on to DigiCert CA admin portal. <br> 2.	Goto the Manage Certificate Profiles. <br> 3.	Click the Certificate Profile used for Intune. <br> 4.	Click the Customize options link. <br> 5.	Click the Advanced options button. <br> 6.	Under Certificate fields – Subject DN, add Common Name (CN) field and delete existing Common Name (CN) field. Add and delete must be performed together. <br> 7.	Click Save. <br><br> With the preceding change, the DigiCert Certificate profile requests “CN=<upn>” instead of mail_firstname and mail_lastname. |
| User manually deleted already deployed certificate from the device. | Intune redeploys the same certificate during next check-in or policy enforcement. In this case, NDES Connector doesn’t receive a PKCS Certificate request. |

## Next steps

- Use the information provided in this article in addition to the information in [What are Microsoft Intune device profiles?](device-profiles.md) to manage your organization's devices and the certificates on them.

[InstallConnector]:  ./media/certificates-symantec-connector-install.png "Install Intune Certificate Connector and select PFX Distribution"
[ConfigureConnector]: ./media/certificates-symantec-configure-connector-configure.png "Configure Intune Certificate Connector"
[ConfigureProfile]: ./media/certificates-symantec-pkcs-example.png "Create PKCS Certificate profile in the Azure portal"
