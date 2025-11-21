# Event Logs
Source: https://help.zscaler.com/zia/event-logs

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `DELETE /eventlogEntryReport`

Cancels the request to generate an event log report.

**Tags:** Event Logs
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /eventlogEntryReport`

Gets the status of the request to generate an event log report. Following a request to generate a report via the POST `/eventlogEntryReport` endpoint, you can call GET `/eventlogEntryReport` to check the current status of report generation. If the status is `COMPLETE`, you can send a GET request to `/eventlogEntryReport/download` to download the report as a CSV file.

**Tags:** Event Logs
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | TaskInfo |

## `POST /eventlogEntryReport`

Creates an event log report for the specified time period and saves it as a CSV file. The report includes event log information for every call made to the ZIA API during the specified time period. Creating a new event log report overwrites the previously-generated report.

**Tags:** Event Logs
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| request | body | EventLogEntryRequest | No | Event log report request, which includes the following information:
- startTime: The start time in the time range used to generate the event log report.
- endTime: The end time in the time range used to generate the event log report.
- category: Filters the list based on the category for which the events were recorded. [Possible values for category](/zia/about-event-logs).
- subcategories: Filters the list based on areas within a category where the events were recorded. [Possible values for sub-category](/zia/about-event-logs).
- actionResult: Filters the list based on the outcome (i.e., Failure or Success) of the events recorded.
- message: The search string used to match against the event log message.
- errorCode: The search string used to match against the error code in event log entries.
- statusCode: The search string used to match against the status code in event log entries. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /eventlogEntryReport/download`

Downloads the most recently generated event log report. Calling this endpoint downloads the file only if the report generation status is `COMPLETE`. Use the GET `/eventlogEntryReport` endpoint to verify the status before calling this endpoint for downloading the file.

**Tags:** Event Logs
**Consumes:** application/json
**Produces:** text/csv
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## Models
### EventLogEntryRequest
Event log report request
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| actionResult | string | No | Filters the list based on the outcome of the events recorded |
| category | string | No | Filters the list based on the category of event log entries |
| endTime | integer (int64) | No | End time for event log entry |
| errorCode | string | No | The search string used to match against the error code in event log entries |
| message | string | No | The search string used to match against the event log message |
| page | integer (int32) | No | Specifies the page offset |
| pageSize | integer (int32) | No | Specifies the page size |
| startTime | integer (int64) | No | Start time for event log entry |
| statusCode | string | No | The search string used to match against the status code in event log entries |
| subcategories | array[string] | No | Filters the list based on the subcategories within a category of event log entries |

### TaskInfo
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| errorCode | string | No |  |
| errorMessage | string | No | Error message |
| progressEndTime | integer (int64) | No | End time |
| progressItemsComplete | integer (int32) | No | Number of items processed |
| status | string | No | Status of running task |
