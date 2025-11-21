# Configuring Emergency Access Users Using API
Source: https://help.zscaler.com/zpa/configuring-emergency-access-users-using-api
PDF: https://help.zscaler.com/pdf/com/en/1485936.pdf

This article provides information on configuring Zscaler Private Access (ZPA) [emergency access users](/zpa/about-emergency-access-users) using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Creating a New Emergency Access User
To create a new emergency access user:
- Send a `POST` request to the following endpoint in the Emergency Access Controller: `/mgmtconfig/v1/admin/customers/{customerId}/emergencyAccess/user`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
For example: `/mgmtconfig/v1/admin/customers/145256180497776640/emergencyAccess/user`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- `emailId`: The email address of the user that you are giving emergency access to.
- `firstName`: The first name of the user that you are giving emergency access to.
- `lastName`: The last name of the user that you are giving emergency access to.
- [View the JSON payload](#postPayload)
[]{
"activatedOn": 0,
"allowedActivate": true,
"allowedDeactivate": true,
"emailId": "emergencyUserExample@safemarch.com",
"firstName": "string",
"lastLoginTime": 0,
"lastName": "string",
"updateEnabled": true,
"userId": "string",
"userStatus": "string"
}
- [View an example JSON payload](#postExamplePayload)
[]{
"activatedOn": 0,
"allowedActivate": true,
"allowedDeactivate": true,
"emailId": "emergencyUserExample@safemarch.com",
"firstName": "John",
"lastLoginTime": 0,
"lastName": "Doe",
"updateEnabled": true,
"userId": "string",
"userStatus": "string"
}
- [View an example response](#postResponse)
[]{
"userId": "00u2gg2qairRJf71G756",
"firstName": "John",
"lastName": "Doe",
"emailId": "emergencyUserExample@safemarch.com",
"userStatus": "Provisioned",
"activatedOn": "1687892531",
"allowedActivate": false,
"allowedDeactivate": true,
"updateEnabled": true
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Microtenant Support
To create a new emergency access user within a Microtenant:
- Send a `POST` request to the following endpoint in the Emergency Access Controller: `/mgmtconfig/v1/admin/customers/{customerId}/emergencyAccess/user?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/72057595111669760/emergencyAccess/user?microtenantId=145260601092866314`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- `emailId`: The email address of the user that you are giving emergency access to.
- `firstName`: The first name of the user that you are giving emergency access to.
- `lastName`: The last name of the user that you are giving emergency access to.
- [View the JSON payload](#postPayloadMicrotenant)
[]{
"activatedOn": 0,
"allowedActivate": true,
"allowedDeactivate": true,
"emailId": "emergencyUserExample@safemarch.com",
"firstName": "string",
"lastLoginTime": 0,
"lastName": "string",
"updateEnabled": true,
"userId": "string",
"userStatus": "string"
}
- [View an example JSON payload](#postExamplePayloadMicrotenant)
[]{
"activatedOn": 0,
"allowedActivate": true,
"allowedDeactivate": true,
"emailId": "emergencyUserExample@safemarch.com",
"firstName": "John",
"lastLoginTime": 0,
"lastName": "Doe",
"updateEnabled": true,
"userId": "string",
"userStatus": "string"
}
- [View an example response](#postResponseMicrotenant)
[]{
"userId": "00u2gg2qairRJf71G756",
"firstName": "John",
"lastName": "Doe",
"emailId": "emergencyUserExample@safemarch.com",
"userStatus": "Provisioned",
"activatedOn": "1687892531",
"allowedActivate": false,
"allowedDeactivate": true,
"updateEnabled": true
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of All Emergency Access Users
To get details of all emergency access users:
- Send a `GET` request to the following endpoint in the Emergency Access Controller: `/mgmtconfig/v1/admin/customers/{customerId}/emergencyAccess/users`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint.
For example: `mgmtconfig/v1/admin/customers/145256180497776640/emergencyAccess/users`.
- [View an example response](#getEmergencyUsers)
[]{
"items": [
{
"userId": "00u1klapaFMGhDDAV756",
"firstName": "John",
"lastName": "Doe",
"emailId": "jdoe@example.com",
"userStatus": "Deprovisioned",
"activatedOn": "1681164192",
"lastLoginTime": "1675100208",
"allowedActivate": true,
"allowedDeactivate": false,
"updateEnabled": false
}
],
"nextPage": "00u1klapaFMGhDDAV756"
}
The `totalCount` and `totalPages` fields are not supported for this endpoint.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports pagination and Microtenants. To get a paginated response of all emergency access users within a Microtenant:
- Send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/emergencyAccess/users?pagesize={pagesize}µtenantId={microtenantId}` in the Emergency Access Controller.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- Valid page size values.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/289370814522851328/approval?pagesize=5µtenantId=145260601092866314`.
- [View an example response](#getPagEAUsers)
[]{
"items": [
{
"userId": "00uaiym546MQ0WKNr5d7",
"firstName": "three",
"lastName": "user",
"emailId": "three.user@safemarch.com",
"userStatus": "Active",
"activatedOn": "1690344891",
"allowedActivate": false,
"allowedDeactivate": true,
"updateEnabled": true
},
{
"userId": "00uaiym6j9wcM0Ck55d7",
"firstName": "four",
"lastName": "user",
"emailId": "four.user@safemarch.com",
"userStatus": "Active",
"activatedOn": "1690344894",
"allowedActivate": false,
"allowedDeactivate": true,
"updateEnabled": true
},
{
"userId": "00uaiymxhpCJcKORa5d7",
"firstName": "two",
"lastName": "user",
"emailId": "two.user@safemarch.com",
"userStatus": "Active",
"activatedOn": "1690344888",
"allowedActivate": false,
"allowedDeactivate": true,
"updateEnabled": true
},
{
"userId": "00uaiynqi7VQH68vV5d7",
"firstName": "one",
"lastName": "user",
"emailId": "one.user@safemarch.com",
"userStatus": "Active",
"activatedOn": "1690344884",
"lastLoginTime": "1690345564",
"allowedActivate": false,
"allowedDeactivate": true,
"updateEnabled": true
},
{
"userId": "00uaiyo66uznlz5Uu5d7",
"firstName": "five",
"lastName": "user",
"emailId": "five.user@safemarch.com",
"userStatus": "Active",
"activatedOn": "1690344897",
"lastLoginTime": "1690349716",
"allowedActivate": false,
"allowedDeactivate": true,
"updateEnabled": true
},
{
"userId": "00uaiyp39p69u8VQR5d7",
"firstName": "dandaver",
"lastName": "groupadmin",
"emailId": "dandaver.groupadmin@safemarch.com",
"userStatus": "Active",
"activatedOn": "1690345139",
"lastLoginTime": "1690791972",
"allowedActivate": false,
"allowedDeactivate": true,
"updateEnabled": true
},
{
"userId": "00uaiyu3r8K3ZaLeM5d7",
"firstName": "RRaja",
"lastName": "UUser",
"emailId": "raja@safemarch.com",
"userStatus": "Provisioned",
"activatedOn": "1690348568",
"allowedActivate": false,
"allowedDeactivate": true,
"updateEnabled": true
},
{
"userId": "00uaiz5ooe9zVwZJf5d7",
"firstName": "SIX",
"lastName": "USER",
"emailId": "six.user@safemarch.com",
"userStatus": "Provisioned",
"activatedOn": "1690348722",
"allowedActivate": false,
"allowedDeactivate": true,
"updateEnabled": true
},
{
"userId": "00uaiz816nAQfrwAw5d7",
"firstName": "John",
"lastName": "User",
"emailId": "john@safemarch.com",
"userStatus": "Active",
"activatedOn": "1690349879",
"lastLoginTime": "1690349966",
"allowedActivate": false,
"allowedDeactivate": true,
"updateEnabled": true
},
{
"userId": "00ualiqq5ibu9fKxT5d7",
"firstName": "Krishna",
"lastName": "Nagaraj",
"emailId": "krishna@safemarch.com",
"userStatus": "Provisioned",
"activatedOn": "1690805711",
"allowedActivate": false,
"allowedDeactivate": true,
"updateEnabled": true
}
]
}
If not provided, the default page size is 20. The maximum page size is 500.
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of a Particular Emergency Access User
To get details of a particular emergency access user:
- Send a `GET` request to the endpoint `/mgmtconfig/v1/admin/customers/{customerId}/emergencyAccess/user/{userId}` in the Emergency Access Controller.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `userId`: The ID of the emergency access user.
For example: `mgmtconfig/v1/admin/customers/145256180497776640/emergencyAccess/user/00u1tjph3y3WjpEaU756`.
- [View an example response](#getEAUser)
[]{
"userId": "00u1tjph3y3WjpEaU756",
"firstName": "John",
"lastName": "Doe",
"emailId": "jdoe@safemarch.com",
"userStatus": "Active",
"activatedOn": "1675200519",
"lastLoginTime": "1675201359",
"allowedActivate": false,
"allowedDeactivate": true,
"updateEnabled": true
}
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports Microtenants. To get a particular emergency access user within a Microtenant:
- Send a `GET` request to the following endpoint in the Emergency Access Controller: `/mgmtconfig/v1/admin/customers/{customerId}/emergencyAccess/user/{userId}?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `userId`: The ID of the emergency access user.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/72057595111669760/emergencyAccess/user/00ualiqq5ibu9fKxT5d7?microtenantId=145260601092866314`.
- [View an example response](#getEaUserMicrotenant)
[]
`{
"userId": "00ualiqq5ibu9fKxT5d7",
"firstName": "John",
"lastName": "Doe",
"emailId": "JohnDoe@safemarch.com",
"userStatus": "Provisioned",
"activatedOn": "1690805711",
"allowedActivate": false,
"allowedDeactivate": true,
"updateEnabled": true
}
`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating an Emergency Access User
To update an emergency access user:
- Send a `PUT` request to the following endpoint in the Emergency Access Controller: `/mgmtconfig/v1/admin/customers/{customerId}/emergencyAccess/user/{userId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `userId`: The ID of the emergency access user.
For example: `/mgmtconfig/v1/admin/customers/145256180497776640/emergencyAccess/user/00u1tjph3y3WjpEaU756`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- `firstName`: The emergency access user's first name.
- `lastName`: The emergency access user's last name.
- [View the JSON payload](#putPayload)
[]{
"firstName": "string",
"lastName": "string"
}
- [View an example response](#putExample)
[]
`{
"userId": "00u1tjph3y3WjpEaU756",
"firstName": "Example firstName",
"lastName": "Example lastName",
"emailId": "exampleEmailId@safemarch.com",
"userStatus": "Active",
"activatedOn": "1675200519",
"lastLoginTime": "1675201359",
"allowedActivate": false,
"allowedDeactivate": true,
"updateEnabled": true
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports Microtenants. To update an emergency access user within a Microtenant:
- Send a `PUT` request to the following endpoint in the Emergency Access Controller: `/mgmtconfig/v1/admin/customers/{customerId}/emergencyAccess/user/{userId}?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `userId`: The ID of the emergency access user.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145256180497776640/emergencyAccess/user/00u1tjph3y3WjpEaU756`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- `firstName`: The emergency access user's first name.
- `lastName`: The emergency access user's last name.
- [View the JSON payload](#putPayloadMicrotenant)
[]{
"firstName": "string",
"lastName": "string"
}
- [View an example response](#putExampleMicrotenant)
[]
`{
"userId": "00u1tjph3y3WjpEaU756",
"firstName": "Example firstName",
"lastName": "Example lastName",
"emailId": "exampleEmailId@safemarch.com",
"userStatus": "Active",
"activatedOn": "1675200519",
"lastLoginTime": "1675201359",
"allowedActivate": false,
"allowedDeactivate": true,
"updateEnabled": true
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Activating the Emergency Access User
To activate the emergency access user:
- Send a `PUT` request to the following endpoint in the Emergency Access Controller: `/mgmtconfig/v1/admin/customers/{customerId}/emergencyAccess/user/{userId}/activate`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `userId`: The ID of the emergeny access user.
For example: `/mgmtconfig/v1/admin/customers/217246660302995456/emergencyAccess/user/00u1tjph3y3WjpEaU756/activate`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
A successful response returns code 200, meaning the emergency access user was activated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports Microtenants. To activate an emergency access user within a Microtenant:
- Send a `PUT` request to the following endpoint in the Emergency Access Controller: `/mgmtconfig/v1/admin/customers/{customerId}/emergencyAccess/user/{userId}/activate?microtenant={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `userId`: The ID of the emergeny access user.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/72057595111669760/emergencyAccess/user/00ualiqq5ibu9fKxT5d7/activate?microtenantId=145260601092866314`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
A successful response returns code 200, meaning the emergency access user was activated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deactivating the Emergency Access User
To deactivate the emergency access user:
- Send a `PUT` request to the following endpoint in the Emergency Access Controller: `/mgmtconfig/v1/admin/customers/{customerId}/emergencyAccess/user/{userId}/deactivate`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `userId`: The ID of the emergency access user.
For example: `/mgmtconfig/v1/admin/customers/145256180497776640/emergencyAccess/user/00u1tjph3y3WjpEaU756/deactivate`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
A successful response returns code 200, meaning the emergency access user is deactivated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
This API supports Microtenants. To deactivate the emergency access user within a Microtenant:
- Send a `PUT` request to the following endpoint in the Emergency Access Controller: `/mgmtconfig/v1/admin/customers/{customerId}/emergencyAccess/user/{userId}/deactivate?microtenantId={microtenantId}`.
- Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `userId`: The ID of the emergency access user.
- `microtenantId`: The unique identifier of the Microtenant for the ZPA tenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/72057595111669760/emergencyAccess/user/00ualiqq5ibu9fKxT5d7/deactivate?microtenantId=145260601092866314`.
- Include the request headers to specify the following parameters about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
A successful response returns code 200, meaning the emergency access user is deactivated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
[]Field Descriptions
The following table includes descriptions of available fields you can use for the emergency access use cases:
[](/zpa/about-microtenants)[](/zpa/about-api-keys)[](/zpa/configuring-microtenants-using-api)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| customerId | The ZPA tenant ID of the customer | Yes | Integer |
| pageId | Indicates the cursor ID, which is the cursor that points to the end of the page of data that has been returned | No | Integer |
| pageSize | Specifies the page size | No | Integer |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. Pass `microtenantId` as null to retrieve data from all customers associated with the tenant. If the `microtenantId` is not passed in the request endpoint when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |