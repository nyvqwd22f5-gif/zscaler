# Configuring Scan Rule for Azure-Managed Databases
Source: https://help.zscaler.com/dspm/configuring-scan-rule-azure-managed-databases
PDF: https://help.zscaler.com/pdf/com/en/1495196.pdf

You can configure the scan rule to scan Azure SQL databases and Azure-Managed PostgreSQL Flexible servers. DSPM scans the databases for any sensitive data and vulnerabilities. The scan results are displayed on the [Resource Inventory page](/dspm/about-resource-inventory).
Before configuring the scan, ensure your Azure SQL database has a Role-Based Access Control (RBAC) policy for the Key Vault.
DSPM does not provide support for scanning Azure SQL databases that are encrypted with a Customer-Managed Key (CMK) without the RBAC policy.
You can configure the scan rules after onboarding the Azure accounts. To learn more, see [About Cloud Accounts](/dspm/about-cloud-accounts).
To configure a scan rule for Azure-managed databases:
- [1. Provide the general information.](#gen-info)
- [2. Select the cloud and resource type.](#azuredb)
- [3. Select the accounts that must be scanned.](#azuredb2)
- [4. Exclude database servers (Optional).](#ds-azure-manageddb-exclude)
- [5. Select the scan type.](#sel_scan_type)
- [6. Set up the scan schedule.](#azuredb3)
- [7. Select the scan scope.](#scanscope)
- [8. Review and complete the configuration.](#azuredb4)
After completing the scan, DSPM deletes the restored servers, databases, and File System (FS) Analyzer to reduce the cost for customers.
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
- For **Resource Category**, select **Database**.
- For **Resource Type**, select **Managed Database**.
[See image.](#azuredb-selectcloudtype)
- Click **Next**.
-
[]On the **Select Resources to Scan** page, choose one of the following options:
-
**Scan All Resources**: Scan all the supported database resources across all onboarded accounts.
[See image.](#azuredb-selectdata)
- **Scan Specific Resources**: Select the checkbox for the specific resources that must be scanned.
- **Select Specific Subscriptions and Regions**: Select the checkbox for specific subscriptions and regions that must be scanned.
-
**Scan Specific Database Servers**: Specify the databases that must be scanned. When you select this option, select the checkbox for the account that must be excluded from the scan.
- **Select from the List**: Select the checkbox for the instances that must be scanned from the list. If you choose **Manual**, enter the database names separated by commas.
-
**Select by Tags**: Enter the key-value pairs for the database servers. All the database servers that match the tag are scanned. Click **Add More** to add multiple key-value pairs.
If multiple key-value pairs are added, DSPM scans all databases that match at least one of the specified key-value pairs. This means the rule uses `OR` logic, and a database is included if it matches any of the key-value pairs.
[See image.](#db-scanspecificacc)
You can [optionally exclude](#ds-exclude) specific databases from the scan.
- Click **Next**.
[][]On the **Exclude Database Servers (Optional)** page, you can specify the database servers that must be excluded from the scan.
If a full scan is already initiated or completed, the databases are excluded in the next incremental scan.
- Enter the database server names separated by commas.
-
**Exclude Database Servers By Tags**: Enable this option and enter the key-value pairs of the database servers that must be excluded from scanning. This option is disabled by default. Click **Add More** to add multiple key-value pairs.
If multiple key-value pairs are added, DSPM excludes any database that matches at least one of the specified key-value pairs. This means the rule uses `OR` logic, and a database is excluded if it matches any of the key-value pairs.
[See image.](#azuredb-optional)
- Click **Next**.
-
[]On the **Scan Type** page, you can choose to perform one of the following scans:
- **Data Sampling Scan**: Scan a sample of recent data in the database.
- **Full Scan**: A complete scan of all databases across all onboarded accounts.
DSPM cannot detect files that are deleted in the AWS console.
[See image.](#img_scan_type)
- Click **Next**.
-
[]On the **Scan Schedule** page, select the scan frequency:
- **On Demand **(Default): Scan the data manually when needed.
- **Daily**: Scan the data daily.
- **Weekly**: Scan the data once a week. Select the day from the drop-down menu.
- **Monthly**: Scan the data once a month.
[See image.](#azuredb-schedule)
- Click **Next**.
-
[]On the **Scan Scope** page, choose a scan scope from the drop-down menu to set up your scan rule.
To learn more about configuring and creating a scan scope, see [Configuring Scan Scope](/dspm/configuring-scan-scope).
[See image.](#img_scanscope)
- Click **Next**.
[]![The scan type selection page with data sampling scan, and full scan options.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-database/ds-scanrule-aws-mdb-scan-type.png)
[]![The Scan Scope page with dropdown menu for selecting scan scope.](/downloads/dspm/scan-settings/configuring-scan-scope/select_scanscope.png)
-
[]Review the scan rule. Click the **Edit** icon to change any values, if needed.
[See image.](#azuredb-review)
- Click **Finish**.
[]![The Scan Settings page with an annotation around the Add New button.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-scan-scan-add-new-scan.png)
[]![Select Cloud and Resource Type page with Azure Cloud Type, Database Resource, and Managed Database Type.](/downloads/dspm/scan-settings/scan-settings-azure/configuring-scan-settings-azure-database/ds-scanrule-azure-select-mdb.png)
[]![The Select Resources to Scan page with Scan All Subscriptions option is selected.](/downloads/dspm/scan-settings/scan-settings-azure/configuring-scan-settings-azure-database/ds-scanrule-azure-scanall.png)
[]![The Select Resources to Scan page with Scan specific instances option selected, showing the fields to enter key-value pair.](/downloads/dspm/scan-settings/scan-settings-azure/configuring-scan-settings-azure-database/ds-scanrule-azure-scan-specific.png)
[]![The Database Servers screen to exclude resources from scanning.](/downloads/dspm/scan-settings/scan-settings-azure/configuring-scan-settings-azure-database/ds-scanrule-azure-mdb-exclude.png)
[]![The scan schedule page with options for daily, weekly, and monthly scan frequency settings.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-virtual-machine/ds-scanrule-scan-weekly.png)
[]![The scan settings review page displays the configured scan settings before completing the scan configuration.](/downloads/dspm/scan-settings/scan-settings-azure/configuring-scan-settings-azure-database/ds-scanrule-azure-mdb-review.png)