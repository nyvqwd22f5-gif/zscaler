# Configuring the Microsoft Intune Assets Connector
Source: https://help.zscaler.com/uvm/configuring-microsoft-intune-assets-connector
PDF: https://help.zscaler.com/pdf/com/en/1530992.pdf

Microsoft Intune is a cloud-based endpoint management solution. It manages user access to organizational resources and simplifies app and device management across your many devices, including mobile devices, desktop computers, and virtual endpoints.
To create the Microsoft Intune Assets data source, go to **Configure** > **Sources**. The connector tile appears among the other available data sources. To learn more, see [Creating Data Sources](/uvm/creating-data-sources).
[See image.](#microsoft-intune-assets-tiles)
This stream retrieves Microsoft Intune Devices that are mapped to Assets in the system.
If you’re looking for Microsoft Intune’s Audit Events, see [Configuring the Microsoft Intune Audit Events Connector](/uvm/configuring-microsoft-intune-audit-events-connector).
[]
![The Microsoft Intune Assets tile](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-microsoft-intune-assets-connector/microsoft-intune-assets-tile.png)
Authentication
To set up the Microsoft Intune Assets connector, you must register an application in Microsoft Intune. If you already have an Avalor app for API, assign the application roles. This does not apply to the SAML application.
Before getting started, ensure that your tenant has an active Microsoft Intune license. If it does not, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses-assign) to activate it.
- [Register an application](#register-application)
- [Declare roles for an application](#declare-roles)
- [Assign app roles](#assign-app-roles)
The source authentication configuration requires the following parameters:
- [Directory (tenant) ID and Application (client) ID](#param1)
- [Client Secret](#param2)
[]
After the registration process is complete, the Microsoft Azure portal displays the app registration **Overview** page. On the **Overview** page, save the **Application (client) ID** and **Directory (tenant) ID**.
[]
To add a client secret, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app#add-a-client-secret). When you are asked to select an expiration date, select **24 months**.
Save the client secret value. Your client secret is not displayed again after you leave this page.
[]
Before you create a new app role, ensure that you sign in to the Microsoft Entra admin center as a Cloud Application Administrator or greater admin role. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
To register an application, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app?tabs=certificate#register-an-application). When you specify who can use the application, select **Accounts in this organizational directory only**.
[]
To declare roles for an application, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps#declare-roles-for-an-application).
In the **Create app role** window, configure the following:
- **Display name**: Enter a name.
- **Allowed member types**: Select **Applications**.
- **Value**: Enter `DeviceManagementManagedDevices.Read.All`.
- **Description**: Enter a description.
- **Do you want to enable this app role?**: Select the checkbox.
[]
To assign app roles to applications, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps#assign-app-roles-to-applications).
- Per step 6, if your application is not found on the **My APIs** tab, it might be located on the **APIs my organization uses** tab.
- Per step 7, select the **Avalor - read devices** role.
To grant admin consent, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps#grant-admin-consent).
Troubleshooting and FAQs
If you are still getting an authorization error after following the steps, assign the role app permissions through the Microsoft APIs tab:
- Log in to the Microsoft Azure portal.
- On the home page, in the **Search resources, services, and docs (G+/)** field, enter `App registrations`. From the drop-down menu, select **App registrations**.
- On the **App registrations** page, select your app registration.
- From the left-side navigation, from the **Manage** drop-down menu, select **API permissions**.
- On the **API permissions** tab, click **Add a permission**.
- On the **Microsoft APIs** tab, click the **Microsoft Graph** tile.
- Select **Application permissions**.
- Select **DeviceManagementManagedDevices.Read.All**.
- Click **Add permissions**.
- Grant admin consent. To grant admin consent, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps#grant-admin-consent).
After completing the steps, rerun the connector in the platform. Hover over the Microsoft Intune Assets data source and click **Process Now**.