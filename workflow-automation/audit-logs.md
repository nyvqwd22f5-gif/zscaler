# Audit Logs
Source: https://help.zscaler.com/workflow-automation/audit-logs

Zscaler Workflow Automation - DLP Incident Management API.

## `POST /dlp/v1/customer/audit`

Filters audit logs based on the specified time period and field values. The result includes audit information for every action made by the admins in the Workflow Automation Admin Portal and the actions made through APIs. The supported field values are:
- Action
- Resource
- Admin
- Module
The supported time range values are:
- Start date and time
- End date and time

**Tags:** Audit Logs

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer | No | Specifies the page number of the incident in a multi-paginated response. This field is not required if page ID field is used. |
| pageSize | query | integer | No | Specifies the page size (i.e., number of incidents per page). |
| pageId | query | string (string) | No | Specifies the page ID of the incident in a multi-paginated response. It is a unique identifier returned in the first search request. The page ID can be used instead of the page number in subsequent search requests for faster and more efficient results. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful operation |  |
| 400 | Bad request |  |
| 401 | Authorization failure |  |
| 500 | Failed to process the request |  |
