# Alerts
Source: https://help.zscaler.com/zdx/alerts-zdx-api

APIs for Zscaler Digital Experience (ZDX).

## `GET /alerts/historical`

Gets the list of alert history rules defined across an organization. All alert history rules are returned if the search filter is not specified. The default is set to the previous 2 hours. Alert history rules have an Ended On date. The Ended On date is used to pull alerts in conjunction with the provided filters. Cannot exceed the 14-day time range limit for alert rules.

**Tags:** Alerts

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 401 |  |  |
| 403 |  |  |

## `GET /alerts/ongoing`

Gets the list of ongoing alert rules across an organization. All ongoing alert rules are returned if the search filter is not specified. The endpoint defaults to the previous 2 hours. Ongoing alerts are alerts that don't have an Ended On date. The alert rule's Started On date is used in conjunction with the provided filters. Cannot exceed the 14-day time range limit for alert rules.

**Tags:** Alerts

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 401 |  |  |
| 403 |  |  |

## `GET /alerts/{alert_id}`

Gets the alert details including the impacted department, Zscaler locations, geolocation, and alert trigger.

**Tags:** Alerts

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| alert_id | path | string | Yes |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 401 |  |  |
| 403 |  |  |

## `GET /alerts/{alert_id}/affected_devices`

Gets the list of all affected devices associated with an alert rule in conjunction with provided filters (e.g., impacted department, locations, and geolocation) by using the Alert ID provided.

**Tags:** Alerts

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| alert_id | path | string | Yes |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 401 |  |  |
| 403 |  |  |
