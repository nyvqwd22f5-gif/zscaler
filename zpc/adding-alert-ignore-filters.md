# Adding Alert Ignore Filters
Source: https://help.zscaler.com/zpc/adding-alert-ignore-filters
PDF: https://help.zscaler.com/pdf/com/en/1433956.pdf

ZPC triggers alerts for all the security violations and vulnerabilities that are detected in your cloud resources. You can set up filters to ignore specific alerts that you don't want to be notified about or you don't want to take any action. To learn more, see [Ignore Filters](/zpc/about-alerts#viewing-ignore-filters-tab).
- The ignore filters are applied only to the newly triggered alerts.
- By default, users with admin and security operations (SecOps) role can add ignore filters. All other ZPC users have view-only permission. You can enable the add permission to other ZPC users by adding or modifying Ignore Rules permissions in [Global Modules](/zpc/zpc-modules-and-global-modules). To learn more, see [Adding a Custom Role](/zpc/adding-custom-role) and [Editing or Deleting a Custom Role](/zpc/editing-deleting-custom-role).
To add ignore filters:
- In the left-side navigation, select **Alerts**.
- On the **Alerts** page, click the **Ignore Filters** tab.
- Click **+ Ignore Filter**.
[See image.](#alertspage)
- On the **General Information** page:
- **Type of Alerts**: Select **Cloud** or **IaC**.
- **Ignore Filter Name**: Enter a unique name for the filter.
- **Filter Description** (Optional): Enter a description.
- **Ignore Filter End Date**: Select the duration for which you want to snooze the alert. This filter is disabled after the end date and alerts are triggered for security policy violations.
[See image.](#general-info)
- Click **Next**.
- On the **Filter Scope** page:
- For **Cloud Alerts**, select at least one of the filters below:
- [Policies](#policies)
- [Cloud Accounts](#cloud-accounts)
- [Cluster Names](#cluster-names)
- [Namespaces](#namespace)
- [Tags](#tags)
- [Assets](#assets)
[See image.](#cloud-filter-scope)
If no filters are selected within the scope, the **Next** button is disabled.
- For **IaC Alerts**, select at least one of the filters below:
- [Policies](#iac-policies)
- [Template Type](#templaye-type)
- [Scan Plugin](#scan-plugin)
- [Repository](#repository)
[See image.](#iacalert-scope)
- Click **Next**.
- Review the summary of the ignore filter scope.
[See image.](#summary)
- Click **Finish**.
All the alerts matching the selected criteria are moved to ignored status.
[![Configure the ignore filter scope for IaC alerts](/downloads/zpc/alerts/alert-filters/adding-ignore-filters/ignore-iac-filter.png)
]
[![View Ignore Filters Summary](/downloads/zpc/alerts/adding-ignore-filters/ignore-filter-summary.png)
]
[![Select the Ignore Filters tab](/downloads/zpc/alerts/alert-filters/adding-ignore-filters/zpc-ignorefilterpage.png)
]
- **All Policies**: The filter applies to all policies.
- **Theme**: Select the required **Policy Theme** from the drop-down menu (**Compliance**, **Security Events**, **Security Exposure**, and **Blank**).
- **Category**: Select the required **Threat Category** from the drop-down menu.
- **[]Severity**: Select the required **Policy Severity** from the drop-down menu.
- **Select Policies**: Select to view the **Select Existing Policies** page, and select the required policies from the table.
To learn more, see [About Security Policies.](/zpc/about-security-policies)
- **Policy Focus**: Select **Asset **or **Identity** from the **Policy Focus** drop-down menu.
By default, the **All Policies** filter is selected.
Select the cloud account, business unit, or provider. Depending on your selection, one of the following additional fields displays:
- **[]Select Accounts**: Select the required [cloud accounts](/zpc/about-cloud-accounts) that must be included in the filter.
- **Business Units**: Select the required [business units](/zpc/about-business-units) that must be included in the filter.
- **Cloud**: Select the cloud provider (**AWS**, **Azure**, **GCP**, or **Kubernetes**). For Kubernetes, select the required **Cluster Names** and **Namespaces** from the drop-down menu.
By default, the **All Accounts** filter is selected.
[]Select from a list of cluster names.
By default, the **All Kubernetes Clusters** filter is selected.
[]Select from a list of namespaces.
By default, the **All Kubernetes Namespaces** filter is selected.
If you don't have any onboarded Kubernetes clusters, then the **Cluster Names** and **Namespaces** fields are not displayed.
[]Click the **Tags** drop-drown menu and choose **Select Tags**. Click the **Add Tags** icon that appears, to include the required tags.
By default, the **All Tags** filter is selected.
- **[]All Assets**: The filter applies to all assets.
- **Asset Type**: Select the required [Asset Type](/zpc/cloud-asset-types-and-asset-categories) from the drop-down menu.
- **Asset Category**: Select the required [Asset Category](/zpc/cloud-asset-types-and-asset-categories) from the drop-down menu.
By default, the **All Assets** filter is selected.
- **[]All Policies**: The filter applies to all policies.
- **Severity**: Select the required **Policy Severity** from the drop-down menu.
- **Select Policies**: Select to view the **Select Existing Policies** page, and select the required policies from the table.
To learn more, see [About Security Policies](/zpc/about-security-policies).
By default, the **All Policies** filter is selected.
[]Select one or more template type (Terraform, CloudFormation, Azure Resource Manager, Kubernetes, Helm Charts, Terraform Plan) from the drop-down menu.
[]Select the [IaC scan plugin](/zpc/about-iac-integrations) from the drop-down menu.
Select the IaC repository from the drop-down menu.[]
[![View the Ignore Filter scope](/downloads/zpc/adding-ignore-filters-draft/ignore-cloud-filter-scope.png)
]
[![View the General Information page](/downloads/zpc/alerts/alert-filters/adding-ignore-filters/general-info.png)
]