# Viewing the Graph for GCP Data Stores
Source: https://help.zscaler.com/dspm/viewing-graph-gcp-data-stores
PDF: https://help.zscaler.com/pdf/com/en/1520001.pdf

The Resource Inventory graph for GCP data stores is a visual representation of the scan result. The graph provides in-depth details of the GCP storage bucket, GCP Cloud Storage instance, and GCP Cloud SQL instance that contain sensitive data, the DLP engines and dictionaries that match the sensitive data, whether it is publicly exposed to the internet, including the public exposure path, the list of entities that can access the resource, and the vulnerabilities and malware detected in the resource. These details are helpful to quickly evaluate and remediate the issues, protect the data, and maintain the security posture.
The following graph depicts the scan results for a GCP storage bucket.
[]
![Graph for a storage bucket containing sensitive data along with the associated resources.](/downloads/dspm/analytics/graphs/viewing-graph-gcp-data-stores/ds-gcp-grapg.png)
The graph includes the following nodes:
- [1. Primary Resource](#GCP_View_primary_resource)
- [2. Public Exposure Path](#GCP_viewing_public_exposure_path)
- [3. Sensitive Records](#GCP_view_sensitive_records)
- [4. Managed Folder](#GCP_view_managed_folders)
- [5. Services](#gcp_services)
- [6. External](#gcp_external)
- [7. Service Accounts](#gcp_service_accounts)
- [8. Domains](#gcp_domains)
- [9. Users](#gcp_users)
[]View the GCP storage bucket details. You can:
- **Data Store Type**: The type of data store.
- **Resource Type**: The primary resource.
- **Project ID**: The unique identifier of the project in which the resource is located.
- **Project Name**: The name of the project in which the resource is located.
- **Organization ID**: The unique identifier of the organization to which the project belongs.
- **Region**: The region where the organization is located.
- **Latest Scan Status**: The status of the last scan.
- **Last Completed Scan**: The date and time when the last scan was completed.
- **Data Scanned**: The amount of data scanned.
- **Triggers**: The number of alerts raised for this resource.
- **Matched Files**: The number of files that matched the DLP engines.
- **DLP Engines**: The [DLP engines](/dspm/understanding-dlp-engines-and-dictionaries) that match the sensitive records.
- **DLP Dictionaries**: The dictionaries associated with the DLP engines.
- **Document Types**: The number of documents detected in the resource.
- **ID**: Copy the project ID to identify this resource in the GCP organization.
- **Tags**: The tags associated with the resource.
- **Posture**: The [security posture](/dspm/understanding-security-posture-state) of the resource.
- **Metadata**: Click to view the metadata for the resource.
![Details of the storage bucket that contains sensitive data](/downloads/dspm/analytics/graphs/viewing-graph-gcp-data-stores/ds-gcp-projectname.png)
[]View the publicly exposed resources. To learn more, see [Viewing the Public Exposure Path](/dspm/viewing-public-exposure-path).
![Describes how the storage bucket is publicly exposed and option to view the list of exposed files.](/downloads/dspm/analytics/graphs/viewing-data-inventory-graph/GCP%20Public%20Exposure_new.png)
[]View the details of a sensitive record.
![Details of the storage container that contains sensitive data.](/downloads/dspm/analytics/graphs/viewing-data-inventory-graph/GCP%20-%20Sensitive%20Records_new.png)
[]View the details of the managed folder in the storage bucket.
![Managed folders associated with the storage bucket.](/downloads/dspm/analytics/graphs/viewing-data-inventory-graph/GCP%20Managed%20Folder_new.png)
[]View the external entities that can access the resource. External entities are users, services, or roles that are part of a different cloud account that is not onboarded to DSPM.
![External entities that can access the primary resource.](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-data-inventory-graph-draft/External_1.png)
[]View the list of users who can access the primary resource.
![Users who can access the primary resource.](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-data-inventory-graph-draft/Users_0.png)
[]View the services that can access the primary resource.
![The services that can access the primary resource.](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-data-inventory-graph-draft/Services_0.png)
[]View the domains that can access the primary resource.
![The domain that can access the primary resource.](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-data-inventory-graph-draft/Domains.png)
[]View the service accounts that can access the primary resource.![The service accounts that can access the primary resource.](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-data-inventory-graph-draft/Service%20Accounts.png)