## Enable Windows 10 automatic enrollment

Automatic enrollment lets users enroll their Windows 10 devices in Intune when adding their work account to their personally-owned devices or joining their corporate-owned devices to your Azure Active Directory. In the background, the user's device registers and joins Azure Active Directory. Once registered, the device is managed with Intune.

**Prerequisites**
- Azure Active Directory Premium subscription ([trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune subscription

### Configure automatic MDM enrollment

1. Sign in to the [Azure management portal](https://portal.azure.com) (https://manage.windowsazure.com), and select **Azure Active Directory**.

   ![Screenshot of the Azure portal](../media/auto-enroll-azure-main.png)

2. Select **Mobility (MDM and MAM)**.

   ![Screenshot of the Azure portal](../media/auto-enroll-mdm.png)

3. Select **Microsoft Intune**.

   ![Screenshot of the Azure portal](../media/auto-enroll-intune.png)

4. Configure **MDM User scope**. Specify which users’ devices should be managed by Microsoft Intune. These users’ Windows 10 devices will be automatically enrolled for management with Microsoft Intune.

   - **None**
   - **Some**
   - **All**

   ![Screenshot of the Azure portal](../media/auto-enroll-scope.png)

5. Use the default values for the following URLs:
   - **MDM Terms of use URL**
   - **MDM Discovery URL**
   - **MDM Compliance URL**

6. Select **Save**.

By default, two-factor authentication is not enabled for the service. However, two-factor authentication is recommended when registering a device. Before requiring two-factor authentication for this service, you must configure a two-factor authentication provider in Azure Active Directory and configure your user accounts for multi-factor authentication. See [Getting started with the Azure Multi-Factor Authentication Server](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).
