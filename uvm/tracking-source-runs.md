# Tracking Source Runs
Source: https://help.zscaler.com/uvm/tracking-source-runs
PDF: https://help.zscaler.com/pdf/com/en/1527671.pdf

When connecting a data source to ingest data into your account, you can schedule automatic full runs and incremental runs, as well as process data manually. To monitor the source's run status, track execution, and troubleshoot errors, you can view the data source run history on the [See Runs page](https://help.zscaler.com/uvm/managing-data-sources#runs).
Viewing Source Runs
You can view a data source's runs from Configure > Sources:
- Hover over the source, and click the **See Runs **icon.
- From the list of sources, select the data source and click **Runs **on the top toolbar.
The **Connector Runs **page appears.
Viewing Run Details
Each entry in the source's run history corresponds to a single run and includes its details.
![758bc336-25f5-42af-b498-328ff7035774.png](/downloads/uvm/configure/sources/tracking-source-runs/758bc336-25f5-42af-b498-328ff7035774.png)
The Runs page includes the following information:
- **Status**: The status column displays the outcome of each run:
- **Completed**: The run successfully completed without authentication or data ingestion issues.
- **Canceled**: The run was intentionally stopped by the user.
- **Failed**: The run encountered an error or issue that prevented it from completing successfully.
- **ID**: A unique identifier for the run that can be used for reference when troubleshooting run failures.
- **Category**: The run's category displays the processing type, indicating the level of processing applied to the ingested data:
- **Map and Aggregate**: The data has undergone unification processes, resulting in a standardized and aggregated format.
- **Map**: The data has not been unified and is presented in its original, raw format.
- **N/A**: This value is displayed for cancelled or failed runs, where no processing has occurred.
- **Data Retrieval Type**: The method used to retrieve data:
- **Full**: The entire dataset is retrieved from the source.
- **Incremental**: Only new or updated data is retrieved from the source.
- **Start Time **and **End Time**: The timestamps when the run started and ended. This information can reveal potential issues with data ingestion and assist during troubleshooting.
Validating Completed Runs
When a run is successful, the Status column displays the Completed status. For additional verification that the run has completed, expand the row to view additional run details and ensure they align with the file you intended to ingest.
[See image.](#completed-run)
Files Details include the following information:
- **File Reader**: The ingested file format.
- **File Size**: The size of the ingested file in megabytes.
- **Number of Files**: The number of files ingested in the run.
- **Total Number of Rows**: The total number of rows ingested.
[]![blobid0.png](/downloads/uvm/configure/sources/tracking-source-runs/blobid0.png)
Troubleshooting Failed Runs
When a run fails, the Status column displays the Failed status. To troubleshoot the issue, expand the row to view the error that occurred. The error appears along with a brief description, including any relevant error codes or messages. This information can be used to identify potential solutions.
[See image.](#failed-run)
Common Errors
Common errors you might encounter when troubleshooting failed runs include:
- [Invalid Credentials](#invalid-creds)
- [Permissions Denied](#permissions-denied)
- [Unknown Error](#unknown-error)
- [Internal Error](#internal-error)
[]![d9b3563c-e63a-4942-86a5-345bf0cd4743.png](/downloads/uvm/configure/sources/tracking-source-runs/d9b3563c-e63a-4942-86a5-345bf0cd4743.png)
[]Error: A data retrieval error due to invalid or missing authentication credentials.
Action: Verify the credentials provided in the data source authentication and ensure they are correct.
[]Error: A data retrieval error due to missing permissions.
Action: Verify the authorization permissions associated with the user provided for authentication and ensure they have the appropriate access rights.
[]If the error is listed as Unknown, the system was unable to categorize the error. In this case, the error details won't provide additional information for troubleshooting. As a first step in resolving unknown errors, verify that all system configurations and settings are correct.
If you are still unable to resolve the issue on your own, contact Zscaler Support for further assistance.
[]Internal errors are continuously being monitored by Zscaler's engineering teams. As a first step in resolving internal errors, try running your source again.
If the issue does not resolve itself, contact Zscaler Support for further assistance.