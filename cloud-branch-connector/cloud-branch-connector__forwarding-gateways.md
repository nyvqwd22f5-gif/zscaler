# Forwarding Gateways
Source: https://help.zscaler.com/cloud-branch-connector/forwarding-gateways

## `GET /gateways`

Retrieves the list of ZIA gateways and Log and Control gateways. To learn more, see [ZIA gateways](/cloud-branch-connector/about-zia-gateways) and [Log and Control gateways](/cloud-branch-connector/about-log-and-control-gateways).

**Tags:** Forwarding Gateways
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `POST /gateways`

Adds a new ZIA gateway or Log and Control gateway based on the specified parameters. To learn more, see [Configuring a ZIA Gateway](/cloud-branch-connector/configuring-zia-gateway) and [Configuring a Log and Control Gateway](/cloud-branch-connector/configuring-log-and-control-gateway).

**Tags:** Forwarding Gateways
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `GET /gateways/lite`

Retrieves the list of [ZIA gateways](/cloud-branch-connector/about-zia-gateways) and [Log and Control gateways](/cloud-branch-connector/about-log-and-control-gateways). This request retrieves basic information about gateways. For extensive details, use the `GET /gateways` request.

**Tags:** Forwarding Gateways
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |

## `DELETE /gateways/{gatewayId}`

Deletes a ZIA gateway or Log and Control gateway based on the specified ID.

**Tags:** Forwarding Gateways

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| gatewayId | path | integer (int32) | Yes | ID of the gateway. |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Default Response |  |
