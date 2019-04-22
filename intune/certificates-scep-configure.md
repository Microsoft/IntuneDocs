---
title: Use SCEP certificates with Microsoft Intune - Azure | Microsoft Docs
description: To use SCEP certificates in Microsoft Intune, configure your on-premises AD domain, create a certification authority, setup the NDES server, and install the Intune Certificate Connector. Then, create a SCEP certificate profile, and then assign this profile to groups. Also, see the different event IDs and their descriptions, and the diagnostic codes for the Intune connector service.
keywords:
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/05/2019
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:


# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.collection: M365-identity-device-management
---

# Configure and use SCEP certificates with Intune

This article shows how to configure your infrastructure, then create and assign Simple Certificate Enrollment Protocol (SCEP) certificate profiles with Intune.

## On-premises infrastructure requirements overview

- **Active Directory domain**: All servers listed in this section (except for the Web Application Proxy Server) must be joined to your Active Directory domain.

- **Certification Authority** (CA): Must be a Microsoft Enterprise Certification Authority (CA) that runs on an Enterprise edition of Windows Server 2008 R2 or later. A Standalone CA is not supported. For details, see [Install the Certification Authority](http://technet.microsoft.com/library/jj125375.aspx).
    If your CA runs Windows Server 2008 R2, you must [install the hotfix from KB2483564](http://support.microsoft.com/kb/2483564/).

- **NDES Server**: On a Windows Server 2012 R2 or later, set up the Network Device Enrollment Service (NDES) server role. Intune doesn't support using NDES on a server that also runs the Enterprise CA. See [Network Device Enrollment Service Guidance](http://technet.microsoft.com/library/hh831498.aspx) for instructions on how to configure Windows Server 2012 R2 to host NDES.
The NDES server must be joined to a domain within the same forest as the Enterprise CA. More information about deploying the NDES server in a separate forest, isolated network, or internal domain can be found in [Using a Policy Module with the Network Device Enrollment Service](https://technet.microsoft.com/library/dn473016.aspx).

- **Microsoft Intune Certificate Connector**: In the Intune portal, go to **Device configuration** > **Certificate Connectors** > **Add**, and follow the *Steps to install connector for SCEP*. Use the download link in the portal to start download of the certificate connector installer **NDESConnectorSetup.exe**.  You'll run this installer on the server with the NDES role.  

This NDES Certificate connector also supports Federal Information Processing Standard (FIPS) mode. FIPS isn't required, but you can issue and revoke certificates when it's enabled.

- **Web Application Proxy Server** (optional): Use a server that runs Windows Server 2012 R2 or later as a Web Application Proxy (WAP) server. This configuration:
  - Allows devices to receive certificates using an Internet connection.
  - Is a security recommendation when devices connect through the Internet to receive and renew certificates.
  
- **Azure AD Application Proxy** (optional): The Azure AD Application Proxy can be used instead of a dedicated Web Application Proxy (WAP) Server to publish the NDES Server to the Internet. For more information, see [How to provide secure remote access to on-premises applications](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).

#### Additional

- The server that hosts WAP [must install an update](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) that enables support for the long URLs that are used by the Network Device Enrollment Service. This update is included with the [December 2014 update rollup](http://support.microsoft.com/kb/3013769), or individually from [KB3011135](http://support.microsoft.com/kb/3011135).
- The WAP server must have an SSL certificate that matches the name being published to external clients, and trust the SSL certificate used on the NDES server. These certificates enable the WAP server to terminate the SSL connection from clients, and create a new SSL connection to the NDES server.

For more information, see [Plan certificates for WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) and [general information about WAP servers](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)).

### Network requirements

If you don't use a reverse proxy, such as WAP or Azure AD App Proxy, then allow TCP traffic on port 443 from all hosts/IP addresses on the internet to the NDES server.

Allow all ports and protocols necessary between the NDES server and any supporting infrastructure. For example, the NDES server needs to communicate with the CA, DNS servers, Configuration Manager servers, domain controllers, and possibly other services within your environment.

We highly recommend publishing the NDES server through a reverse proxy, such as the [Azure AD application proxy](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/), [Web Access Proxy](https://technet.microsoft.com/library/dn584107.aspx), or a third-party proxy.

### Certificates and templates  

|Object|Details|
|----------|-----------|
|**SCEP Certificate Template**|Configure this template on your issuing CA. Used when issuing certificates to the users or devices.|
|**Client authentication certificate**|Requested from your issuing CA or public CA; you install this certificate on the NDES Server, used by the Intune certificate connector.|
|**Server authentication certificate**|Requested from your issuing CA or public CA; you install and bind this SSL certificate in IIS on the NDES server. If the previously mentioned Client authentication certificate also has server authentication key usage set (**Enhanced Key Usages**), then you can use the same certificate.|
|**Trusted Root CA certificate**|You export this certificate as a **.cer** file from the root CA or any device that trusts the root CA. Then, assign it to users, devices, or both using the Trusted CA certificate profile in [Azure portal](https://portal.azure.com).<br /><b>NOTE:<b />When a SCEP certificate profile is assigned, be sure to assign the Trusted root certificate profile referenced in your SCEP certificate profile to the same user or device group.<br /><br />You use a single Trusted Root CA certificate per operating system platform, and associate it with each Trusted Root Certificate profile you create.<br /><br />You can use additional Trusted Root CA certificates when needed. For example, you might do this to provide a trust to a CA that signs the server authentication certificates for your Wi-Fi access points.|

### Accounts

|Name|Details|
|--------|-----------|
|**NDES service account**|Enter a domain user account to use as the NDES Service account. |

## Configure your infrastructure
Before you can configure certificate profiles, complete the following steps. These steps require knowledge of Windows Server 2012 R2 or later, and Active Directory Certificate Services (ADCS):

#### Step 1 - Create an NDES service account

Create a domain user account to use as the NDES service account. You enter this account when you configure templates on the issuing CA before you install and configure NDES. Make sure the user has the default rights, **Logon Locally**, **Logon as a Service** and **Logon as a batch job** rights. Some organizations have hardening policies that disable those rights.

#### Step 2 - Configure certificate templates on the certification authority
In this step, you:

- Configure and publish required certificate templates for SCEP, Intune Certificate Connector and IIS

##### Access your Issuing CA

1. Sign in to your issuing CA as an enterprise administrator.

2. Open the Certification Authority Microsoft Management Console (MMC). Either **Run** 'certsrv.msc' or in **Server Manager**, click **Tools**, and then click **Certification Authority**.

3. Select the **Certificate Templates** node, click **Action** > **Manage**.

##### Create SCEP certitificate template

1. Duplicate an existing template, like the User template, or create a new custom template for use with NDES. Than update the configuration as shown bellow.

   >[!NOTE]
   > The NDES SCEP certificate template must be based off a v2 Certificate Template (with Windows 2003 compatibility).

   The template must have the following configurations:

   - In **General**:
   
       - Confirm the **Publish certificate in Active Directory** property is **not** checked.
       - Enter a friendly **Template display name** for the template.

   - In **Subject Name**, select **Supply in the request**. (Security is enforced by the Intune policy module for NDES).

   - In **Extensions**, confirm the **Description of Application Policies** includes **Client Authentication**.

     > [!IMPORTANT]
     > For iOS and macOS certificate templates, on the **Extensions** tab, edit **Key Usage**, and confirm **Signature is proof of origin** is not selected.

   - In **Security**, add the NDES service account, and give it **Enroll** permissions to the template. Intune admins who create SCEP profiles require **Read** rights so that they can browse to the template when creating SCEP profiles.

     > [!NOTE]
     > To revoke certificates, the NDES service account needs *Issue and Manage Certificates* rights for each certificate template used by a certificate profile.

2. Review the **Validity period** on the **General** tab of the template. By default, Intune uses the value configured in the template. However, you can configure the CA to allow the requester to enter a different value, which you can then set from within the Intune Administrator console. If you want to always use the value in the template, skip the rest of this step.

   > [!IMPORTANT]
   > iOS and macOS always use the value set in the template, regardless of other configurations you make.

Example template configuration:

![Template, request handling tab](./media/scep_ndes_request_handling.png)

![Template, subject name tab](./media/scep_ndes_subject_name.jpg)

![Template, security tab](./media/scep_ndes_security.jpg)

![Template, extensions tab](./media/scep_ndes_extensions.jpg)

![Template, issuance requirements tab](./media/scep_ndes_issuance_reqs.jpg)

> [!IMPORTANT]
> For Application Policies, only add the application policies required. Confirm your choices with your security admins.

##### Create client certitificate template

Intune NDES Connector will require a certificate with Client Authentiction Enhanced Key Usage and Subject name equal to the FQDN of the machine where the connector is installed, as such a Template with the following properties is required:

   - **Extensions** > **Application Policies** must contain **Client Authentication**
   - **Subject name** > **Supply in the request**.
   
If you already have a template that respects this properties, it can be reused, otherwise a new template must be created by either duplicating an existing one or creating a custom template.

##### Create server certitificate template

Comunications between the devices and IIS on the NDES server must be using HTTPS, as such a certificate will be required. This template can be the **Web Server** template, however if you prefer to have a dedicated template, the following must be respected: 
   
   - **Extensions** > **Application Policies** must contain **Server Authentication**
   - **Subject name** > **Supply in the request**.

##### Configure the CA to allow the requester to enter the validity period:

1. On the CA, run the following commands:
   - **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   - **net stop certsvc**
   - **net start certsvc**

2. On the issuing CA, use the Certification Authority snap-in to publish the certificate template.
   Select the **Certificate Templates** node, click **Action** > **New** > **Certificate Template to Issue**, and then select the template you created in step 2.

3. Validate that the template published by viewing it under the **Certificate Templates** folder.

#### Step 3 - Configure prerequisites on the NDES server
In this step, you:

- Add NDES Role to a Windows Server and configure IIS to support NDES
- Add the NDES Service account to the IIS_IUSR group
- Set the service principal name (SPN) for the NDES Service account
- Configure NDES for use with the issuing CA

1. On the server that hosts NDES, sign in as an **Enterprise Administrator**, and then use the [Add Roles and Features Wizard](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11)) to install NDES:

   i. In the Wizard, select **Active Directory Certificate Services** to gain access to the AD CS Role Services. Select the **Network Device Enrollment Service**, uncheck **Certification Authority**, and then complete the wizard.

      > [!TIP]
      > In **Installation progress**, don't check **Close**. Instead, select the **Configure Active Directory Certificate Services on the destination server** link. The **AD CS Configuration** wizard opens, which you use for the next step. After AD CS Configuration opens, you can close the Add Roles and Features wizard.

   ii. When NDES is added to the server, the wizard also installs IIS. Confirm IIS has the following configuration:

       - **Web Server** > **Security** > **Request Filtering**

       - **Web Server** > **Application Development** > **ASP.NET 3.5** 

            Installing ASP.NET 3.5 installs .NET Framework 3.5. When installing .NET Framework 3.5, install both the core **.NET Framework 3.5** feature and **HTTP Activation**.

       - **Web Server** > **Application Development** > **ASP.NET 4.5** 

            Installing ASP.NET 4.5 installs .NET Framework 4.5. When installing .NET Framework 4.5, install the core **.NET Framework 4.5** feature, **ASP.NET 4.5**, and the **WCF Services** > **HTTP Activation** feature.

       - **Management Tools** > **IIS 6 Management Compatibility** > **IIS 6 Metabase Compatibility**

       - **Management Tools** > **IIS 6 Management Compatibility** > **IIS 6 WMI Compatibility**

       - On the server, add the NDES service account as a member of the local **IIS_IUSR** group.

2. In an elevated command prompt, run the following command to set the SPN of the NDES Service account:

    `setspn -s http/<DNS name of NDES Server> <Domain name>\<NDES Service account name>`

    For example, if your NDES Server is named **Server01**, your domain is **Contoso.com**, and the service account is **NDESService**, use:

    `setspn –s http/Server01.contoso.com contoso\NDESService`

3. On the NDES Server, open the AD CS Configuration wizard, and then make the following updates:

    > [!TIP]
    > If you clicked the link in the previous step, this wizard is already open. Otherwise, open Server Manager to access the post-deployment configuration for Active Directory Certificate Services.

   - In **Role Services**, select the **Network Device Enrollment Service**
   - In **Service Account for NDES**, enter the NDES Service Account
   - In **CA for NDES**, click **Select**, and then select the issuing CA where you configured the certificate template
   - In **Cryptography for NDES**, set the key length to meet your company requirements.
   - In **Confirmation**, select **Configure** to complete the wizard.

#### Step 4 - Configure IIS for use with Intune NDES
In this step, you:

- Bind the server authentication (SSL) certificate in IIS
- Configure Request Filtering in IIS to allow long URLs
- Define what SCEP templates NDES will use for each purpose

1. On your NDES Server, request and install a **server authentication** certificate from your internal CA or public CA. You then bind this SSL certificate in IIS.

    > [!TIP]
    > After you bind the SSL certificate in IIS, install a client authentication certificate. This certificate can be issued by any CA that is trusted by the NDES Server. The same certificate can be used if the certificate has the client and server authentication key usages set (**Enhanced Key Usages**). Review the following steps for information about these authentication certificates.

   i. After you get the server authentication certificate, open **IIS Manager**, and select the **Default Web Site**. In the **Actions** pane, select **Bindings**.

   ii. Select **Add**, set **Type** to **https**, and then confirm the port is **443**. Only port 443 is supported for standalone Intune.

   iii. For **SSL certificate**, enter the server authentication certificate.
   
      > [!NOTE]
      > If the NDES server uses an external and internal name for a single network address, then the server authentication certificate must have:
      > - A **Subject Name** with an external public server name
      > - A **Subject Alternative Name** that includes the internal server name

2. Still in **IIS Manager**, select the **Default Web Site** in the **Connections** pane, and then open **Request Filtering**.

3. Select **Edit Feature Settings**, and then set the values:

    - **query string (Bytes)** = **65534**
    - **Maximum URL length (Bytes)** = **65534**

    ![IIS max URL and query length](./media/SCEP_IIS_max_URL.png)

4. Review the following registry key:

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

    Confirm the following values are set as DWORD entries:

    - Name: **MaxFieldLength**, with a decimal value (DWORD) of **65534**
    - Name: **MaxRequestBytes**, with a decimal value (DWORD) of **65534**

5. Define what SCEP templates NDES will use for each purpose update by updating the following registry key on the NDES Server:

    `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

    To update this key, identify the certificate template's **Purpose** (found on its **Request Handling** tab). Then, update the corresponding registry entry by replacing the existing data with the name of the certificate template (not the display name of the template) that you specified in Step 2. 
    The following table maps the SCEP certificate template to be used by each purpose in the registry:

    |Certificate template Purpose (On the Request Handling tab)|Registry value to edit|Value seen in the Intune admin console for the SCEP profile|
    |---|---|---|
    |Signature|SignatureTemplate|Digital Signature|
    |Encryption|EncryptionTemplate|Key Encipherment|
    |Signature and encryption|GeneralPurposeTemplate|Key Encipherment<br/>Digital Signature|

    For example, if the Purpose of your certificate template is **Encryption**, then edit the **EncryptionTemplate** value to be the name of your certificate template.

6. Restart the server. Do not use **iisreset**; it doesn't finalize these changes.
7. Browse to `http://*FQDN*/certsrv/mscep/mscep.dll`. You should see an NDES page similar to the following:

    ![Test NDES](./media/SCEP_NDES_URL.png)

    If you get a **503 Service unavailable**, check the event viewer. It's likely that the application pool is stopped due to a missing right for the NDES user. Those rights are described in Step 1.

#### Step 5 - Enable, install, and configure the Intune certificate connector
In this step, you:

- Request a client authentication certificate for the Intune certificate connector
- Enable support for NDES in Intune.
- Download, install, and configure the Certificate Connector on the server hosting the Network Device Enrollment Service (NDES) role a server in your environment. To increase the scale of the NDES implementation in your organization, you can install multiple NDES servers with a Microsoft Intune Certificate Connector on each NDES server.

1. On your NDES Server, request and install a **client authentication** certificate from your internal CA, or a public certificate authority. This certificate can be the same certificate as the server authentication certificate if that certificate has both capabilities.

    The client authentication certificate must have the following properties:

    - **Enhanced Key Usage**: This value must include **Client Authentication**

    - **Subject Name**: The value must be equal to the DNS name of the server where you're installing the certificate (the NDES Server)

2. Download the certificate connector

    > [!IMPORTANT] 
    > The Microsoft Intune Certificate Connector **must** be installed on a separate Windows server. It can't be installed on the issuing Certificate Authority (CA). It **must** also be installed on the same server as the Network Device Enrollment Service (NDES) role.

    i. In the [Azure portal](https://portal.azure.com), select **All services**, filter on **Intune**, and select **Microsoft Intune**.
    
    ii. Select **Device configuration** > **Certification Connectors** > **Add**.
    
    iii. Download and save the connector for SCEP file. Save it to a location accessible from the server where you're going to install the connector.

       ![ConnectorDownload](./media/certificates-scep-configure/download-certificates-connector.png)


3. After the download completes, go to the server that hosts your Network Device Enrollment Service (NDES). Then:

    i. Be sure .NET 4.5 Framework is installed, as it's required by the NDES Certificate connector. .NET 4.5 Framework is automatically included with Windows Server 2012 R2 and newer versions.
    
    ii. Run the installer (**NDESConnectorSetup.exe**). The installer also installs the policy module for NDES and the CRP Web Service. The CRP Web Service, CertificateRegistrationSvc, runs as an application in IIS.

    > [!NOTE]
    > When you install NDES for standalone Intune, the CRP service automatically installs with the Certificate Connector. When you use Intune with Configuration Manager, you install the Certificate Registration Point as a separate site system role.

4. When prompted for the client certificate for the Certificate Connector, choose **Select**, and select the **client authentication** certificate you installed on your NDES Server in Step 4.

    After you select the client authentication certificate, you are returned to the **Client Certificate for Microsoft Intune Certificate Connector** surface. Although the certificate you selected is not shown, select **Next** to view the properties of that certificate. Select **Next**, and then **Install**.

    > [!IMPORTANT]
    > Internet Explorer Enhanced Security Configuration [must be disabled on the NDES server](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx) hosting the Intune Certificate Connector.

5. After the wizard completes, but before closing the wizard, **Launch the Certificate Connector UI**.

    > [!TIP]
    > If you close the wizard before launching the Certificate Connector UI, you can reopen it by running the following command:
    >
    > <install_Path>\NDESConnectorUI\NDESConnectorUI.exe

6. In the **Certificate Connector** UI:

    i. If your organization uses a proxy server and the proxy is needed for the NDES server to access the Internet, select **Use proxy server**. Then enter the proxy server name, port, and account credentials to connect.

    ii. Select **Sign In**, and enter your Intune service administrator credentials, or credentials for a tenant administrator with the global administration permission. A sucessfull enrollment is represented by a popup window with the message: "Sucessfully enrolled".
    
    > [!IMPORTANT]
    > The user account must be assigned a valid Intune license. If the user account does not have a valid Intune license, then NDESConnectorUI.exe fails.
    
    > [!TIP]
    > After you sucessfully sign-in, the Intune Certificate Connector downloads a certificate from Intune that can be found in Local Machine certificates. This certificate is used for authentication between the connector and Intune.
  
    iii. Select the **Advanced** tab, and then enter credentials for an account that has the **Issue and Manage Certificates** permission on your issuing Certificate Authority. **Apply** your changes. If you leave **Use this computer's SYSTEM Account (default)** selected, then it's the machine that needs **Issue and Manage Certificates** permission.

    You can now close the Certificate Connector UI.

7. Open a command prompt, enter **services.msc**, and then **Enter**. Right-click the **Intune Connector Service** > **Restart**.

To validate that the service is running, open a browser, and enter the following URL. It should return a **403** error:

`http://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

> [!NOTE]
> TLS 1.2 support is included with the NDES Certificate connector. So if the server with NDES Certificate connector installed supports TLS 1.2, then TLS 1.2 is used. If the server doesn't support TLS 1.2, then TLS 1.1 is used. Currently, TLS 1.1 is used for authentication between the devices and server.

## Create a SCEP certificate profile

1. In the [Azure portal](https://portal.azure.com), select **All services**, filter on **Intune**, and select **Microsoft Intune**.
2. Select **Device configuration** > **Profiles** > **Create profile**.
3. Enter a **Name** and **Description** for the SCEP certificate profile.
4. From the **Platform** drop-down list, select the device platform for this SCEP certificate. Currently, you can select one of the following platforms for device restriction settings:
   - **Android**
   - **Android Enterprise**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 and later**
   - **Windows 10 and later**
5. From the **Profile** type drop-down list, select **SCEP certificate**.
6. Enter the following settings:

   - **Certificate type**: Choose **User** for user certificates. A **User** certificate type can contain both user and device attributes in the subject and SAN of the certificate.  Choose **Device** for scenarios such as user-less devices, like kiosks, or for Windows devices, placing the certificate in the Local Computer certificate store. **Device** certificates can only contain device attributes in the subject and SAN of the certificate.  **Device** certificates are available for the following platforms:  
     - Android Enterprise - Work Profile
     - iOS
     - macOS
     - Windows 8.1 and later
     - Windows 10 and later


   - **Subject name format**: Select how Intune automatically creates the subject name in the certificate request. The options change if you choose a **User** certificate type or **Device** certificate type. 

        **User certificate type**  

        You can include the user's email address in the subject name. Choose from:

        - **Not configured**
        - **Common name**
        - **Common name including email**
        - **Common name as email**
        - **IMEI (International Mobile Equipment Identity)**
        - **Serial number**
        - **Custom**: When you select this option, a **Custom** text box is also shown. Use this field to enter a custom subject name format, including variables. Custom format supports two variables: **Common Name (CN)** and **Email (E)**. **Common Name (CN)** can be set to any of the following variables:

            - **CN={{UserName}}**: The user principal name of the user, such as janedoe@contoso.com
            - **CN={{AAD_Device_ID}}**: An ID assigned when you register a device in Azure Active Directory (AD). This ID is typically used to authenticate with Azure AD.
            - **CN={{SERIALNUMBER}}**: The unique serial number (SN) typically used by the manufacturer to identify a device
            - **CN={{IMEINumber}}**: The International Mobile Equipment Identity (IMEI) unique number used to identify a mobile phone
            - **CN={{OnPrem_Distinguished_Name}}**: A sequence of relative distinguished names separated by comma, such as `CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com`

                To use the `{{OnPrem_Distinguished_Name}}` variable, be sure to sync the `onpremisesdistingishedname` user attribute using [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) to your Azure AD.

            - **CN={{onPremisesSamAccountName}}**: Admins can sync the samAccountName attribute from Active Directory to Azure AD using Azure AD connect into an attribute called `onPremisesSamAccountName`. Intune can substitute that variable as part of a certificate issuance request in the subject of a SCEP certificate.  The samAccountName attribute is the user logon name used to support clients and servers from a previous version of Windows (pre-Windows 2000). The user logon name format is: `DomainName\testUser`, or only `testUser`.

                To use the `{{onPremisesSamAccountName}}` variable, be sure to sync the `onPremisesSamAccountName` user attribute using [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) to your Azure AD.

            By using a combination of one or many of these variables and static strings, you can create a custom subject name format, such as:  

            **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**

            In this example, you created a subject name format that, in addition to the CN and E variables, uses strings for Organizational Unit, Organization, Location, State, and Country values. [CertStrToName function](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) describes this function, and its supported strings.

        **Device certificate type**  

        When you use the **Device** certificate type, you can also use the following device certificate variables for the value:  

        ```
        "{{AAD_Device_ID}}",
        "{{Device_Serial}}",
        "{{Device_IMEI}}",
        "{{SerialNumber}}",
        "{{IMEINumber}}",
        "{{AzureADDeviceId​}}",
        "{{WiFiMacAddress}}",
        "{{IMEI}}",
        "{{DeviceName}}",
        "{{FullyQualifiedDomainName}}",
        "{{MEID}}",
        ```

        These variables can be added with static text in a custom value textbox. For example, the common name can be added as `CN = {{DeviceName}}text`.

        > [!IMPORTANT]
        >  - In the static text of the subject, curly brackets **{ }** not enclosing a variable will resolve to an error. 
        >  - When using a device certificate variable, enclose the variable in curly brackets **{ }**.
        >  - `{{FullyQualifiedDomainName}}` only works for Windows and domain-joined devices. 
        >  -  When use device properties such as IMEI, Serial Number, and Fully Qualified Domain Name in the subject or SAN for a device certificate, be aware that these properties could be spoofed by a person with access to the device.
        >  - Profile will not install on device if the device variables specified are not supported. For example, if {{IMEI}} is used in the subject name of the SCEP profile assigned to a device that does not have an IMEI number, the profile installation will fail. 


   - **Subject alternative name**: Enter how Intune automatically creates the values for the subject alternative name (SAN) in the certificate request. The options change if you choose a **User** certificate type or **Device** certificate type. 

        **User certificate type**  

        The following attributes are available:

        - Email address
        - User principal name (UPN)

            For example, if you select a user certificate type, you can include the user principal name (UPN) in the subject alternative name. If a client certificate is used to authenticate to a Network Policy Server, set the subject alternative name to the UPN. 

        **Device certificate type**  

        A table format text box that you can customize. The following attributes are available:

        - DNS

        With the **Device** certificate type, you can use the following device certificate variables for the value:  

        ```
        "{{AAD_Device_ID}}",
        "{{Device_Serial}}",
        "{{Device_IMEI}}",
        "{{SerialNumber}}",
        "{{IMEINumber}}",
        "{{AzureADDeviceId​}}",
        "{{WiFiMacAddress}}",
        "{{IMEI}}",
        "{{DeviceName}}",
        "{{FullyQualifiedDomainName}}",
        "{{MEID}}",
        ```

        These variables can be added with static text in the custom value textbox. For example, the DNS attribute can be added as `DNS name = {{AzureADDeviceId}}.domain.com`.

        > [!IMPORTANT]
        >  - In the static text of the SAN, curly brackets **{ }**, pipe symbols **|**, and semicolons **;** don't work. 
        >  - When using a device certificate variable, enclose the variable in curly brackets **{ }**.
        >  - `{{FullyQualifiedDomainName}}` only works for Windows and domain-joined devices. 
        >  -  When use device properties such as IMEI, Serial Number, and Fully Qualified Domain Name in the subject or SAN for a device certificate, be aware that these properties could be spoofed by a person with access to the device.
        >  - Profile will not install on device if the device variables specified are not supported. For example, if {{IMEI}} is used in the subject alternative name of the SCEP profile assigned to a device that does not have an IMEI number, the profile installation will fail.  

   - **Certificate validity period**: If you ran the `certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE` command on the issuing CA, which allows a custom validity period, you can enter the amount of remaining time before the certificate expires.<br>You can enter a value that is lower than the validity period in the certificate template, but not higher. For example, if the certificate validity period in the certificate template is two years, you can enter a value of one year, but not a value of five years. The value must also be lower than the remaining validity period of the issuing CA's certificate. 
   - **Key storage provider (KSP)** (Windows Phone 8.1, Windows 8.1, Windows 10): Enter where the key to the certificate is stored. Choose from one of the following values:
     - **Enroll to Trusted Platform Module (TPM) KSP if present, otherwise Software KSP**
     - **Enroll to Trusted Platform Module (TPM) KSP, otherwise fail**
     - **Enroll to Passport, otherwise fail (Windows 10 and later)**
     - **Enroll to Software KSP**

   - **Key usage**: Enter the key usage options for the certificate. Your options:
     - **Key encipherment**: Allow key exchange only when the key is encrypted
     - **Digital signature**: Allow key exchange only when a digital signature helps protect the key
   - **Key size (bits)**: Select the number of bits contained in the key
   - **Hash algorithm** (Android, Windows Phone 8.1, Windows 8.1, Windows 10): Select one of the available hash algorithm types to use with this certificate. Select the strongest level of security that the connecting devices support.
   - **Root Certificate**: Choose a root CA certificate profile you previously configured and assigned to the user and/or device. This CA certificate must be the root certificate for the CA that issues the certificate that you are configuring in this certificate profile. Be sure to assign this trusted root certificate profile to the same group assigned in the SCEP certificate profile.
   - **Extended key usage**: **Add** values for the certificate's intended purpose. In most cases, the certificate requires **Client Authentication** so that the user or device can authenticate to a server. However, you can add any other key usages as required.
   - **Enrollment Settings**
     - **Renewal threshold (%)**: Enter the percentage of the certificate lifetime that remains before the device requests renewal of the certificate.
     - **SCEP Server URLs**: Enter one or more URLs for the NDES Servers that issue certificates via SCEP. For example, enter something similar to `https://ndes.contoso.com/certsrv/mscep/mscep.dll`.
     - Select **OK**, and **Create** your profile.

The profile is created and appears on the profiles list pane.

## Assign the certificate profile

Consider the following before you assign certificate profiles to groups:

- When you assign certificate profiles to groups, the certificate file from the Trusted CA certificate profile is installed on the device. The device uses the SCEP certificate profile to create a certificate request by the device.
- Certificate profiles install only on devices running the platform you use when you created the profile.
- You can assign certificate profiles to user collections or to device collections.
- To publish a certificate to a device quickly after the device enrolls, assign the certificate profile to a user group rather than to a device group. If you assign to a device group, a full device registration is required before the device receives policies.
- Although you assign each profile separately, you also need to assign the Trusted Root CA and the SCEP or PKCS profile. Otherwise, the SCEP or PKCS certificate policy fails.

    > [!NOTE]
    > For iOS, you should expect to see multiple copies of the certificate in the management profile if you deploy multiple resource profiles that use the same certificate profile.

For information about how to assign profiles, see [assign device profiles](device-profile-assign.md).

## Intune Connector setup verification and troubleshooting

To troubleshoot issues and verify the Intune Connector setup, see [Certificate Authority script samples](https://aka.ms/intuneconnectorverificationscript)

## Intune Connector events and diagnostic codes

Starting with version 6.1806.x.x, the Intune Connector Service logs events in the **Event Viewer** (**Applications and Services Logs** > **Microsoft Intune Connector**). Use these events to help troubleshoot potential issues in the configuration of the Intune Connector. These events log successes and failures of an operation, and also contain diagnostic codes with messages to help the IT admin troubleshoot.

### Event IDs and descriptions

> [!NOTE]
> For details on the Related Diagnostic Codes for each event, use the **Diagnostic codes** table (in this article).

| Event ID      | Event Name    | Event Description | Related Diagnostic Codes |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | Connector service started | 0x00000000, 0x0FFFFFFF |
| 10020 | StoppedConnectorService  | Connector service stopped | 0x00000000, 0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | Connector enrollment certificate successfully renewed | 0x00000000, 0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | Connector enrollment certificate failed to renew. Reinstall the connector. | 0x00000000, 0x00000405, 0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | Failed to retrieve the connector enrollment certificate from the registry. Review event details for the certificate thumbprint related to this event. | 0x00000000, 0x00000404, 0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | Check diagnostic information in event details. | 0x00000000, 0x00000403, 0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | Successfully issued a PKCS certificate. Review event details for the device ID, user ID, CA name, certificate template name, and certificate thumbprint related to this event. | 0x00000000, 0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | Failed to issue a PKCS certificate. Review event details for the device ID, user ID, CA name, certificate template name, and certificate thumbprint related to this event. | 0x00000000, 0x00000400, 0x00000401, 0x0FFFFFFF |
| 20200 | RevokeCert_Success  | Successfully revoked the certificate. Review event details for the device ID, user ID, CA name, and certificate serial number related to this event. | 0x00000000, 0x0FFFFFFF |
| 20202 | RevokeCert_Failure | Failed to revoke the certificate. Review event details for the device ID, user ID, CA name, and certificate serial number related to this event. For additional information, see the NDES SVC Logs.   | 0x00000000, 0x00000402, 0x0FFFFFFF |
| 20300 | Upload_Success | Successfully uploaded the certificate’s request or revocation data. Review the event details for the upload details. | 0x00000000, 0x0FFFFFFF |
| 20302 | Upload_Failure | Failed to upload the certificate’s request or revocation data. Review the event details > Upload State to determine the point of failure.| 0x00000000, 0x0FFFFFFF |
| 20400 | Download_Success | Successfully downloaded request to sign a certificate, download a client certificate, or revoke a certificate. Review the event details for the download details.  | 0x00000000, 0x0FFFFFFF |
| 20402 | Download_Failure | Failed to download request to sign a certificate, download client certificate, or revoke a certificate. Review the event details for the download details. | 0x00000000, 0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | Certificate Registration Point successfully verified a client challenge | 0x00000000, 0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | Certificate Registration Point completed but rejected the request. See diagnostic code and message for more details. | 0x00000000, 0x00000411, 0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | Certificate Registration Point failed to verify a client challenge. See diagnostic code and message for more details. See event message details for the Device ID corresponding to the challenge. | 0x00000000, 0x00000408, 0x00000409, 0x00000410, 0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | Certificate Registration Point successfully finished notify process and has sent the certificate to the client device. | 0x00000000, 0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | Certificate Registration Point failed to finish notify process. See the event message details for information on the request. Verify connection between the NDES server and the CA. | 0x00000000, 0x0FFFFFFF |

### Diagnostic codes

| Diagnostic Code | Diagnostic Name | Diagnostic Message |
| -------------   | -------------   | -------------      |
| 0x00000000 | Success  | Success |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | Certification authority is not valid or is unreachable. Verify that the certification authority is available, and that your server can communicate with it. |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | Symantec Client Auth certificate was not found in the local cert store. See the article [Install the Symantec registration authorization certificate](https://docs.microsoft.com/intune/certificates-symantec-configure#install-the-symantec-registration-authorization-certificate) for more information.  |
| 0x00000402 | RevokeCert_AccessDenied  | The specified account does not have permissions to revoke a certificate from CA. See CA Name field in the event message details to determine the issuing CA.  |
| 0x00000403 | CertThumbprint_NotFound  | Could not find a certificate that matched your input. Enroll the certificate connector and try again. |
| 0x00000404 | Certificate_NotFound  | Could not find a certificate that matched the input supplied. Re-enroll the certificate connector and try again. |
| 0x00000405 | Certificate_Expired  | A certificate expired. Re-enroll the certificate connector to renew the certificate and try again. |
| 0x00000408 | CRPSCEPCert_NotFound  | CRP Encryption certificate could not be found. Verify that NDES and the Intune Connector is setup correctly. |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | Signing certificate could not be retrieved. Verify the Intune Connector Service is configured correctly, and the Intune Connector Service is running. Verify also that the certificate download events were successful. |
| 0x00000410 | CRPSCEPDeserialize_Failed  | Failed to deserialize SCEP challenge request. Verify the NDES and Intune Connector is setup correctly. |
| 0x00000411 | CRPSCEPChallenge_Expired  | Request denied due to expired certificate challenge. The client device can retry after obtaining a new challenge from the management server. |
| 0x0FFFFFFFF | Unknown_Error  | We are unable to complete your request because a server-side error occurred. Please try again. |

## Next steps

- [Use PKCS certificates](certficates-pfx-configure.md), or [issue PKCS certificates from a Symantec PKI manager web Service](certificates-symantec-configure.md)
- [Add a 3rd-party CA to use SCEP with Intune](certificate-authority-add-scep-overview.md)
- For additional assistance, use the [Troubleshooting SCEP certificate profile deployment in Microsoft Intune](https://support.microsoft.com/help/4457481/troubleshooting-scep-certificate-profile-deployment-in-intune) guide.
