# Time Intervals
Source: https://help.zscaler.com/zia/time-intervals

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /timeIntervals`

Retrieves a list of all configured time intervals. To learn more, see [About Time Intervals](/zia/about-time-intervals).

**Tags:** Time Intervals
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | Search for a configured time interval |
| page | query | integer | No | Set the page number of the response |
| pageSize | query | integer | No | Set the size of the response |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[TimeInterval] |

## `POST /timeIntervals`

Adds a new time interval. To learn more, see [Defining Time Intervals](/zia/defining-time-intervals).

**Tags:** Time Intervals
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | TimeInterval | No | Information about the defined time interval |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | TimeInterval |

## `DELETE /timeIntervals/{Id}`

Deletes a time interval based on the specified ID

**Tags:** Time Intervals
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| Id | path | integer | Yes | Unique identifier for the time interval |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /timeIntervals/{Id}`

Retrieves the configured time interval based on the specified ID

**Tags:** Time Intervals
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| Id | path | integer | Yes | Unique identifier for the time interval |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | TimeInterval |

## `PUT /timeIntervals/{Id}`

Updates the time interval based on the specified ID

**Tags:** Time Intervals
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| Id | path | integer | Yes | Unique identifier for the time interval |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## Models
### TimeInterval
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| daysOfWeek | array[string] | No | Specifies which days of the week apply to the time interval. If set to EVERYDAY, all the days of the week are chosen. |
| endTime | integer (int32) | No | The time interval end time |
| id | integer (int32) | No | System-generated identifier for the time interval |
| name | string | No | Name to identify the time interval |
| startTime | integer (int32) | No | The time interval start time |
