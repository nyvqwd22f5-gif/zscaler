# Reports
Source: https://help.zscaler.com/zdx/reports

APIs for Zscaler Digital Experience (ZDX).

## `GET /active_geo`

Gets the list of all active geolocations for the time range specified. If not specified, the endpoint defaults to the last 2 hours. The state and city data is retrieved only for the US.

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
| parent geo id | query | string | No | The parent geolocation ID. |
| q | query | string | No | The search string used to support search by name. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |

## `GET /apps`

Lists all active applications configured for a tenant. The endpoint gets each application's ZDX Score (default for the previous 2 hours), most impacted location, and the total number of users impacted. To learn more, see [Monitoring the ZDX Dashboard](/zdx/monitoring-zdx-dashboard).

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation. The response contains the ZDX Score, most impacted location details, and total users impacted for each application. |  |
| 401 |  |  |
| 403 |  |  |

## `GET /apps/{appid}`

Gets the application's ZDX Score (for the previous 2 hours), most impacted locations, and the total number of users impacted. To learn more, see [About the ZDX Score](/zdx/about-zdx-score#user).

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
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

## `GET /apps/{appid}/metrics`

Gets the application's average Page Fetch Time metric trend. If the time range is not specified, the endpoint defaults to the previous 2 hours.

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
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

## `GET /apps/{appid}/score`

Gets the application's ZDX Score trend. If the time range is not specified, the endpoint defaults to the previous 2 hours.

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
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

## `GET /apps/{appid}/users`

Gets the list of all users and their devices that were used to access an application. The endpoint allows to get the list of users based on the score category (i.e., Poor, Okay, or Good), location, department, or geolocation. All users and their devices are returned if the criteria is not specified. If the time range is not specified, the endpoint defaults to the previous 2 hours.

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
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

## `GET /apps/{appid}/users/{userid}`

Gets user details including the device information, active geolocations, and Zscaler locations. If the time range is not specified, the endpoint defaults to the previous 2 hours.

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
| userid | path | string | Yes | The unique user ID assigned to the user. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 401 |  |  |
| 403 |  |  |

## `GET /devices`

Gets the list of all active devices and its basic details. All devices are returned if the criteria is not specified. The JSON must contain the user's ID and email address to associate the device to the user. If the time range is not specified, the endpoint defaults to the previous 2 hours.

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
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

## `GET /devices/{deviceid}`

Gets the device details including the device model information, tunnel type, network, and software details. The JSON must contain the user ID and email address to associate the device to a user. If the time range is not specified, the endpoint defaults to the previous 2 hours.

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 401 |  |  |
| 403 |  |  |

## `GET /devices/{deviceid}/apps`

Gets the list all active applications for a device. The endpoint gets the ZDX Score each application. If the time range is not specified, the endpoint defaults to the previous 2 hours.

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 401 |  |  |
| 403 |  |  |

## `GET /devices/{deviceid}/apps/{appid}`

Gets the application's ZDX Score trend for a device. If the time range is not specified, the endpoint defaults to the previous 2 hours.

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 401 |  |  |
| 403 |  |  |

## `GET /devices/{deviceid}/apps/{appid}/call-quality-metrics`

Gets the Call Quality metric trend for a device for a CQM application. If the time range is not specified, the endpoint defaults to the previous 2 hours.

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation. |  |
| 401 |  |  |
| 403 |  |  |

## `GET /devices/{deviceid}/apps/{appid}/cloudpath-probes`

Gets the list of all active Cloud Path probes on a device. If the time range is not specified, the default is the previous 2 hours.

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 401 |  |  |
| 403 |  |  |

## `GET /devices/{deviceid}/apps/{appid}/cloudpath-probes/{probeid}`

Gets the Cloud Path Probe's metric trend on a device for an application. For Cloud Path probes, you can access latency metrics for End to End, Client - Egress, Egress - Application, ZIA Service Edge- Egress, and ZIA Service Edge - Application. If not specified, it defaults to End to End latency. If the time range is not specified, the endpoint defaults to the previous 2 hours.

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
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

## `GET /devices/{deviceid}/apps/{appid}/cloudpath-probes/{probeid}/cloudpath`

Gets the Cloud Path hop data for an application on a specific device. Includes the summary data for the entire path like the total number of hops, packet loss, latency, and tunnel type (if available). It also includes a similar summary of data for each individual hop. If the time range is not specified, the endpoint defaults to the previous 2 hours.

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
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

## `GET /devices/{deviceid}/apps/{appid}/web-probes`

Gets the list of all active Web probes on a device. If the time range is not specified, the endpoint defaults to the previous 2 hours.

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 401 |  |  |
| 403 |  |  |

## `GET /devices/{deviceid}/apps/{appid}/web-probes/{probeid}`

Gets the Web probe's Page Fetch Time (PFT) on a device for an application. If the time range is not specified, the endpoint defaults to the previous 2 hours.

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
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

## `GET /devices/{deviceid}/events`

Gets the Events metrics trend for a device. If the time range is not specified, the endpoint defaults to the previous 2 hours. The event metrics include Zscaler, Hardware, Software and Network event changes.

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 |  |  |
| 401 |  |  |
| 403 |  |  |

## `GET /devices/{deviceid}/health-metrics`

Gets the health metrics trend for a device. If the time range is not specified, the endpoint defaults to the previous 2 hours. The health metrics include CPU, Memory, Disk I/O, Network I/O, Wi-Fi, Network Bandwidth, etc.

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation. |  |
| 401 |  |  |
| 403 |  |  |

## `GET /users`

Gets the list of all active users, their devices, active geolocations, and Zscaler locations. All active users, their devices, active geolocations, and Zscaler locations are returned if the criteria is not specified. If the time range is not specified, the endpoint defaults to the previous 2 hours.

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
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

## `GET /users/{userid}`

Gets user details including the device information, active geolocations, and Zscaler locations. If the time range is not specified, the endpoint defaults to the previous 2 hours.

**Tags:** Reports

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
| userid | path | string | Yes | The unique user ID assigned to the user. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 401 |  |  |
| 403 |  |  |
