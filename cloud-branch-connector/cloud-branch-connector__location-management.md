# Location Management
Source: https://help.zscaler.com/cloud-branch-connector/location-management

## `GET /location`

Lists locations only, not sub-locations. When a location matches the given search parameter criteria only its parent location is included in the result set, not its sub-locations. To learn more, see [About Locations](/cloud-connector/about-locations).

**Tags:** Location Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| groupId | query | integer (int32) | No | Filter based on location group ID for a location. |
| search | query | string | No | The search string used to partially match against a location's name and port attributes. |
| state | query | string | No | Filter based on geographical state for a location. |
| sslScanEnabled | query | boolean | No | This parameter was deprecated and no longer has an effect on SSL policy. It remains supported in the API payload in order to maintain backwards compatibility with existing scripts, but it will be removed in the future.
Filter based on whether Enable SSL Scanning is enabled for a location. |
| xffEnabled | query | boolean | No | Filter based on whether Enforce XFF Forwarding is enabled for a location. |
| authRequired | query | boolean | No | Filter based on whether Enforce Authentication is enabled for a location. |
| bwEnforced | query | boolean | No | Filter based on whether Bandwith Control is enforced for a location. |
| partnerId | query | integer (int32) | No | Not applicable to Cloud & Branch Connector. |
| enforceAup | query | boolean | No | Filter based on whether Acceptable Use Policy (AUP) is enforced for a location. |
| enableFirewall | query | boolean | No | Filter based on whether firewall is enabled for a location. |
| locationType | query | string | No | Filter based on type of location. |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. The default size is 100, but the maximum size is 1000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | default response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `GET /location/lite`

Lists a subset of location information.

**Tags:** Location Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| includeSubLocations | query | boolean | No | If set to true, sub-locations are included in the response. |
| includeParentLocations | query | boolean | No | If set to true, parent locations (i.e., locations with sub-locations) are included in the response. |
| includeDefaultLocation | query | boolean | No | If set to true, default location is included in response. |
| search | query | string | No | The search string used to partially match against the location name and port attributes. |
| groupId | query | integer (int32) | No | Filter based on location group ID for a location. |
| partnerId | query | integer (int32) | No | Not applicable to Cloud & Branch Connector. |
| version | query | integer (int32) | No | Not applicable to Cloud & Branch Connector. |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. The default size is 100, but the maximum size is 1000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | default response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `GET /location/{id}`

Gets location by ID.

**Tags:** Location Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer (int32) | Yes | ID of location. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | default response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `GET /locationTemplate`

Lists location templates.

**Tags:** Location Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. The default size is 250. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | default response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `POST /locationTemplate`

Creates a location template.

**Tags:** Location Management
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | default response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `GET /locationTemplate/lite`

Lists a subset of location template information.

**Tags:** Location Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. The default size is 100. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | default response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `GET /locationTemplate/{id}`

Gets location template specified by location template ID.

**Tags:** Location Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer (int32) | Yes | Location template ID. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | default response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `DELETE /locationTemplate/{templateId}`

Deletes the location template specified by the location template ID.

**Tags:** Location Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| templateId | path | integer (int32) | Yes | ID of the location template. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | default response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `PUT /locationTemplate/{templateId}`

Updates the location template specified by the location template ID.

**Tags:** Location Management

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| templateId | path | integer (int32) | Yes | ID of the location template. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | default response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |
