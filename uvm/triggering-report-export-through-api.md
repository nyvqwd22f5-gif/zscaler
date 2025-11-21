# Triggering Report Export Through an API
Source: https://help.zscaler.com/uvm/triggering-report-export-through-api
PDF: https://help.zscaler.com/pdf/com/en/1527711.pdf

After [creating a report](/uvm/creating-reports), you can trigger it to be exported programmatically using the Reporting API. For details on additional methods for exporting reports, see [Manually Exporting Reports](/uvm/manually-exporting-reports) and [Scheduling Reports to Export](/uvm/scheduling-reports-export).
The Reporting API is a GraphQL-based interface that enables you to export data from the platform to an AWS S3 bucket, or to retrieve a downloadable link to the report data. This article provides a step-by-step guide to using the Reporting API, including example requests for each endpoint.
Prerequisites
To get started with the Reporting API, you first need to define the data you want to export by creating a new report or using an existing report. In addition to defining the data for export, you need to contact your platform representative or support team to obtain API credentials (i.e., a client ID and client secret).
- [Creating a Report](#creating-report)
- [Obtaining Client Credentials](#obtaining-client-creds)
[]There are two methods available for retrieving the exported data:
- Exporting the data to your S3 bucket using the [AWS S3 retrieval method](/uvm/anysource-aws-s3-method).
- Getting a downloadable link to report data.
The steps for using the Reporting API vary slightly depending on the method you choose.
To create a report:
- Go to **Explore** > **Reports**.
- Click **New **to create a new report, or hover over an existing report and click the **Edit** icon.
- Set the report’s **Viewers** access and **Editors** access to **Public**. Only public reports can be accessed through the Reporting API.
- Configure the report to include the data you want to export.
- Click **Save** to apply your changes.
Configuring AWS S3 Export Settings
If you're exporting the report to an S3 bucket, you need to configure the destination settings of the exported report.
To configure the report's destination settings:
-
Click the **Schedule Export** icon located at the top right of the report.
[See image.](#schedule-report-icon)
- In the **Schedule Export Details** window:
-
**Export Format**: Select the format for the exported report.
If you request the report using the pre-signed URL, the scheduling configuration is ignored, and the report is generated in the default CSV format.
- **Delivery Method**: Select **S3 - AWS S3**.
-
**AWS S3 Details**: Enter your connection credentials and destination path.
The integration uses role-based authentication. To learn more, see [Connecting AnySource Using AWS S3](/uvm/connecting-anysource-using-aws-s3#create-a-role-for-the-platform).
- **Frequency and Time**: Set how often** **and** **when the report should run.
-
**Active**: Enable if you want the export to run on a schedule.
If you prefer to run the export manually, you can skip the scheduling settings and leave the **Active** toggle disabled.
- Click **Save** to apply the schedule settings.
[]![Report's Schedule Export icon on the top right](/downloads/uvm/explore/reports/reporting-api/eefb6982-ac52-4c7f-b48e-bedfa99730e3.png)
[]The Reporting API uses token-based authentication with client credentials. To authenticate API requests, you must first obtain client credentials (client ID and client secret) from your platform representative or support team.
Using the API
After completing the prerequisites, you can begin using the Reporting API. Start by authenticating your application—use the client ID and client secret you obtained earlier to request an access token. When authenticated, you can submit API requests to initiate a report and poll for its status.
- [Generating a Token](#generating-token)
- [Making the API Request](#making-request)
[]Using your client ID and client secret, access the `oauth2/token` endpoint to generate a token. The token is valid for one hour only.
Insert the following details in the script below:
- `URL`
- For US: `https://auth.us01.app.avalor.io/oauth2/token`
- For EU: `https://auth.eu.app.avalor.io/oauth2/token`
- `client ID`
- `client secret`
To generate a token, run the following command:
curl --location '<URL>' \
--header 'accept: application/json' \
--header 'content-type: application/x-www-form-urlencoded' \
--data-urlencode 'grant_type=client_credentials' \
--data-urlencode 'client_id=<client ID>' \
--data-urlencode 'client_secret=<client secret>'
[]This API uses GraphQL as its query language to execute requests and retrieve data.
To use the API, review and prepare the following details:
- **Required Headers**: Each request must include the following headers:
- **Authorization**: The access token obtained in the Generating a Token step.
- **accountId**: Your account ID found in the URL of your platform instance (i.e., `https://app.io/``<Account ID>``/platform`).
- **Report ID**: The report ID from the report editing page URL (i.e., `.../explore/reports/edit/``<Report ID>`).
- **GraphQL API Endpoint**:
- For US: `https://api.us01.app.avalor.io/api/graphql`
- For EU: `https://api.eu.app.avalor.io/api/graphql`
API Endpoints
The following API endpoints allow you to interact with the report processing system. Use these endpoints to initiate report processing, check the status of a report, and optionally retrieve a downloadable link to the report.
- [processReport](#processReport)
- [getReportRunStatus](#getReportRunStatus)
[]Run a report by providing a report ID.
Insert the following details in the script below:
- `URL`
- For US: `https://api.us01.app.avalor.io/api/graphql`
- For EU: `https://api.eu.app.avalor.io/api/graphql`
- `account ID`
- `bearer token`
- `report ID`
curl --location '<URL>' \\
--header 'Content-Type: application/json' \\
--header 'accountId: <Account ID>' \\
--header 'graphqlname: processReport' \\
--header 'Authorization: Bearer <Bearer Token>' \\
--data '{"query":"mutation ($id: String!) {processReport(id:$id, isPresignedUrl: true)}","variables":{"id":"<Report ID>"}}'
The `isPresignedUrl` parameter is only required if you want to generate a downloadable link for the report. If you configured the report to export to an S3 bucket, you can omit this parameter. The report that is generated with this method is exported in the format configured in the report scheduling settings.
Response fields include the `runId` of the execution to be used in the `getReportRunStatus` endpoint.
Retrieve the status of the specific report run. If you include the `isPresignedUrl` parameter, this endpoint also returns the downloadable link for the report data.
[]Insert the following details in the script below:
- `URL`
- For US: `https://api.us01.app.avalor.io/api/graphql`
- For EU: `https://api.eu.app.avalor.io/api/graphql`
- `account ID`
- `bearer token`
- `report ID`
- `run ID`: Found in the response to the `processReport` request.
curl --location '<URL>' \
--header 'Content-Type: application/json' \
--header 'accountId: <Account ID>' \
--header 'graphqlname: getReportRunStatus' \
--header 'Authorization: Bearer <Bearer Token>' \
--data '{"query":"query ($reportId: String, $runId: String) { getReportRunStatus(reportId: $reportId, runId: $runId) }","variables":{"reportId":"<report ID>", "runId":"<Run ID>"}}'
Response fields include:
- The current `status` of the report run (e.g., **Running,** **Completed**, **Failed**).
- If the report was exported to an S3 bucket, the `resultFilePath` field is returned with the S3 path where the file was saved, including the file name.
- If the `isPresignedUrl` was included in the `processReport` request, the `presignedUrl` field returns the downloadable link of the report.