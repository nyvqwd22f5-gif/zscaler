# Configuring the Rapid7 InsightVM Connectors
Source: https://help.zscaler.com/uvm/configuring-rapid7-insightvm-connectors
PDF: https://help.zscaler.com/pdf/com/en/1530820.pdf

Rapid7 InsightVM is a vulnerability management solution that scans modern environments, aggregates data from multiple sources, and prioritizes remediation to strengthen security programs.
To create the Rapid7 InsightVM data source, go to **Configure** > **Sources**. The connector tile appears among the other available data sources. To learn more, see [Creating Data Sources](/uvm/creating-data-sources).
[See image.](#rapid7-insightvm-tiles)
There are two available Rapid7 InsightVM streams. Select those that are in scope based on your Rapid7 InsightVM licenses and use cases:
- Vulnerabilities: Retrieves all vulnerabilities found on the assets to which you have access.
- Assets: Retrieves all assets to which you have access.
[]
![The Rapid7 InsightVM tiles](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/connector-drafts/configuring-source-name-connector/rapid7-insightvm-tiles.png)
Authentication
The source authentication configuration requires the following parameters:
- [API Key](#param1)
- [Region](#param2)
[]
This is an API key associated with a user that has the appropriate permissions. Before getting started, ensure that the API key is created by a platform administrator with **View Only (Shared)** permissions or higher. Any user can generate a user key. A user key inherits your account permissions, so the API key can do anything that you do.
To generate an API key:
- Log in to the Rapid7 Insight platform.
-
From the top-right of the page, click the **Gear** icon. From the drop-down menu, select **API Keys**.
[See image.](#gear-api-keys)
The **User Keys** page appears.
-
On the **User Keys** page, click **Generate New User Key**.
[See image.](#user-keys)
- In the **Generate New User Key** window, configure the following:
- **Organization**: From the drop-down menu, select your organization.
-
**Name**: Enter a name for the user key.
This key is associated with your account.
[See image.](#generate-new-user-key)
- Click **Submit**.
-
Click **Copy** to copy the key.
[See image.](#copy-api-key)
Securely store the key, as it cannot be accessed again later.
[]
The region code for the cloud storage region that your organization is provisioned for in Rapid7. You can access your region from the following locations:
-
In the top-right of the Rapid7 platform home page, the **Data Storage Region** contains your region code. The region code is typically fully spelled out. For example, `us3` appears as `United States - 3`. Use the abbreviated region code and not the full name.
[See image.](#region-code-1)
-
The URL of the Rapid7 InsightVM Solution contains the region as a prefix. For example, the URL `us.idr.insight.rapid7.com` means that your data region is `us`. The region code is typically two letters and sometimes a number (e.g., `us`, `us1`, `eu`).
[See image.](#region-code-2)
Retrieval
In the source setup Retrieval section, set the Filter By Severity drop-down filters and specifications. The Filter By Severity drop-down menu allows you to select the severity level of vulnerabilities to include in the scope of the ingested data (i.e., **Critical**, **Low**, **Severe**, **Informational**, **None**, **Moderate**).
The Filter By Severity drop-down menu is applicable in the Vulnerabilities stream.
Roles and Permissions
To retrieve vulnerability and asset data from Rapid7 InsightVM, generate the API key from a platform admin with at least **View Only (Shared)** privileges and the **View Site Asset Data** and **View Group Asset Data** permissions. To learn more, refer to the [Rapid7 documentation](https://docs.rapid7.com/insightvm/managing-users-and-authentication/).
The listed permissions should be automatically set for platform admins.
Any user can generate a user key. A user key inherits your account permissions, so the API key can do anything that you do. To create a user, as an admin:
- Log in to the Rapid7 platform.
-
Go to **Administration** > **User Management** > **Users**.
[See image.](#users-page)
-
Select **Create New User**.
[See image.](#create-new-user)
The **Create User** page appears.
- On the **Create User** page, configure the following:
- In the **User Details** section:
- **Email Address**: Rapid7 requires a valid email address which the admin can access. The admin can use an email alias associated with their existing email address.
- **First Name**: Enter a first name for the user.
- **Last Name**: Enter a last name for the user.
-
**Timezone**: This field is automatically set to **UTC**.
[See image.](#user-details)
-
In the **Platform Administrator Privileges** section, select the **Create this user as a Platform Administrator** checkbox.
[See image.](#platform-administrator-privileges)
- Select **Create User**.
-
On the **Users** page, in the **Users** table, select the **User Name** of the user you created.
[See image.](#user-name)
-
On the user name page, in the **Individual Privileges** section, select **Manage Individual Privileges** to configure the following:
- **InsightVM**: Select the **InsightVM** checkbox.
- **Roles**: From the drop-down menu, assign the **View Only (Shared)** role.
[See image.](#individual-privileges)
- Click **Save Individual Privileges**.
Sign in with this user to generate the API key.
[]
![Navigating to API Keys from the Gear icon drop-down menu in the Rapid7 platform](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-rapid7-insightvm-connectors/rapid7-gear-api-keys.png)
[]
![Clicking Generate New User Key on the User Keys page of the Rapid7 platform](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-rapid7-insightvm-connectors/rapid7-user-keys.png)
[]
![The Generate New User Key window in the Rapid7 platform](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-rapid7-insightvm-connectors/rapid7-generate-new-user-key.png)
[]
![The Copy Your API Key Now window that opens after generating a new user key in Rapid7 platform](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-rapid7-insightvm-connectors/rapid7-insightvm-copy-api-key-1.png)
[]
![The region code located in the top right of the Rapid7 platform home page](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-rapid7-insightvm-connectors/rapid7-data-storage-region.png)
[]
![The region code located in the URL of the Rapid7 platform home page](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-rapid7-insightvm-connectors/rapid7-insightvm-region-2.png)
[]
![Selecting Users from the User Management drop-down menu in the Administration section of the Rapid7 platform](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-rapid7-insightvm-connectors/rapid7-users-page.png)
[]
![Selecting Create New User on the Users page of the Rapid7 platform](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-rapid7-insightvm-connectors/rapid7-create-new-user.png)
[]
![The User Details section of the Create User page in the Rapid7 platform](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-rapid7-insightvm-connectors/rapid7-user-details.png)
[]
![Selecting Create this user as a Platform Administrator in the Platform Administrator Privileges section of the Create User page of the Rapid7 platform](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-rapid7-insightvm-connectors/rapid7-platform-administrator-privileges.png)
[]
![Selecting the User Name from the Users table in the Rapid7 platform](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-rapid7-insightvm-connectors/rapid7-user-name.png)
[]
![Assigning the InsightVM and View Only (Shared) role to the user in the Rapid7 platform](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-rapid7-insightvm-connectors/rapid7-individual-privileges.png)