# Configuring Scan Rule for AWS Unmanaged Databases
Source: https://help.zscaler.com/dspm/configuring-scan-rule-aws-unmanaged-databases
PDF: https://help.zscaler.com/pdf/com/en/1520161.pdf

You can configure the scan rule to scan AWS unmanaged database servers. DSPM scans the databases for any sensitive data and vulnerabilities. The scan results are displayed on the [Resource Inventory page](/dspm/about-resource-inventory).
You can configure the scan rule after onboarding the AWS accounts. To learn more, see [About Cloud Accounts](/dspm/about-cloud-accounts).
To configure a scan rule for AWS unmanaged databases:
- [1. Provide the general information.](#gen-info)
- [2. Select the cloud and resource type.](#umdb)
- [3. Select the resources that must be scanned.](#umdb2)
- [4. Select the scan type.](#sel_scan_type)
- [5. Set up the scan schedule.](#db3)
- [6. Select the scan scope.](#scanscope)
- [7. Review and complete the configuration.](#db4)
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
- []On the **Select Cloud Type and Resource Type** page:
- For **Cloud Type**: Select **AWS**.
- For **Resource Category**: Select **Database**.
- For **Resource Type**: Select **Unmanaged Database**.
- [See image.](#umdb-selectcloudtype)
- Click **Next**.
- []On the **Select the Resources to Scan** page, choose one of the following options:
-
**Scan All Resources**: Scan all the supported database resources across all onboarded accounts.
[See image.](#db-scanall)
-
**Scan Specific Resources**: Select the checkbox for the specific resources that must be scanned.
[See image.](#db-scanspecificacc)
- Click **Next**.
-
[]On the **Scan Type** page:
- **Data Sampling Scan**: Scan a sample of recent data in the database.
DSPM cannot detect files that are deleted from the unmanaged database server.
[See image.](#img_scan_type)
- Click **Next**.
-
[]On the** Scan Schedule** page, select the scan frequency:
- **On-Demand Scan** (Default): The scan runs only when it is initiated manually by the user.
- **Daily**: Scan the data daily at the specified time (e.g., 11:59 PM).
- **Weekly**: Scan the data once a week. Select the day from the drop-down menu and specify the time (e.g., Tuesday at 11:59 PM).
- **Monthly**: Scan the data once a month. Select the day of the month from the drop-down menu and specify the time (e.g., the 24th at 11:59 PM).
[See image.](#db-schedule)
- Click **Next**.
-
[]On the** Scan Scope **page, choose a scan scope from the drop-down menu to set up your scan rule.
To learn more about configuring and creating a scan scope, see [Configuring Scan Scope](/dspm/configuring-scan-scope).
[See image.](#img_scanscope)
- Click **Next**.
[]![The Scan Type page with the Data Sampling Scan selected.](/downloads/dspm/scan-settings/scan-settings-azure/configuring-scan-settings-azure-unmanaged-database/umd_scan_type.png)
[]![Select Scan Scope](/downloads/dspm/scan-settings/configuring-scan-scope/select_scanscope.png)
-
[]Review the scan rule. Click the **Edit** icon to change any values, if needed.
[See image.](#umdb-review)
- Click **Finish**.
[]![The initial scan rule configuration page with no scan rule configured and + Add Scan Rule button.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-initialscanrule.png)
[]![The Scan Settings page with an annotation around the Add New button.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-scan-scan-add-new-scan.png)
[]![A tile list of cloud types, resource categories, and database types. ](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-unmanaged-databases/ds-scanrule-aws-select-umdb.png)
[]![The Select Resources to Scan page with selected unmanaged database servers.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-unmanaged-databases/ds-scanrule-aws-umdb-scanspecific.png)
[]![The scan schedule page with options for daily, weekly, and monthly scan frequency settings.](/downloads/dspm/scan-settings/configuring-scan-settings-snowflake-databases/ds-scanrule-schedule-monthly.png)
[]![The scan settings review page displays the configured scan settings before completing the scan configuration.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-unmanaged-databases/ds-scanrule-aws-umdb-review.png)
[]![ General Information page to set the scan rule name and an optional description field.](/downloads/dspm/scan-settings/scan-settings-premise-unmanaged-database/configuring-scan-settings-premise-unmanaged-database/ds-scan-rule-general-info.png)
[]![Select Resources to Scan page with Scan All Accounts option is selected.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-unmanaged-databases/ds-scanrule-aws-umdb-scanall.png)