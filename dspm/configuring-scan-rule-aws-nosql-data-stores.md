# Configuring Scan Rule for AWS NoSQL Data Stores
Source: https://help.zscaler.com/dspm/configuring-scan-rule-aws-nosql-data-stores
PDF: https://help.zscaler.com/pdf/com/en/1509666.pdf

You can configure the scan rule to scan Amazon Web Services (AWS) NoSQL data stores and DynamoDB. DSPM scans the data stores instances for any sensitive data. The scan results are displayed on the [Resource Inventory page](/dspm/about-resource-inventory).
You can configure the scan rule after onboarding the AWS accounts. To learn more, see [About Cloud Accounts](/dspm/about-cloud-accounts).
To configure a scan rule for AWS data stores:
- [1. Provide the general information.](#gen-info)
- [2. Select the cloud and resource type.](#ds-dbstep1)
- [3. Select the accounts that must be scanned.](#ds-dbstep2)
- [4. Exclude DynamoDB tables (Optional).](#ds-aws-nosql-ds-exclude)
- [5. Select the scan type](#db-scantype)
- [6. Set up the scan schedule.](#ds-dbstep3)
- [7. Select the scan scope.](#scanscope)
- [8. Review and complete the configuration.](#ds-dbstep4)
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
- For **Resource Type**, select **NoSQL Data Stores**.
[See image.](#db-select)
- Click **Next**.
[]![The initial scan rule configuration page with no scan rule configured and + Add Scan Rule button.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-initialscanrule.png)
[]![The Scan Settings page with an annotation around the Add New button.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-scan-scan-add-new-scan.png)
[]![ General Information page to set the scan rule name and an optional description field.](/downloads/dspm/scan-settings/scan-settings-premise-unmanaged-database/configuring-scan-settings-premise-unmanaged-database/ds-scan-rule-general-info.png)
[]![Select Cloud and Resource Type page with an annotation around the AWS Cloud Type and NoSQL Data Stores Resource.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-dynamodb/ds-scanrule-aws-select-nosql-ds.png)
-
[]On the **Select the Resources to Scan** page, choose one of the following options:
-
**Scan All Resources**: Scans all accounts and the associated DynamoDB tables across all onboarded accounts.
[See image.](#db-scanall)
-
**Scan Specific Resources**: Scan only specific resources. When you select this option, select the checkbox for the accounts that must be scanned.
- **Select Specific Accounts and Regions**: Select the checkbox for specific accounts and regions that must be scanned.
- **Scan DynamoDB Tables**: Specify the DynamoDB tables that must be scanned. You can either select the names from the list or specify the tags.
- **Select from the Lis**t: Select the checkbox for the DynamoDB tables that must be scanned. If you choose **Manual**, then you need to enter the names.
-
**Select by Tags**: Specify the tags in key-value pairs. All the DynamoDB tables that match the tag are scanned. Click **Add More** to add multiple key-value pairs.
If multiple key-value pairs are added, DSPM scans all tables that match at least one of the specified key-value pairs. This means the rule uses `OR` logic, and a table is included if it matches any of the key-value pairs.
[See image.](#db-dynamodbtables)
If you chose **Scan All Resources**, or** Scan Specific Resources**, you can [optionally exclude](#ds-exclude) specific DynamoDB tables from the scan.
- Click **Next**.
[][]On the **Exclude DynamoDB Tables (Optional)** page, you can specify the DynamoDB tables that must be excluded from the scan.
If a full scan is already initiated or completed, the DynamoDB tables are excluded in the next incremental scan.
- Enter the DynamoDB table ARNs separated by commas.
-
**Exclude DynamoDB Tables By Tags**: Enable this option and enter the key-value pairs of the DynamoDB tables that must be excluded from scanning. This option is disabled by default. Click **Add More** to add multiple key-value pairs.
If multiple key-value pairs are added, DSPM excludes any table that matches at least one of the specified key-value pairs. This means the rule uses `OR` logic, and a table is excluded if it matches any of the key-value pairs.
[See image.](#db-optionalexclude)
- Click **Next**.
[]![The Select Resources to Scan page with Scan All Accounts option is selected.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-dynamodb/ds-scanrule-aws-nosql-scanall.png)
[]![The Scan Dynamo DB tables page to choose tables from list or by tags.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-dynamodb/ds-scanrule-aws-nosql-scandynamo.png)
[]![The Exclude DynamoDB Tables page to exclude resources from scanning.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-dynamodb/ds-scanrule-aws-nosql-exclude.png)
-
[]On the **Scan Type** page, you can choose to perform one of the following scans:
- **Data Sampling Scan**: Scan a sample of recent data in the database.
- **Full Scan**: A complete scan of all databases across all onboarded accounts.
DSPM cannot detect files that are deleted from the resource.
[See image.](#scantype)
- Click **Next**.
[]![The scan type selection page with data sampling scan, and full scan options.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-database/ds-scanrule-aws-mdb-scan-type.png)
-
[]On the** Scan Schedule** page, select the scan frequency:
- **On Demand **(Default): Scan the data manually when needed.
- **Daily**: Scan the data daily.
- **Weekly**: Scan the data once a week. Select the day from the drop-down menu.
- **Monthly**: Scan the data once a month.
[See image.](#db-schedule)
- Click **Next**.
[]![The scan schedule page with options for daily, weekly, and monthly scan frequency settings.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-scan-schedule.png)
-
[]On the** Scan Scope **page, choose a scan scope from the drop-down menu to set up your scan rule.
To learn more about configuring and creating a scan scope, see [Configuring Scan Scope](/dspm/configuring-scan-scope).
[See image.](#img_scanscope)
- Click **Next**.
[]![The Scan Scope page with dropdown menu for selecting scan scope.](/downloads/dspm/scan-settings/configuring-scan-scope/select_scanscope.png)
-
[]Review the scan rule. Click the **Edit** icon to change any values, if required.
[See image.](#db-scanreview)
- Click **Finish**.
[]![The scan settings review page displays the configured scan settings before completing the scan configuration.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-dynamodb/ds-scanrule-aws-nosql-review.png)