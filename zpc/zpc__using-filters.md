# Using Filters
Source: https://help.zscaler.com/zpc/using-filters
PDF: https://help.zscaler.com/pdf/com/en/1403096.pdf

The ZPC Admin Portal displays information related to your cloud deployment's security posture for all cloud service providers, cloud accounts, and regions. ZPC offers filters across its policies, assets, identities, alerts, and audit logs to easily focus on specific business units or accounts and review the data.
There are common filters across the modules and additional filters for specific modules.
- [Common Filters](#common-filters)
- [Additional Filters](#additional-filters)
Some features such as [Assets](/zpc/about-cloud-assets), [Compliance Dashboard](/zpc/about-compliance-dashboard), and [Identities](/zpc/about-cloud-identities) offer filtering by tags defined in the cloud service provider. You can use the **Add Filter** icon to view available tags.
[Using Filters]
To focus on specific information using filters:
- Use the filter drop-down menus to filter the columns. Each filter drop-down menu offers you multiple choices and text search.
[See image.](#filters)
- Select the **Add Filter **icon (![The add filter icon](/downloads/zpc/getting-started/admin-portal/using-filters/zpc-add-filter-icon.png)
) to add a filter to the required column.
[See image.](#select-column)
- Select the data that must be displayed in the column, then click **Apply**.
[See image.](#select-data)
The specific column shows the filtered results.
To save the filtered results, click the **Settings** icon (![Click the icon to view options for managing filters](/downloads/zpc/getting-started/admin-portal/using-filters/zpc-threedoticon.png)
), then click **Save Changes**.
Managing Filters
You can use the following options to manage the filters:
- [Save Filters](#filter-saveasoption)
- [Set up Default Filter](#default-filter)
- [Reset Filters](#filter-reset)
- [Hide Filters](#filter-hide)
- [Delete Filters](#filter-delete)
- []After applying a filter, click the **Settings** icon (![Click the icon to view options for managing filters](/downloads/zpc/getting-started/admin-portal/using-filters/zpc-threedoticon.png)
),then click **Save As**.
[See image.](#filter-saveas)
- In the **Save Filters** window, enter a name for the filter, then click **Save**.
[See image.](#save-filter)
- The saved filter name is displayed in the **Select Filters** drop-down menu. You can reuse this filter when required.
[See image.](#select-savedfilter)
[]To reset the filters to the original system setting, click **Reset**.
[See image.](#reset-filters)
[]To hide the filters that are displayed on the page, click **Hide Filters**.
[See image.](#hide-filters)
- []Click the **Settings **icon (![Click the icon to view options for managing filters](/downloads/zpc/getting-started/admin-portal/using-filters/zpc-threedoticon.png)
), then click **Delete**.
[See image.](#delete-filters)
- Read the confirmation message, then click **Delete**.
[See image.](#delete-confirmmsg)
The additional filters are deleted and the table displays data based on the default setting.
[]The following filters are available by default:
- **Business Units**: Returns results only from selected business units. Business units are logical groups of multiple cloud accounts.
- **Cloud**: Returns results only from selected cloud service providers (AWS, Azure, GCP, Kubernetes).
- **Accounts**: Returns results only from selected cloud accounts. You can select cloud accounts using either the cloud account name or the cloud account ID.
- **Regions**: Returns results only from selected regions.
[]ZPC offers the following additional filters for specific modules:
- [Cloud Alert Filters](#cloud-alert-filters)
- [IaC Alert Filters](#iac-alert-filters)
- [Asset Filters](#asset-filters)
- [Identity Filters](#identity-filters)
- [Policy Filters](#policy-filters)
- [Compliance Filters](#compliance-filters)
- [Vulnerability Management Filters](#vulnerability-management-filters)
[]
- **Updated Date**: Returns alerts scanned in the specified time range (Last 12 hours, Last day, Last week, Last month, Exact Date, or Custom Range).
- **Alert Status**: Returns alerts based on selected alert status (Open, Closed, Resolved, or Ignored).
- **Theme**: Returns alerts based on selected theme (Compliance, Security Events, Security Exposure, and Blank).
- **Risk Level**: Returns alerts based on alert risk level (Critical, High, Medium, or Low).
- **Policy Source**: Returns alerts based on how the alert policy was created (Predefined or Custom).
- **Policy Threat Category**: Returns alerts in a specific threat category such as external exposure.
- **Severity**: Returns alerts of specific severity (e.g., critical and high alerts).
- **Alert Focus**: Returns alerts based on the alert focus (Asset or Identity).
- **Asset Type**: Returns assets of a cloud-defined service type, such as EC2 instances.
- **Asset Category**: Returns assets of a ZPC-defined asset category. For example, the Compute asset category includes virtual machines and EC2 instances.
- **Compliance**: Returns alerts for security policies in a specific compliance benchmark.
- **Ignore End Date**: Returns alerts based on the Ignore Filter End Date (1 Day, 1 Week, 1 Month, 6 Months, 1 Year, Exact Date, or a Custom Range).
- **Created Date**: Returns alerts created during a specified time range (Last 12 hours, Last day, Last week, Last month, Exact Date, or Custom Range).
- **Alert Age**: Returns alerts based on a set age parameter (in days). Select one of the following:
- **= Exact Days**: Return alerts that are exactly the specified number of days old.
- **> Older Than**: Return alerts that are older than the specified number of days.
- **< Newer Than**: Return alerts that are newer than the specified number of days.
- **MITRE ATT&CK**: Returns alerts of a specific MITRE technique.
- **Policy ID**: Returns alerts for specific policy IDs.
- **Policy Name**: Returns alerts for specific policy names.
- **Clusters**: Returns alerts for the selected clusters.
- **Namespaces**: Returns alerts for the selected namespaces.
- **Cluster Type**: Returns alerts for the selected cluster type (AKS, EKS, and GKE).
- **Remediation Status**: Returns alerts for the selected remediation status (In Progress, Failed, Successful).
- **Supports Remediation**: Returns alerts that support remediation or not (True, False).
- **Remediation Allowed**: Returns alerts that allow remediation or not (True, False).
- **Remediation Initiated By**: Returns alerts that are remediated by the selected user.
- **Trusted IP**: Returns alerts based on the selection:
- **True**: Return alerts that are publicly exposed and associated with a trusted IP list.
- **False**: Return alerts that are publicly exposed but not associated with a trusted IP list.
- **Time Range**: Returns alert data for the selected time range.
- **Event Type**: Returns alert data for the selected event type.
- **Updated By**: Returns alert data that is updated by the selected user.
[]
- **Scan Time**: Returns alerts scanned in the specified time range (Last 12 hours, Last day, Last week, Last month, Exact Date, or Custom Range).
- **Alert Status**: Returns alerts based on selected alert status (Open, Closed, Resolved, and Ignored).
- **Scan Plugin**: Returns alerts based on the scan plugin app (i.e., Jenkins, Github).
- **Repository**: Returns alerts based on the repository.
- **Scan Type**: Returns alerts based on the scan type (Pull Request, Push, and Build).
- **Compliance**: Returns alerts for security policies in a specific compliance benchmark.
- **Template Type**: Returns alerts based on the template type (i.e., Kubernetes, Terraform, etc.).
- **Updated Date**: Returns alerts updated during a specified time range (Last day, Last week, Last month, Exact Date, or Custom Range).
- **Created Date**: Returns alerts created during a specified time range (Last 12 hours, Last day, Last week, Last month, Exact Date, or Custom Range).
- **Alert Age**: Returns alerts based on a set age parameter (in days). Select one of the following:
- **= Exact Days**: Return alerts that are exactly the specified number of days old.
- **> Older Than**: Return alerts that are older than the specified number of days.
- **< Newer Than**: Return alerts that are newer than the specified number of days.
- **Policy ID**: Returns alerts for specific policy IDs.
- **Policy Name**: Returns alerts for specific policy names.
[]
- **Status**: Returns either passed or failed assets.
- **Asset Types**: Returns assets of a cloud-defined service type such as EC2 instances.
- **Asset Categories**: Returns assets of a ZPC-defined asset category. For example, the Compute asset category includes virtual machines and EC2 instances.
- **Resource Groups**: Returns the assets for the selected resource groups.
- **Publicly Exposed**: Returns assets either publicly exposed or not publicly exposed assets (Yes or No).
- **Trusted IP**: Returns assets that are associated with a trusted IP list (Yes or No).
- **Sensitive Data**: Returns assets on which data loss prevention (DLP) has detected sensitive data (True or False).
- **Clusters**: Returns the assets for selected Kubernetes clusters.
- **Cluster Types**: Returns the assets for the selected cluster types (AKS, EKS, and GKE).
- **Namespaces**: Returns the assets for the selected namespaces.
[]
- **Has Open Alerts**: Returns identities that have open alerts associated with them.
- **Type**: Returns human or non-human identities.
- **Source**: Returns federated, local, or external identities.
- **Power Score**: Returns either admin or user identities based on the identity power score.
- **Power Category**: Returns identities belonging to a specific power category, such as Data Admin.
- **Roles**: Returns identites belonging to specific identity roles.
- **Creation Date**: Returns local AWS identities that were created on the selected date.
- **Has MFA**: Returns local AWS identities that have multi-factor authentication enabled.
- **Has Password**: Returns local AWS identities that have password-based authentication enabled.
- **Has Access Keys**: Returns local AWS identities that have access key-based authentication enabled.
- **Has Certificate**: Returns local AWS identities that have certificate-based authentication enabled.
[]
- **Policy Name**: Returns a security policy of a specific name.
- **Policy ID: **Returns security policies of specified IDs.
- **Policy Focus**: Returns security policies focusing on asset or identity misconfigurations.
- **Policy Severity**: Returns security policies of specific severity (Critical, High, Medium, or Low).
- **Theme**: Returns security policies of a specific theme (Compliance, Security Events, Security Exposure, and Blank).
- **Policy Threat Category**: Returns security policies of a specific threat category (Ransomware, Misconfiguration, or Account takeover).
- **MITRE ATT&CK**: Returns security policies of a specific MITRE technique.
- **Policy State**: Returns enabled or disabled security policies.
- **Allow Skip**: Returns security policies that have Allow Skip enabled.
- **Compliance**: Returns security policies belonging to a specified compliance benchmark.
- **Compliance Domain**: Returns security policies belonging to a specified compliance domain.
- **Compliance Control Number**: Returns security policies belonging to a specified compliance control number.
[]
- **Severity**: Returns compliance benchmark details of specific severity (Critical, High, Medium, or Low).
- **Status**: Returns passed, failed, manual, ignored, or disabled security policies for the compliance benchmark.
- **Control Category**: Returns compliance benchmark details for a specific control category, such as Networking.
- **Resource Group **(Microsoft Azure): Returns compliance benchmark details for a specific resource group.
- **Policy ID**: Returns compliance benchmark details for specified security policy IDs.
- **Clusters**: Returns the compliance benchmark details for selected Kubernetes clusters.
- **Cluster Types**: Returns the compliance benchmark details for the selected cluster types (AKS, EKS, and GKE).
[]
- **Cloud Type**: Returns the cloud service provider (Google, Amazon, or AWS).
- **CVSS Score**: Returns vulnerabilities of a specific CVSS score. To learn more, see [CVSS Score](https://nvd.nist.gov/vuln-metrics/cvss).
- **Severity**: Return vulnerabilities of specific severity (Critical, High, Medium, Low, or Unknown).
- **Fix Available**: Returns vulnerabilities with an available or unavailable fix.
- **Time Range**: Returns vulnerabilities in a specific time range (1 Day, 7 Days, 15 Days, or 30 Days).
- **Scan Status**: Returns images, instances, workloads, or containers with the filtered scan status (Completed or Not Scanned).
- **Cluster**: Returns the selected cluster.
- **Cluster Type**: Returns containers associated with the selected cluster type (Amazon EKS or Google Kubernetes).
- **Container**: Returns the selected container.
[]You can define a default filter to view customized data on a page. You can view the same customized data every time you revisit the page or when you log out and log in to the ZPC Admin Portal.
To set up a default filter:
- After [adding a new filter](#using-filters), click **Apply**.
- Click **Save**.
- In the **Save Filter** window, enter a name for this filter.
- Select the **Set as Default** checkbox if you want to save this filter as the default filter.
[See image.](#save-as-default)
- Click **Save**.
The default filter is added to the **Saved Filters** list and data on the page is displayed based on this filter.
[See image.](#list-defaut-filter)
You can also choose another saved filter as the default filter.
- Click the **Saved Filter** drop-down menu.
- Click the **Default Filter** (![Default filter icon](/downloads/zpc/getting-started/admin-portal/using-filters/zpc-star-icon.png)
) icon for the specific filter that you want set as default.
[See image.](#set-defaultfilter)
A confirmation message is displayed. [See image. ](#confirm-defaultmsg)
You can define only one default filter for a page. Also, clicking **Reset** displays data based on the default system settings.
[![Filter options](/downloads/zpc/getting-started/admin-portal/using-filters/zpc-filtersandsearchoption.png?1676614893)
]
[![Select the column that must be filtered](/downloads/zpc/getting-started/admin-portal/using-filters/zpc-addfilter.png)
]
[![Select the data that must be displayed](/downloads/zpc/getting-started/admin-portal/using-filters/zpc-applyfiltericon.png)
]
[![Save the filter](/downloads/zpc/getting-started/admin-portal/using-filters/zpc-savefilter-window.png)
]
[![Save the newly added filter](/downloads/zpc/getting-started/admin-portal/using-filters/zpc-filter-saveas.png?1676886332)
]
[![Select a saved filter](/downloads/zpc/getting-started/admin-portal/using-filters/zpc-selectsavedfiltermenu.png)
]
[![Reset filter](/downloads/zpc/getting-started/admin-portal/using-filters/zpc-resetfilter.png)
]
[![Hide filters](/downloads/zpc/getting-started/admin-portal/using-filters/zpc-hidefilter.png)
]
[![Delete filters](/downloads/zpc/getting-started/admin-portal/using-filters/zpc-deletefilter.png)
]
[![Confirmation message to delete a filter](/downloads/zpc/getting-started/admin-portal/using-filters/zpc-deletefiltermsg.png)
]
[![Select the default filter](/downloads/zpc/getting-started/admin-portal/using-filters/zpc-defaultfilter.png)
]
[![Save as default filter](/downloads/zpc/getting-started/admin-portal/using-filters/zpc-savedefaultfilter.png?1685337970)
]
[![Default filter](/downloads/zpc/getting-started/admin-portal/using-filters/zpc-saveddefaultfilterlist.png)
]
[![Confirmation message](/downloads/zpc/getting-started/admin-portal/using-filters/zpc-defaultfilter-msg.png)
]