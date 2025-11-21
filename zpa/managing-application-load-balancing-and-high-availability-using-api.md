# Managing Application Load Balancing and High Availability Using API
Source: https://help.zscaler.com/zpa/managing-application-load-balancing-and-high-availability-using-api
PDF: https://help.zscaler.com/pdf/com/en/1486006.pdf

This article provides information for managing application load balancing configurations on application segments using API. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Prerequisite API Call
Before managing application load balancing on an application segment, you must get the application ID of the application segment. To learn more, see [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api).
[]Getting Details of an Application Load Balancing Configuration
To get details of the application load balancing configuration of an application segment:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/application/{applicationId}/weightedLbConfig?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `applicationId`: The application segment ID.
- `microtenantId`: The unique identifier of the Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/217329507000909824/application/217329507000909927/weightedLbConfig?microtenantId=0`.
- [View an example response](#getResponse)
[]
`{
"applicationId": "217329507000909927",
"weightedLoadBalancing": true,
"applicationToServerGroupMappings": [
{
"id": "217329507000909879",
"weight": "12",
"passive": false,
"name": "ServerGrp6Updated"
},
{
"id": "217329507000909868",
"weight": "30",
"passive": false,
"name": "testExampleSrvrGrp"
},
{
"id": "217329507000909872",
"weight": "500",
"passive": false,
"name": "Test Example Server Grp1"
}
]
} `
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating the Application Load Balancing Configuration
To update the application load balancing configuration of an application segment:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/application/{applicationId}/weightedLbConfig?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `applicationId`: The application segment ID.
- `microtenantId`: The unique identifier of the Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/217329507000909824/application/217329507000909927/weightedLbConfig?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- The application segment ID.
- Include the `weightedLoadBalancing` field set to `true`.
- The application-to-server-group mappings. This model is highlighted in red, and includes the following fields:
- `id`: The unique identifier of the server groups captured in [Getting Details of Application Load Balancing Configurations](#getDetailsWlb).
- `weight`: The weight of the load balancing configuration. This is an integer between 0 and 1,000. To learn more, see [Adding Field Descriptions](#AddingFieldDescriptions).
- `passive`: If set to `false`, the server groups are in an active state and can load balance. If `true`, the server groups stay passive.
- `name`: The name of the server group.
- [View the JSON payload](#PutPayload)
[]
`{
"applicationId": "<applicationId>",
"weightedLoadBalancing": boolean,
"applicationToServerGroupMappings": [
{
"id": "<serverGroupId>",
"weight": "int",
"passive": boolean,
"name": "<serverGroupName>"
},
{
"id": "<serverGroupId>",
"weight": "int",
"passive": boolean,
"name": "<serverGroupName>"
},
{
"id": "<serverGroupId>",
"weight": "int",
"passive": boolean,
"name": "<serverGroupName>"
}
]
}`
- [View the example payload](#PutExamplePayload)
[]
`{
"applicationId": "217329507000909927",
"weightedLoadBalancing": true,
"applicationToServerGroupMappings": [
{
"id": "217329507000909879",
"weight": "12",
"passive": false,
"name": "ServerGrp6Updated"
},
{
"id": "217329507000909868",
"weight": "30",
"passive": false,
"name": "testSrvrGrp"
},
{
"id": "217329507000909872",
"weight": "500",
"passive": false,
"name": "Test Server Grp1"
}
]
}`
A successful response yields code 204, meaning the application segment is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Adding Field Description
The following table includes descriptions of available fields you can use for the application load balancing configuration use cases:
[](/zpa/configuring-application-segments-using-api)
-
-
-
-
[](/zpa/about-api-keys)[](/zpa/configuring-microtenants-using-api)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| applicationId | The application segment ID. To learn more, see Configuring Application Segments Using API. | Yes | Integer |
| weightedLoadBalancing | Indicates if the application load balancing configuration for application segments is enabled (`true`) or disabled (`false`) | Yes | BooleanSupported values:`true``false`Default value: `false` |
| id | The unique identifier of the server group | Yes | Integer |
| weight | The weight of the load balancing configuration. Weights with a lower value indicate that a lesser number of requests are served by the App Connectors linked to the server group. Weights with a higher value than other server groups indicate that the App Connectors linked to the server group serve a greater number of requests. Server groups with weights set to 0 do not route requests. | Yes | IntegerSupported values are [0–1,000] |
| passive | Indicates if the server groups are in an active state and can load balance (`false`), or if the server groups stay passive (`true`) | Yes | BooleanSupported values:`true``false` |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. Pass `microtenantId` as null to retrieve data from all customers associated with the tenant. If the `microtenantId` is not passed in the request endpoint when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |