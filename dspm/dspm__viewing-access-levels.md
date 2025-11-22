# Viewing the Access Levels
Source: https://help.zscaler.com/dspm/viewing-access-levels
PDF: https://help.zscaler.com/pdf/com/en/1478251.pdf

Access level refers to the identity and access management (IAM) permissions granted to the entities (user, application, service, etc.) that are associated with the cloud resources. While scanning the cloud resources for sensitive data and vulnerabilities, DSPM also detects the entities and the permissions they have to access the cloud resources.
To view the access level of the entities that are associated with the primary resource:
- Go to **Analytics **> **Resource Inventory**.
- Click any **Resource Name** to view the drawer.
- Select the **Access** tab to see the details for:
- [AWS resource](#ds-aws-access)
- [Azure resource](#ds-azure-access)
- [GCP resource](#ds-GCP-access)
- [Unmanaged Database](#ds-unmanaged_database_access)
- [Snowflake](#ds-snowflake_access)
Supported Entity Types
DSPM discovers the following entity types during data scanning:
- [AWS](#aws_entity_types)
- [Azure](#azure_entity_types)
- [GCP](#gcp_entity_types)
- [Unmanaged Database](#unmanaged_database_entity_types)
- [Snowflake](#snowflake_entity_types)
[]
- **AWS API Gateway**: An entity that can access resources through AWS backend services, (such as Lambda, EC2, or S3) using IAM roles associated with API Gateway.
- **AWS EC2 Instance**: A compute resource that can access other AWS services (such as S3, RDS, or DynamoDB) using IAM roles associated with the EC2 instance profile.
- **AWS Organization Account**: A central management account that can access resources in the same AWS account using IAM roles with AWS Security Token Service (STS) permission.
- **IAM All Principals**: All entities, including users, services, and roles (both internal and external) that can access resources.
- **IAM External Account**: An account outside your current AWS organization that can access resources.
- **IAM External Role**: An IAM role that can access resources from an external AWS account.
- **IAM External User**: An IAM user who can access resources from an external AWS account.
- **Federated**: A federated entity is authenticated by an external identity provider (IdP), such as Okta or ADFS, permitting users from non-AWS systems to access AWS resources.
- **IAM Unmanaged Role**: An entity that can access resources through a role from another AWS account within the same organization that is not managed or onboarded to DSPM.
- **IAM Unmanaged User**: An IAM user that can access resources through a user from another AWS account within the same organization that is not managed or not onboarded to DSPM.
- **IAM User**: An individual entity that can access resources through an IAM user from the same AWS account. These users have credentials and permissions defined in IAM policies and can access resources based on assigned roles.
- **Lambda Function**: A serverless compute service that can access resources based on the permissions of the IAM role assigned to the AWS Lambda function.
[]
- **App Services**: A web-based service that can access resources using system-managed or user-defined identities.
- **Applications**: An entity that can access resources using service principals.
- **Azure AI Service**: An artificial intelligence service that can access resources using managed identities or service principals.
- **Azure Machine Learning Workspaces**: A central resource that can access resources such as data storage, compute resources, and other services required for machine learning tasks using managed identities or service principals.
- **Azure SQL Server**: A service that can access other resources, including a key vault using managed identities or service principals.
- **Azure Storage Account**: A service that can access resources using managed identities or service principals.
- **Azure Virtual Machine**: A compute resource that can access resources using managed identities or service principals.
- **Managed Identity Service Principals**: A service that can access resources using managed identity service principals.
- **PostgreSQL Flexible Server**: A service that can access resources using managed identities or service principals.
- **SQL Database**: A service that can access resources using managed identities or service principals.
- **User**: An individual user that can access resources via Azure Active Directory (AAD) identities.
- **Virtual Machine Scale Sets**: A compute resource that can access resources using managed identities or service principals.
[]
- **Domain**: A networking entity that can access resources through all identities (users, service accounts, etc.) using IAM roles.
- **External Service Account**: A service account outside your current GCP organization that can access resources.
- **External User**: A user outside your current GCP organization that can access resources.
- **Organization Service Account**: A service account within your organization that can access resources.
- **Organization User**: An individual user within your organization who can access resources.
- **Public User**: An individual user who is not part of your GCP organization can access resources.
- **Unmanaged Service Account**: A service account from a project within the same organization but not onboarded to DSPM can access resources.
[]
- **Onprem Unmanaged MySQL Server User**: A user that can access the database resources by logging in to MySQL Server.
- **Onprem Unmanaged Postgres Server User**: A user that can access the database resources by logging in to Postgres Server.
- **Onprem Unmanaged SQL Server Login**: An entity that can access the database resources by logging in to SQL Server.
- **Unmanaged AWS Postgres Server Users**: A user that can access the database resources by logging in to AWS Postgres Server.
- **Unmanaged AWS SQL Server Login**: An entity that can access the database resources by logging in to AWS SQL Server.
- **Unmanaged AWS MySQL Server User**: A user that can access the database resources by logging in to AWS MySQL Server.
- **Unmanaged Azure PostgreSQL User**: A user that can access the database resources by logging in to Azure Postgres Server.
- **Unmanaged Azure SQL Server Login**: An entity that can access the database resources by logging in to Azure SQL Server.
- **Unmanaged Azure MySQL Server User**: A user that can access the database resources by logging in to Azure MySQL Server.
[]
-
**Snowflake User**: Individual users or entities with access to a Snowflake account. Each user is represented by a user object within Snowflake, which stores their login name, password, and default settings like their primary role, virtual warehouse, and namespace.
-
**Snowflake Service**: A service or application that interacts with Snowflake.
-
**Snowflake Legacy Service**: Represents a non-interactive user or service but allows password and SAML authentication.
- []**ARN**: The Amazon Resource Name (ARN) to identify the resource.
- **Entity Type**: The type of entity (User, External, SSO IdP, etc.) that has access to the resource.
- **Access Level**: The permissions (Read, Edit, or Full Access) assigned to the entity.
- **Policy ARN**: The policy that defines the access level and grants permission to access the resource.
- **Last Activity**: The date and time the entity performed any action on the resource.
- **MFA Enabled**: Whether multi-factor authentication (MFA) is enabled for the entity.
- **Has Access Keys**: Whether the entity is assigned an access key. Access keys are long-term credentials for an IAM user or the AWS account root user.
![The AWS entities that have access to the resource](/downloads/dspm/analytics/data-inventory/viewing-access-levels/ds-aws-access.png)
- []**Entity Name**: The name of the Azure entity.
- **Entity Type**: The type of entity (User or Service Principal) that has access to the resource.
- **Access Level**: The permissions (Read, Edit, or Full Access) assigned to the entity.
- **Last Activity**: The date and time the entity performed any action on the resource.
- **MFA Enabled**: Whether multi-factor authentication (MFA) is enabled for the entity.
- **Role Definition ID**: The ID of the role. Role definition is a collection of permissions (read, write, delete, etc.). Azure has a collection of built-in roles that are assigned to users. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/role-based-access-control/role-definitions-list).
- **Role Assignment ID**: The assignment ID of the role. Role assignments control access to Azure resources. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles).
![Azure entities that have access to the resource](/downloads/dspm/analytics/data-inventory/viewing-access-levels/ds%20-%20azure-access.png)
- []**Principal**: The identity that has access to the storage bucket or GCP Cloud SQL instance.
- **Entity Type**: The type of entity (User or Service Principal) that has access to the storage bucket or GCP Cloud SQL instance.
- **Role**: The permissions assigned to the entity to perform specific actions (read, write, delete, etc.). To learn more, refer to the [Google documentation](https://cloud.google.com/iam/docs/roles-overview).
- **Policy ID**: The unique identifier for the policy.
- **Policy Scope**: The scope of the policy.
- **Access Level**: The permissions (Read, Edit, or Full Access) assigned to the entity.
![The GCP entities that have access to the resource](/downloads/dspm/analytics/data-inventory/viewing-access-levels/ds-gcp-access-1.png)
- []**Principal Name**: The identity that has access to the database.
- **Entity Type**: The type of entity (User) that has access to the database.
- **Access Path**: The access path to the database.
- **Target Entity**: The server or database name being accessed.
- **Access Level**: The permissions (Read, Edit, or Full Access) assigned to the entity.
![Shows the access tab details for unmanaged database](/downloads/dspm/analytics/resource-inventory/viewing-access-levels/ds-unmanageddatabase.png)
- []**Principal Name**: The identity that has access to the Snowflake account.
- **Principal Type**: The type of entity (user or service) that has access to the resource.
- **Target Entity**: The target database that is being accessed.
- **Access Level**: The permissions (Read, Edit, or Full Access) assigned to the entity.