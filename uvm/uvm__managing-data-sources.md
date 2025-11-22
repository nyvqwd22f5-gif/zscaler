# Managing Data Sources
Source: https://help.zscaler.com/uvm/managing-data-sources
PDF: https://help.zscaler.com/pdf/com/en/1527971.pdf

After [creating a data source](/uvm/creating-data-sources), you can manage it within a comprehensive list of all your data sources.
When managing data sources, you can perform the following actions:
- [Configure Auto-Scheduling](#auto-scheduling-settings)
- [Edit Data Sources](#editing)
- [Delete Data Sources](#deleting)
- [Deactivate Data Sources](#deactivating)
- [View Source Runs](#runs)
- [Map Source Data](#mapping)
- [Process Data Sources](#processing)
- [Rerun Last Execution](#rerunning)
- [View the Audit Logs](#auditing)
[]Source auto-scheduling coordinates the ingestion of multiple data sources so they run as a single process. Scheduling ensures that sources contributing to the same entity are processed at the same time, leading to more consistent and up-to-date data, and reducing the need for manual scheduling coordination.
Auto-scheduling is enabled by default. You can adjust the schedule to better align with your data availability or processing windows.
To configure auto-scheduling:
- Go to **Configure** > **Sources**.
-
Click the **More Actions** icon (![more actions icon in the sources page](/downloads/uvm/configure/sources/managing-data-sources/more%20actions%20icon.png)
).
The **Auto Scheduling Settings** window appears.
- Set the UTC hour at which all sources should run.
- Click **Save**.
All configured sources will run their ingestion processes simultaneously at the specified UTC time each day.
[]You can edit a data source to update its general details, retrieval details, scheduling, remediation detection settings, and suppression rules.
To edit a data source:
- Go to **Configure** > **Sources**.
-
Choose a data source using one of the following methods:
- Hover over the data source, and click the **Edit **icon.
- Select a data source from the list, and click **Edit **on the toolbar.
The **Edit Connector **page appears.
- Make the necessary changes to the data source.
- Click **Save**.
This action cannot be performed in bulk.
[]You can delete a data source when it is no longer required, such as when the associated vendor is no longer used by your organization.
To delete a data source:
- Go to **Configure** > **Sources**.
-
Choose one of the following deletion methods:
- To delete a single data source, hover over the source and click the **Delete **icon.
- To delete multiple data sources, select the sources from the list, and click **Delete **on the toolbar.
The **Delete data from source** window appears.
[See image.](#delete-data-from-source-window)
- Select a deletion option:
- **Keep the data source, delete the underlying data**: Delete the data only, leaving the data source configuration unchanged. This is useful during initial source setup if you want to fix errors without having to recreate the entire source from scratch. After applying the changes or fixes to the source, you can rerun the last execution to repopulate the source correctly.
- **Delete all**: Delete the data source along with all associated data.
-
Click **Delete**.
All data is permanently deleted from the system and cannot be restored.
[]![Warning message for deleting data from source with two deletion options](/downloads/uvm/configure/sources/managing-data-sources/ce00c36e-2506-4bcb-858d-ad83ae205762.png)
[]You can deactivate a data source to temporarily suspend data retrieval, allowing you to pause the process without losing historical data. This is useful during transitions, such as when migrating to a new security product, where you might need to interrupt the current data flow while preserving existing data records.
To deactivate a data source:
- Go to **Configure **> **Sources**.
-
Hover over the source, and click the **Edit** icon.
The data source editing page appears.
- Disable **Active** located to the right of the source's **Name** to deactivate the data source.
- Click **Save** to apply your change.
To deactivate multiple data sources:
- From the list of sources, select the data sources you want to deactivate.
- Click **Deactivate** on the toolbar.
[]You can monitor source runs to track execution timestamps and status updates, including success, cancellation, or failure. This is useful during troubleshooting, allowing you to identify and resolve issues with failed runs.
To view a data source's runs:
- Go to **Configure **> **Sources**.
-
Choose one of the following methods:
- Hover over the source, and click the **See Runs **icon.
- Select the data source from the list, and click **Runs **on the toolbar.
The <Source**> Runs **page appears.
- View the run for the data source.
To learn more, see [Tracking Source Runs](/uvm/tracking-source-runs).
[]You can view and edit the mapped connections of a data source.
To view mapping for a data source:
- Go to **Configure **> **Sources**.
-
Choose one of the following methods:
- Hover over the source, and click the **Map Data** icon.
- Select the data source from the list, and click **Map Data **on the toolbar.
The **Map <**Source**> **page appears.
- View the mapping for the data source.
[]You can process a source manually to bypass its regular scheduled processing and run the source immediately.
To process a data source manually:
- Go to **Configure** > **Sources**.
- Choose one of the following methods:
- Hover over the source, and click the **Process Now **icon.
- Select the data source from the list, and click **Process Now **on the toolbar.
-
In the window that appears, click **Process Now**.
[See image.](#dialog1)
Processing AnySource sources manually opens a file upload window. To learn more, see [Connecting AnySource](/uvm/connecting-anysource).
[]![image.png](/downloads/uvm/configure/sources/managing-data-sources/image.png)
[]You can rerun the latest data retrieval from a source to re-execute the previous run, maintaining the same run type (incremental or full refresh) to refresh the data. This is useful when implementing changes to the source settings or mapping to ensure that the changes are applied correctly.
To rerun the data source's last run manually:
- Go to **Configure **> **Sources**.
- Choose one of the following methods:
- Hover over the source, and click the **Rerun Last Execution **icon.
- Select the data source from the list, and click **Rerun Last Execution **on the toolbar.
- In the window that appears, click **Rerun**.
[]You can view the source's audit logs to track changes that were made to it.
- Go to **Configure **> **Sources**.
-
Click the source that you want to view.
The source setup page appears.
-
Click the **More **icon, and select **Audit Logs**.
A list of audit logs appears.
[See image.](#auditlogs)
[]![the more icon with the audit logs visible on the rapid7 vulnerabilities connector setup page](/downloads/uvm/configure/sources/managing-data-sources/audit%20logs.png)