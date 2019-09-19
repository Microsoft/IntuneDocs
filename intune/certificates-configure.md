---
# required metadata

title: Create certificates profile in Microsoft Intune - Azure | Microsoft Docs
description: For your devices, add or create a certificate profile by configuring SCEP or PKCS certificate environment, export the public certificate, create the profile in the Azure portal, and then assign SCEP or PKCS to the certificate profiles in Microsoft Intune in the Azure portal
keywords:
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1

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

# Use certificates for authentication in Microsoft Intune  

Use certificates with Intune to authenticate your users to applications and corporate resources through VPN, Wi-Fi, or email profiles. When you use certificates to authenticate these connections, your end users won't need to enter usernames and passwords, which helps to make their access seamless. Certificates are also used for signing and encryption of email using S/MIME.

Intune supports the following certificate types:  

- Simple Certificate Enrollment Protocol (SCEP)  
- PKCS#12 (or PFX)  
- PKCS imported certificates

To deploy these certificates, you’ll create and assign certificate profiles to devices.  

Each individual certificate profile you create supports a single platform. For example, if you use PKCS certificates, you’ll create PKCS certificate profile for Android and a separate PKCS certificate profile for iOS. If you also use SCEP certificates for those two platforms, you’ll create a SCEP certificate profile for Android, and another for iOS.  

**General considerations**:  
- If you don't have an Enterprise Certification Authority (CA), you must create one or use one from [one of our supported partners](certificate-authority-add-scep-overview.md#third-party-certification-authority-partners).
- If you use SCEP certificate profiles using Microsoft Active Directory Certificate Services, you’ll configure a Network Device Enrollment Service (NDES) server.
- If you use SCEP with one of our certification authority partners, you'll need to [integrate it with Intune](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration).
- Both SCEP and PKCS certificate profiles require you to download, install, and configure the Microsoft Intune Certificate Connector. 
- PCKS imported certificates require you to download, install, and configure the PFX Certificate Connector for Microsoft Intune.
- PKCS imported certificates require that you export certificates from your certification authority and import them to Microsoft Intune. See [the PFXImport PowerShell project](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell)
- For a device to use SCEP, PCKS, or PKCS imported certificate profiles, that device must trust your root Certification Authority. You use a *trusted certificate profile* to deploy your Trusted Root CA certificate to devices.  

## Supported platforms and certificate profiles  
| Platform              | Trusted certificate profile | PKCS certificate profile | SCEP certificate profile | PKCS imported certificate profile  |
|--|--|--|--|---|
| Android device administrator | ![Supported](./media/certificates-configure/green-check.png) | ![Supported](./media/certificates-configure/green-check.png) | ![Supported](./media/certificates-configure/green-check.png)|  ![Supported](./media/certificates-configure/green-check.png) |
| Android Enterprise <br> - Device Owner   | ![Supported](./media/certificates-configure/green-check.png) |   |  |   |
| Android Enterprise <br> - Work Profile    | ![Supported](./media/certificates-configure/green-check.png) | ![Supported](./media/certificates-configure/green-check.png) | ![Supported](./media/certificates-configure/green-check.png) | ![Supported](./media/certificates-configure/green-check.png) |
| iOS                   | ![Supported](./media/certificates-configure/green-check.png) | ![Supported](./media/certificates-configure/green-check.png) | ![Supported](./media/certificates-configure/green-check.png) | ![Supported](./media/certificates-configure/green-check.png) |
| macOS                 | ![Supported](./media/certificates-configure/green-check.png) |   |![Supported](./media/certificates-configure/green-check.png)|![Supported](./media/certificates-configure/green-check.png)|
| Windows Phone 8.1     |![Supported](./media/certificates-configure/green-check.png)  |  | ![Supported](./media/certificates-configure/green-check.png)| ![Supported](./media/certificates-configure/green-check.png) |
| Windows 8.1 and later |![Supported](./media/certificates-configure/green-check.png)  |  |![Supported](./media/certificates-configure/green-check.png) |   |
| Windows 10 and later  | ![Supported](./media/certificates-configure/green-check.png) | ![Supported](./media/certificates-configure/green-check.png) | ![Supported](./media/certificates-configure/green-check.png) | ![Supported](./media/certificates-configure/green-check.png) |

## Export the trusted root CA certificate  
To use PKCS,  SCEP, and PKCS imported certificates, devices must trust your root Certification Authority. To establish this trust, you export the Trusted Root Certification Authority (CA) certificate, as well as any intermediate or issuing Certification Authority certificates, as a public certificate (.cer). You can get these certificates from the issuing CA, or from any device that trusts your issuing CA.  

To export the certificate, refer to the documentation for your Certification Authority. You’ll need to export the public certificate as a .cer file.  Don't export the private key, a .pfx file.  

You’ll use this .cer file when you [create trusted certificate profiles](#create-trusted-certificate-profiles) to deploy that certificate to your devices.  

## Create trusted certificate profiles  
Create a trusted certificate profile before you can create a SCEP, PKCS, or PKCS imported certificate profile. Deploying a trusted certificate profile ensures each device recognizes the legitimacy of your CA. SCEP certificate profiles directly reference a trusted certificate profile. PKCS certificate profiles don’t directly reference the trusted certificate profile but do directly reference the server that hosts your CA. PKCS imported certificate profiles don't directly reference the trusted certificate profile but may utilize it on the device. Deploying a trusted certificate profile to devices ensures this trust is established. When a device doesn’t trust the root CA, the SCEP or PKCS certificate profile policy will fail.  

Create a separate trusted certificate profile for each device platform you want to support, just as you'll do for SCEP, PCKS, and PKCS imported certificate profiles.  


### To create a trusted certificate profile  

1. Sign in to the [Intune portal](https://aka.ms/intuneportal).  
2. Select **Device configuration** > **Manage** > **Profiles** > **Create profile**.  
3. Enter a **Name and Description** for the trusted certificate profile.  
4. From the **Platform** drop-down list, select the device platform for this trusted certificate.  
5. From the **Profile type** drop-down list, choose **Trusted certificate**.  
6. Browse to the trusted root CA certificate .cer file you exported for use with this certificate profile, and then select **OK**.  
7. For Windows 8.1 and Windows 10 devices only, select the **Destination Store** for the trusted certificate from:  
   - **Computer certificate store - Root**
   - **Computer certificate store - Intermediate**
   - **User certificate store - Intermediate**
8. When you're done, choose **OK**, go back to the **Create profile** pane, and select **Create**.
The profile appears in the list of profiles on the *Device configuration – Profiles* view pane, with a profile type of **Trusted certificate**.  Be sure to assign this profile to devices that will use SCEP or PCKS certificates. To assign the profile to groups, see [assign device profiles](device-profile-assign.md).

> [!NOTE]  
> Android devices might display a message that a third party has installed a trusted certificate.  

## Additional resources  
- [Assign device profiles](device-profile-assign.md)  
- [Use S/MIME to sign and encrypt emails](certificates-s-mime-encryption-sign.md)  
- [Use third-party certification authority](certificate-authority-add-scep-overview.md)  

## Next steps  
After you create and assign trusted certificate profiles, create SCEP, PKCS, or PKCS imported certificate profiles for each platform you want to use. To continue, see the following articles:  
- [Configure infrastructure to support SCEP certificates with Intune](certificates-scep-configure.md)  
- [Configure and manage PKCS certificates with Intune](certficates-pfx-configure.md)  
- [Create a PKCS imported certificate profile](certificates-imported-pfx-configure.md#create-a-pkcs-imported-certificate-profile)  

