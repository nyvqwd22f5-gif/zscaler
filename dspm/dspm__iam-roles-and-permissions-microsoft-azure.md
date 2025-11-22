# IAM Roles and Permissions for Microsoft Azure
Source: https://help.zscaler.com/dspm/iam-roles-and-permissions-microsoft-azure
PDF: https://help.zscaler.com/pdf/com/en/1486396.pdf

As part of the [onboarding](/dspm/onboarding-microsoft-azure-tenant) process, you need to deploy the DSPM templates in the Microsoft Entra tenant. These templates create a service principal (enterprise application), custom roles, and managed identities in Microsoft Entra ID. DSPM requires these roles to connect to the Microsoft Entra tenant, discover the resources, and collect metadata.
IAM Roles
DSPM creates the following IAM roles to access the Azure subscriptions:
- [Resource Discovery Role](#resource-discovery)
- [DSPM Access Role](#dspm-access-role)
- [Target Role](#target-role)
- [Orchestrator Role](#orchestrator-role)
- [Scanner Role](#scanner-role)
- [Custom Network Configuration Role](#byon)
- [Encryption Role](#encryption-role)
[]This role is used by the Local Scanner Platform to perform the CMK encryption related tasks on instances.
| Permission | Scope | Type | Purpose |
| ---------- | ----- | ---- | ------- |
| `Microsoft.KeyVault/vaults/keys/read` | DSPM resource group | Actions | To list the keys in a specified vault |
| `Microsoft.KeyVault/vaults/keys/unwrap/action` | DSPM resource group | DataActions | To unwrap a symmetric key with a Key Vault key |
| `Microsoft.KeyVault/vaults/keys/wrap/action` | DSPM resource group | DataActions | To wrap a symmetric key with a Key Vault key |
| `Microsoft.KeyVault/vaults/keys/read` | DSPM resource group | DataActions | To list the keys in a specified vault |
| `Microsoft.KeyVault/vaults/keys/decrypt/action` | DSPM resource group | DataActions | To decrypt ciphertext with a key |
| `Microsoft.KeyVault/vaults/keys/encrypt/action` | DSPM resource group | DataActions | To encrypt plaintext with a key |
[]DSPM requires the resource discovery role to identify resources within the onboarded subscriptions. This role is assigned at the management group level and has the following permissions:
| Permission | Scope | Type | Purpose |
| ---------- | ----- | ---- | ------- |
| `*/read` | Management group | Actions | To allow read permissions to read the metadata of Azure resources |
| `Microsoft.Insights/DiagnosticSettings/read` | Management group | Actions | To discover diagnostic settings |
| `Microsoft.Insights/eventtypes/values/read` | Management group | Actions | To read activity logs |
| `Microsoft.Resources/subscriptions/resourceGroups/read` | Management group | Actions | To discover Azure resource groups |
| `Microsoft.Storage/storageAccounts/blobServices/containers/read` | Management group | Actions | To discover Azure blob containers |
| `Microsoft.Storage/storageAccounts/listkeys/action` | Management group | Actions | To discover Azure storage account keys |
[]DSPM requires the access role to send data scan requests to the storage account queues that are used by the orchestrator subscription. The role is assigned at the DSPM resource group level and has the following permissions:
| Permission | Scope | Type | Purpose |
| ---------- | ----- | ---- | ------- |
| `Microsoft.Compute/virtualMachines/read` | DSPM resource group | Actions | To read virtual machines |
| `Microsoft.Compute/virtualMachineScaleSets/deallocate/action` | DSPM resource group | Actions | To deallocate virtual machine scale set |
| `Microsoft.Compute/virtualMachineScaleSets/virtualMachines/delete` | DSPM resource group | Actions | To delete virtual machine in a virtual machine scale set |
| `Microsoft.Compute/virtualMachineScaleSets/write` | DSPM resource group | Actions | To create or update virtual machine scale set |
[]The orchestrator subscription requires the target role to scan the data stores. The role is assigned at the monitoring scope or target subscriptions level and has the following permissions:
| Permission | Scope | Type | Purpose |
| ---------- | ----- | ---- | ------- |
| `*/read` | Monitored Subscriptions | Actions | To allow read permissions to read the metadata of Azure resources |
| `Microsoft.Compute/disks/beginGetAccess/action` | Monitored Subscriptions | Actions | To get the SAS URI of the disk |
| `Microsoft.DBforPostgreSQL/flexibleServers/write` | Monitored Subscriptions | Actions | To restore the PostgreSQL Flexible Server into the Orchestrator subscription |
| `Microsoft.Insights/DiagnosticSettings/write` | Monitored Subscriptions | Actions | To create a diagnostic setting for Azure storage accounts |
| `Microsoft.Sql/servers/databases/write` | Monitored Subscriptions | Actions | To restore the SQL server into the Orchestrator subscription |
| `Microsoft.Storage/storageAccounts/listkeys/action` | Monitored Subscriptions | Actions | To read Azure storage account keys |
| `Microsoft.KeyVault/vaults/keys/read` | Monitored Subscriptions | DataActions | To list the keys in a specified vault |
| `Microsoft.KeyVault/vaults/keys/unwrap/action` | Monitored Subscriptions | DataActions | To unwrap a symmetric key with a Key Vault key |
| `Microsoft.KeyVault/vaults/keys/wrap/action` | Monitored Subscriptions | DataActions | To wrap a symmetric key with a Key Vault key |
| `Microsoft.Storage/storageAccounts/blobServices/*/read` | Monitored Subscriptions | DataActions | To read blobs from containers |
| `Microsoft.KeyVault/vaults/secrets/getSecret/action` | Monitored Subscriptions | DataActions | To get the value of a secretThis permission is conditional and only required if Custom Network is used with Unmanaged DB Scanning. |
[]To configure a custom network in your organization, the orchestrator requires the following roles and permissions at the subscription level, to establish a connection between the custom network components, the scanner instance, and SQL database.
These permissions are conditional and only required if Custom Network is selected.
| Permission | Scope | Type | Purpose |
| ---------- | ----- | ---- | ------- |
| `Microsoft.Network/networkSecurityGroups/join/action` | Orchestrator Subscription | Actions | To join the Network Security Group of the Custom Network mode |
| `Microsoft.Network/virtualNetworks/subnets/join/action` | Orchestrator Subscription | Actions | To join the subnet of the Custom Network |
| `Microsoft.Network/virtualNetworks/subnets/joinViaServiceEndpoint/action` | Orchestrator Subscription | Actions | To join the SQL database to a subnet of the Custom Network |
[]The scanner role is used by the scanner instances that are launched in the orchestrator subscription to perform data scanning. The role is assigned at the DSPM resource group level and has the following permissions:
| Permission | Scope | Type | Purpose |
| ---------- | ----- | ---- | ------- |
| `*/read` | DSPM resource group | Actions | To allow read permissions to read the metadata of Azure resources |
| `Microsoft.KeyVault/vaults/secrets/getSecret/action` | DSPM resource group | DataActions | To get the value of a secret |
| `Microsoft.Storage/storageAccounts/blobServices/*/read` | DSPM resource group | DataActions | To read blobs from containers |
[]The orchestrator instance requires this role to scan the data. The role is assigned at the DSPM resource group level and has the following permissions:
| Permission | Scope | Type | Purpose |
| ---------- | ----- | ---- | ------- |
| `*/read` | DSPM resource group | Actions | To allow read permissions to read the metadata of Azure resources |
| `Microsoft.Compute/disks/beginGetAccess/action` | DSPM resource group | Actions | To get the SAS URI of the disk |
| `Microsoft.Compute/disks/delete` | DSPM resource group | Actions | To delete the disk |
| `Microsoft.Compute/disks/write` | DSPM resource group | Actions | To create the disk |
| `Microsoft.Compute/snapshots/delete` | DSPM resource group | Actions | To delete the snapshot |
| `Microsoft.Compute/snapshots/write` | DSPM resource group | Actions | To create a snapshot |
| `Microsoft.Compute/virtualMachines/delete` | DSPM resource group | Actions | To delete the virtual machine |
| `Microsoft.Compute/virtualMachines/extensions/write` | DSPM resource group | Actions | To create virtual machine extensionThis permission is conditional and only required if Custom Network is selected. |
| `Microsoft.Compute/virtualMachines/write` | DSPM resource group | Actions | To create a virtual machine for scanning |
| `Microsoft.Compute/virtualMachineScaleSets/read` | DSPM resource group | Actions | To read the properties of virtual machine scale sets |
| `Microsoft.Compute/virtualMachineScaleSets/virtualMachines/write` | DSPM resource group | Actions | To update the properties of a virtual machine in a VM scale sets |
| `Microsoft.DBforPostgreSQL/flexibleServers/delete` | DSPM resource group | Actions | To delete the PostgreSQL flexible server used for scanning |
| `Microsoft.DBforPostgreSQL/flexibleServers/PrivateEndpointConnectionsApproval/action` | DSPM resource group | Actions | To determine if the user is allowed to approve a private endpoint connection |
| `Microsoft.DBforPostgreSQL/flexibleServers/read` | DSPM resource group | Actions | To read the properties of the PostgreSQL flexible server |
| `Microsoft.DBforPostgreSQL/flexibleServers/write` | DSPM resource group | Actions | To create the PostgreSQL flexible server for scanning |
| `Microsoft.KeyVault/vaults/keys/versions/read` | DSPM resource group | Actions | To list the versions of a specified key, or read the specified version of a key |
| `Microsoft.KeyVault/vaults/secrets/write` | DSPM resource group | Actions | To create a new secret |
| `Microsoft.ManagedIdentity/userAssignedIdentities/assign/action` | DSPM resource group | Actions | To assign the user-managed identity to scanner-related instances |
| `Microsoft.Network/networkSecurityGroups/join/action` | DSPM resource group | Actions | To join the scanner network security group |
| `Microsoft.Network/privateEndpoints/delete` | DSPM resource group | Actions | To delete the private endpoint created for scanning |
| `Microsoft.Network/privateEndpoints/write` | DSPM resource group | Actions | To create the private endpoint for scanning |
| `Microsoft.Network/virtualNetworks/subnets/join/action` | DSPM resource group | Actions | To join the scanner virtual network |
| `Microsoft.Network/virtualNetworks/subnets/joinViaServiceEndpoint/action` | DSPM resource group | Actions | To join SQL database to scanner subnet |
| `Microsoft.Sql/servers/databases/delete` | DSPM resource group | Actions | To delete the SQL server database created for scanning |
| `Microsoft.Sql/servers/databases/write` | DSPM resource group | Actions | To create the SQL server database for scanning |
| `Microsoft.Sql/servers/delete` | DSPM resource group | Actions | To delete the SQL server for scanning |
| `Microsoft.Sql/servers/write` | DSPM resource group | Actions | To create the SQL server for scanning |
| `Microsoft.Sql/servers/virtualNetworkRules/delete` | DSPM resource group | Actions | To delete a virtual network rule added for scanning |
| `Microsoft.Sql/servers/virtualNetworkRules/write` | DSPM resource group | Actions | To create a virtual network rule for scanning |
| `Microsoft.Storage/storageAccounts/listkeys/action` | DSPM resource group | Actions | To discover Azure storage account keys |
| `Microsoft.Storage/storageAccounts/queueServices/queues/read` | DSPM resource group | Actions | To read DSPM queues |
| `Microsoft.KeyVault/vaults/keys/read` | DSPM resource group | DataActions | To list the keys in a specified vault |
| `Microsoft.KeyVault/vaults/keys/unwrap/action` | DSPM resource group | DataActions | To unwrap a symmetric key with a Key Vault key |
| `Microsoft.KeyVault/vaults/keys/wrap/action` | DSPM resource group | DataActions | To wrap a symmetric key with a Key Vault key |
| `Microsoft.KeyVault/vaults/secrets/delete` | DSPM resource group | DataActions | To delete a secret created for scanning |
| `Microsoft.KeyVault/vaults/secrets/getSecret/action` | DSPM resource group | DataActions | To get the value of a secret |
| `Microsoft.KeyVault/vaults/secrets/readMetadata/action` | DSPM resource group | DataActions | To read the metadata of the secret |
| `Microsoft.KeyVault/vaults/secrets/setSecret/action` | DSPM resource group | DataActions | To set the value for the secret |