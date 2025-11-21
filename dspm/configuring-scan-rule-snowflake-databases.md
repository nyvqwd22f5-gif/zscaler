# Configuring Scan Rule for Snowflake Databases
Source: https://help.zscaler.com/dspm/configuring-scan-rule-snowflake-databases
PDF: https://help.zscaler.com/pdf/com/en/1529992.pdf

You can configure the scan rule to scan Snowflake databases. DSPM scans the databases for any sensitive data and vulnerabilities and displays the scan results on the [Resource Inventory page](/dspm/about-resource-inventory).
Prerequisites
Before configuring the scan rule, you need to configure the Snowflake account. To learn more, see [About Snowflake](/dspm/about-service-registration).
Configuring Scan Rule
To configure a scan rule for Snowflake databases:
- [1. Provide the general information.](#gen-info)
- [2. Select the cloud and resource type.](#snwdb)
- [3. Select the resources that must be scanned.](#snwdb2)
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
The **General Information** window appears.
-
On the **General Information **page:.
- **Scan Rule Name**: Enter a unique and descriptive name for the scan rule.
- **Scan Rule Description (Optional)**: Enter a description of the scan rule (maximum 500 characters).
[See image.](#ds-scan-gen-info)
- Click **Next**.
-
[]On the **Select Cloud and Resource Type** page:
- **Cloud Type**: Select **Snowflake**.
- **Resource Type**: Select **Database**.
[See image.](#ds-scan-selecttype)
- Click **Next**.
-
[]On the **Select Resources to Scan** page, choose one of the following options:
- **Scan All Accounts**: Scan all the resources across all the registered workspaces.
- **Scan Specific Accounts**: Select the checkbox for specific resources that must be scanned.
[See image.](#umdb-select-resource)
- Click **Next**.
-
[]On the **Scan Type** page, select **Data Sampling Scan** to scan a sample of recent data in the database.
DSPM cannot detect files that are deleted from the Snowflake database.
[See image.](#img_scan_type)
- Click **Next**.
-
[]On the **Scan Schedule** page, select the scan frequency:
- **On-Demand Scan** (Default): The scan runs only when it is initiated manually by the user.
- **Daily**: Scan the data daily at the specified time (e.g., 11:59 PM).
- **Weekly**: Scan the data once a week. Select the day from the drop-down menu and specify the time (e.g., Tuesday at 11:59 PM).
- **Monthly**: Scan the data once a month. Select the day of the month from the drop-down menu and specify the time (e.g., the 24th at 11:59 PM).
[See image.](#db-schedule)
- Click **Next**.
-
[]On the **Scan Scope** page, choose a scan scope from the drop-down menu.
To learn more about configuring and creating a scan scope, see [Configuring Scan Scope](/dspm/configuring-scan-scope).
[See image.](#img_scanscope)
- Click **Next**.
[]![The scan type selection page with Data Sampling option selected.](/downloads/dspm/scan-settings/configuring-scan-settings-snowflake-databases/snowflake_scan_type.png)
[]![The Scan Scope page with dropdown menu for selecting scan scope.](/downloads/dspm/scan-settings/configuring-scan-settings-snowflake-databases/select_scanscope.png)
-
[]Review the scan rule. Click the **Edit** icon to change any values, if needed.
[See image.](#umdb-review)
- Click **Finish**.
[]![The initial scan rule configuration page with no scan rule configured and + Add Scan Rule button.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-initialscanrule.png)
[]![The Scan Settings page with an annotation around the Add New button.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-scan-scan-add-new-scan.png)
[]![A tile list of cloud types, resource categories, and database types. ](/downloads/dspm/scan-settings/configuring-scan-settings-snowflake-databases/ds-admin-scan-select-snowflake.png)
[]![The Select Resources to Scan page with few specific resources are selected to scan. ](/downloads/dspm/scan-settings/configuring-scan-settings-snowflake-databases/ds-scanrule-snowflake-resource.png)
[]![The scan schedule page with options for daily, weekly, and monthly scan frequency settings.](/downloads/dspm/scan-settings/configuring-scan-settings-snowflake-databases/ds-scanrule-schedule-monthly.png)
[]![The scan settings review page displays the configured scan settings before completing the scan configuration.](/downloads/dspm/scan-settings/configuring-scan-settings-snowflake-databases/ds-scanrule-snowflake-review.png)
[]![ General Information page to set the scan rule name and an optional description field.](/downloads/dspm/scan-settings/scan-settings-premise-unmanaged-database/configuring-scan-settings-premise-unmanaged-database/ds-scan-rule-general-info.png)