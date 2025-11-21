# Adding Ignore Alert Filters
Source: https://help.zscaler.com/dspm/adding-ignore-filters
PDF: https://help.zscaler.com/pdf/com/en/1477821.pdf

You can add ignore alert filters to exclude the generation of alerts for less critical violations or for alerts that you don't want to receive notifications for. For example, you can add an ignore alert filter to ignore alerts generated for policies with low severity or for a specific cloud account.
To add ignore alert filters:
- Go to **Alerts **> **Alert Settings** > **Ignore Alert Filter**.
-
Click **Ignore Alert Filter**.
[See image.](#ignorefilter)
-
On the **General Information** page:
- **Ignore Filter Name**: Enter a unique name for the filter.
- **Filter Description**: (Optional) Enter a description for the filter.
[See image.](#generalinfo)
- Click **Next**.
-
On the **Filter Scope** page, select at least one of the following filters:
- [Policies](#policies)
- [Cloud Accounts](#cloudaccounts)
- [Tags](#tags)
- [Resources](#resources)
- [DLP Engines](#dlp-engines)
[See image.](#filterscope)
- Click **Next**.
-
Review the ignore alert filter configuration, then click **Finish**.
[See image.](#review)
If the selected filters of the filter scope are deleted (e.g., policies are deleted, accounts are offboarded, or the business unit is deleted), the ignore alert filter is disabled, and an exclamation mark is displayed indicating the filter is invalid. [See image.](#disabled-invalid-filter)
The ignore alert filter is added to the [ignore alert filter table](/dspm/about-ignore-filters) and is enabled by default. The newly triggered alerts matching these filter criteria are ignored.
[]Select the policy, category, or severity. Depending on your selection, one of the following additional fields is displayed:
- **Category**: Select the [threat category](/dspm/threat-categories) (**Public Exposure**, **External Users**, **Risky Credentials**, **Malicious Access**, **Data Loss**, **Data Governance**) from the drop-down menu.
- **Severity**: Select the policy severity (**Critical**, **High**, **Medium**, or **Low**) from the drop-down menu.
-
**Select Policies**: Select to view the** Select Existing Policies** page, and select the required [policies](/dspm/about-data-posture-policies) (**Custom** and **Predefined**) from the table.
[See image.](#existingpoliciesdropdown)
[See image.](#policiesdropdown)
By default, the **All Policies** option is selected.
[]Select the cloud accounts, business units, or cloud provider. Depending on your selection, one of the following additional fields is displayed:
- **Select Accounts**: Select the [cloud accounts](/dspm/viewing-cloud-accounts-and-organizations) from the drop-down menu.
- **Business Units**: Select the [business units](/dspm/about-business-units) from the drop-down menu.
- **Cloud Provider**: Select the cloud provider (**AWS**, **Azure**,** **or **GCP**) from the drop-down menu.
[See image.](#cloudaccountsdropdown)
By default, the **All Account** option is selected.
[]Click the **Tags** drop-down menu and choose **Select Tags**. Click the **Add Tags** icon that appears to include the required tags.
[See image.](#tagsdropdown)
By default, the **All Tags** option is selected.
[]Click the **Resources** drop-down menu and choose **Resource Type**. Select the required data stores from the drop-down menu.
[See image.](#resourcesdropdown)
By default, the **All Resources** option is selected.
[]Click the **DLP Engines** drop-down menu and choose **Specific** **DLP Engines**. Select the required DLP engines.
[See image.](#dlpengines-filterscope)
By default, the **All DLP Engines** option is selected.
[]![Review the ignore alert filter details](/downloads/dspm/alerts/ignore-alert-filters/adding-ignore-filters/dspm-summarypage-ignorefilter.png)
[]![Add ignore alert filter scope](/downloads/dspm/alerts/ignore-alert-filters/adding-ignore-filters/dspm-filter-scope-dlp-engines.png)
[]![Add ignore alert filters](/downloads/dspm/alerts/ignore-alert-filters/adding-ignore-filters/dspm-ignora-alert-filter-gi.png)
[]![Add Ignore alert filter](/downloads/dspm/alerts/ignore-alert-filters/adding-ignore-filters/dspm-add-ignore-alert-filter.png)
[]![Select the required policies scope](/downloads/dspm/alerts/ignore-alert-filters/adding-ignore-filters/dspm-policies-drop-down.png)
[]![Select the required cloud accounts](/downloads/dspm/alerts/ignore-alert-filters/adding-ignore-filters/dspm-cloud-accounts.png)
[]![Select Existing Policies page](/downloads/dspm/alerts/ignore-alert-filters/adding-ignore-filters/dspm-select-existing-policies_0.png)
[]![Select the required resources](/downloads/dspm/alerts/ignore-alert-filters/adding-ignore-filters/dspm-resource-types.png)
[]![Select the required tags](/downloads/dspm/alerts/ignore-alert-filters/adding-ignore-filters/dspm-ignore-alert-tags.png)
[]![View the disabled ignore alert filter](/downloads/dspm/alerts/ignore-alert-filters/adding-ignore-filters/dspm-ignore-alert-scope.png)
[]![Select the filter scope](/downloads/dspm/alerts/ignore-alert-filters/adding-ignore-filters/dspm-dlp-engines.png)