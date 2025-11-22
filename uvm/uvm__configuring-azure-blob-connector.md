# Configuring the Azure Blob Connector
Source: https://help.zscaler.com/uvm/configuring-azure-blob-connector
PDF: https://help.zscaler.com/pdf/com/en/1530972.pdf

Azure Blob Storage is a cloud-based object storage solution provided by Microsoft Azure, allowing users to store and serve large amounts of unstructured data.
To create the Azure Blob data source, go to **Configure** > **Sources**. The connector tile appears among the other available data sources. To learn more, see [Creating Data Sources](/uvm/creating-data-sources).
[See image.](#azure-blob-tiles)
The Azure Blob connector is used for uploading files from your Azure storage to the platform, such as scan results, compliance reports, or any other security-related data stored in your Azure Blob containers. The connector is compatible with the following file formats:
- .json
- .csv
- .jsonl
Files in unsupported formats are not processed by the Azure Blob connector.
[]
![The Azure Blob tile](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/connector-drafts/configuring-source-name-connector/azure-blob-tiles.png)
Authentication
The source authentication configuration requires the Azure Blob Storage Account Connection parameter, which is your storage account connection string:
- [Retrieving the Connection String](#retrieve-connection-string)
- [Assigning Permissions](#assign-permissions)
[]
To retrieve the connection string:
- Log in to the Microsoft Azure portal.
- On the home page, in the **Search resources, services, and docs (G+/)** field, enter `Storage accounts`. From the drop-down menu, select **Storage accounts**.
- On the **Storage accounts** page, in the table, select the name of your storage account.
- From the left-side navigation, select **Security + networking** > **Access keys**.
- Click **Show** to display the connection string and **Copy**.
- Click **Copy** to copy the connection string.
[]
To assign the required permissions to the user associated with the connection string:
- Log in to the Microsoft Azure portal.
- On the home page, in the **Search resources, services, and docs (G+/)** field, enter `Storage accounts`. From the drop-down menu, select **Storage accounts**.
- On the **Storage accounts** page, in the table, select the name of your storage account.
- From the left-side navigation, select **Access Control (IAM)**.
- Click **Add** > **Add role assignment**.
- From the drop-down role menu, select a role with the required permissions (i.e., the built-in Storage Blob Data Reader role). The Storage Blob Data Reader role is a built-in Azure Blob role that covers the necessary permissions to access and read data from a storage account.
- In the **Assign access to** section, choose the relevant entity type (i.e., User, Group, or Service Principal) and select the desired entity.
- Click **Save**.
Retrieval
In the source setup Retrieval section, set the following filters and specifications:
- [Requested Containers List checkbox/drop-down menu](#requested-containers-list)
- [Requested Tags checkbox/drop-down menu](#requested-tags)
[]
The requested containers list is a list of containers in the storage account from which you can optionally specify a list of containers in your Azure Blob storage account from which you want to retrieve data, which limits the scope of data retrieval. If the containers are specified, only blobs from the mentioned containers are retrieved. If no containers are specified, data is retrieved from all containers in the storage account.
[]
The requested tags are a list of user-defined tags, in the format `key : value`. You can optionally specify a list of user-defined tags to filter the blobs retrieved from Azure Blob storage account containers. To limit the scope of data to those including specified tags, add tags in the format `key : value`, where the value can be empty. If the tags are specified, only blobs that include at least one of the listed tags are retrieved.
Roles and Permissions
The user or service principal associated with the connection string must have the following Azure RBAC permissions:
- Blob service operation - List Containers: `Microsoft.Storage/storageAccounts/blobServices/containers/read`. Ensure that the role is scoped to the storage account or above.** **To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/rest/api/storageservices/list-containers2?tabs=microsoft-entra-id).
- Blob service operation - List Blobs: `Microsoft.Storage/storageAccounts/blobServices/containers/blobs/read`. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/rest/api/storageservices/list-blobs?tabs=microsoft-entra-id).
To ensure successful connectivity, enable network access to your Azure Blob Storage account. You can allow access from all networks or restrict it to specific IP addresses. To enable network access:
- Log in to the Microsoft Azure portal.
- On the home page, in the **Search resources, services, and docs (G+/)** field, enter `Storage accounts`. From the drop-down menu, select **Storage accounts**.
- On the **Storage accounts** page, in the table, select the name of your storage account.
- From the left-side navigation, select **Security + networking** > **Networking**.
- On the **Firewalls and virtual networks** tab, in the **Public network access** section, configure your preferred access:
- If **Enabled from all networks** is selected, no further action is required.
-
To restrict access to specific IP addresses, select **Enabled from selected virtual networks and IP addresses**. Add the following IP addresses to the allowed range:
-
-
-
[](https://config.zscaler.com/zscalertwo.net/hubs)
| **Region** | **IP Addresses** |
| ---------- | ---------------- |
| US | 3.137.47.190/323.15.110.62/323.129.232.141/32 |
| EU | Refer to the Zscaler Config. |
These IP addresses must be added to allow the Zscaler service to connect to your Azure Blob storage account.