# About Identity Inventory
Source: https://help.zscaler.com/dspm/about-identity-inventory
PDF: https://help.zscaler.com/pdf/com/en/1529532.pdf

An identity represents a user, device, application, or service that can access data stores containing sensitive data in the cloud environment. While securing sensitive data, it is crucial to control and manage the permissions assigned to identities, as excessive permissions and insecure configurations could lead to security breaches. DSPM detects identities in all the onboarded cloud accounts (AWS, Azure, and GCP), including [managed and unmanaged databases, and Snowflake.](/dspm/viewing-graph-databases)
Identity Inventory has the following benefits and enables you to:
- View the identities that can access resources containing sensitive data within your cloud environment.
- View the data stores accessed by an identity.
- View the type of sensitive data accessed by each identity.
- View the security posture of the identity.
About the Identity Inventory Page
On the Identity Inventory page (Analytics > Identity Inventory), you can do the following:
- View the list of identities. For each identity, you can see:
- **Entity Name**: The name of the entity. [Click the entity name to view additional details.](#ds-identitydetails)
- **Entity ID**: The unique identifier of the identity.
- **Entity Type**: The type of the identity (AWS Organization Account, IAM Unmanaged User, etc.).
- **Cloud**: The cloud service provider in which the identity is present.
- **Data Stores**: The number of data stores that the identity has access to.
- **Sensitive Data Stores**: The number of data stores containing sensitive data.
- **Triggers**: The total number of records that matched the DLP engines.
- **Files & Tables**: The number of files and tables the identity has access to.
- **Posture**: The security posture assigned to the identity (Dormant Identity, MFA Disabled, etc.). Hover over the label to see the description of each posture.
- **DLP Engines**: The DLP engines in the data stores.
- **DLP Dictionaries**: The DLP dictionaries associated with the DLP Engines.
- **Document Types**: The different document types present in the data store.
- **Document Categories**: The document category to which the document type belongs.
- Apply [filters ](/dspm/using-filters)to view specific data.
- Click the Add icon (![sss.png](/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-about-identity-inventory/sss.png)
) to apply additional filters.
- Sort the column data.
- View the list of DLP engines that the identity has access to.
[See image.](#ds-dlp_engines)
- View the list of document categories.
[See image.](#ds-documentcategories)
- [Show or hide columns in the table.](/dspm/using-tables)
- Search for specific data in the searchable columns.
- Export the results and [download the report ](/dspm/downloading-reports)as an Excel file.
![Shows the list of all the identities in the cloud environment.](/downloads/dspm/analytics/identity-inventory/about-identity-inventory/ds-identity-page.png)
[]
![Shows the list of DLP engines that matched the data stores](/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-about-identity-inventory/ds-dlpenigined_0.png)
[]
![Shows the list of document categories that matched the data stores](/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-about-identity-inventory/ds-documentcategories.png)
[]
![Shows additional details about identities](/downloads/dspm/analytics/identity-inventory/about-identity-inventory/ds-identity-details.png)