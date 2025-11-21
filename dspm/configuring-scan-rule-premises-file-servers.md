# Configuring Scan Rule for On-Premises File Servers
Source: https://help.zscaler.com/dspm/configuring-scan-rule-premises-file-servers
PDF: https://help.zscaler.com/pdf/com/en/1532033.pdf

You can configure the scan rule to scan on-premises file servers. DSPM scans these resources for any sensitive data and vulnerabilities and displays the scan results on the [Resource Inventory page](/dspm/about-resource-inventory).
Prerequisites
Before configuring the scan rule, you need to configure the on-premises file servers. To learn more, see [About Service Registration](/dspm/about-service-registration).
Configuring Scan Rule
To configure a scan rule for on-premises file servers:
- [1. Provide the general information.](#gen-info)
- [2. Select the cloud and resource type.](#snwdb)
- [3. Select the resources that must be scanned.](#snwdb2)
- [4. Select the scan type.](#sel_scan_type)
- [5. Select the scan scope.](#scanscope)
- [6. Review and complete the configuration.](#db4)
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
- **Cloud Type**: Select **On-Premises**.
- **Resource Category**: Select **File Servers**.
- **Resource Type**: Select **File Shares**.
[See image.](#ds-scan-selecttype)
- Click **Next**.
-
[]On the **Select Resources to Scan** page, choose one of the following options:
- **Scan All Resources**: Scan all the resources across all the file server.
- **Scan Specific Resources**: Select the checkbox for specific resources that must be scanned.
[See image.](#select-resource)
- Click **Next**.
-
[]On the **Scan Type** page, choose one of the following options:
- **Full Scan**: Scans all objects on the on-premises file server.
- **Full + Incremental Scan**: Scans all objects, including those that are newly added or modified since the previous scan.
-
Select one of the scan durations: **1 Day**, **1 Week**, **1 Month**, **Continuous**, **Custom Duration**.
If you select **Custom Duration**, enter the number of days to define the scan window.
- **Incremental Scan**: Scans only the files that are newly added or modified since the previous scan.
-
Select one of the scan durations: **1 Day**, **1 Week**, **1 Month**, **Continuous**, **Custom Duration**.
If you select **Custom Duration**, enter the number of days to define the scan window.
- **Historical Scan**: Scans files based on a specified look back period.
- **Lookback Period**: Enter the number of days to scan historical data.
- **Historical + Incremental Scan**: Scans files based on a specified lookback period and scan files that are newly added or modified since the previous scan.
- **Lookback Period**: Enter the number of days to scan historical data.
- **Duration**: Specify the number of days for incremental scanning.
DSPM cannot detect files that are deleted from the on-premises file server.
[See image.](#img_scan_type)
- Click **Next**.
-
[]On the **Scan Scope** page, choose a scan scope from the drop-down menu.
To learn more about configuring and creating a scan scope, see [Configuring Scan Scope](/dspm/configuring-scan-scope).
[See image.](#img_scanscope)
- Click **Next**.
[]![The scan type selection page with the available options.](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-scanrule-fileserver-scan-type.png)
[]![The Scan Scope page with dropdown menu for selecting scan scope.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-scan-scope.png)
-
[]Review the scan settings. Click the **Edit** icon to change any values, if needed.
[See image.](#scan-review)
- Click **Finish**.
[]![The initial scan rule configuration page with no scan rule configured and + Add Scan Rule button.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-initialscanrule.png)
[]![The Scan Settings page with an annotation around the Add New button.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-scan-scan-add-new-scan.png)
[]![A tile list of cloud types, resource categories, and database types. ](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-scanrule-fileserver-select-type.png)
[]![The Select Resources to Scan page with selected Databricks workspaces.](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-scanrule-fileserver-select-resource.png)
[]![The scan settings review page displays the configured scan settings before completing the scan configuration.](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-scanrule-fileserver-review.png)
[]![ General Information page to set the scan rule name and an optional description field.](/downloads/dspm/scan-settings/scan-settings-premise-unmanaged-database/configuring-scan-settings-premise-unmanaged-database/ds-scan-rule-general-info.png)