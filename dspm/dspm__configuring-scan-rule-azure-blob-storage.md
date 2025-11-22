# Configuring Scan Rule for Azure Blob Storage
Source: https://help.zscaler.com/dspm/configuring-scan-rule-azure-blob-storage
PDF: https://help.zscaler.com/pdf/com/en/1483196.pdf

You can configure the scan rule to scan Azure blob storage resources. DSPM scans the blob containers for any sensitive data. The scan results are displayed on the [Resource Inventory page](/dspm/about-resource-inventory).
You can configure the scan rule after onboarding the Azure accounts. To learn more, see [About Cloud Accounts](/dspm/about-cloud-accounts).
To configure a scan rule for Azure blob storage:
- [1. Provide the general information.](#gen-info)
- [2. Select the cloud and resource type.](#ds-azureblob1)
- [3. Select the accounts that must be scanned.](#ds-azureblob2)
- [4. Exclude storage account containers and prefixes (Optional).](#ds-azure-cs-exclude)
- [5. Select the scan type.](#ds-azureblob3)
- [6. Select the scan scope.](#scanscope)
- [7. Review and complete the configuration.](#ds-azureblob4)
Enable the scan rule on the [Scan Settings](/dspm/about-scan-settings) page to initiate scheduled or on-demand scans.
[]
- []Go to **Administration** > **Scan Settings**.
-
Select the **Scan Rules **tab.
If you are configuring the scan rule for the first time, the following page appears:
[See image.](#scan-initial)
-
Click **Add Scan Rule**.
[See image.](#new-scan)
The **General Information** page appears.
-
On the **General Information **page:
- **Scan Rule Name**: Enter a unique and descriptive name for the scan rule.
- **Scan Rule Description (Optional)**: Enter a description for the scan rule (maximum is 500 characters).
[See image.](#ds-scan-gen-info)
- Click **Next**.
[]![The initial scan rule configuration page with no scan rule configured and + Add Scan Rule button.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-initialscanrule.png)
[]![ General Information page to set the scan rule name and an optional description field.](/downloads/dspm/scan-settings/scan-settings-premise-unmanaged-database/configuring-scan-settings-premise-unmanaged-database/ds-scan-rule-general-info.png)
-
[]On the **Select Cloud and Resource Type** page:
- For **Cloud Type**, select **Azure**.
- For **Resource Category**, select **Cloud Storage**.
- For **Resource Type**, select **Blob Containers**.
[See image.](#azurecs-selectcloud)
- Click **Next**.
-
[]On the **Select Resources to Scan** page, choose one of the following options:
-
**Scan All Resources**: Scans all the subscriptions or storage accounts.
[See image.](#azurecs-selectdata)
-
**Scan Specific Resources**: Scan only specific resources. When you select this option, select the checkbox for the resources that must be scanned.
- **Select Specific Subscriptions and Regions**: Select the checkbox for specific subscriptions and regions that must be scanned.
- **Scan Specific Storage Account**: Specify the storage accounts that must be scanned.
- **Select from the List**: Select the checkbox for the accounts or subscriptions that must be scanned from the list.
-
**Select by Tags**: Enter the key-value pairs for the accounts or subscriptions. Click **Add More** to add multiple key-value pairs.
If multiple key-value pairs are added, DSPM scans all accounts or subscriptions that match at least one of the specified key-value pairs. This means the rule uses `OR` logic, and a account or subscription is included, if it matches any of the key-value pairs.
- **Scan Blob Containers**: Select the checkbox for the blob containers that must be scanned from the list. If you choose **Manual**, enter the blob container names and prefixes separated by commas.
[See image.](#azurecs-specificacc)
If you select any of the above options, you can optionally [exclude specific databases](#optionally-exclude) from the scan.
-
**Enable Malware Scanning**: Enable this option if the resources must be scanned for malware. This option is disabled by default.
[See image.](#malwarescan)
- Click **Next**.
[]On the **Exclude Storage Account Containers and Prefixes (Optional)** page, you can specify the storage account containers and prefixes that must be excluded from the scan.
[]If a full scan is already initiated or completed, the bucket or folder is excluded in the next incremental scan.
- Enter the name of the blob containers, or include the folder name followed by a forward slash (/). For example, to exclude a folder named `myblobcontainer` within the storage account `https://storagename.blob.core.windows.net/`, enter `https://storagename.blob.core.windows.net/myblobcontainer`. Additionally, you can use wildcards with the storage account names instead of relying on tags. Based on the wildcard, DSPM excludes all the matching storage account containers from scanning. This is applicable to both existing storage accounts and the ones that might be added in the future.
-
**Exclude Subscriptions & Storage Accounts By Tags**: Enable this option and enter the key-value pairs of the subscriptions or storage accounts that must be excluded from scanning. This option is disabled by default. Click **Add More** to add multiple key-value pairs.
If multiple key-value pairs are added, DSPM excludes any accounts or subscriptions that matches at least one of the specified key-value pairs. This means the rule uses `OR` logic, and an account or subscription is excluded, if it matches any of the key-value pairs.
-
**Exclude Azure Blob Containers with Wildcards**: Select the checkbox and enter the wildcard expressions to exclude blob containers by name using wildcards. For example, `*logs*` excludes any blob name that contains the word `logs`.
[See image.](#azurecs-optionalexclude)
- Click **Next**.
-
[]On the **Scan Type** page choose one of the following options:
- **Full Scan**: Scans all objects on the on-premises file server.
- **Full + Incremental Scan**: Scans all objects, including those that are newly added or modified since the previous scan.
-
Select one of the scan durations: **1 Day**, **1 Week**, **1 Month**, **Continuous**, **Custom Duration**.
If you select **Custom Duration**, enter the number of days to define the scan window.
- **Incremental Scan**: Scans only those files that are newly added or modified since the previous scan.
-
Select one of the scan durations: **1 Day**, **1 Week**, **1 Month**, **Continuous**, **Custom Duration**.
If you select **Custom Duration**, enter the number of days to define the scan window.
- **Historical Scan**: Scans files based on a specified look back period.
- **Lookback Period**: Enter the number of days (1 to 365 days) to scan historical data.
- **Historical + Incremental Scan**: Scans files based on a specified lookback period and scan files that are newly added or modified since the previous scan.
- **Lookback Period**: Enter the number of days (1 to 365 days) to scan historical data.
- **Duration**: Specify the number of days for incremental scanning.
DSPM cannot detect files that are deleted in Azure.
[See image.](#azurecs-scantype)
- Click **Next**.
-
[]On the **Scan Scope** page, choose a scan scope from the drop-down menu to set up your scan rule.
To learn more about configuring and creating a scan scope, see [Configuring Scan Scope](/dspm/configuring-scan-scope).
[See image.](#img_scanscope)
- Click **Next**.
[]![The Scan Scope page with drop-down menu for selecting scan scope.](/downloads/dspm/scan-settings/configuring-scan-scope/select_scanscope.png)
-
[]Review the scan rule. Click the **Edit** icon to change any values, if required.
[See image.](#azurecs-review)
- Click **Finish**.
[]![The Scan Settings page with an annotation around the Add New button.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-scan-scan-add-new-scan.png)
[]![The Select Resources to Scan page with Scan All Subscriptions & Storage Accounts option is selected.](/downloads/dspm/scan-settings/scan-settings-azure/configuring-scan-settings-azure-cloud-storage/ds-scanrule-azure-cs-scan-all.png)
[]![The Select Resources to Scan page with Scan Specific Subscription & Storage option selected.](/downloads/dspm/scan-settings/scan-settings-azure/configuring-scan-settings-azure-cloud-storage/ds-scanrule-azure-cs-scan-specific.png)
[]![Exclude storage account containers from scanning](/downloads/dspm/scan-settings/scan-settings-azure/configuring-scan-settings-azure-cloud-storage/ds-scanrule-azure-cs-exclude.png)
[]![Enable malware scanning option is enabled with the toggle button.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-virtual-machine/ds-scanrule-enable-malware-scan.png)
[]![The scan type selection page with the available options.](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-scanrule-fileserver-scan-type.png)
[]![The scan settings review page displays the configured scan settings before completing the scan configuration.](/downloads/dspm/scan-settings/scan-settings-azure/configuring-scan-settings-azure-cloud-storage/ds-scanrule-azure-cs-review.png)
[]![Select Cloud and Resource Type page with Azure Cloud Type, Cloud Storage Resource Category, and Blob Storage Resource Type selected.](/downloads/dspm/scan-settings/scan-settings-azure/configuring-scan-settings-azure-cloud-storage/ds-scanrule-azure-select-blob.png)