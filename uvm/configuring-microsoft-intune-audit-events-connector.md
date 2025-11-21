# Configuring the Microsoft Intune Audit Events Connector
Source: https://help.zscaler.com/uvm/configuring-microsoft-intune-audit-events-connector
PDF: https://help.zscaler.com/pdf/com/en/1531006.pdf

Microsoft Intune is a cloud-based endpoint management solution. It manages user access to organizational resources and simplifies app and device management across your many devices, including mobile devices, desktop computers, and virtual endpoints.
To create the Microsoft Intune Audit Events data source, go to **Configure** > **Sources**. The connector tile appears among the other available data sources. To learn more, see [Creating Data Sources](/uvm/creating-data-sources).
[See image.](#microsoft-intune-audit-events-tile)
If you’re looking for Microsoft Intune’s Assets, see [Configuring the Microsoft Intune Assets Connector](/uvm/configuring-microsoft-intune-assets-connector).
[]
![The Microsoft Intune Audit Events tile](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/connector-drafts/configuring-source-name-connector/microsoft-intune-audit-events-tile.png)
Authentication
To set up the Microsoft Intune Audit Events connector, you must register an application in Microsoft Intune. In the setup process, you can retrieve the required parameters. The Microsoft Graph API for Intune requires an active Intune license for the tenant. If you already have an Avalor application for API, you can assign the application roles. This does not apply to the SAML application.
- [Register an application](#register-app)
- [Declare roles for an application](#declare-app-roles)
- [Assign application roles](#assign-app-roles)
The source authentication configuration requires the following parameters:
- [Directory (tenant) ID and Application (client) ID](#param1)
- [Client Secret](#param2)
[]
After the registration process is completed, the Microsoft Azure portal displays the application registration **Overview** page. On the **Overview** page, save the **Application (client) ID** and **Directory (tenant) ID**.
[]
To add a client secret, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app#add-a-client-secret). When you are asked to select an expiration date, select **24 months**.
Save the client secret value. Your client secret is not displayed again after you leave this page.
[]
To register an application, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app?tabs=certificate#register-an-application). When you are asked to specify who can use the application, select **Accounts in this organizational directory only**.
[]
To declare roles for an application, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps#declare-roles-for-an-application).
In the **Edit app role** window, configure the following:
- **Display name**: Enter a name.
- **Allowed member types**: Select **Applications**.
- **Value**: Enter `DeviceManagementApps.Read.All`.
- **Description**: Enter a description.
- **Do you want to enable this app role?**: Select the checkbox.
[]
To assign app roles to applications, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps#assign-app-roles-to-applications). When you reach step 7, select the `intune read` role.
To grant admin consent, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps#grant-admin-consent).