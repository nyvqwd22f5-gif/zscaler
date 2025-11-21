# Device Groups
Source: https://help.zscaler.com/zia/device-groups

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /deviceGroups`

Gets a list of device groups.

**Tags:** Device Groups
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| includeDeviceInfo | query | boolean | No | Include or exclude device information. |
| includePseudoGroups | query | boolean | No | Include or exclude Zscaler Client Connector and Cloud Browser Isolation-related device groups. |
| includeIOTGroups | query | boolean | No | Include or exclude IoT device groups. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[DeviceGroup] |

## `GET /deviceGroups/devices`

Gets a list of devices. Any given search parameters are applied during device search. Search parameters are based on device name, model, owner, OS type, and OS version. The devices listed can also be restricted to return information only for ones belonging to specific users.

**Tags:** Device Groups
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| name | query | string | No | The device group name. |
| model | query | string | No | The device models. |
| owner | query | string | No | The device owners. |
| osType | query | string | No | The device's operating system. |
| osVersion | query | string | No | The device's operating system version. |
| deviceGroupId | query | integer | No | The unique identifier for the device group. |
| userIds | query | array | No | Used to list devices for specific users. |
| search_all | query | string | No | Used to match against all device attribute information. |
| includeAll | query | boolean | No | Used to include or exclude Cloud Browser Isolation devices. |
| page | query | integer | No | Specifies the page offset. |
| pageSize | query | integer | No | Specifies the page size. The default size is 100, but the maximum size is 1000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[Device] |

## `GET /deviceGroups/devices/lite`

Gets a list of devices that includes device ID, name, and owner name. Any given search parameters are applied during device search. Search parameters are based on device or user name and owner. The devices listed can also be restricted to return information only for ones belonging to specific users.

**Tags:** Device Groups
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| name | query | string | No | The device group name. |
| userIds | query | array | No | Used to list devices for specific users. |
| includeAll | query | boolean | No | Used to include or exclude Cloud Browser Isolation devices. |
| page | query | integer | No | Specifies the page offset. |
| pageSize | query | integer | No | Specifies the page size. The default size is 100, but the maximum size is 1000. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[Device] |

## Models
### Device
Device information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| description | string | No | The device's description. |
| deviceGroupType | string | No | The device group type. |
| deviceModel | string | No | The device model. |
| hostName | string | No | The hostname of the device. |
| id | integer (int32) | No | The unique identifier for the device. |
| name | string | No | The device name. |
| osType | string | No | The operating system (OS). |
| osVersion | string | No | The operating system version. |
| ownerName | string | No | The device owner's user name. |
| ownerUserId | integer (int32) | No | The unique identifier of the device owner (i.e., user). |

### DeviceGroup
Device group information.
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| description | string | No | The device group's description. |
| deviceCount | integer (int32) | No | The number of devices within the group. |
| groupType | string | No | The device group type. |
| id | integer (int32) | No | The unique identifer for the device group. |
| name | string | No | The device group name. |
| osType | string | No | The operating system (OS). |
| predefined | boolean | No | Indicates whether this is a predefined device group. If this value is set to true, the group is predefined. |
