# Configuring Scan Rule for GCP Databases
Source: https://help.zscaler.com/dspm/configuring-scan-rule-gcp-databases
PDF: https://help.zscaler.com/pdf/com/en/1520166.pdf

You can configure the scan rule to scan Google Cloud Platform (GCP) databases such as SQL, MySQL and PostgreSQL. DSPM scans the database instances for any sensitive data. The scan results are displayed on the [Resource Inventory page](/dspm/about-resource-inventory).
You can configure the scan rule after onboarding the GCP organizations. To learn more, see [About Cloud Accounts](/dspm/about-cloud-accounts).
To configure a scan rule for GCP databases:
- [1. Provide the general information.](#gen-info)
- [2. Select the cloud and resource type.](#ds-dbstep1)
- [3. Select the projects that must be scanned.](#ds-dbstep2)
- [4. Exclude database servers (Optional).](#ds-gcp-manageddb-exclude)
- [5. Select the scan type.](#sel_scan_type)
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
[]![The initial scan rule configuration page with no scan rule configured and + Add Scan Rule button.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-initialscanrule.png)
[]![ General Information page to set the scan rule name and an optional description field.](/downloads/dspm/scan-settings/scan-settings-premise-unmanaged-database/configuring-scan-settings-premise-unmanaged-database/ds-scan-rule-general-info.png)
-
[]On the **Select Cloud and Resource Type** page:
- For **Cloud Type**, select **Google Cloud**.
- For **Resource Type**, select **Database**.
[See image.](#db-select)
- Click **Next**.
-
[]On the **Select Resources to Scan** page, choose one of the following options:
-
**Scan All Resources**: Scans all the supported databases across all onboarded projects.
[See image.](#db-scanall)
-
**Scan Specific Resources**: Scan only specific projects.
- **Select Specific Projects and Regions**: Select the checkbox for the projects that must be scanned.
- **Scan Specific Database Instances or Clusters**: Specify the instances or clusters that must be scanned.
- **Select from the List**: Select the checkbox for the instances that must be scanned from the list. If you choose **Manual**, enter the database names separated by commas.
-
**Select by Labels**: Enter the key-value pairs for the instances. All the instances that match the tag are scanned. Click **Add More** to add multiple key-value pairs.
If multiple key-value pairs are added, DSPM scans all instances that match at least one of the specified key-value pairs. This means the rule uses `OR` logic, and a instance is included if it matches any of the key-value pairs.
[See image.](#db-scanspecific)
You can [optionally exclude](#ds-exclude) specific databases from the scan.
- Click **Next**.
[][]On the **Exclude Database Servers (Optional)** page, you can specify the databases that must be excluded from the scan.
If a full scan is already initiated or completed, the databases are excluded in the next incremental scan.
- Enter the database names separated by commas.
-
**Exclude Databases By Labels**: Enable this option and enter the key-value pairs of the databases that must be excluded from scanning. This option is disabled by default. Click **Add More** to add multiple key-value pairs.
If multiple key-value pairs are added, DSPM excludes any databases that matches at least one of the specified key-value pairs. This means the rule uses `OR` logic, and a database is excluded if it matches any of the key-value pairs.
[See image.](#db-optionalexclude)
- Click **Next**.
-
[]On the **Scan Type** page, you can choose to perform one of the following scans:
- **Data Sampling Scan**: Scan a sample of recent data in the database.
- **Full Scan**: A complete scan of all databases across all onboarded projects.
DSPM cannot detect files that are deleted in the GCP console.
[See image.](#img_scan_type)
- Click **Next**.
-
[]On the **Scan Schedule** page, select the scan frequency:
- **On Demand** (Default): The scan runs only when it is initiated manually by the user.
- **Daily**: Scan the data daily.
- **Weekly**: Scan the data once a week. Select the day from the drop-down menu.
- **Monthly**: Scan the data once a month.
[See image.](#db-schedule)
- Click **Next**.
-
[]On the **Scan Scope** page, choose a scan scope from the drop-down menu to set up your scan rule.
To learn more about configuring and creating a scan scope, see [Configuring Scan Scope](/dspm/configuring-scan-scope).
[See image.](#img_scanscope)
- Click **Next**.
[]![The scan type selection page with data sampling scan, and full scan options.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-database/ds-scanrule-aws-mdb-scan-type.png)
[]![The Scan Scope page with dropdown menu for selecting scan scope.](/downloads/dspm/scan-settings/configuring-scan-scope/select_scanscope.png)
-
[]Review the scan rule. Click the **Edit** icon to change any values, if required.
[See image.](#db-scanreview)
- Click **Finish**.
[]![The Scan Settings page with an annotation around the Add New button.](/downloads/dspm/scan-settings/configuring-scan-rule-databricks-workspace/ds-scan-scan-add-new-scan.png)
[]![Select Cloud and Resource Type page with annotated Google Cloud as cloud, Database as resource.](/downloads/dspm/scan-settings/scan-settings-gcp/configuring-scan-settings-gcp-database/ds-scanrule-gcp-select-db.png)
[]![Select resources to scan page with Scan All Projects option is selected.](/downloads/dspm/scan-settings/scan-settings-gcp/configuring-scan-settings-gcp-database/ds-scanrule-gcp-db-scanall.png)
[]![The scan specific database instances or clusters page, to specify instances or clusters with key-value pair.](/downloads/dspm/scan-settings/scan-settings-gcp/configuring-scan-settings-gcp-database/ds-scanrule-gcp-db-scan-specific.png)
[]![The scan schedule page with options for daily, weekly, and monthly scan frequency settings.](/downloads/dspm/scan-settings/scan-settings-aws/configuring-scan-settings-aws-virtual-machine/ds-scanrule-scan-weekly.png)
[]![The scan settings review page displays the configured scan settings before completing the scan configuration.](/downloads/dspm/scan-settings/scan-settings-gcp/configuring-scan-settings-gcp-database/ds-scanrule-gcp-db-review.png)
[]![The Exclude Databases screen to exclude resources from scanning.](/downloads/dspm/scan-settings/scan-settings-gcp/configuring-scan-settings-gcp-database/ds-scanrule-gcp-db-exclude.png)