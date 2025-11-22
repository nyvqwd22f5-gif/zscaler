# Configuring the Microsoft Defender for Cloud Connectors
Source: https://help.zscaler.com/uvm/configuring-microsoft-defender-cloud-connectors
PDF: https://help.zscaler.com/pdf/com/en/1531041.pdf

Microsoft Defender for Cloud is a cloud-native application protection platform (CNAPP) that safeguards cloud-based applications from cyber threats through unified security management, breach prevention, and workload protection.
To create the Microsoft Defender for Cloud data source, go to **Configure** > **Sources**. The connector tile appears among the other available data sources. To learn more, see [Creating Data Sources](/uvm/creating-data-sources).
[See image.](#microsoft-defender-cloud-tiles)
There are two available Microsoft Defender for Cloud streams. Select those that are in scope based on your Microsoft licenses and use cases:
- Findings: Retrieves security findings for Azure assets, providing details on vulnerabilities, compliance issues, and recommended remediations.
- Assets: Retrieves comprehensive asset information across Azure subscriptions, including metadata, configurations, and properties of resources for centralized insights and management.
These connectors retrieve cloud data only.
If you’re looking for Microsoft’s Defender for Endpoints, see [Configuring the Microsoft Defender for Endpoints Connectors](/uvm/configuring-microsoft-defender-endpoints-connectors).
[]
![The Microsoft Defender for Cloud - Findings and Microsoft Defender for Cloud - Assets tiles](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/connector-drafts/configuring-source-name-connector/microsoft-defender-cloud-tiles.png)
Prerequisites
To enable Microsoft Defender for Cloud for your Azure subscriptions, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/defender-for-cloud/connect-azure-subscription#enable-defender-for-cloud-on-your-azure-subscription).
Authentication
To establish secure authentication and authorization for an Azure application, create an Azure Active Directory (Azure AD) application, generate a client secret, assign the required permissions, and configure role assignments for the relevant subscriptions. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity-platform/howto-create-service-principal-portal).
The source authentication configuration requires the following parameters:
- [Application (client) ID and Directory (tenant) ID](#param1)
- [Client Secret](#param2)
[]
The Application (client) ID and the Directory (tenant) ID are located in the Overview tab of an application.
To create a new application:
- Log in to the Microsoft Azure portal.
- On the home page, in the **Search resources, services, and docs (G+/)** field, enter `App registrations`. From the drop-down menu, select **App registrations**.
- On the **App registrations** page, click **New registration**.
- **Name**: Enter a name for the application.
- **Support account types**: Select **Accounts in this organizational directory only**.
- **Redirect URI (optional)**: Optionally configure these settings.
-
Click **Register** to create the application.
The application **Overview** section appears.
- In the **Overview** section, copy the generated **Application (client) ID** and the **Directory (tenant) ID**.
[]
On the application **Certificates & secrets** tab, generate and copy a client secret for the application.
To generate a client secret:
- Log in to the Microsoft Azure portal.
- On the home page, in the **Search resources, services, and docs (G+/)** field, enter `App registrations`. From the drop-down menu, select **App registrations**.
- On the **App registrations** page, select your app registration.
- From the left-side navigation, from the **Manage** drop-down menu, select **Certificates & secrets**.
- Click **New client secret**.
- Optionally, enter a description.
- Enter an expiration date.
- Click **Add**.
- Copy the client secret value. Save the client secret securely, as it is not available after leaving the process.
Retrieval
In the source setup Retrieval section, set the following filters and specifications:
- [Specific Subscription IDs](#specific-subscription-ids)
- [All Subscription IDs in org](#all-subscription-ids-org)
- [Findings Types drop-down menu](#findings-types)
[]
Enter the subscription IDs from which you want to retrieve data.
The Specific Subscription IDs checkbox/drop-down menu/field is applicable in the following streams:
- Microsoft Defender for Cloud - Assets
- Microsoft Defender for Cloud - Findings
In the subscriptions service, retrieve the subscription ID for the relevant subscriptions and configure the role assignment. To retrieve your subscription ID:
- Log in to the Microsoft Azure Portal.
- On the home page, in the **Search resources, services, and docs (G+/)** field, enter `Subscriptions`. From the drop-down menu, select **Subscriptions**.
- On the **Subscriptions** page, select the subscription you want to use.
-
On the **Overview** tab, copy the **Subscription ID**.
[See image.](#subscription-id)
You can enter multiple subscription IDs in the platform.
To assign the Reader role to a single subscription:
- Log in to the Microsoft Azure Portal.
- On the home page, in the **Search resources, services, and docs (G+/)** field, enter `Subscriptions`. From the drop-down menu, select **Subscriptions**.
- On the **Subscriptions** page, from the left-side navigation, select **Access control (IAM)**.
-
On the **Access control (IAM)** tab, click **Add** > **Add role assignment** to configure the following:
- On the **Role** tab, select the **Reader** role.
- On the **Members** tab, select **User, group, or service principal**.
- Click **+ Select members** and select the application you registered previously.
- On the **Assignment type** tab, set the assignment duration.
- On the **Review + assign** tab, review the assignment and click **Review + assign**.
To learn more, refer to [Microsoft documentation](https://learn.microsoft.com/en-us/azure/role-based-access-control/role-assignments-portal).
[]
Data is retrieved from all subscriptions in your organization.
The Specific Subscription IDs checkbox/drop-down menu/field is applicable in the following streams:
- Microsoft Defender for Cloud - Assets
- Microsoft Defender for Cloud - Findings
If you have multiple subscriptions, you can organize them into a single management group to set access control in bulk. To assign the Reader role to multiple subscriptions:
- Log in to the Microsoft Azure Portal.
- On the home page, in the **Search resources, services, and docs (G+/)** field, enter `Management groups`. From the drop-down menu, select **Management groups**.
- On the **Management groups** page, click **Create** to configure the following:
- **Management group ID**: The directory unique identifier that is used to submit commands on this management group. You cannot edit this ID after creation.
- **Management group display name**: (Optional) The name displayed in the Azure portal.
- Click **Submit**.
- On the **Management groups** page, click the name of the management group you created.
- Click **Add subscription**. The **Add subscription** window appears.
- In the **Add subscription** window, select the subscription you want to add to the management group.
- Click **Save**.
- Select the name of the subscription group you added.
- On the subscription group page, from the left-side navigation, click **Access control (IAM)**.
- Click **Add **> **Add role assignment** to configure the following:
- On the **Role** tab, select the **Reader** role.
- On the **Members** tab, select **User, group, or service principal**.
- Click **+ Select members** and select the application you registered previously.
- Click **Select members**, and then select the application you registered previously.
- On the **Review + assign** tab, review the assignment and click **Review + assign**.
To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/governance/management-groups/overview).
[]
Select the finding type that you want to include in the scope of data ingestion.
The Findings Type is applicable in the Findings stream.
Roles and Permissions
In the application API permission tab, assign the permissions to the application. To assign permissions to the app:
- Log in to the Microsoft Azure Portal.
- On the home page, in the **Search resources, services, and docs (G+/)** field, enter `App registrations`. From the drop-down menu, select **App registrations**.
- On the **App registrations** page, select your app registration.
- In your app registration, in the left-side navigation, from the **Manage** drop-down menu, select **API permissions**.
- In the **Configured permissions** section, click **Add a permission**.
- Go to the **Microsoft APIs** tab.
- Select **Microsoft Graph**.
- Select **Application permissions**.
- Add the **PrivilegedAccess.Read.AzureResources** permission.
- Click **Add permissions**.
- If admin consent is required for these permissions, select **Grant admin consent**.
- Click **Yes** to confirm the action.
[]
![Copying the Subscription ID on the Subscriptions page of the Microsoft Azure portal](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-microsoft-defender-cloud-connectors/microsoft-defender-cloud-connectors-subscription-id.png)