# Administration
Source: https://help.zscaler.com/zdx/administration-0

APIs for Zscaler Digital Experience (ZDX).

## `GET /administration/departments`

Gets configured departments.

**Tags:** Administration

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
| Search | query | string | No | The search string used to support search by name or department ID. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 401 |  |  |
| 403 |  |  |

## `GET /administration/locations`

Gets Zscaler locations. All configured Zscaler locations are returned if the search filters is not specified.

**Tags:** Administration

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
|  |  |  | No |  |
|  |  |  | No |  |
| q | query | string | No | The search string used to support search by name or location ID. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation |  |
| 401 |  |  |
| 403 |  |  |
