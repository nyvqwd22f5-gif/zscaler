# Troubleshooting
Source: https://help.zscaler.com/zdx/troubleshooting

APIs for Zscaler Digital Experience (ZDX).

## `POST /analysis`

Start a ZDX Score analysis on a device for a specific application. The response contains an ID to identify the operation and can be used in subsequent endpoints that require it.

**Tags:** Troubleshooting
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 |  |  |
| 401 |  |  |
| 403 |  |  |

## `DELETE /analysis/{analysis_id}`

Stop the score analysis that is currently running.

**Tags:** Troubleshooting

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| analysis_id | path | string | Yes | The analysis ID. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 |  |  |
| 401 |  |  |
| 403 |  |  |

## `GET /analysis/{analysis_id}`

Get the status of the score analysis (e.g., progress or results).

**Tags:** Troubleshooting

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| analysis_id | path | string | Yes | The analysis ID. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 |  |  |
| 401 |  |  |
| 403 |  |  |

## `GET /devices/{deviceid}/deeptraces`

Get a list of deep traces. The response contains an ID to identify the operation and can be used in subsequent endpoints that require access to data.

**Tags:** Troubleshooting

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Lists the deep traces with their status. |  |

## `POST /devices/{deviceid}/deeptraces`

Start a deep trace on a device. Limited to 1 active session on a device at any time. There is a maximum of 15 active sessions at any point of time across all devices (includes sessions initiated from UI).

**Tags:** Troubleshooting

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Deep trace request accepted. |  |
| 401 |  |  |
| 403 |  |  |

## `DELETE /devices/{deviceid}/deeptraces/{trace_id}`

Stop the deep trace session that is currently running.

**Tags:** Troubleshooting

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
| trace_id | path | string | Yes | trace id |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successfully deleted the deep trace request. |  |
| 401 |  |  |
| 403 |  |  |

## `GET /devices/{deviceid}/deeptraces/{trace_id}`

Get the deep trace's status.

**Tags:** Troubleshooting

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
| trace_id | path | string | Yes | trace id |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 |  |  |
| 401 |  |  |
| 403 |  |  |

## `GET /devices/{deviceid}/deeptraces/{trace_id}/cloudpath`

Get a list of Cloud Paths from the deep trace session.

**Tags:** Troubleshooting

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
| trace_id | path | string | Yes | The deep trace ID. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 |  |  |
| 401 |  |  |
| 403 |  |  |

## `GET /devices/{deviceid}/deeptraces/{trace_id}/cloudpath-metrics`

Get the Cloud Path metrics (e.g., latency, packet drops, etc.) from the deep trace session.

**Tags:** Troubleshooting

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
| trace_id | path | string | Yes | The deep trace ID. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 |  |  |
| 401 |  |  |
| 403 |  |  |

## `GET /devices/{deviceid}/deeptraces/{trace_id}/events`

Get the events metrics trend for a device. The event metrics include Zscaler, Hardware, Software and Network event changes.

**Tags:** Troubleshooting

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
| trace_id | path | string | Yes | trace id |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 |  |  |
| 401 |  |  |
| 403 |  |  |

## `GET /devices/{deviceid}/deeptraces/{trace_id}/health-metrics`

Get the device health metrics from a deep trace session.

**Tags:** Troubleshooting

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
| trace_id | path | string | Yes | trace id |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 |  |  |
| 401 |  |  |
| 403 |  |  |

## `GET /devices/{deviceid}/deeptraces/{trace_id}/top-processes`

Get the top processes from the deep tracing session.

**Tags:** Troubleshooting

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
| trace_id | path | string | Yes | trace id |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 |  |  |
| 401 |  |  |
| 403 |  |  |

## `GET /devices/{deviceid}/deeptraces/{trace_id}/webprobe-metrics`

Get the Web probe metrics from the deep trace session.

**Tags:** Troubleshooting

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
| trace_id | path | string | Yes | trace id |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 |  |  |
| 401 |  |  |
| 403 |  |  |
