# Managing Administrators Using API
Source: https://help.zscaler.com/zpa/managing-administrators-using-api
PDF: https://help.zscaler.com/pdf/com/en/1529291.pdf

This article provides information for managing Zscaler Private Access (ZPA) administrators using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Getting Administrator Details
To get the details of an administrator:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/administrators/{adminId}?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `adminId`: The unique identifier of the administrator.
- `microtenantId`: The unique identifier of the Microtenant. If the administrator is within a Microtenant, then this field is required. If the administrator is within the Default Microtenant, then this field must be passed as `0`. To learn more, see [Configuring Microtenant Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145256180497776640/administrators/145256180497776640`.
- [View an example response](#getAdminResponse)
[]
`{
"modifiedTime": "1695815396",
"creationTime": "1695815322",
"modifiedBy": "145256180497778056",
"id": "145256180497778056",
"username": "exampletest@145256180497776640.zpa-customer.com",
"email": "exampletest@145256180497776640.zpa-customer.com",
"customerId": "145256180497776640",
"isDeleted": "0",
"role": {
"id": "12",
"name": "ZPA Administrator"
},
"eula": "0",
"isEnabled": true,
"twoFactorAuthEnabled": false,
"phoneNumber": "+911111111111",
"forcePwdChange": false,
"pinSession": true,
"localLoginDisabled": false,
"isLocked": false,
"microtenantId": "145256180497776789"
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting All Administrators for a Customer or Company
To get details of all administrators for a customer or company:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/administrators`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/145256180497776640/administrators`.
- [View an example response](#getAllAdminsResponse)
[]
`[
{
"modifiedTime": "1695815396",
"creationTime": "1695815322",
"modifiedBy": "145256180497778056",
"id": "145256180497778056",
"username": "exampletest@145256180497776640.zpa-customer.com",
"email": "exampletest@145256180497776640.zpa-customer.com",
"customerId": "145256180497776640",
"isDeleted": "0",
"role": {
"id": "12",
"name": "ZPA Administrator"
},
"eula": "0",
"isEnabled": true,
"twoFactorAuthEnabled": false,
"phoneNumber": "+911111111111",
"forcePwdChange": false,
"pinSession": true,
"localLoginDisabled": false,
"isLocked": false,
"microtenantId": "145256180497776789"
},
{
"modifiedTime": "1685997687",
"creationTime": "1667540273",
"modifiedBy": "72057594038006701",
"id": "145256180497776790",
"username": "mtAdmin_145256180497776789@145256180497776640.zpa-customer.com",
"displayName": "Zscaler Private Access Scope Administrator",
"email": "mtAdmin_145256180497776789@145256180497776640.zpa-customer.com",
"customerId": "145256180497776640",
"isDeleted": "0",
"role": {
"id": "12",
"name": "ZPA Administrator"
},
"eula": "0",
"isEnabled": false,
"twoFactorAuthEnabled": false,
"phoneNumber": "2342321312312",
"forcePwdChange": false,
"pinSession": true,
"localLoginDisabled": false,
"isLocked": false,
"microtenantId": "145256180497776789"
}
]`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Prerequisite API Calls
Before you create or update an administrator, you must get the unique identifier of the role for the administrator. To learn more, see [Managing Administrator Roles Using API](/zpa/managing-administrator-roles-using-api).
Creating an Administrator
To create an administrator:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/administrators`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant. If the administrator is within a Microtenant, then this field is required. If the administrator is within the Default Microtenant, then this field must be passed as `0`. To learn more, see [Configuring Microtenant Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145256180497776640/administrators?microtenantId=145256180497776789`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- `tmpPassword`: The temporary password of the administrator. The password must be at least 8 characters in length, and include at least one uppercase letter, one special character, and one number.
- `password`: The password for the admin. The password must be at least 8 characters in length, and include at least one uppercase letter, one special character, and one number.
- `username`: This is the login ID for the administrator. It must be an email address, where the domain name matches your company's authentication domain name.
- `email`: (Optional) Enter the email address for the administrator. Updates regarding ZPA are sent to this email address.
- `phoneNumber`: The 10-digit phone number without any hyphens (-). This field is mandatory and is used for password recovery purposes.
- `roleId`: The unique identifier of the role for the administrator. To learn more, see [Managing Administrator Roles Using API](/zpa/managing-administrator-roles-using-api).
- [View the JSON payload](#viewJsonPayloadPost)
[]
`{
"microtenantId": 0,
"microtenantName": "string",
"username": "string",
"displayName": "string",
"email": "string",
"timezone": "string",
"password": "string",
"tmpPassword": "string",
"roleId": "string",
"comments": "string",
"languageCode": "string",
"eula": "string",
"groupIds": [
"string"
],
"isEnabled": true,
"forcePwdChange": true,
"twoFactorAuthEnabled": true,
"twoFactorAuthType": "string",
"tokenId": "string",
"phoneNumber": "string",
"localLoginDisabled": true,
"pinSession": true,
"isLocked": true,
"syncVersion": 0,
"deliveryTag": 0,
"operationType": "UPSERT"
}`
- [View an example JSON payload](#viewExamplePostJson)
[]
`{
"isEnabled":true,
"forcePwdChange":true,
"pinSession":true,
"username":"exampleuser@lanukcorp.com",
"email":"",
"phoneNumber":"1234567890",
"twoFactorAuthEnabled":false,
"allowLocalLogin":true,
"password":"Admin@123!",
"confirmPassword":"Admin@123!",
"twoFactorAuthType":"",
"roleId":"144118148382065792",
"localLoginDisabled":false
}`
- [View an example response](#postExampleResponse)
[]
`{
"id": "144118148382065795",
"username": "exampleuser@lanukcorp.com",
"roleId": "144118148382065792",
"isEnabled": true,
"forcePwdChange": true,
"twoFactorAuthEnabled": false,
"phoneNumber": "1234567890",
"localLoginDisabled": false,
"pinSession": true,
"isLocked": false,
"syncVersion": "0",
"deliveryTag": "0",
"oneIdentityUser": false
} `
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating Details of an Administrator
To update an administrator:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/administrators/{adminId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `adminId`: The unique identifier of the administrator.
- `microtenantId`: The unique identifier of the Microtenant. If the administrator is within a Microtenant, then this field is required. If the administrator is within the Default Microtenant, then this field must be passed as `0`. To learn more, see [Configuring Microtenant Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145256180497776640/administrators/145256180497778056?microtenantId=145256180497776789`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following information:
- `tmpPassword`: The temporary password of the administrator. The password must be at least 8 characters in length, and include at least one uppercase letter, one special character, and one number.
- `username`: This is the login ID for the administrator. It must be an email address, where the domain name matches your company's authentication domain name.
- `email`: (Optional) The email address for the administrator. Updates regarding ZPA are sent to this email address.
- `phoneNumber`: The 10-digit phone number without any hyphens (-). This field is mandatory and is used for password recovery purposes.
- `roleId`: The unique identifier of the role for the administrator. To learn more, see [Managing Administrator Roles Using API](/zpa/managing-administrator-roles-using-api).
- [View the JSON payload](#putJsonPayload)
[]
`{
"microtenantId": 0,
"microtenantName": "string",
"username": "string",
"displayName": "string",
"email": "string",
"timezone": "string",
"password": "string",
"tmpPassword": "string",
"roleId": "string",
"comments": "string",
"languageCode": "string",
"eula": "string",
"groupIds": [
"string"
],
"isEnabled": true,
"forcePwdChange": true,
"twoFactorAuthEnabled": true,
"twoFactorAuthType": "string",
"tokenId": "string",
"phoneNumber": "string",
"localLoginDisabled": true,
"pinSession": true,
"isLocked": true,
"syncVersion": 0,
"deliveryTag": 0,
"operationType": "UPSERT"
}`
A successful response returns code 204, meaning the administrator is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting an Administrator
To delete an administrator:
- Send a DELETE request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/administrators/{adminId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `adminId`: The unique identifier of the administrator.
- `microtenantId`: The unique identifier of the Microtenant. If the administrator is within a Microtenant, then this field is required. If the administrator is within the Default Microtenant, then this field must be passed as `0`. To learn more, see [Configuring Microtenant Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145256180497776640/administrators/145256180497778056?microtenantId=145256180497776789`.
A successful response returns code 204, meaning the administrator is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Adding Field Descriptions
The following table includes available fields you can use for the administrator API use cases:
[](/zpa/configuring-microtenants-using-api)[](/zpa/configuring-zpa-administrators)
[](/zpa/configuring-zpa-administrators)
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| microtenantId | The unique identifier of the Microtenant for the ZPA tenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained in the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations are limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as 0 when making requests to retrieve data from the Default Microtenant. Pass `microtenantId` as null to retrieve data from all Microtenants associated with the tenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see Configuring Microtenants Using API. | No | Integer |
| tmpPassword | The temporary password of the administrator. The password must be at least 8 characters in length, and include at least one uppercase letter, one special character, and one number. | Yes | String |
| password | The password for the admin. The password must be at least 8 characters in length, and include at least one uppercase letter, one special character, and one number. To learn more, see Configuring ZPA Administrators. | Yes | String |
| username | This is the login ID for the administrator. It must be an email address, where the domain name matches your company's authentication domain name. | Yes | String |
| phoneNumber | The 10-digit phone number without any hyphens (-). This field is mandatory and is used for password recovery purposes. | Yes | Integer |
| forcePwdChange | Forces the admin to reset their password at login if set to `true`. | No | Default: `true`Supported values: `true`, `false` |
| twoFactorAuthEnabled | Allows the admin to use two-factor authentication (2FA) if set to `true`. | No | Default: `true`Supported values: `true`, `false` |
| twoFactorAuthType | The 2FA type. This field is required if `twoFactorAuthEnabled` is set to `true`. To learn more, see Configuring ZPA Administrators. | No | StringThe supported value is `YUBIKEY` |