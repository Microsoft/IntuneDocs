---
# required metadata

title: Quickstart - Try Microsoft Intune for free
titlesuffix: 
description: In this quickstart you will create a free trial subscription, understand supported configurations and networking requirements, and optionally configure your domain name.
keywords:
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/11/2019
ms.topic: quickstart
ms.prod:
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c

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

# Quickstart: Try Microsoft Intune for free 

Microsoft Intune helps you protect your workforce's corporate data by managing devices and apps. In this quickstart, you will create a free subscription to try Intune in a test environment.

Intune provides mobile device management (MDM) and mobile app management (MAM) from a secure cloud-based service that is administered using the Microsoft Azure portal. Using Intune, you can ensure your workforce's corporate resources (data, devices, and apps) are correctly configured, accessed, and updated, to meet your company's compliance policies and requirements. 

## Prerequisites
Before setting up Microsoft Intune, review the following requirements:

   - [Supported operating systems and browsers](supported-devices-browsers.md) 
   - [Network configuration requirements and bandwidth](network-bandwidth-use.md)

## Sign up for a Microsoft Intune free trial

You can try out Intune for free for 30 days. If you already have a work or school account, **sign in** with that account and add Intune to your subscription. Otherwise, you can **sign up** for a new account to use Intune for your organization.

> [!IMPORTANT]
> You cannot combine an existing work or school account after you sign up for a new account.

To sign up for a new 30-day free Intune trial: 

1. Go to the [Microsoft Intune Trial](https://go.microsoft.com/fwlink/?linkid=2019088) page and fill out the form.

    ![Screenshot of the Microsoft Intune Trial account sign-up web page](./media/account-sign-up-site-full-browser.png)

    If most of your IT operations and users are in a different locale to you, you might want to select that locale under **Country or region**. Azure uses your regional information to deliver the right services. This setting cannot be changed later.

2. Create an account using your company name followed by **.onmicrosoft.com** 

    ![Screenshot of the Intune trial account new credential process](./media/account-sign-up-site-user-id.png)

    You can use the Microsoft 365 admin center (described later in this article), if you want to use your own custom domain name rather than **.onmicrosoft.com**

3. View your new account information at the end of the sign-up process.

    ![Image of your account information](./media/intune-end-of-sign-up-process.png) 

## Sign in to the Azure portal

1. Open a new browser window and enter **https://portal.azure.com** in the address bar. 
2. Use the credentials you were given in the steps above to sign in.

    ![Image of the Azure portal sign-in page](./media/azure-portal-signin.png)

3. To view Microsoft Intune in the Azure portal, select **All services** from the sidebar on the left of the page.
4. Search for **Microsoft Intune** in the filter box and select it.
5. Select the **star** to add Intune to the bottom of the list of your favorite services and open the Intune dashboard.

When you sign up for a trial, you will also receive an email message that contains your account information and the email address you provided during the sign-up process. This email confirms your trial is active.

> [!TIP]
> When working with the Azure portal, you may have better results working with a browser in regular rather than private mode.

## Set the MDM authority to Intune

After signing in to the Azure portal and selecting Intune, you may see an orange banner indicating you haven't set the MDM authority. The mobile device management (MDM) authority setting determines how you manage your devices. The MDM authority must be set before users can enroll devices for management.

To set the MDM authority to Intune:

1. Open a new browser window and enter **https://portal.azure.com** in the address bar. 
2. Choose **All services** > **Microsoft Intune**.
3. Select the banner indicating you haven't enabled device management, or if you don't immediately see the banner, select **Device enrollment**. The **Choose MDM Authority** blade will be displayed if you haven't enabled device management yet.

    > [!NOTE]
    > If you have set the MDM Authority, you will see the MDM authority value on the **Device enrollment** blade. The orange banner is only displayed if you haven't yet set the MDM authority. 

    ![Image of the Choose MDM Authority blade](./media/choose-mdm-authority.png) 

4. If your MDM Authority is not set, under **Choose MDM Authority** set your MDM authority to **Intune MDM Authority**.

See [Set the mobile device management authority](mdm-authority-set.md) for more information about the MDM authority.

## Configure your custom domain name (Optional)

As mentioned above, if your organization has its own custom domain that you want to use without **.onmicrosoft.com**, you can change it in the Microsoft 365 admin center. You can add, verify, and configure your custom domain name using the following steps.  

> [!IMPORTANT]
> You cannot rename or remove the *initial* **onmicrosoft.com** part of the domain name. However, you can add, verify, or remove *custom* domain names used with Intune to keep your business identity clear. For more information, see [Configure a custom domain name](custom-domain-name-configure.md).

1. Go to [Microsoft 365 admin center](https://admin.microsoft.com) and sign in using your administrator account.

2. In the navigation pane, choose **Setup** > **Domains** > **Add domain**.

3. Type your custom domain name. Then, select **Next**.

   ![Screenshot of Microsoft 365 admin center - Add domain](./media/domain-custom-add.png)

4. Verify you are the owner of the domain that you entered previously. 
    
    Clicking **send code via email** will send an email to the registered contact of your domain. After you receive the email, copy the code and enter it in the **Type your verification code here** field. If the verification code matches, the domain will be added to your tenant. The email displayed may not look familiar. Some registrars hide the real email address. Also, the email address may be different then that provided when the domain was originally registered.

   ![Screenshot of Microsoft 365 admin center - Verify domain](./media/domain-custom-verify.png)

   > [!NOTE]
   > See [Create DNS records at any DNS hosting provider for Office 365](https://support.office.com/article/Create-DNS-records-at-any-DNS-hosting-provider-for-Office-365-7B7B075D-79F9-4E37-8A9E-FB60C1D95166) for TXT record verification details.

## Admin experiences

There are two portals you might use:
- The Intune dashboard in Azure ([portal.azure.com](https://portal.azure.com)) is where you can explore the [capabilities of Intune](what-is-intune.md). Normally, you’ll do your work in the Intune dashboard.
- The Microsoft 365 admin center ([admin.microsoft.com](https://admin.microsoft.com)) is where you can add and manage users, if you are not using Azure Active Directory for this. You can also manage other aspects of your account, including billing and support.

## Next steps

In this quickstart, you've created a free subscription to try Intune in a test environment. For more information about setting up Intune, see [Set up Intune](setup-steps.md).

To follow this series of Intune quickstarts, continue to the next quickstart.

> [!div class="nextstepaction"]
> [Quickstart: Create a user and assign a license to it](quickstart-create-user.md)
