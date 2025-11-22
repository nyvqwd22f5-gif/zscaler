# Admin Audit Logs
Source: https://help.zscaler.com/zia/admin-audit-logs

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `DELETE /auditlogEntryReport`

Cancels the request to create an audit log report.

**Tags:** Admin Audit Logs
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |

## `GET /auditlogEntryReport`

Gets the status of a request for an audit log report. After sending a POST request to `/auditlogEntryReport` to generate a report, you can continue to call GET `/auditlogEntryReport` to check whether the report has finished generating. Once the status is `COMPLETE`, you can send another GET request to `/auditlogEntryReport/download` to download the report as a CSV file.

**Tags:** Admin Audit Logs
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | TaskInfo |

## `POST /auditlogEntryReport`

Creates an audit log report for the specified time period and saves it as a CSV file. The report includes audit information for every call made to the cloud service API during the specified time period. Creating a new audit log report overwrites a previously-generated report.

**Tags:** Admin Audit Logs
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| request | body | AuditLogEntryRequest | No | Audit log entry request, which includes the following values:
- startTime: The timestamp, in epoch, of the admin's last login.
- endTime: The timestamp, in epoch, of the admin's last logout.
- actionTypes: The action performed by the admin in the Zscaler Admin Portal (i.e., Admin UI) or API. [Possible values for actionTypes](/zia/about-audit-logs#action).
- category: The location in the Zscaler Admin Portal (i.e., Admin UI) where the actionType was performed. [Possible values for category](/zia/about-audit-logs#category).
- subcategories: The area within a category where the actionType was performed. [Possible values for subcategories](/zia/about-audit-logs#sub).
- actionResult: The outcome (i.e., Failure or Success) of an actionType.
- actionInterface: The interface (i.e., Admin UI or API) where the actionType was performed.
- clientIP: The source IP address for the admin.
- adminName: The admin's login ID. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 204 | Successful Operation |  |

## `GET /auditlogEntryReport/download`

Downloads the most recently created audit log report. After a call to GET `/auditlogEntryReport` indicates that the report (CSV file) was generated, you can send a GET request to `/auditlogEntryReport/download` to download the file.

**Tags:** Admin Audit Logs
**Consumes:** application/json
**Produces:** text/csv
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |

## Models
### AuditLogEntryRequest
Audit log entry request
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| actionInterface | string | No | Interface for audit log entry |
| actionResult | string | No | Result for audit log entry |
| actionTypes | array[string] | No | Action type for audit log entry |
| adminName | string | No | Admin name for audit log entry |
| category | string | No | Category for audit log entry |
| clientIP | string | No | Client IP for audit log entry |
| endTime | integer (int64) | No | End time for audit log entry |
| objectName | string | No | Object name for audit log entry |
| page | integer (int32) | No |  |
| pageSize | integer (int32) | No |  |
| startTime | integer (int64) | No | Start time for audit log entry |
| subcategories | array[string] | No | Subcategories for audit log entry |
| targetOrgId | integer (int32) | No |  |
| traceId | string | No | A trace ID is generated and logged for transactions associated with ZIA API requests made via [Zscaler OneAPI](/oneapi/understanding-oneapi). The trace ID helps admins correlate API transactions with the OneAPI platform and you can use the trace ID for debugging purposes. |

### TaskInfo
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| errorCode | string | No |  |
| errorMessage | string | No | Error message |
| progressEndTime | integer (int64) | No | End time |
| progressItemsComplete | integer (int32) | No | Number of items processed |
| status | string | No | Status of running task |
