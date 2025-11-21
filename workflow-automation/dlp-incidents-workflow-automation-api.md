# DLP Incidents
Source: https://help.zscaler.com/workflow-automation/dlp-incidents-workflow-automation-api

Zscaler Workflow Automation - DLP Incident Management API.

## `POST /dlp/v1/incidents/search`

Filters DLP incidents based on the given time range and the field values. The supported field values are:
- Severity
- Priority
- Transaction ID
- Status
- Source
- Source DLP Type
- Labels
- Incident Group
- Engine
The supported time range values are:
- Start date and time
- End date and time

**Tags:** DLP Incidents

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer | No | Specifies the page number of the incident in a multi-paginated response. This field is not required if page ID field is used. |
| pageSize | query | integer | No | Specifies the page size (i.e., number of incidents per page). The maximum page size is 100. |
| pageId | query | string (string) | No | Specifies the page ID of the incident in a multi-paginated response. It is a unique identifier returned in the first search request. The page ID can be used instead of the page number in subsequent search requests for faster and more efficient results. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful operation |  |
| 400 | Bad request |  |
| 401 | Authorization failure |  |
| 500 | Failed to process the request |  |

## `GET /dlp/v1/incidents/transactions/{transactionId}`

Gets the list of all DLP incidents associated with the transaction ID. A transaction ID can contain one or more DLP incidents.

**Tags:** DLP Incidents

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| transactionId | path | string (string) | Yes | The ID of the transaction that violated the DLP rules. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful operation |  |
| 401 | Authorization failure |  |
| 404 | Resource does not exist |  |
| 500 | Failed to process the request |  |

## `DELETE /dlp/v1/incidents/{dlpIncidentId}`

Deletes the DLP incident for the specified incident ID.

**Tags:** DLP Incidents

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dlpIncidentId | path | string (string) | Yes | The ID of the incident. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful operation |  |
| 401 | Authorization failure |  |
| 404 | Resource does not exist |  |

## `GET /dlp/v1/incidents/{dlpIncidentId}`

Gets the DLP incident details based on the incident ID.

**Tags:** DLP Incidents

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dlpIncidentId | path | string (string) | Yes | The ID of the incident. |
| fields | query | array[string] | No | The fields associated with the DLP incident. For example, `sourceActions`, `contentInfo`, `status`, `resolution`, etc. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful operation |  |
| 401 | Authorization failure |  |
| 404 | Resource does not exist |  |
| 500 | Failed to process the request |  |

## `GET /dlp/v1/incidents/{dlpIncidentId}/change-history`

Gets the details of updates made to an incident based on the given ID and timeline.

**Tags:** DLP Incidents

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dlpIncidentId | path | string (string) | Yes | The ID of the incident. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful operation |  |
| 401 | Authorization failure |  |
| 404 | Resource does not exist |  |
| 500 | Failed to process the request |  |

## `POST /dlp/v1/incidents/{dlpIncidentId}/close`

Updates the status of the incident to resolved and closes the incident with a resolution label and a resolution code.

**Tags:** DLP Incidents

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dlpIncidentId | path | string (string) | Yes | The ID of the incident. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful operation |  |
| 400 | Bad request |  |
| 401 | Authorization failure |  |
| 404 | Resource does not exist |  |

## `GET /dlp/v1/incidents/{dlpIncidentId}/evidence`

Gets the evidence URL of the incident. The evidence link can be used to view and download the XML file with the actual data that triggered the incident.

**Tags:** DLP Incidents

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dlpIncidentId | path | string (string) | Yes | The ID of the incident for which evidence URL is fetched. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful operation |  |
| 401 | Authorization failure |  |
| 404 | Resource does not exist |  |

## `POST /dlp/v1/incidents/{dlpIncidentId}/incident-groups/search`

Filters a list of DLP incident groups to which the specified incident ID belongs.

**Tags:** DLP Incidents

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dlpIncidentId | path | string (string) | Yes | The ID of the incident. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful operation |  |
| 401 | Authorization failure |  |
| 404 | Resource does not exist |  |
| 500 | Failed to process the request |  |

## `POST /dlp/v1/incidents/{dlpIncidentId}/labels`

Assign lables (a label name and it's associated value) to DLP incidents.

**Tags:** DLP Incidents

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dlpIncidentId | path | string (string) | Yes | The ID of DLP incident to which the label is assigned. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful operation |  |
| 400 | Bad request |  |
| 401 | Authorization failure |  |
| 404 | Resource does not exist |  |

## `POST /dlp/v1/incidents/{dlpIncidentId}/notes`

Adds notes to the incident during updates or status changes.

**Tags:** DLP Incidents

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dlpIncidentId | path | string (string) | Yes | The ID of the incident for which the note is added. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful operation |  |
| 400 | Bad request |  |
| 401 | Authorization failure |  |
| 404 | Resource does not exist |  |

## `GET /dlp/v1/incidents/{dlpIncidentId}/tickets`

Gets the information of the ticket generated for the incident. For example, ticket type, ticket ID, ticket status, etc.

**Tags:** DLP Incidents

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dlpIncidentId | path | string (string) | Yes | The ID of the incident. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful operation |  |
| 401 | Authorization failure |  |
| 404 | Resource does not exist |  |
| 500 | Failed to process the request |  |

## `GET /dlp/v1/incidents/{dlpIncidentId}/triggers`

Downloads the actual data that triggered the incident.

**Tags:** DLP Incidents

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| dlpIncidentId | path | string (string) | Yes | The ID of the incident for which the trigger data is downloaded. |
| fetchTriggerContext | query | boolean | No | (Optional) Specifies whether to download the complete incident trigger data, including the prefix and suffix information. Set this field to `true` to fetch the prefix and suffix data.The default value is `false`. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful operation |  |
| 401 | Authorization failure |  |
| 404 | Resource does not exist |  |
