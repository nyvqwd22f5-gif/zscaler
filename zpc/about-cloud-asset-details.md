# Viewing Cloud Asset Details
Source: https://help.zscaler.com/zpc/about-cloud-asset-details
PDF: https://help.zscaler.com/pdf/com/en/1394211.pdf

ZPC displays a slew of information for each [asset](/zpc/about-cloud-assets) it finds in your cloud infrastructure. You can view each asset in detail by selecting the asset name.
![View the Cloud Assets](/downloads/zpc/cloud-posture/cloud-assets/viewing-cloud-asset-details/zpc-cloud-assets-page.gif)
On the Asset Details (Cloud Asset > Asset name) page, you can view the following tabs:
- [Properties](#viewing-cloud-asset-properties)
- [Graph View](#viewing-cloud-asset-graph)
- [Timeline](#viewing-cloud-asset-timeline)
- [Compliance Policies](#viewing-cloud-asset-policies)
- [Alerts](#viewing-cloud-asset-alerts)
- [Tags](#viewing-cloud-asset-tags)
- [Vulnerabilities](#viewing-cloud-asset-vulnerabilities)
[]The cloud asset properties offer information on asset details and asset configuration metadata.
On the Properties tab, you can do the following:
- View the asset details. ZPC extracts the details from the asset metadata JSON.
When an asset is publicly exposed and associated with a trusted IP list, a link is provided against the publicly exposed attribute to navigate to the associated trusted IP list on the Trusted IP Management page. [See image.](#trusted-ip)
- View the metadata. ZPC displays the asset configuration metadata it collects from your cloud account.
- Download the metadata JSON file.
- Copy the metadata to your clipboard.
![View the Cloud Asset Properties](/downloads/zpc/cloud-posture/cloud-assets/viewing-cloud-asset-details/zpc-cloud-assets-properties-tab_0.png)
[]The Asset Graph View tab offers a topological co-relation with other [assets](/zpc/about-cloud-assets), [roles](/zpc/about-roles), [identities](/zpc/about-cloud-identities), and [asset types](/zpc/cloud-asset-types-and-asset-categories). You can interact with each graph node to view more information on the details panel.
![View the Graph View tab](/downloads/zpc/cloud-posture/cloud-assets/viewing-graph-view-tab/zpc-cloud-assets-graph-view.gif)
[]The cloud asset compliance policies offer information on the status of the compliance policy for the cloud asset.
On the Compliance Policies tab, you can do the following:
- View the following details in the compliance policy table:
- **Policy ID**: The [security policy](/zpc/about-security-policies) ID.
- **Policy**: The name of the security policy.
- **Status**: The status of the security policy (Passed, Failed).
- Filter the policies based on the status (All, Passed, Failed).
- Search for a specific policy.
- [Modify the table and its columns](/zpc/using-tables).
![View the Compliance Policies Tab](/downloads/zpc/cloud-posture/cloud-assets/viewing-cloud-asset-details/zpc-compliance_policies-tab_0.png)
[]The cloud asset alerts offer information on the [alerts](/zpc/about-alerts) and the status of the alerts for the cloud asset.
On the Alerts tab, you can do the following:
- View the following details in the alert table:
- **Alert ID**: Unique ID of the alert. Click to view the [alert details](/zpc/about-alerts) (Alert Details, Policy Details, Metadata) for open and resolved alerts.
- **Risk Level**: The alert risk level (Critical, High, Medium, or Low).
- **Policy Name**: The name of the [security policy](/zpc/about-security-policies).
- **Last Updated**: The timestamp for when the alert was last modified.
- **Alert Age**: The age of the alert (in days) from the last time the Alert Status was set to Open.
- **Status**: The status (Open, Closed, Resolved, or Ignored) of the alert.
- Filter the alerts based on the status (Open, Closed, Resolved, or Ignored).
- Search for a specific alert using the searchable columns.
[]The cloud asset tags offer information on the key-value tag pairs. Tags are used to group various asset types across ZPC. The key-value tag pairs provide additional details about the resources.
On the Tags tab, you can do the following:
- View key-value tag pairs.
- Search for keys or values in the tag table.
![View the Cloud Assets Tag](/downloads/zpc/cloud-posture/cloud-assets/viewing-cloud-asset-details/zpc-cloud-assets-tag_1.png)
[]The cloud asset timeline offers information on the cloud asset changes, CSP events, or activities in the cloud infrastructure.
On the Timeline tab, you can do the following:
- View all the CSP events or activities in the cloud infrastructure performed on a cloud asset and identify the Cloud Identity modifier and the timestamp for when the asset was last modified. You can click on the modifier identity for the [Cloud Identity details](zpc/about-cloud-identity-details).
- View the changes on the cloud asset, track, correlate, and investigate incidents and perform potential root cause analysis of the same. For AWS, you can also view the account ID and request parameters during resource state creation or update.
- View the data for up to 6 months.
-
View the alerts triggered by data collection activity for the asset.
[See image.](#zpc-timeline-alerts)
- View the assets of the newly onboarded CSP account along with the metadata.
![View the Cloud Assets Timeline Tab](/downloads/zpc/cloud-posture/cloud-assets/viewing-cloud-asset-details/zpc-cloud-assets-timeline-tab.png)
[![View the Alerts](/downloads/zpc/cloud-posture/cloud-assets/viewing-cloud-asset-details/zpc-timeline-alerts.png)
]
[]ZPC detects vulnerabilities that exist in your cloud assets and provides in-depth information about assets and the common vulnerability and exposure (CVE) details, so you can quickly investigate and fix the issues. To learn more, see [About Vulnerability Management](/zpc/about-vulnerability-management).
You can view the total number of vulnerabilities that ZPC detects in assets within containers and also the vulnerability details associated with a specific package.
Viewing the Asset Vulnerabilities
To view the total number of vulnerabilities detected in a container asset:
- In the left-side navigation of the ZPC Admin Portal, go to **Cloud Posture** > **Cloud Assets**.
The **Cloud Assets** page is displayed.
[See image.](#assets-page)
- From the list of **Asset Categories**, search for **Containers**, then click the **Asset Type** for which you want to view the details.
The asset details are displayed.
[See image.](#asset-details)
- Click the required **Asset Name** to view additional details and select **Vulnerabilities**.
[See image.](#cloud-assets-tab)
- On the **Vulnerabilities** tab, you can do the following:
- View the following details in the vulnerability table:
-
**Package Name**: The name of the impacted package. Click to [view the CVE and package details](#view-package-vuln).
Packages with the highest count of CVEs and highest level of severity are listed first in the table.
- **Version**: The version of the impacted package.
- **Package Path**: The path of the impacted package.
- **Vulnerabilites**: The total number of vulnerabilities based on the level of severity.
- Filter the data by:
- **Vulnerable Packages**: View all packages, or packages with or without vulnerabilities.
- **Package**: View the details of a specific package.
- **Version**: View the package version.
- Export the vulnerability data to a CSV file and [download the report](/zpc/downloading-reports).
![View the Vulnerability Tab](/downloads/zpc/cloud-posture/cloud-assets/viewing-cloud-asset-details/zpc-assets-vulnerability-tab_0.png)
[]Viewing the Package Vulnerabilities
When you click the **Package Name** in step 4 of the previous section, another drawer displays the following details:
- The left-side navigation displays a list of packages.
- On the **Vulnerabilities **page, you can see the following:
- **CVE ID**: The unique identifier for the CVE. Click to [view additional vulnerability details](/zpc/viewing-vulnerability-details).
- **Severity**: The severity level (Low, Medium, High, or Critical) of the vulnerability.
- **CVSS SCORE**: The [severity score](https://www.first.org/cvss/) assigned to the vulnerability.
- **Age of CVE**: The number of days the vulnerability was present in the source code when reported.
- **Fix Available**: The fix version for the package is available or not.
- **Fix Version**: The package version that contains the vulnerability fix.
- Filter the packages by:
- **Severity**: View packages for a specific level of severity (Critical, High, Medium, Low, or Unknown).
- **CVSS Score**: View packages based on the CVSS score.
- **Fix Available**: View packages for which a fix version is available or view packages that don't have a fix version. By default, all the packages are displayed when you first view the data. You can then apply the filter as required.
- Search for a specific CVE ID.
![View the package details](/downloads/zpc/cloud-posture/cloud-assets/viewing-cloud-asset-details/zpc-vulnerability-packages.png)
[![View the Cloud Assets page](/downloads/zpc/cloud-posture/cloud-assets/viewing-package-vulnerabilities/zpc-assetpage.png)
]
[![View the asset details](/downloads/zpc/cloud-posture/cloud-assets/viewing-package-vulnerabilities/zpc-assetdetailspage.png?1688665283)
]
[![View the Cloud Assets Tab](/downloads/zpc/cloud-posture/cloud-assets/viewing-cloud-asset-details/zpc-cloud-assets-tabs.png)
]
[![View the Cloud Asset Properties](/downloads/zpc/cloud-posture/cloud-assets/viewing-properties-tab-0/zpc-assets-trusted-ip.gif)
]