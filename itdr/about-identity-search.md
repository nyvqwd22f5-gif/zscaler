# About Identity Search
Source: https://help.zscaler.com/itdr/about-identity-search
PDF: https://help.zscaler.com/pdf/com/en/1531882.pdf

The Identity Search feature addresses the challenge of correlating identity information and risk in situations involving identity sprawl. Currently, organizations operate multiple identity providers, such as Active Directory (AD), Entra ID, Okta, etc. For example, organizations might sync identities from AD to Entra ID to provide access to SaaS applications. This can make it challenging for organizations to gain correlated visibility into the statuses of these identities.
The Identity Search page enables you to search for a specific identity (user) and retrieve information across various identity platforms (Active Directory (AD), Entra ID, and Okta), all correlated on a single page in the Zscaler ITDR Admin Portal. You can search for identities using different parameters, such as username, first name, last name, email ID, etc. Most importantly, these identities are correlated and enriched with information from the ITDR posture capabilities, including what credentials they store on endpoints and any risky changes recorded against the identities.
Before using the Identity Search feature, do the following:
- Run an [AD](/itdr/scanning-active-directory) or [Entra ID](/itdr/connecting-entra-id-tenant-zscaler-itdr-admin-portal) scan that enriches identity information with posture issues affecting the identity. Enable attribute collection for [AD](/itdr/enabling-active-directory-attribute-collection) and [Entra ID](/itdr/about-entra-id-posture-scan) when configuring these scans. This allows you to view the attributes of AD and Entra ID that are relevant to the investigation context.
- [Integrate ITDR with Okta](/itdr/integrating-itdr-okta). This is required to correlate identities in Okta.
- [Run an endpoint credential exposure scan](/itdr/configuring-endpoint-credential-exposure-scan) to enrich identity information with the state of stored credentials and flag any risky credentials or settings.
- [Configure a threat detection policy](/itdr/creating-threat-detection-policy) to enrich identity information with threat events recorded for a given identity.
To use the Identity Search feature, you must run an AD or Entra ID posture scan with attribute collection enabled. The more ITDR capabilities you use, the more correlated information is available for a given identity.
The Identity Search page provides the following benefits and enables you to:
- Quickly search for a specific identity and view correlated information on a single page without the need to navigate through multiple pages.
- View consolidated insights into posture issues, recent active changes, exposed endpoint credentials, etc. for a specific identity across identity platforms.
About the Identity Search Page
On the Identity Search page (ITDR > Dashboard > Identity Search), you can do the following:
- Search for an identity across various identity platforms (AD, Entra ID, and Okta).
- View the search results for the identity. For each identity, you can view:
- **Identity**: The identity details. [Click an identity to view additional details](/itdr/viewing-identity-details).
- **Sources**: The name of the identity platform (**AD**,** Entra ID**, and **Okta**) from which the information is sourced.
- **Last Login**: The date and time when the identity was last logged in on the respective identity platform.
- **Issues**: The total number of issues identified for each identity across different identity platforms, showing counts for **AD**, **Entra ID**, and **Okta**.
- **Privileged User**: Indicates if the identity has privileged access. A checkmark indicates that the user is a privileged user on the corresponding platform, and an **X** mark indicates that the user is not a privileged user.
- **MFA Enabled**: Indicates multi-factor authentication (MFA) is enabled for the identity on each platform. A checkmark indicates that MFA is enabled for the user on the corresponding platform, and an **X** mark indicates that MFA is not enabled.
- Filter the results. You can use a combination of filters to query the results. For example, you can select **Entra ID** and **MFA not enabled** to view the results for a specific Entra ID identity for which MFA is not enabled. The following filters are available:
- **AD**, **Entra ID**, and **Okta**
- **Issues**
- **Changes**
- **Is Privileged**
- **MFA not enabled**
- **Credential Issues**
-
Show or hide table columns. By default, all columns are displayed. You can use the column selector to show or hide the column.
[See image.](#itdr-id-search-column-selector-image)
- [Copy specific columns from the table](/itdr/using-tables#itdr-copy-columns-table-section) and [download the details as a CSV or JSON file](/itdr/using-tables#itdr-export-table-csv-section).
![About the Identity Search page](/downloads/itdr/dashboard/identity-search/about-identity-search/itdr-about-identity-search-page-1.png)
[]![View column selector](/downloads/itdr/dashboard/identity-search/about-identity-search/itdr-about-identity-search-page-column-selector.png)