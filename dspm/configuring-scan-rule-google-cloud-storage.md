# Configuring Scan Rule for Google Cloud Storage
Source: https://help.zscaler.com/dspm/configuring-scan-rule-google-cloud-storage
PDF: https://help.zscaler.com/pdf/com/en/1504436.pdf

You can configure the scan rule to scan Google Cloud Storage buckets and folders. DSPM scans the resources for any sensitive data. The scan results are displayed on the [Resource Inventory page](/dspm/about-resource-inventory).
You can configure the scan rule after onboarding the Google Cloud Platform (GCP) accounts. To learn more, see [About Cloud Accounts](/dspm/about-cloud-accounts).
To configure a scan rule for Google Cloud Storage:
- [1. Provide the general information.](#gen-info)
- [2. Select the cloud and resource type.](#gcp_cloud)
- [3. Select the accounts that must be scanned.](#gcp_select_datascan)
- [4. Exclude cloud storage buckets and prefixes (Optional).](#ds-gcp-cs-exclude)
- [5. Select the scan type.](#gcp-cs-scantype)
- [6. Select the scan scope.](#scanscope)
- [7. Review and complete the configuration.](#gcp-cs-review)
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
-
[]On the **Select Cloud and Resource Type** page:
- For **Cloud Type**, select **Google Cloud**.
- For **Resource Type**, select **Cloud Storage**.
[See image.](#gcp-selectcloud)
- Click **Next**.
[]![ General Information page to set the scan rule name and an optional description field.](/downloads/dspm/scan-settings/scan-settings-premise-unmanaged-database/configuring-scan-settings-premise-unmanaged-database/ds-scan-rule-general-info.png)
[]![The initial scan rule configuration page with no scan rule configured and + Add Scan Rule button.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-initialscanrule.png)
[]![The Scan Settings page with an annotation around the Add New button.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-scan-scan-add-new-scan.png)
[]![Select Cloud and Resource Type page with an annotation around the Google Cloud Type and Cloud Storage Resource.](/downloads/dspm/scan-settings/scan-settings-gcp/configuring-scan-settings-gcp-cloud-storage/ds-scanrule-gcp-select-cs.png)
- []On the **Select Resources to Scan** page, choose one of the following options:
-
**Scan All Resources**: Scan all storage buckets in all onboarded GCP projects.
[See image.](#gcp-scanall)
-
**Scan Specific Resources**: Scan only specific projects.
- **Select Specific Projects and Regions**: Select the checkbox for the projects that must be scanned.
- **Scan Cloud Storage Buckets**: Specify the storage buckets that must be scanned. You can either select the names from the list or specify the tags.
- **Select from the List**: Select the checkbox for the storage buckets that must be scanned. If you choose **Manual**, then you need to enter the names.
-
**Select by Tag**: Specify the tags in key-value pairs. All the storage buckets that match the tag are scanned. Click **Add More** to add multiple key-value pairs.
If multiple key-value pairs are added, DSPM scans all storage buckets that match at least one of the specified key-value pairs. This means the rule uses `OR` logic, and a bucket is included if it matches any of the key-value pairs.
[See image.](#gcp-specific)
-
**Enable Malware Scanning**: Enable this option if the resources must be scanned for malware. This option is disabled by default.
[See image.](#malwarescan)
- Click **Next**.
[]![The Select Resources to Scan page with Scan All Accounts option is selected.](/downloads/dspm/scan-settings/scan-settings-gcp/configuring-scan-settings-gcp-cloud-storage/ds-scanrule-gcp-scanall.png)
[]![Select the Resources to Scan page with Scan Specific Projects option selected and selected few projects to scan.](/downloads/dspm/scan-settings/scan-settings-gcp/configuring-scan-settings-gcp-cloud-storage/ds-scanrule-gcp-cs-scan-specific.png)
[]![Enable malware scanning option is enabled with the toggle button.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-virtual-machine/ds-scanrule-enable-malware-scan.png)
[]On the **Exclude Cloud Storage Buckets & Prefixes (Optional)** page, you can specify the buckets and prefixes that must be excluded from the scan.
If a full scan is already initiated or completed, the bucket or folder is excluded in the next incremental scan.
- Enter the name of the bucket, or prefix the name of the folder with a forward slash (/) before the bucket name. For example, to exclude a folder named `reports` within a bucket named `my-bucket`, enter `my-bucket/reports/`. Additionally, you can use wildcards with storage bucket names instead of relying on tags. Based on the wildcard, DSPM excludes all the matching storage buckets from scanning. This is applicable to both existing storage buckets and the ones that might be added in the future.
-
**Exclude Cloud Storage Buckets By Labels**: Enable this option and enter the key-value pairs of the buckets that must be excluded from scanning. This option is disabled by default. Click **Add More** to add multiple key-value pairs.
If multiple key-value pairs are added, DSPM excludes any bucket that matches at least one of the specified key-value pairs. This means the rule uses `OR` logic, and a bucket is excluded if it matches any of the key-value pairs.
-
**Exclude Buckets with Wildcards**: Select the checkbox and enter the wildcard expressions to exclude buckets by name using wildcards. For example, `*logs*` — excludes any bucket name that contains the word `logs`.
[See image.](#optionalexclude)
- Click **Next**.
[]![The Select Resources to Scan page with Exclude Projects from the Scan option selected and selected few projects to exclude.](/downloads/dspm/scan-settings/scan-settings-gcp/configuring-scan-settings-gcp-cloud-storage/ds-scanrule-gcp-cs-exclude.png)
-
[]On the **Scan Type** page, choose one of the following options:
- **Full Scan**: Scans all objects in the storage buckets and folders.
- **Full + Incremental Scan**: Scans all objects, including those that are newly added or modified since the previous scan.
-
Select one of the scan durations: **1 Day**, **1 Week**, **1 Month**, **Continuous**, **Custom Duration**.
If you select **Custom Duration**, enter the number of days to define the scan window.
- **Incremental Scan**: Scans only the files that are newly added or modified since the previous scan.
-
Select one of the scan durations: **1 Day**, **1 Week**, **1 Month**, **Continuous**, **Custom Duration**.
If you select **Custom Duration**, enter the number of days to define the scan window.
- **Historical Scan**: Scans files based on a specified look back period.
- **Lookback Period**: Enter the number of days (1 to 365 days) to scan historical data.
- **Historical + Incremental Scan**: Scans files based on a specified lookback period and scan files that are newly added or modified since the previous scan.
- **Lookback Period**: Enter the number of days (1 to 365 days) to scan historical data.
- **Duration**: Specify the number of days for incremental scanning.
DSPM cannot detect files that are deleted in Cloud Storage.
[See image.](#gcp-scantype)
- Click **Next**.
[]![The scan type selection page with the available options.](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-scanrule-fileserver-scan-type.png)
-
[]On the **Scan Scope** page, choose a scan scope from the drop-down menu to set up your scan rule.
To learn more about configuring and creating a scan scope, see [Configuring Scan Scope](/dspm/configuring-scan-scope).
[See image.](#img_scanscope)
- Click **Next**.
[]![The Scan Scope page with dropdown menu for selecting scan scope.](/downloads/dspm/scan-settings/configuring-scan-scope/select_scanscope.png)
-
[]Review the scan rule. Click the **Edit** icon to change any values, if required.
[See image.](#gcp-review)
- Click **Finish**.
[]![The scan settings review page displays the configured scan settings before completing the scan configuration.](/downloads/dspm/scan-settings/scan-settings-gcp/configuring-scan-settings-gcp-cloud-storage/ds-scanrule-gcp-cs-review.png)