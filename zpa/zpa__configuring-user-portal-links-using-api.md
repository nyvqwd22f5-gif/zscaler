# Configuring User Portal Links Using API
Source: https://help.zscaler.com/zpa/configuring-user-portal-links-using-api
PDF: https://help.zscaler.com/pdf/com/en/1530976.pdf

This article provides information on managing user portal links use cases using APIs. All APIs are rate limited. To learn more, see [About User Portal Links](/zpa/about-user-portal-links) and [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Prerequisite API Calls
Before you create a user portal link or get details of user portal links, you must get the `portalId`, the unique identifier of the user portal. To learn more, see [Configuring User Portals Using API](/zpa/configuring-user-portals-using-api).
[]Getting Details of All User Portal Links
To get details of all user portal links:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/userPortalLink/?microtenantId={microtenantId}&page={page}&pagesize={pagesize}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
- `page`: Specifies the page number.
- `pagesize`: Specifies the page size. If not provided, the default page size is 20. The maximum page size is 500.
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/userPortalLink/?microtenantId=0&page=1&pagesize=20`.
- [View an example response](#getAllUserPortalLinksExample)
[]
`{
"totalPages": "1",
"totalCount": "2",
"list": [
{
"id": "145283994705985846",
"modifiedTime": "1748372770",
"creationTime": "1748372770",
"modifiedBy": "72057594038779845",
"name": "test aneela1",
"microtenantName": "Default",
"enabled": true,
"link": "aneela.com",
"userPortals": [
{
"id": "145283994705985838",
"modifiedTime": "1747939958",
"creationTime": "1747939958",
"modifiedBy": "72057594038779845",
"name": "test aneela",
"enabled": true,
"domain": "aneela-aneela-com.d.zscalerportal.net",
"userNotificationEnabled": true,
"extDomainTranslation": "aneela.com",
"extLabel": "aneela"
}
]
},
{
"id": "145283994705985863",
"modifiedTime": "1753247856",
"creationTime": "1753247856",
"modifiedBy": "72057594038779845",
"name": "test name",
"microtenantName": "Default",
"enabled": true,
"description": "test description",
"link": "aneela1.com",
"userPortals": [
{
"id": "145283994705985838",
"modifiedTime": "1747939958",
"creationTime": "1747939958",
"modifiedBy": "72057594038779845",
"name": "test aneela",
"enabled": true,
"domain": "aneela-aneela-com.d.zscalerportal.net",
"userNotificationEnabled": true,
"extDomainTranslation": "aneela.com",
"extLabel": "aneela"
}
]
}
]
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details for a Particular User Portal Link
To get details for a particular user portal link:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/userPortalLink/{id}?microtenantId={microtenantId}&page={page}&pagesize={pagesize}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the user portal link.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
- `page`: Specifies the page number.
- `pagesize`: Specifies the page size. If not provided, the default page size is 20. The maximum page size is 500.
For example `/mgmtconfig/v1/admin/customers/{customerId}/userPortalLink/{id}?microtenantId={microtenantId}&page={page}&pagesize={pagesize}`.
- [View an example response](#getPortalLinkResponse)
[]
`{
"id": "145283994705985846",
"modifiedTime": "1748372770",
"creationTime": "1748372770",
"modifiedBy": "72057594038779845",
"name": "test aneela1",
"microtenantName": "Default",
"enabled": true,
"link": "aneela.com",
"userPortals": [
{
"id": "145283994705985838",
"modifiedTime": "1747939958",
"creationTime": "1747939958",
"modifiedBy": "72057594038779845",
"name": "test aneela",
"enabled": true,
"domain": "aneela-aneela-com.d.zscalerportal.net",
"userNotificationEnabled": true,
"extDomainTranslation": "aneela.com",
"extLabel": "aneela"
}
]
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting the User Portal Link Details by User Portal ID
To get details of the user portal link by user portal ID:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/userPortalLink/userPortal/{portalId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `portalId`: The unique identifier of the user portal. To learn more, see [Configuring User Portals Using API](/zpa/configuring-user-portals-using-api).
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/userPortalLink/userPortal/145283994705985838`.
- [View an example response](#getUserPortalLinkByUserPortalResponse)
[]
`{
"totalPages":"1",
"totalCount":"0",
"list":[
{
"id":"145283994705985864",
"modifiedTime":"1756929922",
"creationTime":"1753811234",
"modifiedBy":"72057594038779845",
"name":"aneela.com",
"enabled":true,
"description":"test",
"link":"aneela.com",
"iconText":"data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABcAAAAgCAYAAAD5VeO1AAAHFklEQVR4AbSWe2yWVx3HP+c8T/uWltKWjZYNlkI3YSAMDPcUqDjRjE2Y6BYG20hxCfgHajQSUeOiJoozZkv4Y9lMdFOWLWGIS0TUxBXNNmcibsZyCQWBFZZCL2/79vJensvxe57CP9vfnJzvuf7uv9953tcunz3brW2d6Ta23eE+e1+ba1/8Cbdy0Xy3evEC1750UYaOFYvchlX3uY2rl7pNa5e5hzuWuS8Kj2xY7nbcv8rtfGCN2/Vgu9v9hfVuzxZha4fb86WOszZNU4wx+GYJMc6CM77jWxAEuNRgUqftJDyPhw4yOpckWH9lJmWFWKoEm5CQitE5R5UNsMYCEuaJgdRVtAPj9ykSYrA68XD4Q0eQ8fi1xXpDDVmziBA1q9lkEjyRDm50T+fhtzdnvxa57xlu7rP55iBi66TVKwtFZjK3vPD0BonLLLaZUoOnS+VhttDGGJ0xSaslRlxOMMavDDLYZddp5iJZM8ZfZmTaG9auWsa65Qs58Pyvee7Q68yZt4DpzXdIsdglQkTg8yRJntNIjYdFizA0hFUQyAifOKckpwIi3vjJWeSKQ4wN9XHomX386pnv8fievXzrxz+n86nd4nb4fHk5fKRlHiepxcsyVlUiAqcEe+M/t3gW/YUxLvdd48R7ZxkcHufs2QscO/Iab7z2Mp/f3inrjTiYVCDrvVEezqU++TJeFie68GRWCmxgqQ1DxqTkeiFitJgwv3U2Q4UJGB1hSfEqK0pXcPIs8TnIxPvBgazyRvpZkqVV5RiIKE0inICwatEcclXVNE3LUR1WqUxDqrVvq8+RsymBeHZu6sAo5k68Hvi1DJVWL1Q7bl2zVrFB7sfSnj0gpxfpQqbW5GSdpa5uCo0NdTQ2NtDaeic9pQrxXa3QdjfNs1vFaibjjTfWYa1F7mRQhCFxUJECJ0UN02qY2TyNXC5gSl0dUxun03B7M43NLazftJnHOr/Cp3ftY/2u/Rx44RXCtEKQvQPwxvl3YEyAMaESqgB5bcoDSWqY2TKDe+fNRSYIAYmIIhGHtbXcNmMGd86ZQ1V1PTaolbCUfYdPZjSopTLOy0KJlslkPqQy3akcrQ7Hi2UGVRWlOKSUWGJ5lcSGKEo50/1fGqa3ECUxpUqZ0z1X+N+FXomVGIxmJkfxyGYvHBRiUAWE+nBFZZgYSxkpJ0yUIqISjJeKFCsRtVMbGRsvcubsObq7T9P17inGRvoJbCxZqQShHGjOxAZYY4wODMYEOGuJjKWM5frwBPnhUfL5IYYG8/Re7aNvIM9b73bzxvF3OHrsbf7T3UN1KH/tFFLxG2MAkyXY5896D1DLZl06XaZClEBZ4YpvoKywXB8sZN5MKHTjxRKVKFLia2RUIAkf7zZREry+RKWYBiGxrI6U2ELRMDCeUFBo/Au9lq/Q9XY3H/SNcOnq9QxD+RGaVUVpdS6T7DS6NNU42W3kk6YyjJxUJBXSKCapJJSViGJcw7WJkIGohkJUTWJruHiln/GJiFIp5nLPORpnNFF/e4ukGRKNqQ8tKZFgW+9pm6wIeaBogC49CqWUohRUmEJkasDUUlAVOVNF76WLXDzfQ2OLeCMng1IQs1HcUWqtNRIhtM+tonP7A6xf0kp9XY7QFUlLef2aQqLfxihOiCqyJI5wCt1A34fU1k1lWkMj+/c+SuttKWP9V1C6JBbNFiNuD3v0zR5Gau7kzfd7GVCFFIZHmBgewpoYC1RZizERCP6BJKrv0dFhCqOqnPcvyfmAIC6hNOGMDMLgbsA6/bT94bcvkwt1o+5ApemwOo8m8liduzgmEEN1lVGt51i1Yinr1qzAlYc53+eo6H146U65k2RSDR5Wsm5Zt4nRI1Asx1NZLOu8a5pwxTxZhRULVKlEbVKkWqGp1zdm1oyQ2S0hTz76EFOn6D+LYqKiU+INPvYqKwmz2Ae/fD8bt+/gu794jo3bdrKkfR1zFy5gekMtM6cYyuMDuChPU0PI5fPdNKYf8tIvX+Lgs8/TsfJTtC+8m66Tl/jjP85x/J1zHP37aY6c+DdHut7DHnm9iyOHXmX/17/JwYMvcvh3f+IvXf/kbydPkR/s53Jvnt7LFzlz6lT2wRrJD5NERVIlMY7L8rBIHJUIVFlWFWXTWL+riRBjA4VEDmCwpPLJfwX90ye1DEYhJoxEFICnsIYJlSU+vfoUG2OIP5Y1f+DpQ+y9x99iS+dP2frk93nhN3/ma/tf5BHttz11gM2/P8ETe55l646f8I2nX2HLEz+kbfkOVm7YxZrP7GLugvXUTp9HyTVSTuupUEtsctm3xlmLbTp8itGojpGkiWN/7eZ87xiFco7xchVHPximf7yawZLlwtURuu+Zz3ee3s1dC9fRNGc1/zrxMzY/vJdtnd/mqz94lYce+xGbHz/AuUtX6RG8D9yq9n8AAAD//1Uj1yQAAAAGSURBVAMA7KFWRoEvvM4AAAAASUVORK5CYII=",
"protocol":"https://",
"userPortals":[
{
"id":"145283994705985838",
"modifiedTime":"1753811811",
"creationTime":"1747939958",
"modifiedBy":"72057594038779845",
"name":"test aneela updated 2",
"enabled":true,
"domain":"aneela-aneela-com.d.zscalerportal.net",
"userNotificationEnabled":true,
"extDomainTranslation":"aneela.com",
"extLabel":"aneela",
"extDomain":"aneela.com",
"extDomainName":"aneela-com.d.zscalerportal.net",
"microtenantName":"Default"
}
]
},
{
"id":"145283994705985846",
"modifiedTime":"1748372770",
"creationTime":"1748372770",
"modifiedBy":"72057594038779845",
"name":"test aneela1",
"enabled":true,
"link":"aneela.com",
"userPortals":[
{
"id":"145283994705985838",
"modifiedTime":"1753811811",
"creationTime":"1747939958",
"modifiedBy":"72057594038779845",
"name":"test aneela updated 2",
"enabled":true,
"domain":"aneela-aneela-com.d.zscalerportal.net",
"userNotificationEnabled":true,
"extDomainTranslation":"aneela.com",
"extLabel":"aneela",
"extDomain":"aneela.com",
"extDomainName":"aneela-com.d.zscalerportal.net",
"microtenantName":"Default"
}
]
}
]
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Adding a User Portal Link
To add a user portal link:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/userPortalLink?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/userPortalLink?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following:
- `userPortalId`: The unique identifier of the user portal. To learn more, see [Configuring User Portals Using API](/zpa/configuring-user-portals-using-api).
- `name`: The name of the user portal link.
- `link`: The domain name of IP address for the application link.
- [View the JSON payload](#postJsonPayload)
[]
` {
"enabled":true,
"name":"<example user portal link name>",
"link":"<exampleLink.com>",
"linkPath":"",
"description":"<example optional description>",
"logoFileName":"",
"userPortalId": <user portal ID>
}`
- [View an example JSON payload](#postExampleJsonPayload)
[]
` {
"enabled":true,
"name":"test name 1",
"link":"aneela1.com",
"linkPath":"",
"description":"test description",
"logoFileName":"",
"userPortalId": 145283994705985838
}`
- [View an example response](#postExampleResponse)
[]
` {
"id": "145283994705985874",
"modifiedTime": "1756940241",
"creationTime": "1756940241",
"modifiedBy": "145283994705985860",
"name": "test name 1",
"enabled": true,
"description": "test description",
"link": "aneela1.com"
}`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Adding a List of User Portal Links
To add a list of user portal links:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/userPortalLink/bulk?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/userPortalLink/bulk?microtenantId={microtenantId}`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following:
- `id`: The unique identifier of the user portal. To learn more, see [Configuring User Portals Using API](/zpa/configuring-user-portals-using-api).
- `name`: The name of the user portal link.
- `link`: The domain name of IP address for the application link.
- [View the JSON payload](#bulkPostJsonPayload)
[]
`{
"userPortalLinks":[
{
"enabled":true,
"name":"<example name>",
"link":"<exampleLink.com>",
"linkPath":"",
"description":"<example description>",
"logoFileName":"",
"protocol":""
}
],
"userPortals":[
{
"id":"<user portal ID>"
}
]
}`
- [View an example JSON payload](#bulkPostExampleJsonPayload)
[]
`{
"userPortalLinks":[
{
"enabled":true,
"name":"test name",
"link":"aneela1.com",
"linkPath":"",
"description":"test description",
"logoFileName":"",
"protocol":""
}
],
"userPortals":[
{
"id":"145283994705985838"
}
]
}`
- [View an example response](#bulkPostExampleResponse)
[]
`{
"userPortalLinks":[
{
"id":"145283994705985863",
"name":"test name",
"enabled":true,
"description":"test description",
"link":"aneela1.com",
"userPortals":[
{
"id":"145283994705985838",
"enabled":true
}
]
}
],
"userPortals":[
{
"id":"145283994705985838",
"enabled":true
}
]
}`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a User Portal Link
To update a user portal link:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/userPortalLink/{id}?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the user portal link. To learn more, see [Getting Details of All User Portal Links](#getAll).
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/userPortalLink/145283994705985863?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following:
- `id`: The unique identifier of the user portal. To learn more, see [Configuring User Portals Using API](/zpa/configuring-user-portals-using-api).
- `name`: The name of the user portal link.
- `link`: The domain name of IP address for the application link.
- [View the JSON payload](#putJsonPayload)
[]
`{
"enabled":true,
"id":"145283994705985863",
"modifiedTime":"1753247856",
"creationTime":"1753247856",
"modifiedBy":"72057594038779845",
"name":"<example user portal name>",
"microtenantName":"Default",
"description":"<example description>",
"link":"<exampleLink.com>",
"userPortals":[
{
"id":"<user portal ID>"
}
],
"linkPath":"",
"logoFileName":"",
"protocol":""
}`
- [View an example JSON payload](#putExampleJsonPayload)
[]
`{
"enabled":true,
"id":"145283994705985863",
"modifiedTime":"1753247856",
"creationTime":"1753247856",
"modifiedBy":"72057594038779845",
"name":"test name updated",
"microtenantName":"Default",
"description":"test description",
"link":"aneela1.com",
"userPortals":[
{
"id":"145283994705985838"
}
],
"linkPath":"",
"logoFileName":"",
"protocol":""
}`
A successful response returns code 204, meaning the user portal link is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting a User Portal Link
To delete a user portal link:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/userPortalLink{id}?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the user portal link. To learn more, see [Getting Details of All User Portal Links](#getAll).
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/userPortalLink145283994705985863?microtenantId=0`.
A successful response returns code 204, meaning the user portal link is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Adding Field Descriptions
The following table includes descriptions of available fields you can use for the user portal link use cases:
-
-
| Field | Description | Required | Value |
| ----- | ----------- | -------- | ----- |
| iconText | The logo or favicon for the link | No | String |
| link | The domain name of IP address for the application link | Yes | String |
| linkPath | The specific path for the URL (e.g., entering `/preferences` creates a link pointing to `www.example.com/preferences`) | No | String |
| logoFileName | The name for the logo or favicon | No | String |
| protocol | The protocol for the user portal link. This is only supported for private applications where Browser Access is not enabled. For private applications where Browser Access is enabled, this field defaults to the protocol that was configured in the application segment, and cannot be changed. | No | StringSupported values:`https://``http://` |

## Contents
- **API Developer & Reference Guide**
  - [Getting Started](/zpa/getting-started-zpa-api)
  - [Configuring the Postman REST API Client](/zpa/configuring-postman-rest-api-client)
  - [Understanding Rate Limiting](/zpa/understanding-rate-limiting)
  - [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages)
  - **Reference Guide**
    - [Admin Single Sign-On Management](/zpa/admin-single-sign-management)
    - [API Key Management](/zpa/api-key-management-zpa-api-reference)
    - [Application Segment Management](/zpa/application-segment-management)
    - [Segment Group Management](/zpa/segment-group-management)
    - [AppProtection Control Management](/zpa/appprotection-control-management)
    - [AppProtection Profile Management](/zpa/appprotection-profile-management)
    - [App Connector Management API](/zpa/app-connector-management-api)
    - [App Connector Group Management](/zpa/app-connector-group-management)
    - [Certificate Management](/zpa/certificate-management-api)
    - [Customers](/zpa/customers)
    - [Customer Domain Management](/zpa/customer-domain-management)
    - [Cloud Connector Groups](/zpa/cloud-connector-groups)
    - [Emergency Access User Management](/zpa/emergency-access-user-management)
    - [Enrollment Certificates](/zpa/enrollment-certificates)
    - [Feature Configuration Management](/zpa/feature-configuration-management)
    - [IdP Configurations](/zpa/idp-configurations)
    - [Isolation Profiles](/zpa/isolation-profiles)
    - [Log Streaming Service (LSS) Configuration](/zpa/log-streaming-service-lss-configuration)
    - [Machine Groups](/zpa/machine-groups)
    - [Delegated Tenant Administration](/zpa/delegated-tenant-administration)
    - [Policy Management](/zpa/policy-management)
    - [Posture Profiles](/zpa/posture-profiles)
    - [Private Service Edge Management](/zpa/private-service-edge-management-api)
    - [Private Service Edge Group Management](/zpa/private-service-edge-group-management)
    - [Private Cloud Controller Management](/zpa/private-cloud-controller-management-zpa-api-reference)
    - [Private Cloud Controller Group Management](/zpa/private-cloud-controller-group-management)
    - [Privileged Approval Management](/zpa/privileged-approval-management)
    - [Privileged Console Management](/zpa/privileged-console-management)
    - [Privileged Credential Management](/zpa/privileged-credential-management)
    - [Privileged Portal Management](/zpa/privileged-portal-management)
    - [Provisioning Key Management](/zpa/provisioning-key-management)
    - [SAML Attributes](/zpa/saml-attributes)
    - [SCIM Attributes](/zpa/scim-attributes)
    - [SCIM Groups](/zpa/scim-groups)
    - [Server Management](/zpa/server-management)
    - [Server Group Management](/zpa/server-group-management)
    - [Trusted Networks](/zpa/trusted-networks)
    - [User Portal Management](/zpa/user-portal-management)
    - [User Portal Link Management](/zpa/user-portal-link-management)
    - [Version Profiles](/zpa/version-profiles)
    - [VPN (for Legacy Apps) API](/zpa/vpn-legacy-apps-api)
    - [Zscaler Clouds ](/zpa/zscaler-clouds)
    - [Zscaler Virtual IP Address Range Management](/zpa/zscaler-virtual-ip-address-range-management)
  - **Working with APIs**
    - [Managing Administrators Using API](/zpa/managing-administrators-using-api)
    - [Managing Administrator Roles Using API](/zpa/managing-administrator-roles-using-api)
    - [Managing Admin Single Sign-On Login Configurations Using API](/zpa/managing-admin-single-sign-login-configurations-using-api)
    - [Managing Client Settings Using API](/zpa/managing-client-settings-using-api)
    - [Obtaining Alternative Cloud Domain Details Using API](/zpa/obtaining-alternative-cloud-domain-details-using-api)
    - [Configuring API Keys Using API](/zpa/configuring-api-keys-using-api)
    - [Managing Application Load Balancing and High Availability Using API](/zpa/managing-application-load-balancing-and-high-availability-using-api)
    - [Configuring Application Segments Using API](/zpa/configuring-application-segments-using-api)
    - [Configuring Application Segment Multimatch Using API](/zpa/configuring-application-segment-multimatch-using-api)
    - [Configuring Segment Groups Using API](/zpa/configuring-segment-groups-using-api)
    - [Managing App Connectors Using API](/zpa/managing-app-connectors-using-api)
    - [Configuring Auto Delete for Disconnected App Connectors Using API](/zpa/configuring-auto-delete-disconnected-app-connectors-using-api)
    - [Configuring App Connector Groups Using API](/zpa/configuring-app-connector-groups-using-api)
    - [Configuring Browser Access Application Segments Using API](/zpa/configuring-browser-access-application-segments-using-api)
    - [Configuring Certificates Using API](/zpa/configuring-certificates-using-api)
    - [Obtaining Cloud Connector Group Details Using API](/zpa/obtaining-cloud-connector-group-details-using-api)
    - [Obtaining Customer Details Using API](/zpa/obtaining-customer-details-using-api)
    - [Managing Customer Domains Using API](/zpa/managing-customer-domains-using-api)
    - [Configuring Emergency Access Users Using API](/zpa/configuring-emergency-access-users-using-api)
    - [Obtaining Enrollment Certificate Details Using API](/zpa/obtaining-enrollment-certificate-details-using-api)
    - [Managing Feature Configurations Using API](/zpa/managing-feature-configurations-using-api)
    - [Obtaining IdP Configuration Details Using API](/zpa/obtaining-idp-configuration-details-using-api)
    - [Configuring AppProtection Controls Using API](/zpa/configuring-appprotection-controls-using-api)
    - [Configuring AppProtection Profiles Using API](/zpa/configuring-appprotection-profiles-using-api)
    - [Obtaining Isolation Profile Details Using API](/zpa/obtaining-isolation-profile-details-using-api)
    - [Managing Log Streaming Service Configurations Using API](/zpa/managing-log-streaming-service-configurations-using-api)
    - [Configuring Access Policies Using API](/zpa/configuring-access-policies-using-api)
    - [Configuring AppProtection Policies Using API](/zpa/configuring-appprotection-policies-using-api)
    - [Configuring Client Forwarding Policies Using API](/zpa/configuring-client-forwarding-policies-using-api)
    - [Configuring Isolation Policies Using API](/zpa/configuring-isolation-policies-using-api)
    - [Configuring Privileged Policies Using API](/zpa/configuring-privileged-policies-using-api)
    - [Configuring Redirection Policies Using API](/zpa/configuring-redirection-policies-using-api)
    - [Configuring Timeout Policies Using API](/zpa/configuring-timeout-policies-using-api)
    - [Obtaining Machine Group Details Using API](/zpa/obtaining-machine-group-details-using-api)
    - [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api)
    - [Obtaining Posture Profile Details Using API](/zpa/obtaining-posture-profile-details-using-api)
    - [Configuring Privileged Approvals Using API](/zpa/configuring-privileged-approvals-using-api)
    - [Configuring Privileged Credentials Using API](/zpa/configuring-privileged-credentials-using-api)
    - [Configuring Privileged Consoles Using API](/zpa/configuring-privileged-consoles-using-api)
    - [Configuring Privileged Portals Using API](/zpa/configuring-privileged-portals-using-api)
    - [Configuring Provisioning Keys Using API](/zpa/configuring-provisioning-keys-using-api)
    - [Obtaining SAML Attribute Details Using API](/zpa/obtaining-saml-attribute-details-using-api)
    - [Obtaining SCIM Attribute Details Using API](/zpa/obtaining-scim-attribute-details-using-api)
    - [Obtaining SCIM Group Details Using API](/zpa/obtaining-scim-group-details-using-api)
    - [Configuring Servers Using API](/zpa/configuring-servers-using-api)
    - [Configuring Server Groups Using API](/zpa/configuring-server-groups-using-api)
    - [Managing ZPA Private Service Edges Using API](/zpa/managing-zpa-private-service-edges-using-api)
    - [Configuring ZPA Private Service Edge Groups Using API](/zpa/configuring-zpa-private-service-edge-groups-using-api)
    - [Managing Private Cloud Controllers Using API](/zpa/managing-private-cloud-controllers-using-api)
    - [Managing Private Cloud Controller Groups Using API](/zpa/managing-private-cloud-controller-groups-using-api)
    - [Obtaining VPN (for Legacy Apps) Resources Using API](/zpa/obtaining-vpn-legacy-apps-resources-using-api)
    - [Obtaining Trusted Network Details Using API](/zpa/obtaining-trusted-network-details-using-api)
    - [Obtaining Version Profile Details Using API](/zpa/obtaining-version-profile-details-using-api)
    - [Configuring User Portals Using API](/zpa/configuring-user-portals-using-api)
    - [Configuring User Portal Links Using API](/zpa/configuring-user-portal-links-using-api)
    - [Configuring Zscaler Virtual IP Address Ranges Using API](/zpa/configuring-zscaler-virtual-ip-address-ranges-using-api)