# About Service Registration
Source: https://help.zscaler.com/dspm/about-service-registration
PDF: https://help.zscaler.com/pdf/com/en/1517561.pdf

Service registration is the process of onboarding, configuring, and managing database services within DSPM. DSPM provides support for configuring managed and unmanaged databases, Snowflake, on-premises file servers, and Databricks workspaces. DSPM scans these services or databases for sensitive data and vulnerabilities.
- **Managed Database**: A cloud-based DB service where the cloud service provider manages the entire infrastructure, maintenance, and administration of the database. For example, Azure SQL, MySQL, PostgreSQL are some of the managed database services.
- **Unmanaged Database**: The database is managed by organizations and is hosted on servers or virtual machines (VMs). Organizations use unmanaged databases for increased control over their infrastructure and lower costs, but this also requires more expertise and resources to maintain and secure it.
- **Snowflake**: A cloud-based data platform used for data warehousing and secure data sharing.
- **On-Premises File Servers**: A physical server hosted within an organization’s infrastructure.
- **Databricks**: A unified, open analytics platform for managing large-scale data, analytics, and AI solutions.
Service registration provides the following benefits and enables you to:
- Gain visibility into the sensitive data stored in the databases.
- Know about the vulnerabilities and misconfigurations present in the databases.
- Protect sensitive data and improve the overall security posture of the database services.
- Maintain compliance with data protection standards.
About the Service Registration Page
On the Service Registration page (Administration > Configuration > Service Registration), the following tabs contain the database details and Snowflake account details:
- [Unmanaged Databases](#unmanaged-tab)
- [Snowflake](#snowflake-tab)
- [On-Premises File Servers](#on-prem-tab)
- [Databricks](#databricks-tab)
![Service Registration page showing Unmanaged Databases tab with a list of registered database servers and search option.](/downloads/dspm/administration/unmanaged-database/about-unmanaged-database/service-registration-page.png)
[]
On the On-Premises File Servers tab, you can do the following:
- [Add a File Server](/dspm/adding-premises-file-servers).
- Search for specific data in the searchable columns.
- View the list of on-premises file servers. For each file server, you can view:
- **Name**: The name of the file server. Click the server name to view more details.
- [On-Premises File Server Details](#on-prem-details)
- **Cloud**: The cloud service provider, if applicable.
- **Added By**: The user who added the file server.
- **Added On**: The date and time the file server was added.
- **Discovery Status**: The current status of the file server discovery process.
- **Last Discovered**: The number of file servers discovered during the last scan.
- **Discovery Date**: The date and time of the most recent discovery.
- Sort the column data.
- [Modify the table and its columns](/dspm/using-tables).
- Click the **Actions **icon to [edit](/dspm/editing-or-deleting-premises-file-servers) or [delete](/dspm/editing-or-deleting-premises-file-servers) the database server configuration.
![The on-premises file servers page with a list of file servers and annotations on different parts of the page.](/downloads/dspm/administration/unmanaged-database/about-unmanaged-database/service-reg-onprem-tab.png)
[]For each on-premises file server, you can view:
- **File Server Information**:
- **Added By**: The user who added the file server.
- **Added On**: Date and time the file server was added.
- **File Server Type**: The type of the file server.
- **Protocol**: The protocol used for file sharing and communication.
- Action menu to [edit](/dspm/editing-or-deleting-premises-file-servers) or [delete](/dspm/editing-or-deleting-premises-file-servers) the on-premises file server configuration.
- **Connection Attributes:**
- **File Server Name**: The IP address or hostname of the file server to establish a network connection.
- **Domain Name**: The domain name associated with the file server for authentication in domain-based environments.
- **PORT_TYPE**: The configuration port type, default port or a custom port based on your network requirements.
- **Port**: The port used for communication.
- **Authentication:**
- **Secret Provider Type**: The type of secret management service used to store and retrieve credentials.
- **Username**: The username used by DSPM to connect to the file server.
- **Password**: The password associated with the username.
- **Data Center Association**:
- **Data Center**: The data center associated with this file server to organize and locate resources geographically.
- **Location**: The physical location of the selected data center.
[]![Details of an individual on-premises file server](/downloads/dspm/administration/unmanaged-database/about-unmanaged-database/onprem-details.png)
[]
The Databricks tab provides two views: **Workspace** and **Account**. Click the corresponding button to switch views.
![Databricks tab showing Workspace and Account buttons to switch views.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/ds-db-wrkspace-accounts-button.png)
Through these options, you can do the following:
Workspace view:
- [Onboard a workspace or account.](/dspm/adding-databricks-workspace)
- Toggle between the **Workspace** view and **Account** view.
- Search for specific data in the searchable columns.
- View the list of Databricks workspaces. For each workspace, you can view:
- **Workspace Name**: The name of the Databricks workspace. Click the workspace name to view more details.
- [Workspace Details](#databricks-details)
- **Workspace ID**: The unique identifier for the workspace.
- **Cloud Account**: The cloud account that hosts the workspace.
- **Region**: The region where the workspace is deployed.
- **Added By**: The user who added the workspace.
- **Added On**: The date and time the workspace was added.
- Sort the column data.
- [Modify the table and its columns](/dspm/using-tables).
- Click the **Actions** icon to [edit](/dspm/editing-or-deleting-databricks-workspace) or [delete](/dspm/editing-or-deleting-databricks-workspace) the Databricks workspace configuration.
![The Databricks page with a list of workspaces and annotations on different parts of the page.](/downloads/dspm/administration/unmanaged-database/about-unmanaged-database/service-reg-databricks-workspace-tab.png)
Account view:
- [Onboard a workspace or account.](/dspm/adding-databricks-workspace)
- Toggle between the **Workspace** view and **Account** view.
- Search for specific data in the searchable columns.
- View the list of Databricks accounts. For each account, you can view:
- **Account Name**: The name of the Databricks account. Click the account name to view more details.
- [Account Details](#account-details)
- **Account ID**: The unique identifier for the account.
- **Cloud**: The cloud provider of the account.
- **Discovered Workspaces**: The number of Databricks workspaces discovered in the account.
- **Added By**: The user who added the account.
- **Added On**: The date and time the account was added.
- Sort the column data.
- [Modify the table and its columns](/dspm/using-tables).
- Click the **Actions** icon to [edit](/dspm/editing-or-deleting-databricks-workspace) or [delete](/dspm/editing-or-deleting-databricks-workspace) the Databricks account configuration.
![The Databricks page with a list of workspaces and annotations on different parts of the page.](/downloads/dspm/administration/unmanaged-database/about-unmanaged-database/service-reg-databricks-account-tab.png)
[]For each Databricks account, you can view:
- **Account Information**:
- **Added By**: The user who added the Databricks account.
- **Added On**: The date and time the Databricks account was added.
- **Cloud Type**: The cloud service provider associated with the Databricks account.
- **Workspace ID**: The unique identifier assigned to the Databricks account.
- **Account**: The account name under which the account is registered.
- **Integration Details**:
- **DSPM Integration Alias**: The unique alias used for DSPM integration.
- **Client ID**: The client identifier issued by the cloud provider.
- **Client Secret ARN**: The AWS Secrets Manager ARN that stores the client secrets.
[]![Details of an individual Databricks account.](/downloads/dspm/administration/service-registration/databricks/adding-databricks-workspace/db-account-details.png)
[]For each Databricks workspace, you can view:
- **Workspace Information**:
- **Added By**: The user who added the Databricks workspace.
- **Added On**: Date and time the Databricks workspace was added.
- **Cloud Type**: The cloud service provider associated with the Databricks workspace.
- **Workspace ID**: The unique identifier assigned to the Databricks workspace.
- **Account**: The account name under which the workspace is registered.
- Action menu to [edit](/dspm/editing-or-deleting-databricks-workspace) or [delete](/dspm/editing-or-deleting-databricks-workspace) the Databricks workspace configuration.
- **Integration Details**: Applicable only to Azure cloud account configurations.
- **DSPM Integration Alias**: The unique alias used for DSPM integration.
- **Orchestrator Service Principal Application ID**: The application ID used by the orchestrator service principal for secure access.
- **Scanner Service Principal Application ID**: The application ID used by the scanner service principal for secure access.
- **Connection String**: The JDBC connection string used to connect to the Databricks workspace.
- **Execute the script in the Databricks Workspace**: Applicable only to Azure cloud account configurations.
- **Copy Script**: The copy button to copy the script to the clipboard.
- **Download Script**: The download button to download the script file for local execution.
[]![Details of an individual Databricks workspace.](/downloads/dspm/administration/unmanaged-database/about-unmanaged-database/databricks-details.png)
[]
On the Unmanaged Database tab, you can do the following:
- [Add an unmanaged database.](/dspm/adding-unmanaged-database)
- Search for specific data in the searchable columns.
- View the list of unmanaged databases. For each unmanaged database, you can view:
- **Name**: The name of the database server. Click the database server name to view more details.
- [Unmanaged Database Server Details](#db-details)
- **Cloud**: The cloud service provider.
- **Account**: The cloud account that hosts the database server.
- **Type**: The type of database server.
- **Version**: The version of the database server.
- **Added by**: The user who added the database server.
- **Added On**: The date and time the database server was added.
- Sort the column data.
- [Modify the table and its columns](/dspm/using-tables).
- Click the **Actions **icon to [edit](/dspm/editing-or-deleting-unmanaged-database) or [delete](/dspm/editing-or-deleting-unmanaged-database) the database server configuration.
![The Unmanaged Databases page with a list of databases and annotations on different parts of the page.](/downloads/dspm/administration/unmanaged-database/about-unmanaged-database/ser-reg-umdb-tab.png)
[]On the Snowflake Database tab, you can do the following:
- [Add a Snowflake account](/dspm/adding-snowflake-database-account).
- Search for specific data in the searchable columns.
- View the list of Snowflake accounts. For each snowflake database, you can view:
- **Name**: The name assigned to the Snowflake account in DSPM. Click the Snowflake account name to view more details.
- [Snowflake Account Details](#details-snowflake)
- **Account**: The account that hosts the Snowflake server.
- **Organization**: The organization that hosts the Snowflake server.
- **Cloud**: The cloud service provider that hosts the Snowflake.
- **Region**: The region where the Snowflake account is deployed.
- **Business Unit**: The internal business unit associated with the Snowflake account.
- **Added By**: The user who added the Snowflake account.
- **Added On**: The date and time the Snowflake account was added.
- Sort the column data.
- [Modify the table and its columns](/dspm/using-tables).
- Click the **Actions **icon to [edit](/dspm/editing-or-deleting-unmanaged-database) or [delete](/dspm/editing-or-deleting-unmanaged-database) the database server configuration.
![The Snowflake tabwith a list of accounts and annotations on different parts of the page.](/downloads/dspm/administration/unmanaged-database/about-unmanaged-database/service-reg-snowflake-tab.png)
[]For each snowflake account, you can view:
- **General Information**:
- **Created By**: The user who added the snowflake account.
- **Created On**: Date and time the snowflake account was added.
- **Account Information:**
- **Account Alias**: The name of the Snowflake account.
- **Account Edition**: The edition of the Snowflake account.
- **Account Name**: The Snowflake account name as configured in the Snowflake.
- **Organization Name**: The name of the Snowflake organization.
- **Cloud Provider**: The cloud platform hosting the Snowflake account.
- **Cloud Region**: The region where the Snowflake account is configured.
- **Business Unit**: The business unit associated with the Snowflake account.
- **DSPM Integration ID**: The unique identifier assigned by DSPM.
- **Authentication:**
- **Secret Provider Type**: The type of secret management service used to store and retrieve credentials.
- **Authentication Type**: The method used to authenticate access to the Snowflake account.
- **Username**: The username used by DSPM to connect to the Snowflake account.
- **AWS Secret ARN** or **Azure Key Vault URI** or **GCP Secret ID**: The unique identifier to retrieve the authentication secret.
- Action menu to edit or delete the Snowflake account configuration.
[]![Details of an individual Snowflake database server](/downloads/dspm/administration/unmanaged-database/about-unmanaged-database/snowflake-details.png)
[]For each database server, you can view:
- **General Information**:
- **Created By**: The user who added the database server.
- **Created On**: Date and time the database server was added.
- **Cloud**:
- **Cloud Type**: The cloud service provider.
- **Account ID**: The cloud account that hosts the database server.
- **Cloud Region**: The region where the database server is hosted.
- **Virtual Machine ID**: The virtual machine on which the database server is hosted.
- **Database Server**:
- **Database Server Name**: Name of the database server.
- **Database Engine**: The type of database engine.
- **Database Version**: The version of the database server.
- **Type of Connection String** (for Oracle Only): The following connection strings are available:
- **Container Database**: A database that contains multiple, independent databases called Pluggable Databases (PDBs).
- **Pluggable Database**: A portable collection of schemas, schema objects, and non-schema objects.
- **Database Instance**: This is a set of memory structures and background processes to manage database files.
- **Connection String**: The string value used to establish a connection to the database server.
- **Authentication**:
- **Secret Provider Type**: The type of secret provider used to access the database server.
- **Username**: The login username of the HashiCorp Vault (when HashiCorp Vault is selected as the **Secret Provider Type**).
- **Endpoint**: The URL of the HashiCorp Vault instance (when HashiCorp Vault is selected as the **Secret Provider Type**).
- **KeyVault URI**: The secret URI/ARN where HashiCorp vault login password is saved (when HashiCorp Vault is selected as the **Secret Provider Type**).
- **Authentication Type**: You can use any of the following authentication types (when Azure Key Vault or AWS Secrets Manager is selected as the **Secret Provider Type**).
- [SQL Authentication](#sqlauth)
- [Microsoft Entra Service Principal (for Azure only)](#entraauth)
- [Microsoft Entra Authentication with User-Managed Identity (for Azure only)](#entraauth_umi)
- **Database Authentication**: This is applicable when HashiCorp Vault is selected as the Secret Provider Type.
- **Authentication Type**: The authentication type used to authenticate access to the unmanaged database.
- **Username**: The username that DSPM uses to connect to the unmanaged database.
- **HashiCorp Vault Secret Path**: The full path in the HashiCorp Vault where the secret is stored.
- **HashiCorp Vault Secret Key**: The HashiCorp key that stores the database login password.
- Action menu to [edit](/dspm/editing-or-deleting-unmanaged-database) or [delete](/dspm/editing-or-deleting-unmanaged-database) the database server configuration.
[]![Details of an individual unmanaged database server](/downloads/dspm/administration/unmanaged-database/about-unmanaged-database/unmanaged-db-details.png)
- []**Username**: The username for SQL authentication.
- **Key Vault URI**: The URI of the Key Vault instance.
- []**Application ID**: The application ID for Microsoft Entra authentication.
- **Key Vault URI**: The URI of the Key Vault instance.
[]**Azure Resource ID**: The Azure Resource ID for user-managed identity authentication.