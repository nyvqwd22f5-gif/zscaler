# Managing Queued Contracts
Source: https://help.zscaler.com/business-insights/managing-queued-contracts
PDF: https://help.zscaler.com/pdf/com/en/1506986.pdf

Whenever the uploaded contract file is not processed successfully, the status field displays **Error** on the [Processing Queue](/business-insights/processing-queue-contracts) page.
To understand and resolve the error with the uploaded file:
- Go to **Applications** > **All Contracts** > **Processing Queue**.
-
Locate the contract, and click the **Edit** icon.
The **Edit Upload** drawer appears.
- Depending on the error encountered by the Business Insights service while processing the file, perform the following troubleshooting steps:
-
If the error encountered is because the items in the contracts don't have the application linked to it, the **Application** column in the Contract Information table shows missing application linkage. Use the drop-down menu to link to the application. If the application is not listed in the drop-down menu, click **Create New Application Request** to submit a request to add the application to the list. The Business Insights team will contact you after adding the requested application.
[See image.](#link-app)
-
If the error encountered is because the Business Insights service is unable to parse any relevant metadata from the file, the Contract Information table shows no data. To resolve the error, reupload the contract file in the supported format. To learn more, see [Uploading Application Contracts](/business-insights/uploading-application-contracts).
[See image.](#fix-file)
[]![Edit Application Details](/downloads/business-insights/application-insights/application-settings/editing-queued-contracts/Business-Insights-Edit-Contract-Application-Linking.png)
[]![Contact Table](/downloads/business-insights/application-insights/application-settings/editing-queued-contracts/Business-Insights-Edit-Contract-No-Data.png)