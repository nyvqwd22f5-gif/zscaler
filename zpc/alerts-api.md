# Alerts
Source: https://help.zscaler.com/zpc/alerts-api

To access detailed ZPC API documentation, including references and use cases, refer to the [Zscaler Help Portal](https://help.zscaler.com/zpc/understanding-zpc-api).

## `GET /alerts/cloud`

Gets a list of cloud alerts for the specified criteria.

**Tags:** Alerts

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| limit | query | integer (int64) | No | Indicates the page size. If not provided, the default page size is 100. The maximum limit for page size is 100. |
| offset | query | integer (int64) | No | Specifies the page number. |
| created[start] | query | integer (int32) | No | The created starting date for the alert in epoch seconds. Zscaler recommends you are aware of the following:
- If start and end times are not specified, then alerts are retreived for the last 48 hours by default.
- If only the start time is specified, then alerts are retrieved for up to 48 hours from start time.
- If only the end time is specified, then alerts are retrieved from end time to 48 hours before.
- If both the created and updated start and end times are specified, then only the alerts within the specified time range are retrieved. |
| created[end] | query | integer (int32) | No | The created ending date for the alert in epoch seconds. Zscaler recommends you are aware of the following:
- If start and end times are not specified, then alerts are retreived for the last 48 hours by default.
- If only the start time is specified, then alerts are retrieved for up to 48 hours from start time.
- If only the end time is specified, then alerts are retrieved from end time to 48 hours before.
- If both the created and updated start and end times are specified, then only the alerts within the specified time range are retrieved. |
| updated[start] | query | integer (int32) | No | The updated starting date for the alert in epoch seconds. Zscaler recommends you are aware of the following:
- If neither start or end times are specified, then alerts are retreived for the next 48 hours by default.
- If only the start time is specified, then alerts are retrieved for the next 48 hours.
- If only the end time is specified, then only the alerts from the previous 48 hours are retrieved.
- If both the created and updated start and end times are specified, then only the alerts within the specified time range are retrieved. |
| updated[end] | query | integer (int32) | No | The updated ending date for the alert in epoch seconds. Zscaler recommends you are aware of the following:
- If neither start or end times are specified, then alerts are retreived for the next 48 hours by default.
- If only the start time is specified, then alerts are retrieved for the next 48 hours.
- If only the end time is specified, then only the alerts from the previous 48 hours are retrieved.
- If both the created and updated start and end times are specified, then only the alerts within the specified time range are retrieved. |
| cloud_account_type | query | array[string] | No | Indicates the cloud account type of the alert based on the specified filter. |
| business_units | query | array[string] | No | Filters the alert by business unit name based on the specified filter. |
| regions | query | array[string] | No | Filters the alerts based on the specified regions. |
| alert_status | query | array[string] | No | Filters alerts by the specified `AlertStatus` value. |
| risk_level | query | array[string] | No | Filters alerts by the specified `RiskLevel` value. |
| order_by | query | string | No | Orders the alerts by the specified `order_by` value. |
| fields | query | array[string] | No | Filters the alerts by the specified `fields` value. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 429 | Rate Limit Fail |  |
| 500 | Internal Server Error |  |

## `GET /alerts/iac`

Gets a list of IaC alerts for the specified criteria.

**Tags:** Alerts

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| limit | query | integer (int64) | No | Indicates the page size. If not provided, the default page size is 100. The maximum limit for page size is 100. |
| offset | query | integer (int64) | No | Specifies the page number. |
| created[start] | query | integer (int32) | No | The created starting date for the alert in epoch seconds. Zscaler recommends you are aware of the following:
- If neither start or end times are specified, then alerts are retreived for the next 48 hours by default.
- If only the start time is specified, then alerts are retrieved for the next 48 hours.
- If only the end time is specified, then only the alerts from the previous 48 hours are retrieved.
- If both the created and updated start and end times are specified, then only the alerts within the specified time range are retrieved. |
| created[end] | query | integer (int32) | No | The created ending date for the alert in epoch seconds. Zscaler recommends you are aware of the following:
- If neither start or end times are specified, then alerts are retreived for the next 48 hours by default.
- If only the start time is specified, then alerts are retrieved for the next 48 hours.
- If only the end time is specified, then only the alerts from the previous 48 hours are retrieved.
- If both the created and updated start and end times are specified, then only the alerts within the specified time range are retrieved. |
| updated[start] | query | integer (int32) | No | The updated starting date for the alert in epoch seconds. Zscaler recommends you are aware of the following:
- If neither start or end times are specified, then alerts are retreived for the next 48 hours by default.
- If only the start time is specified, then alerts are retrieved for the next 48 hours.
- If only the end time is specified, then only the alerts from the previous 48 hours are retrieved.
- If both the created and updated start and end times are specified, then only the alerts within the specified time range are retrieved. |
| updated[end] | query | integer (int32) | No | The updated ending date for the alert in epoch seconds. Zscaler recommends you are aware of the following:
- If neither start or end times are specified, then alerts are retreived for the next 48 hours by default.
- If only the start time is specified, then alerts are retrieved for the next 48 hours.
- If only the end time is specified, then only the alerts from the previous 48 hours are retrieved.
- If both the created and updated start and end times are specified, then only the alerts within the specified time range are retrieved. |
| order_by | query | string | No | Orders the alerts by the specified `order_by` value. |
| cloud_account_type | query | array[string] | No | Indicates the cloud account type of the alert based on the specified filter. |
| alert_status | query | array[string] | No | Filters alerts by the specified `alert_status` value. |
| risk_level | query | array[string] | No | Filter alerts by the specified `risk_Level` value. |
| fields | query | array[string] | No | Filters the alerts by the specified `fields` value. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK |  |
| 400 | Bad Request |  |
| 401 | Unauthorized |  |
| 403 | Forbidden |  |
| 429 | Rate Limit Fail |  |
| 500 | Internal Server Error |  |
