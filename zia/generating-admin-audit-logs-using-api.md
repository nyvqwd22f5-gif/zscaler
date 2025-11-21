# Generating Admin Audit Logs Using API
Source: https://help.zscaler.com/zia/generating-admin-audit-logs-using-api
PDF: https://help.zscaler.com/pdf/com/en/1400431.pdf

Admin audit logs are stored for the last 6 months and you can download reports for up to 31 days or a maximum of 1,000 records at a time.
To generate and export a CSV-formatted admin audit log report via the API:
- Generate an audit log report by sending a POST request to `/auditlogEntryReport`, where the request body specifies:
- `startTime`: The timestamp, in epoch, of the admin's last login.
- `endTime`: The timestamp, in epoch, of the admin's last logout.
For example, in Python:
payload = {
"startTime":1493967600000,
"endTime":1496645999999
}
The request body can also include the following attributes:
- `actionTypes`: The action performed by the admin in the ZIA Admin Portal (i.e., Admin UI) or API. [Possible values for actionTypes](/zia/about-audit-logs#action).
- `category`: The location in the ZIA Admin Portal (i.e., Admin UI) where the `actionType` was performed. [Possible values for category](/zia/about-audit-logs#category).
- `subcategories`: The area within a category where the `actionType` was performed. [Possible values for subcategories](/zia/about-audit-logs#sub).
- `actionResult`: The outcome (i.e., Failure or Success) of an `actionType`.
- `actionInterface`: The interface (i.e., Admin UI or API) where the `actionType` was performed.
- `clientIP`: The source IP address for the admin.
- `adminName`: The admin's login ID.
- `traceId`: A trace ID is generated and logged for transactions associated with ZIA API requests made via [Zscaler OneAPI](/oneapi/understanding-oneapi). The trace ID helps admins correlate API transactions with the OneAPI platform and you can use the trace ID for debugging purposes.
Generating a new report overwrites a previously-generated report.
- When the report has generated, you can export it by sending a GET request to `/auditlogEntryReport/download`.
The response is formatted according to the time zone configured under **Administration **> **My Profile** within the ZIA Admin Portal. To learn more, see [Customizing Your Admin Account Settings](/zia/customizing-your-admin-account-settings).
To check whether the report has finished generating, send a GET request to `/auditlogEntryReport`. You can also cancel a POST request to generate a report by sending a DELETE request to `/auditlogEntryReport`.
To learn more about each endpoint, see [API Reference](/zia/admin-audit-logs).