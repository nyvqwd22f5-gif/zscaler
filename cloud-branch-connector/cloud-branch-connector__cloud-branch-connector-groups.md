# Cloud & Branch Connector Groups
Source: https://help.zscaler.com/cloud-branch-connector/cloud-branch-connector-groups

## `GET /ecInstance/lite`

Lists a subset of Cloud & Branch Connector instance information.

**Tags:** Cloud & Branch Connector Groups
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `DELETE /ecVm/uuid/{vmInstanceId}`

Deletes a VM based on the provided Cloud or Branch Connector native public cloud instance ID.

**Tags:** Cloud & Branch Connector Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| vmInstanceId | path | string | Yes | The ID of the VM native public cloud instance. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `GET /ecVm/uuid/{vmInstanceId}`

Retrieves details about a VM based on the provided Cloud or Branch Connector native public cloud instance ID.

**Tags:** Cloud & Branch Connector Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| vmInstanceId | path | string | Yes | The ID of the VM native public cloud instance. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `GET /ecgroup`

Lists Cloud & Branch Connector groups.

**Tags:** Cloud & Branch Connector Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. The default size is 250. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `GET /ecgroup/lite`

Lists a subset of Cloud & Branch Connector group information.

**Tags:** Cloud & Branch Connector Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. The default size is 20. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `DELETE /ecgroup/{ecgroupId}/vm/{vmId}`

Deletes a VM specified by Cloud or Branch Connector group ID and VM ID.

**Tags:** Cloud & Branch Connector Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ecgroupId | path | integer (int32) | Yes | Cloud or Branch Connector group ID. |
| vmId | path | integer (int32) | Yes | VM ID. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `GET /ecgroup/{ecgroupId}/vm/{vmId}`

Gets a VM by specified Cloud or Branch Connector group ID and VM ID

**Tags:** Cloud & Branch Connector Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ecgroupId | path | integer (int32) | Yes | Cloud or Branch Connector group ID. |
| vmId | path | integer (int32) | Yes | VM ID. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |

## `GET /ecgroup/{ecgroupId}/vm/{vmId}/intf`

Retrieves the list of interfaces associated with a specific VM in a Cloud or Branch Connector group.

**Tags:** Cloud & Branch Connector Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ecgroupId | path | integer (int32) | Yes | The Cloud or Branch Connector group ID. |
| vmId | path | integer (int32) | Yes | The ID of the VM. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `POST /ecgroup/{ecgroupId}/vm/{vmId}/intf`

Creates an interface for a specific VM in a Cloud or Branch Connector group.

**Tags:** Cloud & Branch Connector Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ecgroupId | path | integer (int32) | Yes | The Cloud or Branch Connector group ID. |
| vmId | path | integer (int32) | Yes | The ID of the VM. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `DELETE /ecgroup/{ecgroupId}/vm/{vmId}/intf/{intfId}`

Deletes a Cloud or Branch Connector interface within a specific VM based on the provided interface ID.

**Tags:** Cloud & Branch Connector Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ecgroupId | path | integer (int32) | Yes | The Cloud or Branch Connector group ID. |
| vmId | path | integer (int32) | Yes | The ID of the VM. |
| intfId | path | integer (int32) | Yes | The interface ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `GET /ecgroup/{ecgroupId}/vm/{vmId}/intf/{intfId}`

Retrieves the Cloud or Branch Connector interface within a specific VM based on the provided interface ID.

**Tags:** Cloud & Branch Connector Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ecgroupId | path | integer (int32) | Yes | The Cloud or Branch Connector group ID. |
| vmId | path | integer (int32) | Yes | The ID of the VM. |
| intfId | path | integer (int32) | Yes | The interface ID. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `PUT /ecgroup/{ecgroupId}/vm/{vmId}/intf/{intfId}`

Updates the Cloud or Branch Connector interface within a specific VM based on the provided interface ID.

**Tags:** Cloud & Branch Connector Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ecgroupId | path | integer (int32) | Yes | The Cloud or Branch Connector group ID. |
| vmId | path | integer (int32) | Yes | The ID of the VM. |
| intfId | path | integer (int32) | Yes | The interface ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `DELETE /ecgroup/{ecgroupId}/vm/{vmId}/route`

Deletes a specific Cloud or Branch Connector route associated with a VM in the group.

**Tags:** Cloud & Branch Connector Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ecgroupId | path | integer (int32) | Yes | The Cloud or Branch Connector group ID. |
| vmId | path | integer (int32) | Yes | The ID of the VM. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `GET /ecgroup/{ecgroupId}/vm/{vmId}/route`

Retrieves the list of Cloud or Branch Connector routes for the specified VM in the group.

**Tags:** Cloud & Branch Connector Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ecgroupId | path | integer (int32) | Yes | The Cloud or Branch Connector group ID. |
| vmId | path | integer (int32) | Yes | The ID of the VM. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `POST /ecgroup/{ecgroupId}/vm/{vmId}/route`

Creates a Cloud or Branch Connector route within a specific VM in the group.

**Tags:** Cloud & Branch Connector Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ecgroupId | path | integer (int32) | Yes | The Cloud or Branch Connector group ID. |
| vmId | path | integer (int32) | Yes | The ID of the VM. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `DELETE /ecgroup/{ecgroupId}/vm/{vmId}/route/{ecRouteId}`

Deletes a Cloud or Branch Connector route within a specific VM based on the provided route ID.

**Tags:** Cloud & Branch Connector Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ecgroupId | path | integer (int32) | Yes | The Cloud or Branch Connector group ID. |
| vmId | path | integer (int32) | Yes | The ID of the VM. |
| ecRouteId | path | integer (int32) | Yes | The Cloud or Branch Connector route ID. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `GET /ecgroup/{ecgroupId}/vm/{vmId}/route/{ecRouteId}`

Retrieves the details of the Cloud or Branch Connector route within a specific VM based on the provided route ID.

**Tags:** Cloud & Branch Connector Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ecgroupId | path | integer (int32) | Yes | The Cloud or Branch Connector group ID. |
| vmId | path | integer (int32) | Yes | The ID of the VM. |
| ecRouteId | path | integer (int32) | Yes | The Cloud or Branch Connector route ID. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `PUT /ecgroup/{ecgroupId}/vm/{vmId}/route/{ecRouteId}`

Updates the Cloud or Branch Connector route details within a specific VM based on the provided route ID.

**Tags:** Cloud & Branch Connector Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| ecgroupId | path | integer (int32) | Yes | The Cloud or Branch Connector group ID. |
| vmId | path | integer (int32) | Yes | The ID of the VM. |
| ecRouteId | path | integer (int32) | Yes | The Cloud or Branch Connector route ID. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default response. To learn more, see [API Response Codes and Error Messages](/cloud-branch-connector/api-response-codes-and-error-messages). |  |

## `GET /ecgroup/{id}`

Gets Cloud or Branch Connector group by ID.

**Tags:** Cloud & Branch Connector Groups

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| id | path | integer (int32) | Yes | ID of Cloud or Branch Connector group. |
| page | query | integer (int32) | No | Specifies the page offset. |
| pageSize | query | integer (int32) | No | Specifies the page size. The default size is 250. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response. See [API Response Codes](https://help.zscaler.com/cloud-branch-connector/api-response-codes-and-error-messages) |  |
