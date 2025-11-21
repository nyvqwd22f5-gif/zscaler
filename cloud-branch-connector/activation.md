# Activation
Source: https://help.zscaler.com/zia/activation

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /eusaStatus/latest`

Retrieves the End User Subscription Agreement (EUSA) acceptance status. If the status does not exist, it returns a status object with no ID.

**Tags:** Activation
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | EusaStatus |

## `PUT /eusaStatus/{eusaStatusId}`

Updates the EUSA status based on the specified status ID

**Tags:** Activation
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| eusaStatusId | path | integer | Yes | The EUSA status ID |
| body | body | EusaStatus | No | The EUSA status details |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | EusaStatus |

## `GET /status`

Gets the activation status for the saved configuration changes. To learn more about activating configuration changes, see [Saving and Activating Changes in the ZIA Admin Portal](/zia/saving-and-activating-changes-zia-admin-portal).

**Tags:** Activation
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | ActivationStatus |

## `POST /status/activate`

Activates the saved configuration changes. To learn more, see [Saving and Activating Changes in the ZIA Admin Portal](/zia/saving-and-activating-changes-zia-admin-portal).

**Tags:** Activation
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | ActivationStatus |

## Models
### ActivationStatus
Organization Policy Edit/Update Activation status
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| status | string | No |  |

### EntityReference
This is an immutable reference to an entity that mainly consists of id and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### EusaStatus
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| acceptedStatus | boolean | No | A Boolean value that specifies the EUSA status. If set to true, the EUSA is accepted. If set to false, the EUSA is in an 'agreement pending' state. The default value is false. |
| id | integer (int32) | No | System-generated identifier for the EUSA status |
| version | EntityReference | Yes | Specifies the EUSA info ID version. This field is for Zscaler internal use only. |
