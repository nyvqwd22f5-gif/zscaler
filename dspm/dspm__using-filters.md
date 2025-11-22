# Using Filters
Source: https://help.zscaler.com/dspm/using-filters
PDF: https://help.zscaler.com/pdf/com/en/1479271.pdf

The DSPM Admin Portal includes filters on the dashboard, policies, alerts, data sensitivity settings, and data inventory pages. You can use these filters to focus on specific information and take the necessary action.
Common Filters
The following filters are available by default:
- **Business Units**: Returns results only from selected business units. Business units are logical groups of multiple cloud accounts or data centers.
- **Cloud**: Returns results from selected cloud service providers (AWS, Azure, or GCP), Snowflake, and on-premises databases.
- **Accounts**: Returns results from selected cloud accounts and data centers.
- **Regions**: Returns results only from selected regions.
Additional Filters
Additional filters are available for the following features:
- [Data Inventory](#ds-difilters)
- [Data Posture Policies](#ds-policyfilters)
- [Alerts](#ds-alertsfilter)
- [Investigation](#ds-investigatefilters)
- [Compliance](#ds-compliancefilters)
- [Data Duplication](#ds-dataduplicationsfilter)
Managing Filters
You can use the following options for filters:
- [Apply a Filter](#ds-applyfilter)
- [Add a Filter](#ds-addf)
- [Reset Filters](#filter-reset)
- []**Sensitive Data**
- **Sensitive**: Shows the data stores containing sensitive data. This result depends on the DLP settings you've configured on the [Data Sensitivity Settings page](/dspm/about-data-sensitivity-settings).
- **Sensitive & Non Sensitive**: Shows any data store that has data matched by a DLP engine or document type, regardless of whether you have defined the engine as sensitive or not. If DSPM scans a data store but does not detect any data, then this filter does not return any result.
-
**All**: Shows all the data stores.
Let's consider this scenario. A cloud account has 10 S3 buckets. You have marked the PCI DLP engine as sensitive, and the HIPPA DLP engine as non-sensitive. DSPM scans 5 S3 buckets and detects data that matches PCI in 1 bucket, HIPPA in 3 buckets, and no matched data in 1 bucket. When you apply any of the above filters, you can see this result:
- **Sensitive**: One S3 bucket that contains sensitive data.
- **Sensitive & Non-Sensitive**: 4 S3 buckets.
- **All**: All 10 buckets.
- **Posture**: Returns resources based on the selected posture.
- [List of Posture Labels](#ds-posturelabels)
- **DLP Engines**: Returns records that matched a specific [DLP engine](/dspm/understanding-dlp-engines-and-dictionaries). You can exclude DLP engines as required.
- **DLP Dictionaries**: Returns records that matched a specific [DLP dictionary](/dspm/understanding-dlp-engines-and-dictionaries). You can exclude DLP dictionaries as required.
- **Resource Type:** Returns data related to the [specific resource type](/dspm/supported-data-stores) (AWS EC2 Instance, Azure Storage Account, GCP Storage Account, etc.).
- **Resource Category**: Returns data specific to a resource category.
- [List of Resource Categories](#ds-resourcecategories)
- **Document Type**: Returns the selected document types (financial, medical, HR, legal, technical, etc.).
- [List of Document Types](#ds-documenttypeslist)
- **Scan Status**: Returns resources based on the selected [scan status](/dspm/understanding-scan-status).
- **Tags**: Returns resources that match a specific tag.
- **Malware**: Returns resources containing malware.
- **Scanned Once**: Returns resources that are scanned at least once.
- **Malware Type**: Returns data specific to a malware type.
- **Managed Folder**: Returns sensitive data specific to a managed folder.
- **Container**: Returns sensitive data specific to a container.
- **Access Level**: Returns data based on the selected access level (Edit, Read, or Full Access).
- **Entity Type**: Returns data based on the selected entity type.
- **Risk Levels**: Returns resources based on the selected risk level. The following is the risk score range:
- 1–25: Low
- 25–50: Medium
- 50–75: High
- 75–100: Critical
- **Regions**: Returns resources for the selected regions. You can exclude regions as required.
- **Principal**: Returns the entered principal value.
- **Principal Type**: Returns the selected type of the principal.
- **Event Name**: Returns the name of the event.
- []**Policy Severity**: Returns policies based on the severity level (Critical, High, Medium, and Low).
- **Policy Category**: Returns policies based on the [threat category](/dspm/threat-categories).
- **Policy State**: Returns policies based on the enabled or disabled state.
- **Policy Source**: Returns predefined or custom policies.
- **Primary Resource Type**: Returns policies based on the selected primary resource type.
- **Compliance Framework**: Returns policies that match a specific compliance framework.
- **MITRE ATT&CK**: Returns policies that match a specific [MITRE ATT&CK ](https://attack.mitre.org/).
- []**Resource Type**: Returns data related to the specific resource.
- **Alert Status**: Returns alerts that match a specific alert status.
- **Policy Category**: Returns policies based on the [threat category](/dspm/threat-categories).
- **Severity**: Returns alerts based on the selected severity level (Critical, High, Medium, and Low). By default, the critical alerts are displayed first on the Alerts page.
- **Risk Level**: Returns resources that match the selected risk level (Critical, High, Medium, and Low).
- **Tags**: Returns resources that match the specific tag.
- **Malware Name**: Returns data specific to a malware name.
- **Created Date**: Returns alerts that match the specific duration or date.
- **Managed Folder**: Returns sensitive data specific to a managed folder.
- **DLP Engines**: Returns records that matched a specific [DLP engine](/dspm/understanding-dlp-engines-and-dictionaries). You can exclude DLP engines as required.
- **DLP Dictionaries**: Returns records that matched a specific [DLP dictionary](/dspm/understanding-dlp-engines-and-dictionaries). You can exclude DLP dictionaries as required.
- **Document Types**: Returns the selected document types (financial, medical, HR, legal, technical, etc.).
- **Policy**: Returns alerts generated for the selected policy ID.
[]
- **Control Number**: Returns data specific to a control number.
- **Control Category**: Returns data specific to a control category.
- **Policy**: Returns alerts generated for the selected policy ID.
[]
- **DLP Engines**: Returns duplicate files that match a specific [DLP engine](/dspm/understanding-dlp-engines-and-dictionaries). You can exclude DLP engines as required.
- **DLP Dictionaries**: Returns duplicate files that match a specific [DLP dictionary](/dspm/understanding-dlp-engines-and-dictionaries). You can exclude DLP dictionaries as required.
- **Document Types**: Returns duplicate files that match the selected [document types](/dspm/understanding-data-classification) (financial, medical, HR, legal, technical, etc.).
- **Modification Time**: Returns duplicate files that match the selected time range.
- []**Cloud Type**: Return queries for a specific cloud type (AWS, Azure, or GCP).
- **Resource Type**: Returns queries for a specific resource type.
- **Date**: Returns queries that match the specific duration or date.
[]To reset the filters to the original system settings, click **Reset**.
[See image.](#ds-resetfilters)
[]To apply a specific filter:
- Use the filter drop-down menus. Each filter drop-down menu has multiple choices and text search.
-
Select the checkbox for the data that must be displayed in the column, then click **Apply**.
The specific column shows the filtered results.
[See image.](#ds-selectf)
[]To add a new filter:
- Click the** Add Filter** icon (![ds-addfiltericon.png](/downloads/dspm/getting-started/admin-portal/using-filters/ds-addfiltericon.png)
).
-
Select the data that must be displayed in the column, then click **Apply**.
The specific column shows the filtered results.
[See image.](#ds-addfilters)
- To cancel the settings, click **Cancel**. The table reverts to the previous settings.
[]![Apply a filter](/downloads/dspm/getting-started/admin-portal/using-filters/ds-filters-select.png)
[]![Add a new filter](/downloads/dspm/getting-started/admin-portal/using-filters/ds-filtersadd.png)
[]![Reset the filters](/downloads/dspm/getting-started/admin-portal/using-filters/ds-filterreset.png)
- []AI and Machine Learning
- Backup
- Compute
- Database
- NoSQL Database
- Storage
- []Backup Enabled
- No Backup
- Publicly Exposed
- Not Exposed
- Encrypted
- Not Encrypted
- PMK Encrypted
- CMK Encrypted
- Logging Enabled
- Logging Disabled
- Partial Logging
- DR Enabled
- No DR Policy
- Exposed to AI Service
- Not Exposed to AI Service
- []Department of Motor Vehicles (DMV)
- Financial
- HR
- Immigration
- Insurance
- Legal
- Medical
- Real Estate
- Source Code
- Technical