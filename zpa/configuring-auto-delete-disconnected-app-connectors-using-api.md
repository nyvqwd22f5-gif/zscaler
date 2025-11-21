# Configuring Auto Delete for Disconnected App Connectors Using API
Source: https://help.zscaler.com/zpa/configuring-auto-delete-disconnected-app-connectors-using-api
PDF: https://help.zscaler.com/pdf/com/en/1485801.pdf

This article provides information on configuring Auto Delete for disconnected App Connectors using the ZPA cloud service API. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Configuring Auto Delete for Disconnected App Connectors
To configure auto deletion for disconnected App Connectors:
- Send a `POST` request to the following endpoint in the connector-controller: `/mgmtconfig/v1/customer/{customerId}/connectorSchedule`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
For example: `/mgmtconfig/v1/customer/145259576743165952/connectorSchedule`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following details to schedule a frequency for the auto deletion:
- `customerId`: The ZPA tenant ID of the customer.
- `frequency`: The scheduled frequency at which the disconnected App Connectors are eligible for deletion. The supported value is `days`.
- `frequencyInterval`: The number of days after an App Connector disconnects for it to become eligible for deletion. The minimum supported value is `5`.
- [View the JSON payload](#PostPayload)
[]{
"customerId": 0,
"deleteDisabled": true,
"enabled": true,
"frequency": "string",
"frequencyInterval": integer,
}
- [View an example JSON payload](#PostJsonPayload)
[]{
"customerId": 145259576743165952,
"deleteDisabled": true,
"enabled": true,
"frequency": "days",
"frequencyInterval": 5,
}
A successful response returns `Code 204 No Content`, meaning Auto Delete frequency in the App Connector settings is successfully enabled. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting the Auto Delete Frequency for Disconnected App Connectors
To get the auto deletion frequency for the disconnected App Connectors:
- Send a `GET` request to the following endpoint in the connector-controller: `/mgmtconfig/v1/customer/{customerId}/connectorSchedule`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
For example: `/mgmtconfig/v1/customer/145259576743165952/connectorSchedule`.
- [View an example response](#GetExample)
[]{
"id": 9,
"frequencyInterval": 5,
"frequency": "days",
"enabled": true,
"customerId": 145259576743165952,
"deleteDisabled": true,
}
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating the Auto Delete Frequency for Disconnected App Connectors
To update the Auto Delete frequency for the disconnected App Connectors:
- Send a `PUT` request to the following endpoint in the connector-controller: `/mgmtconfig/v1/customer/{customerId}/connectorSchedule/{id}`.
- Provide the following in the request endpoint:
- `customerId`: the ZPA tenant ID of the customer, in the request endpoint.
- `id`: The unique identifier for the App Connector auto deletion configuration for a customer captured in [Getting the Auto Delete Frequency for Disconnected App Connectors](#GetAutoDeleteFreq).
For example: `/mgmtconfig/v1/customer/145259576743165952/connectorSchedule/9`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following details to schedule a frequency for the auto deletion:
- `customerId`: The ZPA tenant ID of the customer.
- `frequency`: The scheduled frequency at which the disconnected App Connectors are deleted. The supported value is `days`.
- `frequencyInterval`: The interval at which the auto deletion frequency is triggered. The minimum supported value is `5`.
- [View the JSON payload](#PutJsonPayload)
[]{
"customerId": 0,
"deleteDisabled": true,
"enabled": true,
"frequency": "string",
"frequencyInterval": integer,
}
- [View an example JSON payload](#PutExamplePayload)
[]{
"customerId": 145259576743165952,
"deleteDisabled": true,
"enabled": true,
"frequency": "days",
"frequencyInterval": 5,
}
A successful response returns `Code 204 No Content`, meaning Auto Delete frequency in the App Connector settings is successfully updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Adding Field Descriptions
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| id | The unique identifier for the App Connector auto deletion configuration for a customer. This field is only required for the `PUT` request to update the frequency of the App Connector Settings. | No | IntegerThe minimum supported value is `5`. |
| frequency | The scheduled frequency at which the disconnected App Connectors are deleted | Yes | StringSupported value: `days` |
| frequencyInterval | The interval for the configured frequency value. The minimum supported value is `5`. | Yes | Integer |
| deleteDisabled | Indicates if the App Connectors are included for deletion if they are in a disconnected state based on `frequencyInterval` and `frequency` values | Yes | Boolean: `true`, `false` |
| enabled | Indicates if the setting for deleting App Connectors is enabled or disabled | Yes | Boolean: `true`, `false` |