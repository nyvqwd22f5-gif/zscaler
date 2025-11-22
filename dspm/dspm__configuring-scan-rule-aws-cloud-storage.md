# Configuring Scan Rule for AWS Cloud Storage
Source: https://help.zscaler.com/dspm/configuring-scan-rule-aws-cloud-storage
PDF: https://help.zscaler.com/pdf/com/en/1478131.pdf

You can configure the scan rule to scan Amazon Web Services (AWS) cloud storage resources such as S3 buckets. DSPM scans the S3 buckets for any sensitive data. The scan results are displayed on the [Resource Inventory page](/dspm/about-resource-inventory).
- You can configure the scan rule after onboarding the AWS accounts. To learn more, see [About Cloud Accounts](/dspm/about-cloud-accounts).
- DSPM automatically excludes the active [CloudTrail](/dspm/understanding-aws-cloudtrail)[ ]and VPC flow log buckets from sensitive data scans even if they match the scan criteria.
- DSPM also excludes AWS workloads that were created using the AWS Marketplace from scanning.
To configure a scan rule for AWS cloud storages:
- [1. Provide the general information.](#gen-info)
- [2. Select the cloud and resource type.](#ds-step1)
- [3. Select the accounts that must be scanned.](#ds-step2)
- [4. Exclude S3 buckets and prefixes (Optional).](#ds-aws-cs-exclude)
- [5. Select the scan type.](#ds-step3)
- [6. Select the scan scope.](#scanscope)
- [7. Review and complete the configuration.](#ds-step4)
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
- For **Cloud Type**, select **AWS**.
- For **Resource Type**, select **Cloud Storage**.
[See image.](#ds-selectaws-cs)
- Click **Next**.
- []On the **Select Resources to Scan** page, choose one of the following options:
-
**Scan All Resources**: Scan all the cloud storage resources across all onboarded accounts.
[See image.](#ds-selectaccts)
-
**Scan Specific Resources**: Select the checkbox for the specific accounts and regions that must be scanned.
-
**Select Specific Accounts and Regions**: Select the checkbox for specific accounts and regions that must be scanned.
[See image.](#ds-specificaccts)
- **Scan S3 Buckets**: Specify the S3 buckets that must be scanned. You can either select the names from the list or specify the tags.
- **Select from the List**: Select the checkbox for the S3 buckets that must be scanned. If you choose **Manual**, then you need to enter the names.
-
**Select by Tag**: Specify the tags in key-value pairs. All the S3 buckets that match the tag are scanned. Click **Add More** to add multiple key-value pairs.
If multiple key-value pairs are added, DSPM scans all buckets that match at least one of the specified key-value pairs. This means the rule uses `OR` logic, and a bucket is included if it matches any of the key-value pairs.
[See image.](#ds-selectbuckets)
-
**Enable Malware Scanning**: Enable this option if the resources must be scanned for malware. This option is disabled by default.
[See image.](#malwarescan)
- Click **Next**.
[]On the **Exclude S3 Buckets and Prefixes (Optional)** page, you can specify the S3 buckets and prefixes that must be excluded from the scan.
If a full scan is already initiated or completed, the bucket or folder is excluded in the next incremental scan.
- Enter the name of the bucket, or include the folder name followed by a forward slash (/). For example, to exclude a folder named `reports` within a bucket named `my-bucket`, enter `my-bucket/reports/`. Additionally, you can use wildcards with the S3 bucket names instead of relying on tags. Based on the wildcard, DSPM excludes all the matching S3 buckets from scanning. This is applicable to both existing S3 buckets and the ones that might be added in the future.
-
**Exclude S3 Buckets By Tags**: Select the checkbox and enter the key-value pairs of the S3 buckets that must be excluded from scanning. This option is disabled by default. Click **Add More** to add multiple key-value pairs.
If multiple key-value pairs are added, DSPM excludes any bucket that matches at least one of the specified key-value pairs. This means the rule uses `OR` logic, and a bucket is excluded if it matches any of the key-value pairs.
-
**Exclude S3 Bucket Names Using Wildcards**: Select the checkbox and enter the wildcard expressions to exclude buckets by name using wildcards. For example, `*logs*` — excludes any bucket name that contains the word `logs`.
[See image.](#ds-cs-optional)
- Click **Next**.
-
[]On the **Scan Type** page, choose one of the following options:
- **Full Scan**: Scans all objects in the S3 buckets.
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
DSPM cannot detect files that are deleted in the AWS console.
[See image.](#ds-cs-scantype)
- Click **Next**.
-
[]On the** Scan Scope **page, choose a scan scope from the drop-down menu to set up your scan rule.
To learn more about configuring and creating a scan scope, see [Configuring Scan Scope](/dspm/configuring-scan-scope).
[See image.](#img_scanscope)
- Click **Next**.
[]![The Scan Scope page with dropdown menu for selecting scan scope.](/downloads/dspm/scan-settings/configuring-scan-scope/select_scanscope.png)
-
[]Review the scan rule. Click the **Edit** icon to change any values, if required.
[See image.](#ds-cs-review)
- Click **Finish**.
[]![The Scan Settings page with an annotation around the Add New button.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-scan-scan-add-new-scan.png)
[]![ General Information page to set the scan rule name and an optional description field.](/downloads/dspm/scan-settings/scan-settings-premise-unmanaged-database/configuring-scan-settings-premise-unmanaged-database/ds-scan-rule-general-info.png)
[]![The initial scan settings configuration page with no scan settings configured and + Configure Scan Settings button.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-cloud-storage/ds-initialscanrule.png)
[]![Select Cloud and Resource Type page with an annotation around the AWS Cloud Type and Cloud Storage Resource.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-cloud-storage/ds-scanselect.png)
[]![Select Resources to Scan page with Scan All Accounts option is selected.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-cloud-storage/ds-scanrule-aws-scanall.png)
[]![Select Resources to Scan page with Scan Specific Accounts option selected and selected few accounts to scan.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-cloud-storage/ds-scanrule-aws-scanspecific.png)
[]![Select Resources to Scan page with Scan S3 Buckets option selected.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-cloud-storage/ds-scanrule-aws-scans3.png)
[]![Enable malware scanning option is enabled with the toggle button.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-cloud-storage/ds-scanrule-aws-enable-malware.png)
[]![Exclude specific buckets from the scan](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-cloud-storage/ds-scanrule-aws-cloud-exclude.png)
[]![The scan type selection page with the available options.](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-scanrule-fileserver-scan-type.png)
[]![The scan settings review page displays the configured scan settings before completing the scan configuration.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-cloud-storage/ds-scanrule-aws-cloud-review.png)