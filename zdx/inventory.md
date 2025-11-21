# Inventory
Source: https://help.zscaler.com/zdx/inventory

APIs for Zscaler Digital Experience (ZDX).

## `GET /inventory/software`

Gets the current overview about your organization's distribution of software across all users (e.g., software names, the number of users using a specific model, and the software vendor).

**Tags:** Inventory

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Software Inventory List |  |
| 401 |  |  |
| 403 |  |  |

## `GET /inventory/softwares/{software_key}`

Gets the list of all users and devices for the given software name and version.

**Tags:** Inventory

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| software_key | path | string | Yes |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Software User List |  |
| 401 |  |  |
| 403 |  |  |
