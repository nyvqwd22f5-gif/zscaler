# Configuring API Keys Using API
Source: https://help.zscaler.com/zpa/configuring-api-keys-using-api
PDF: https://help.zscaler.com/pdf/com/en/1530945.pdf

This article provides information on managing Zscaler Private Access (ZPA) API key use cases using APIs. All APIs are rate limited. To learn more, see [About API Key Management](/zpa/about-api-key-management) and [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Prerequisite API Call
Before you create or update an API key, you must get the `roleId`, the unique identifier of the administrator role. To learn more, see [Managing Administrator Roles Using API](/zpa/managing-administrator-roles-using-api).
Creating an API Key
To create an API key:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/apiKeys?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/apiKeys?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following:
- `roleId`: The unique identifier of the administrator role. To learn more, see [Managing Administrator Roles Using API](/zpa/managing-administrator-roles-using-api).
- `name`: The name of the API key.
- `tokenExpiryTimeInSec`: The amount of time the key is available to use. The maximum amount of time is 3,600 seconds.
- [View the JSON payload](#createApiKeyJson)
[]
`{
"enabled":true,
"tokenExpiryTimeInSec":"<integer>",
"name":"<example name>",
"roleId":"<role ID>"
}`
- [View the sample JSON payload](#createApiKeySampleJson)
[]
`{
"enabled":true,
"tokenExpiryTimeInSec":"3600",
"name":"test API key",
"roleId":"28"
}`
- [View an example response](#createApiKeyExampleResponse)
[]
`{
"id":"145283994705985861",
"name":"test aneela jul22",
"scopeId":"0",
"clientId":"MTQ1MjgzOTk0NzA1OTg1ODYxLWIwYjEyYWFhLTkxNzQtNGNlMi05ZWQxLTBmYzVmYjdmYzYyNg==",
"clientSecret":"'[dbx(&.Y(mDtrx*jj2ysoV7lM)9G-t9",
"enabled":true,
"tokenExpiryTimeInSec":"3600",
"roleId":"28",
"pinSessionEnabled":false,
"isLocked":false
}`
A successful response returns code 201, meaning the API key is created. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Getting Details for All API Keys
To get details for all API keys:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/apiKeys?microtenantId={microtenantId}&page={pageNumber}&pageSize={pageSize}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
- `page`: Specifies the page number.
- `pageSize`: Specifies the page size. If not provided, the default page size is 20. The maximum page size is 500.
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/apiKeys?microtenantId=0&page=1&pageSize=20`.
- [View an example response](#getAllKeysResponse)
[]
`{
"totalPages": "2",
"totalCount": "37",
"list": [
{
"modifiedTime": "1753213126",
"creationTime": "1744752949",
"modifiedBy": "72057594038779845",
"id": "145283994705985775",
"clientId": "MTQ1MjgzOTk0NzA1OTg1Nzc1LTAyNWFiMTYyLTllODgtNDg1MC1hYWQ0LWUyNDM3YjVjZjQyMA==",
"name": "test user apr15_2",
"tokenExpiryTimeInSec": "360",
"enabled": true,
"pinSessionEnabled": false,
"isLocked": false,
"syncVersion": "0",
"deliveryTag": "0",
"customerId": "145283994705985536",
"roleId": "28",
"readOnly": false,
"restrictedEntity": false,
"zscalerManaged": false
}
]
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details for a Particular API Key
To get details for a particular API key:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/apiKeys/{id}?microtenantId={microtenantId}&page={pageNumber}&pageSize={pageSize}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the API key. To learn more, see [Getting Details for All API Keys](#get-all-keys).
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
- `page`: Specifies the page number.
- `pageSize`: Specifies the page size. If not provided, the default page size is 20. The maximum page size is 500.
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/apiKeys/145283994705985775?microtenantId=0&page=1&pageSize=20`.
- [View an example response](#getApiKeyResponse)
[]
`{
"modifiedTime": "1753213126",
"creationTime": "1744752949",
"modifiedBy": "72057594038779845",
"id": "145283994705985775",
"clientId": "MTQ1MjgzOTk0NzA1OTg1Nzc1LTAyNWFiMTYyLTllODgtNDg1MC1hYWQ0LWUyNDM3YjVjZjQyMA==",
"name": "aneela17 user apr15_2",
"tokenExpiryTimeInSec": "360",
"enabled": true,
"pinSessionEnabled": false,
"isLocked": false,
"syncVersion": "0",
"deliveryTag": "0",
"customerId": "145283994705985536",
"roleId": "28",
"readOnly": false,
"restrictedEntity": false,
"zscalerManaged": false
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating an API Key
To update an API key:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/apiKeys/{id}?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the API key. To learn more, see [Getting Details for All API Keys](#get-all-keys).
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/apiKeys?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following:
- `roleId`: The unique identifier of the administrator role. To learn more, see [Managing Administrator Roles Using API](/zpa/managing-administrator-roles-using-api).
- `name`: The name of the API key.
- [View an example JSON payload](#updateApiKeyPayload)
[]
`{
"enabled":true,
"tokenExpiryTimeInSec":"360",
"id":"145283994705985775",
"objectType":"ClientCredential",
"action":"EDIT",
"modifiedTime":"1748384838",
"creationTime":"1744752949",
"modifiedBy":"72057594038779845",
"clientId":"MTQ1MjgzOTk0NzA1OTg1Nzc1LTAyNWFiMTYyLTllODgtNDg1MC1hYWQ0LWUyNDM3YjVjZjQyMA==",
"name":"test user apr15_2",
"pinSessionEnabled":false,
"isLocked":false,
"syncVersion":"0",
"deliveryTag":"0",
"customerId":"145283994705985536",
"roleId":"28",
"readOnly":false,
"restrictedEntity":false,
"zscalerManaged":false
}`
A successful response returns code 204, meaning the API key is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting an API Key
To delete an API key:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/apiKeys/{id}?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the API key. To learn more, see [Getting Details for All API Keys](#get-all-keys).
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/apiKeys/145283994705985775/?microtenantId=0`.
A successful response returns code 204, meaning the API key is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).