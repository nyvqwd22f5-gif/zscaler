# Adding Unmanaged Databases
Source: https://help.zscaler.com/dspm/adding-unmanaged-database
PDF: https://help.zscaler.com/pdf/com/en/1517566.pdf

You can add an [unmanaged database server](/dspm/about-unmanaged-database) to DSPM. DSPM scans the unmanaged databases for sensitive data and identifies any potential security posture risks.
Prerequisites
Before adding unmanaged databases to DSPM, ensure the following prerequisites are met:
- [Onboard the account using a custom model](/dspm/onboarding-microsoft-azure-tenant#SelectNetworkConfiguration) to establish network connectivity between DSPM and the unmanaged database.
- Modify security groups to allow connections from the scanner or orchestrator subnets.
- Create a [custom role with required permissions to configure SQL authentication.](/dspm/configuring-sql-authentication-unmanaged-databases)
- Provide SQL connection strings and authentication credentials to allow DSPM to access the unmanaged database.
- If the database uses a self-hosted HashiCorp Vault:
- Ensure the network policies allow inbound connectivity from the DSPM scanner subnets to the HashiCorp Vault and unmanaged databases.
- Create a DSPM user in the HashiCorp Vault for authentication.
- Add secrets in the HashiCorp Vault to allow DSPM to fetch the credentials and connect to the unmanaged database to scan sensitive data. To learn more, refer to the [HashiCorp documentation](https://developer.hashicorp.com/vault/docs/commands/secrets).
Adding an Unmanaged Database Server
To add an unmanaged database server:
- Go to **Administration **>** Configuration **>** Service Registration**.
-
On the **Service Registration** page, select the **Unmanaged Database** tab, and click **Add Database Server**.
[See image.](#img_add)
The **Add Unmanaged Database Server **window appears.
-
In the **Add Unmanaged Database Server** window, select the database server type:
- [Cloud Database](#nt-cloud)
- [On-Premises Database](#nt-onprem)
[See image.](#ds-addumdb-selecttype)
-
In the **Database Server** section:
- **Database Server Name**: Enter a unique name for the database server.
- **Database Engine**: Select the database engine type (MS-SQL, PostgreSQL, Oracle, MySQL).
- **Database Version**: Select the version of the database server.
- **Type of Connection String** (for Oracle Only): Select any of the following connection strings:
- **Container Database**: A database that contains multiple, independent databases called Pluggable Databases (PDBs).
- **Pluggable Database**: A portable collection of schemas, schema objects, and non-schema objects.
- **Database Instance**: This is a set of memory structures and background processes to manage database files.
- **Connection String**: Enter the connection string required to connect to the database server.
[See image.](#img-dbserver)
-
In the **Authentication** section:
The authentication type differs depending on the deployment type.
- For cloud deployments, authentication is based on the cloud type.
- For on-premises deployments, authentication is based on the associated cloud network.
**Secret Provider Type**: Select the secret provider used for authentication.
- [Azure Key Vault or AWS Secrets Manager](#aws-azure-secret-provider)
- [Self Hosted HashiCorp Vault](#hashicorp)
-
**Database Authentication**: This is applicable when HashiCorp Vault is selected as the **Secret Provider Type**.
- **Authentication Type**: Select the authentication type from the list to authenticate to the unmanaged database.
- **Username**: Enter the username that DSPM uses to connect to the unmanaged database. This should match the username stored in the HashiCorp Vault secret.
- **HashiCorp Vault Secret Path**: Enter the HashiCorp Vault path where the secret is stored. For example, `hashicorp/vault/zscaler/password`.
- **HashiCorp Vault Secret Key**: Enter the HashiCorp key that stores the database login password.
[See image.](#img-hashicorp-db-authentication)
- Click **Save**.
The unmanaged database server is added and displayed on the [Unmanaged Databases](/dspm/about-unmanaged-database) page. To configure the scan settings, see [Configuring Scan Settings for Azure Unmanaged Databases](/dspm/configuring-scan-settings-azure-unmanaged-database), [Configuring Scan Settings for On-Premises Unmanaged Database](/dspm/configuring-scan-settings-premise-unmanaged-database), and [Configuring Scan Settings for AWS Unmanaged Databases](/dspm/configuring-scan-settings-aws-unmanaged-databases).
- []**Endpoint**: Enter the URL of the HashiCorp Vault.
- **Username**: Enter the login username of the HashiCorp Vault.
-
**Key Vault URI** or **AWS Secrets Manager ARN**: Enter the secret URI or ARN where HashiCorp vault login password is saved.
The label of this field changes based on the selected cloud provider:
- For AWS, it appears as **Secrets Manager ARN**.
- For Azure, it appears as **Key Vault URI**.
[See image.](#img-hashicorp-authentication)
- []**Authentication Type**: Select the authentication type (SQL Authentication, Microsoft Entra Service Principal, or Microsoft Entra Authentication with user-managed identity).
- [SQL Authentication (For Azure, AWS, and On-Premises)](#sqlauth)
- [Microsoft Entra Service Principal (for Azure only)](#entraauth)
- [Microsoft Entra Authentication with User-Managed Identity (for Azure only)](#entraauth_umi)
- []**Associate Database Server with Virtual Machine**: Enable the toggle to associate the database server with a virtual machine.
- **Cloud Type**: Select the cloud service provider (AWS, Azure, or GCP) where your database server is hosted.
- **Account**: Select the cloud account in which the database server is stored.
- **Cloud Region**: Select the region where the database server is located.
-
**Virtual Machine**: Select the virtual machine or an EC2 instance that must be associated with the database server.
The **Virtual Machine** option is only available when the **Associate Database Server with Virtual Machine** toggle is enabled.
[See image.](#img_cloud)
-
[]In the **Data Center Information** section:
- **Data Center**: Select the name of the data center where the database server is located.
- **Location**: This is automatically populated based on the selected data center.
[See image.](#ds-addumdb-onprem-dci)
-
In the **On-Premises to Cloud Network Information** section:
- **Cloud Network Association**: Select the cloud network that must be associated with the on-premises data center.
- **Connected Cloud**: The cloud provider is automatically populated based on the associated cloud network.
- **DSPM Alias**: The name of the DSPM tenant or management group is automatically populated based on the associated cloud network.
- **Connected Cloud Region**: The region is automatically populated based on the associated cloud network.
[See image.](#ds-addumdb-onprem-cni)
[]
- **Username**: Enter the username for SQL authentication.
-
**Key Vault URI**: Enter the Uniform Resource Indicator (URI), a unique identifier of the Key Vault instance. In order for DSPM to read the password and connect to the database, ensure you do the following:
-
-
-
-
-
| Database Type | Secret Storage Details |
| ------------- | ---------------------- |
| Unmanaged | **AWS**:** **Create and store the secret in the AWS target account.**Azure**:** **Create and store the secret in any Key Vault of the target subscription. |
| On-premises | **AWS**: Create and store the secret in the AWS account where the orchestrator account is present.**Azure**: Create and store the secret in the Key Vault of the worker plane resource group [integration_id_worker_plane_rg] of the subscription where the orchestrator account is present.**GCP**: Create and store the secret in the secret manager of the GCP project where the orchestrator account is present. |
[See image.](#img_auth_sql)
When using SQL Authentication, [create a custom server reader role with the necessary permissions](/dspm/configuring-sql-authentication-unmanaged-databases) to scan the database.
[]
- **Application ID**: Enter the application ID for Microsoft Entra authentication.
-
**AWS Secret Manager ARN** (for AWS): Enter the ARN of the AWS Secret Manager.
This ARN must be available in the account where the unmanaged database is located.
-
**Key Vault URI **(for Azure): Enter the Uniform Resource Indicator (URI) of the Key Vault instance.
This URI must be available in the same account where the unmanaged database is present, and the Key Vault should follow the `Azure role-based access control` permission model.
[See image.](#img_auth_entrasp)
[]A user-managed identity in Azure that is created and managed by the user.
**Azure Resource ID**: Enter the Azure Resource ID for user-managed identity authentication.
[See image.](#img_auth_umi)
[]![The authentication configuration details for SQL authentication, with username, Vault secret path, and Vault secret key.](/downloads/dspm/administration/unmanaged-database/adding-unmanaged-database/hashicorp-db-authentication.png)
[]![Authentication details for HashiCorp Vault, endpoint, username, and key vault URI.](/downloads/dspm/administration/unmanaged-database/adding-unmanaged-database/hashicorp-authentication.png)
[]![Configure on-premises to cloud network information to choose the cloud network association, and cloud details.](/downloads/dspm/administration/unmanaged-database/adding-unmanaged-database/ds-umdb-onprem-onprem-cni.png)
[]![Add Unmanaged Database Server page to choose the data center and respective location.](/downloads/dspm/administration/unmanaged-database/adding-unmanaged-database/ds-umdb-onprem-dci.png)
[]![ Add unmanaged database server page to select Cloud or On-Premises database server type.](/downloads/dspm/administration/unmanaged-database/adding-unmanaged-database/ds-umdb-selecttype.png)
[]![The Unmanaged Databases page with a list of databases and annotation around the Add Database Server button.](/downloads/dspm/administration/unmanaged-database/adding-unmanaged-database/umdb_add-button.png)
[]![Add Cloud Details for Unmanaged Database](/downloads/dspm/administration/unmanaged-database/adding-unmanaged-database/img_cloud.png)
[]![Database Server Details for Add Unmanaged Database](/downloads/dspm/administration/unmanaged-database/adding-unmanaged-database/img-ds-add-umdb-dbserver.png)
[]![SQL Authentication Details](/downloads/dspm/administration/unmanaged-database/adding-unmanaged-database/auth_sql.png)
[]![Microsoft Entra Authentication Details](/downloads/dspm/administration/unmanaged-database/adding-unmanaged-database/auth_entrasp.png)
[]![Microsoft Entra Authentication with User Managed Identity Details](/downloads/dspm/administration/unmanaged-database/adding-unmanaged-database/auth_umi.png)