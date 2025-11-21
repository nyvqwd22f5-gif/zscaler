# Configuring Suppression Rules
Source: https://help.zscaler.com/uvm/configuring-suppression-rules
PDF: https://help.zscaler.com/pdf/com/en/1527996.pdf

When [creating a data source](/uvm/creating-data-sources) to ingest data into the Zscalerer]] Security Operations (SecOps) platform, you can apply suppression rules to control which data is included in the ingestion process. Suppression rules allow you to either exclude specific data (e.g., from decommissioned assets or test environments) or include only a targeted subset of the source data. This helps reduce noise, avoid processing irrelevant or sensitive information, and ensure that only actionable findings are brought into the platform.
Suppression rules can be configured either during [initial source setup](#new-source) or [after the source has ingested data](#existing-source) for the first time. The best approach depends on how familiar you are with the structure of the source fields. After configuring your rules and reprocessing the data, be sure to [validate that the suppression is working](#validating-rules) as intended.
Suppression rules only apply to data ingested after the rules are configured. The rules do not retroactively affect data that was previously processed and ingested into the platform.
[]Configuring Rules on an Existing Source
Suppression rules rely on the original field names provided by the third-party data source. If you're not already familiar with the source field names and field types, Zscaler recommends allowing the source to ingest data once without any suppression rules configured.
This initial ingestion populates the field name drop-down menu in the suppression rules configuration screen, making it easier to select the correct fields for filtering. When the fields are visible, you can set up rules to include or exclude specific data.
- [Step 1: Configure Suppression Rules](#step1-configure-rule)
- [Step 2: Delete Existing Data](#step2-delete-data)
- [Step 3: Reprocess the Data](#step3-reprocess)
[]To set up suppression rules on a source that has already ingested data:
- In the SecOps platform, go to **Configure** > **Sources**.
-
Hover over the source in the list, and click the **Edit** icon.
[See image.](#hover-edit)
- On the source setup page, scroll down to the **Suppression Rules** section.
- Select the rule scope:
- **Exclude Rows**: Filter out data that should not be ingested.
-
**Include Rows**: Ingest only data that matches your criteria.
[See image.](#rule-setup)
-
Select the field from the drop-down menu to serve as the filter criterion for data suppression.
The drop-down menu is populated with field names from the source after at least one ingestion run.
-
Select the field type (e.g., **Text**, **Date**, **Number**, or **Boolean**). The field type determines the available filter operators.
[See image.](#field-type)
- Select a filter operator (e.g., **Equals**, **Contains**, **<**).
-
Enter the value to filter by (i.e., to exclude or include in the data ingestion).
Suppression rules are** **case sensitive.
- (Optional) Use **AND**/**OR** logic to define compound rules.
- Click **Save** to save the rules to the source.
Saving the source along with your configured suppression rules returns you to the Sources page.
[]**![af62b01c-83e6-4db0-9906-f7c7370a31dc.png](/downloads/uvm/configure/sources/suppression-rules/af62b01c-83e6-4db0-9906-f7c7370a31dc.png)
**
[]**![e2c04131-448b-4661-895b-f81181ab924e.png](/downloads/uvm/configure/sources/suppression-rules/e2c04131-448b-4661-895b-f81181ab924e.png)
**
[]**![e2609d5b-216b-48e7-b181-8ffaa633d992.png](/downloads/uvm/configure/sources/suppression-rules/e2609d5b-216b-48e7-b181-8ffaa633d992.png)
**
[]Data retrieved from the source before setting up the suppression rules is not retroactively removed. Before reprocessing the data source, remove the data that was ingested in the first run to ensure clean and accurate data.
To delete existing data ingested by the source:
- Go to **Configure **> **Sources**.
-
Hover over the source in the sources list, and click the **Delete** icon.
[See image.](#hover-delete)
- Select **Keep the data source, delete the underlying data**.
- Click **Delete**.
[]![31e2d6b5-98b6-4e55-ae08-5718d4314f21.png](/downloads/uvm/configure/sources/suppression-rules/31e2d6b5-98b6-4e55-ae08-5718d4314f21.png)
[]After you delete the existing data from the system, make sure to re-ingest the data excluding the suppressed fields.
To re-ingest the source data:
- Go to **Configure **> **Sources**.
-
Hover over the source in the sources list, and click the **Process Now **icon.
[See image.](#hover-process-now)
A message appears at the top of the page, indicating whether the process action was successful. To view the run status, hover over the source and click the **See Runs **icon. To learn more, see [Tracking Source Runs](/uvm/tracking-source-runs).
[]![b0ea2232-c8ff-4729-b281-43b67db6d303.png](/downloads/uvm/configure/sources/suppression-rules/b0ea2232-c8ff-4729-b281-43b67db6d303.png)
[]Configuring Rules on a New Source
If you're familiar with the source's original field names, you can also apply suppression rules when setting up a new source. Here, you'll need to add the field names manually in the rule configuration process.
To configure rules on a new source:
- Go to **Configure** > **Sources.**
- Click **Create**.
- Select the desired source from the list, and follow the setup process in [Creating Data Sources](/uvm/creating-data-sources).
- Select the rule scope:
- **Exclude Rows**: Filter out data that should not be ingested.
-
**Include Rows**: Ingest only data that matches your criteria.
[See image.](#rule-setup2)
- In the **Select Field** drop-down menu, enter the field name, then press** **`Enter`.
-
Select the field from the drop-down menu to serve as the filter criterion for data suppression.
The drop-down menu is populated with field names from the source after at least one ingestion run.
-
Select the field type (e.g., **Text**, **Date**, **Number**, **Boolean**). The field type determines the available filter operators.
[See image.](#field-type2)
- Select a filter operator (e.g., **Equals**, **Contains**, **<**).
-
Enter the value to filter by (i.e., to exclude or include in the data ingestion).
Suppression rules are** **case sensitive.
- (Optional) Use **AND**/**OR** logic to define compound rules.
- Click **Save** to save the rules to the source.
Saving the source along with your configured suppression rules returns you to the Sources page.
Saving the source does not run the source. To process the source immediately, hover over the source in the list and click the **Process Now** icon. Otherwise, the source runs automatically based on its configured [Scheduling settings](/uvm/creating-data-sources).
[]**![e2609d5b-216b-48e7-b181-8ffaa633d992.png](/downloads/uvm/configure/sources/suppression-rules/e2609d5b-216b-48e7-b181-8ffaa633d992.png)
**
[]**![e2c04131-448b-4661-895b-f81181ab924e.png](/downloads/uvm/configure/sources/suppression-rules/e2c04131-448b-4661-895b-f81181ab924e.png)
**
[]Validating Suppression Rules
After configuring suppression rules and reprocessing the source, it's important to confirm that the rules are working as intended. You can validate suppression in one of two ways.
Check for a Decrease in Row Count
Checking for a decrease in row count is a quick way to verify that suppression rules are filtering data during ingestion.
To check for a decrease in source runs:
- Go to **Configure** > **Sources**.
- Hover over the source, and click the **See Runs** icon.
- Expand the most recent run to view the total number of ingested rows.
- Asses the row count, or compare the row count with a previous run to confirm that data has been suppressed. To learn more, see [Tracking Source Runs](/uvm/tracking-source-runs).
Review Ingested Logs
To verify that your suppression rule is working as intended, you can search the logs to check whether the targeted data was successfully excluded. To learn more, see [Building Queries and Searching Logs](/uvm/building-queries-searching-logs).
To search the logs for suppressed data:
- Go to **Explore** > **Logs**.
-
Build a query to search for the suppressed or included data:
- Select the suppressed source field.
- Use the **Equals** operator.
- Enter the relevant value based on the suppression rule type:
- **Exclude Rows**: Enter a value you specified in the suppression rule.
- **Include Rows**: Enter a value not included in the suppression rule.
[See image.](#logs-rule-search)
-
Click **Search**.
If the query returns no results, the suppression rule is likely to be functioning as expected.
[]**![mceclip3.png](/downloads/uvm/configure/sources/suppression-rules/mceclip3.png)
**