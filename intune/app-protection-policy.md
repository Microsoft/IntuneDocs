---
# required metadata

title: What are app protection policies
titleSuffix: Microsoft Intune
description: Learn how Microsoft Intune app protection policies help protect your company data and prevent data loss.
keywords:
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 03/08/2018
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: joglocke
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# What are app protection policies?


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune app protection policies help protect your company data and prevent data loss.

## How you can protect app data
Your employees use mobile devices for both personal and work tasks.  While making sure your employees can be productive, you also want to prevent data loss, intentional and unintentional.  In addition, you want to have the ability to protect company data accessed using devices even in the case where they are not managed by you.

You can use Intune  app protection policies to help protect your company’s data. Because Intune app protection policies can be used **independent of any mobile-device management (MDM) solution**, you can use it to protect your company’s data with or without enrolling devices in a device management solution. By implementing **app-level policies**, you can restrict access to company resources and keep data within the purview of your IT department.

App protection policies can be configured for app running on devices that are:

- **Enrolled in Microsoft Intune:** The devices in this category are typically corporate owned devices.

-   **Enrolled in a third-party Mobile device management (MDM)  solution:**   The devices in this category are typically corporate owned devices.

  > [!NOTE]
  > Mobile app management policies should not be used with third party mobile app management  or secure container solutions.

-   **Not enrolled in any mobile device management solution:**  The devices in this category are typically employee owned devices that are not managed or enrolled in Intune or other MDM solutions.

> [!IMPORTANT]
> You can create mobile app management policies for Office mobile apps that connect to Office 365 services. App protection policies are not supported for apps that connect to on-premises Exchange or SharePoint services.

**The important benefits of using App protection policies are**

-   Protecting your company data at the app level.  Since mobile app management does not require device management, you can protect company data on both managed and unmanaged devices. The management is centered on the user identity, which removes the requirement for device management.

-   End user productivity is not impacted, and the policies are not applied when using the app in a personal context.  The policies are applied only in a work context, thus giving you the ability to protect company data without touching personal data.

There are additional benefits to using MDM with App protection  policies, and companies can use both App protection policies with and without MDM at the same time. For example, an employee may use a phone issued by the company as well as a personal tablet.  In this case, the company phone is enrolled in MDM and protected by App protection policies, and the personal device is protected by App protection policies only.

- **MDM makes sure that the device is protected**.  For example, you can require a PIN to access the device, or you can deploy managed apps to the device. You can also deploy apps to devices through your MDM solution, to give you more control over app management.

- **App protection policies makes sure that the app-layer protections are in place**. For example, you can require a PIN to open an app in a work context, or if data can be shared between apps, or preventing company app data from being saved to a personal storage location.


### Supported platforms for app protection polices
Intune app protection policies platform support is aligned with Office application platform support. For details, see [Office System Requirements](https://products.office.com/en-US/office-system-requirements).

Windows devices are currently not supported. However, when you enroll Windows 10 devices with Intune, you can use Windows Information Protection, which offers similar functionality. For details, see [Protect your enterprise data using Windows Information Protection (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).
##  How app protection policies protect app data

####  Apps without app protection policies

![Image that shows data can move freely between apps when there are no App protection policies in place](./media/apps-without-protection-policies.png)

When apps are used without restrictions, company and personal data can get intermingled.  Company data could end up in locations like personal storage or transferred to apps outside of your  purview,  resulting in data loss. The arrows in the diagram show unrestricted data movement between apps (corporate and personal) and to storage locations.


### Data protection with app protection policies

![Image that shows how company data is protect when App protection policies are applied ](./media/apps-with-protection-policies.png)


You can use App protection policies to prevent company data from saving to the local storage of the device, and restrict data movement to other apps that are not protected by App protection policies. App protection policy settings include:
- Data relocation policies like
 **Prevent Save As**, **Restrict cut, copy, and paste**.
- Access policy settings like **Require simple PIN for access**, **Block managed apps from running on jailbroken or rooted devices**.

### Data protection with app protection policies on devices managed by a MDM solution

![Image that shows how App protection policies work on BYOD devices](./media/app-protection-policies-with-mdm.png)

**For devices enrolled in an MDM solution**-

The illustration above shows the layers of protection that MDM and App protection policies offer together.

The MDM solution:

-   Enrolls the device

-   Deploys the apps to the device

-   Provides ongoing device compliance and management

**App protection policies add value by:**

-   Helping protect  company data from leaking to consumer apps and services

-   Applying restrictions (save-as, clipboard, PIN, etc.) to mobile apps

-   Wipe company data from apps without removing those apps from the device


### Data protection with app protection policies for devices without enrollment

![Image that shows how App protection policies work on managed devices](./media/app-protection-policies-without-mdm.png)

The diagram above illustrates how the data protection policies work at the app level without MDM.

For BYOD devices not enrolled in any MDM solution, App protection policies can help protect company data at the app level.
However, there are some limitations to be aware of, like:

-   You cannot deploy apps to the device.  The end user has to get the apps from the store.

-   You cannot provision certificate profiles on these devices.

-   You cannot provision company Wi-Fi and VPN settings on these devices.


## Multi-identity

Apps that support multi-identity let you use different accounts (work and personal) to access the same apps, while app protection policies are applied only when the apps are used in the work context.

For example, when a user starts the OneDrive app by using their work account, they can't move the files to a personal storage location. However, when they use OneDrive with their personal account, they can copy and move data from their personal OneDrive without restrictions.

- Learn more about the apps that support [MAM and multi-identity](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) with Intune.

##  Next steps

[How to create and deploy app protection policies with Microsoft Intune](app-protection-policies.md)

## See also
3rd party apps such as the Salesforce mobile app work with Intune in specific ways to protect corporate data. To learn more about how the Salesforce app in particular works with Intune (including MDM app configurations settings), see [Salesforce App and Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf).
