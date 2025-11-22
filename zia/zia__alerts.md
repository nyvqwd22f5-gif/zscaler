# Alerts
Source: https://help.zscaler.com/zia/alerts

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /alertSubscriptions`

Retrieves a list of all alert subscriptions. To learn more, see [About Alert Subscriptions](/zia/about-alert-subscriptions).

**Tags:** Alerts
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[AlertSubscription] |

## `POST /alertSubscriptions`

Adds a new alert subscription. To learn more, see [Adding Alert Subscriptions](/zia/adding-alert-subscriptions).

**Tags:** Alerts
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | AlertSubscription | No | Information about the alert subscription |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AlertSubscription |

## `GET /alertSubscriptions/{alertSubscriptionId}`

Retrieves the alert subscription information based on the specified ID

**Tags:** Alerts
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| alertSubscriptionId | path | integer | Yes | The alert subscription ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AlertSubscription |

## `PUT /alertSubscriptions/{alertSubscriptionId}`

Updates an existing alert subscription based on the specified ID

**Tags:** Alerts
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| alertSubscriptionId | path | integer | Yes | The alert subscription ID |
| body | body | AlertSubscription | No | Information about the alert subscription |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AlertSubscription |

## Models
### AlertSubscription
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| complySeverities | array[string] | No |  |
| deleted | boolean | No | Deletes an existing alert subscription |
| description | string | No | Additional comments or information about the alert subscription |
| email | string | No | The email address of the alert recipient |
| id | integer (int32) | No | System-generated identifier for the alert subscription |
| manageSeverities | array[string] | No |  |
| pt0Severities | array[string] | No | Lists the severity levels of the Patient 0 Alert class information that the recipient receives |
| secureSeverities | array[string] | No | Lists the severity levels of the Secure Alert class information that the recipient receives |
| systemSeverities | array[string] | No | Lists the severity levels of the System Alerts class information that the recipient receives |
