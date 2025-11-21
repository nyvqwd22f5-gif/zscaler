# Managing Client Settings Using API
Source: https://help.zscaler.com/zpa/managing-client-settings-using-api
PDF: https://help.zscaler.com/pdf/com/en/1529290.pdf

This article provides information for managing Zscaler Private Access (ZPA) client settings using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Getting Details of Client Settings
To get details of client settings for a given customer:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/clientSetting`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/145256180497776640/clientSetting`.
- [View an example response](#exampleGetDetailsResponse)
[]
`[
{
"id": "6025",
"creationTime": "1635186837",
"modifiedBy": "72057594038006701",
"clientCertificateType": "ZAPP_CLIENT",
"signingCertExpiryInEpochSec": "2108226836",
"name": "Client",
"enrollmentCertId": "13965",
"enrollmentCertName": "Client"
}
]`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Prerequisite API Calls
Before you can create or update client settings, you must get the enrollment certificate details. To learn more, see [Obtaining Enrollment Certificate Details Using API](/zpa/obtaining-enrollment-certificate-details-using-api).
Creating or Updating Client Settings
To create client settings:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/clientSetting`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/145256180497776640/clientSetting`.
- Use the following JSON payload provide the following information:
- `enrollmentCertId`: The unique identifier of the generated enrollment certificate. To learn more, see [Obtaining Enrollment Certificate Details Using API](/zpa/obtaining-enrollment-certificate-details-using-api).
- `clientCertificateType`: The client certificate type. The supported values are:
- `APP_PROTECTION`: This enrollment (CA) certificate enrolls AppProtection-enabled application segments.
- `ISOLATION_CLIENT`: This enrollment (CA) certificate enrolls Isolation clients.
- `NONE`: This enrollment (CA) certificate enrolls App Connectors, ZPA Private Service Edges, or Private Cloud Controllers.
- `ZAPP_CLIENT`: This enrollment (CA) certificate enrolls Zscaler Client Connector.
- `enrollmentCertName`: The name of the generated enrollment certificate.
- `name`: The name of the client settings.
- [View the JSON payload](#examplePostJson)
[]
`{
"modifiedTime": 0,
"creationTime": 0,
"modifiedBy": 0,
"microtenantId": <Microtenant ID>,
"enrollmentCertId": <enrollment certificate ID>,
"clientCertificateType": "ZAPP_CLIENT",
"enrollmentCertName": "string",
"signingCertExpiryInEpochSec": 0,
"name": <Name of the client settings>
}`
- [View an example JSON payload](#exampleJsonPayloadPost)
[]
`{
"signingCertId: "227050",
"clientCertificateType: "APP_PROTECTION"
}`
- [View an example response](#examplePostResponse)
[]
`[
{
"id":"150207",
"modifiedTime":"1746657505",
"creationTime":"1743663009",
"modifiedBy":"72057594038040687",
"signingCertId":"227050",
"clientCertificateType":"APP_PROTECTION",
"signingCertName":"Example Cert Test",
"signingCertExpiryInEpochSec":"2692737505",
"name":"Example Cert Test"
}
]`
A successful response returns code 204, meaning the client settings are created or updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting Client Settings
To delete client settings:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/clientSetting`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/145256180497776640/clientSetting`.
- Provide the `type` (i.e., the client certificate type), as a query-string parameter. The supported values are:
- `APP_PROTECTION`: This enrollment (CA) certificate enrolls AppProtection-enabled application segments.
- `ISOLATION_CLIENT`: This enrollment (CA) certificate enrolls Isolation clients.
- `NONE`: This enrollment (CA) certificate enrolls App Connectors, ZPA Private Service Edges, or Private Cloud Controllers.
- `ZAPP_CLIENT`: This enrollment (CA) certificate enrolls Zscaler Client Connector.
A successful response returns code 204, meaning the client settings are deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of All Client Settings
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/clientSetting/all`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/145256180497776640/clientSetting/all`.
- [View an example response](#getAllClientSettingsResponse)
[]
`[
{
"id": "13370",
"modifiedTime": "1692635903",
"creationTime": "1692635903",
"modifiedBy": "72057594038006701",
"clientCertificateType": "ISOLATION_CLIENT",
"name": "Isolation Client",
"enrollmentCertId": "26781",
"enrollmentCertName": "Isolation Client"
},
{
"id": "16239",
"modifiedTime": "1728667950",
"creationTime": "1728667884",
"modifiedBy": "72057594038006517",
"clientCertificateType": "APP_PROTECTION",
"name": "test 123",
"enrollmentCertId": "33645",
"enrollmentCertName": "test 123"
}
]`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Adding Field Descriptions
The following table includes available fields you can use for the client settings API use cases:
-
-
-
-
[](/zpa/obtaining-enrollment-certificate-details-using-api)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| clientCertificateType | The client certificate type | Yes | StringThe supported values are:`APP_PROTECTION`: This enrollment (CA) certificate enrolls AppProtection-enabled application segments.`ISOLATION_CLIENT`: This enrollment (CA) certificate enrolls Isolation clients.`NONE`: This enrollment (CA) certificate enrolls App Connectors, ZPA Private Service Edges, or Private Cloud Controllers.`ZAPP_CLIENT`: This enrollment (CA) certificate enrolls Zscaler Client Connector. |
| enrollmentCertId | The unique identifier of the enrollment certificate. To learn more, see Obtaining Enrollment Certificate Details Using API. | Yes | Integer |
| enrollmentCertName | The name of the enrollment certificate | Yes | String |