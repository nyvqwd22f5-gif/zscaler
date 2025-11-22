# Viewing the Graph for Azure Data Stores
Source: https://help.zscaler.com/dspm/viewing-graph-azure-data-stores
PDF: https://help.zscaler.com/pdf/com/en/1519951.pdf

The Resource Inventory graph for Azure data stores is a visual representation of the scan result. The graph provides in-depth details of the [Azure resource](/dspm/supported-data-stores) that contains sensitive data, the DLP engines and dictionaries that match the sensitive data, whether it is publicly exposed to the internet, including the public exposure path, the list of entities that can access the resource, and the vulnerabilities and malware detected in the resource. These details are helpful to quickly evaluate and remediate the issues, protect the data, and maintain the security posture.
Azure File Share and Azure Table Storage are also detected as associated resources.
The following graph depicts the scan results for an Azure virtual machine.
[]
![Graph for an Azure virtual machine and all the associated resources.](/downloads/dspm/analytics/graphs/viewing-graph-azure-data-stores/ds-azure-graph-store_0.png)
The graph includes the following nodes:
- [1. Primary Resource](#azure_primary_resource)
- [2. Public Exposure Path](#azure_public_exposure_path)
- [3. Resource with Sensitive Data](#azure_impacted_volume)
- [4. Sensitive Records](#azure_sensitive_records)
- [5. Databases](#azure_all_volumes)
- [6. CVE](#azure_cve)
- [7. Malware](#azure_malware)
- [8. External](#azure_external)
- [9. Applications](#azure_applications)
- [10. Services](#azure_services)
- [11. Managed Identities](#azure_managed_identities)
- [12. Users](#azure_users)
[]
- **Data Store Type**: The type of data store.
- **Resource Type**: The primary resource.
- **Subscription ID**: The unique identifier of the subscription in which the resource is stored.
- **Subscription Name**: The name of the subscription in which the resource is stored.
- **Tenant ID**: The unique identifier of the tenant to which the subscription belongs.
- **Region**: The region where the resource is located.
- **Latest Scan Status**: The status of the last scan.
- **Last Completed Scan**: The date and time when the last scan was completed.
- **Data Scanned**: The amount of data scanned.
- **Triggers**: The number of sensitive records in the resource.
- **Matched Files**: The number of files that matched the DLP engines.
- **DLP Engines**: The [DLP engines](/dspm/understanding-dlp-engines-and-dictionaries) that match the sensitive records.
- **DLP Dictionaries**: The dictionaries associated with the DLP engines.
- **Document Types**: The number of documents detected in the resource.
- **ID**: Copy the tenant ID to identify this resource in the Azure tenant.
- **Tags**: The tags associated with the resource.
- **Posture**: The [security posture](/dspm/understanding-security-posture-state) of the resource.
- **Metadata**: Click to view the metadata for the resource.
![Details of the Azure virtual machine](/downloads/dspm/analytics/graphs/viewing-graph-azure-data-stores/ds-azure-subscriptioname.png)
[]View the publicly exposed resources. Click **Show Public Exposure Path** to view another graph that shows how the resource is publicly exposed due to misconfigurations or vulnerabilities in the associated resources. To learn more, see [Viewing the Public Exposure Path](/dspm/viewing-public-exposure-path).
[See image.](#public_exposure_path_image)
![The details of the network interface that is misconfigured](/downloads/dspm/analytics/graphs/viewing-graph-azure-data-stores/ds-public_internet_azure.png)
[]View the details of the database that contains sensitive data.
![Details of the database that contains sensitive data](/downloads/dspm/analytics/graphs/viewing-graph-azure-data-stores/ds-workspace_azure.png)
[]View the details of the sensitive record.
![View the sensitive records](/downloads/dspm/analytics/graphs/viewing-graph-azure-data-stores/ds-pci_record_azure.png)
[]View all the associated resources (servers, managed and unmanaged databases), including those that do not contain any sensitive data and the ones that are not scanned. In this scenario, the Azure virtual machine has two databases that contain sensitive data.
Azure Machine Learning workspace contains AI applications and services that can read from and write data to the storage accounts. DSPM detects and displays the Azure Machine Learning workspaces that can access the storage account. [See image.](#ds-di-azureml)
![All the resources that are associated with the primary resource.](/downloads/dspm/analytics/graphs/viewing-data-inventory-graph/Azure%20All%20Volume%20Node_new.png)
[]View the total number of vulnerabilities classified by severity. Click **View All CVEs** to see the [vulnerability details](/dspm/viewing-vulnerability-details).
![List of vulnerabilities detected in the primary resource along with the severity levels.](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-azure-graph-draft/CVE.png)
[]View the malware detected in the resource. Click **View All Malware **to see the [malware details](/dspm/viewing-malware-details).
![Details of malware found in the primary resource.](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-azure-graph-draft/Malware.png)
[]View the list of applications that can access the resource.
![The applications that can access the primary resource.](/downloads/dspm/analytics/graphs/viewing-graph-azure-data-stores/ds-applications_azure.png)
[]View the external entities that can access the resource. These entities are part of a different cloud account that is not onboarded to the DSPM Admin Portal.
![The list of external users who can access the primary resource.](/downloads/dspm/analytics/graphs/viewing-graph-azure-data-stores/ds-external-azure.png)
[]View the managed entities that can access the primary resource.
![The managed identities that can access the primary resource](/downloads/dspm/analytics/graphs/viewing-graph-azure-data-stores/ds-managed_identity_azure.png)
[]View the list of users who can access the resource.
![The list of users who can access the primary resource.](/downloads/dspm/analytics/graphs/viewing-graph-azure-data-stores/ds-user_azure.png)
[]View the Azure services that can access the resource.
![The list of Azure services that can access the primary resource.](/downloads/dspm/analytics/graphs/viewing-graph-azure-data-stores/ds-services_azure.png)
[]
![Public exposure graph shows the misconfigured entity that caused the resource to be publicly exposed.](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-data-inventory-graph-draft/Public%20Exposure%20Path%202_0.png)
[]![Details of the Azure ML workspace that has access to the primary resource](/downloads/dspm/analytics/graphs/viewing-data-inventory-graph/ds-di-mlresource.png)