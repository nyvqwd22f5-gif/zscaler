# Configuring User Portals Using API
Source: https://help.zscaler.com/zpa/configuring-user-portals-using-api
PDF: https://help.zscaler.com/pdf/com/en/1530947.pdf

This article provides information on managing Zscaler Private Access (ZPA) user portal use cases using APIs. All APIs are rate limited. To learn more, see [About User Portals](/zpa/about-user-portals) and [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Prerequisite API Call
Before you create or update a user portal, you must get the certificate ID. To learn more, see [Configuring Certificates Using API](/zpa/configuring-certificates-using-api).
Creating a User Portal
To create a user portal:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/userPortal?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/userPortal?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following:
- `managedByZs`: Indicates if the certificate type is Managed (`true`) or Custom (`false`).
-
`domain`: Enter the full URL for the portal. This is the URL that users access to view the portal. The URL must use the HTTPS protocol and be a fully qualified domain name (FQDN). A user portal's FQDN cannot be configured as an application within an application segment.
The `domain` field is only required if `managedByZs` is set to `false`.
-
`certificateId`: The unique identifier of the certificate. To learn more, see [Configuring Certificates Using API](/zpa/configuring-certificates-using-api).
The `certificateId` field is only required if `managedByZs` is set to `false`.
- `enabled`: Indicates if the user portal is enabled (`true`) or disabled (`false`). If disabled, the portal is inaccessible to users.
- `name`: The name of the user portal.
- `extLabel`: The authentication domain name prefix used for the portal URL. The supported string can include integers, lowercase characters, and hyphens (-). This field supports integers between 3 and 31. For example, `server-2`.
- `extDomain`: The authentication domain name prefix used for a Zscaler-managed certificates when [creating a privileged portal](/zpa/configuring-privileged-portals). If you are using Zscaler-managed certificates and pass the external domain name prefix, the `certificateId` field becomes null. Periods (.) are not supported since the FQDN includes a period as part of the suffix or top-level domain.
- [View the JSON payload](#createUserPortalPayload)
[]
`{
"enabled":true,
"name":"<example name>",
"certManagedByZsRadio":"<string>",
"domain":"<string>",
"description":"<example description>",
"userNotificationEnabled":true,
"userNotification":"<example user notification>",
"certificateId":"<certificate ID>",
"managedByZs":true,
"extLabel":"<string>",
"extDomain":"<string>"
}`
- [View an example JSON payload](#createUserPortalSamplePayload)
[]
`{
"enabled":true,
"name":"userportal name",
"certManagedByZsRadio":"managed",
"domain":"",
"description":"test description",
"userNotificationEnabled":true,
"userNotification":"test message text",
"certificateId":"",
"managedByZs":true,
"extLabel":"portalurl",
"extDomain":"aneela.com"
}`
- [View an example response](#createUserPortalExampleResponse)
[]
`{
"id":"145283994705985862",
"modifiedTime":"1753247369",
"creationTime":"1753247369",
"modifiedBy":"72057594038779845",
"name":"userportal name",
"enabled":true,
"description":"test description",
"domain":"portalurl-aneela-com.d.zscalerportal.net",
"userNotification":"test message text",
"userNotificationEnabled":true,
"extDomainTranslation":"aneela.com",
"extLabel":"portalurl",
"extDomain":"aneela.com"
}`
A successful response returns code 201. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of All User Portals
To get details of all user portals for a given customer:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/userPortal/?microtenantId={microtenantId}&page={page}&pagesize={pageSize}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
- `page`: Specifies the page number.
- `pagesize`: Specifies the page size. If not provided, the default page size is 20. The maximum page size is 500.
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/userPortal/?microtenantId=0&page=1&pagesize=20`.
- [View an example response](#getAllUserPortalsResponse)
[]
`{
"totalPages": "1",
"totalCount": "1",
"list": [
{
"id": "145283994705985838",
"modifiedTime": "1747939958",
"creationTime": "1747939958",
"modifiedBy": "72057594038779845",
"name": "test user portal",
"scopeName": "Default",
"enabled": true,
"domain": "aneela-aneela-com.d.zscalerportal.net",
"userNotificationEnabled": true,
"extDomainTranslation": "aneela.com",
"extLabel": "aneela",
"extDomain": "aneela.com",
"extDomainName": "aneela-com.d.zscalerportal.net"
}
]
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting Details of a Particular User Portal
To get details of a particular user portal:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/userPortal/{id}?microtenantId={microtenantId}&page={page}&pagesize={pageSize}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the user portal.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
- `page`: Specifies the page number.
- `pagesize`: Specifies the page size. If not provided, the default page size is 20. The maximum page size is 500.
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/userPortal/145283994705985862?microtenantId=0&page=1&pagesize=20`.
- [View an example response](#getUserPortalDetailsResponse)
[]
`{
"id": "145283994705985862",
"modifiedTime": "1753247369",
"creationTime": "1753247369",
"modifiedBy": "72057594038779845",
"name": "userportal name",
"scopeName": "Default",
"enabled": true,
"description": "test description",
"domain": "portalurl-aneela-com.d.zscalerportal.net",
"userNotification": "test message text",
"userNotificationEnabled": true,
"extDomainTranslation": "aneela.com",
"extLabel": "portalurl",
"extDomain": "aneela.com",
"extDomainName": "aneela-com.d.zscalerportal.net"
}`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a User Portal
To update a user portal:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/userPortal/{Id}?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the user portal.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/userPortal/145283994705985862?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Use the following JSON payload and provide the following:
- `managedByZs`: Indicates if the certificate type is Managed (`true`) or Custom (`false`).
-
`domain`: Enter the full URL for the portal. This is the URL that users access to view the portal. The URL must use the HTTPS protocol and be a fully qualified domain name (FQDN). A user portal's FQDN cannot be configured as an application within an application segment.
The `domain` field is only required if `managedByZs` is set to `false`.
-
`certificateId`: The unique identifier of the certificate. To learn more, see [Configuring Certificates Using API](/zpa/configuring-certificates-using-api).
The `certificateId` field is only required if `managedByZs` is set to `false`.
- `enabled`: Indicates if the user portal is enabled (`true`) or disabled (`false`). If disabled, the portal is inaccessible to users.
- `name`: The name of the user portal.
- `extLabel`: The authentication domain name prefix used for the portal URL. The supported string can include integers, lowercase characters, and hyphens (-). This field supports integers between 3 and 31. For example, `server-2`.
- `extDomain`: The authentication domain name prefix used for a Zscaler-managed certificates when [creating a privileged portal](/zpa/configuring-privileged-portals). If you are using Zscaler-managed certificates and pass the external domain name prefix, the `certificateId` field becomes null. Periods (.) are not supported since the FQDN includes a period as part of the suffix or top-level domain.
- [View the JSON payload](#updateUserPortalPayload)
[]
`{
"enabled":true,
"id":"<id>",
"objectType":"UserPortals",
"action":"EDIT",
"modifiedTime":"1753247369",
"creationTime":"1753247369",
"modifiedBy":"72057594038779845",
"name":"<example user portal name>",
"scopeName":"Default",
"description":"<example description>",
"domain":"",
"userNotification":"<example user notification>",
"userNotificationEnabled":true,
"extDomainTranslation":"aneela.com",
"extLabel":"portalurl",
"extDomain":"aneela.com",
"extDomainName":"aneela-com.d.zscalerportal.net",
"hideInfoTooltip":true,
"restrictedEntity":false,
"certManagedByZsRadio":"managed",
"certificateId":"",
"managedByZs":true
}`
- [View an example JSON payload](#updateUserPortalExamplePayload)
[]
`{
"enabled":true,
"id":"145283994705985862",
"objectType":"UserPortals",
"action":"EDIT",
"modifiedTime":"1753247369",
"creationTime":"1753247369",
"modifiedBy":"72057594038779845",
"name":"userportal name updated",
"scopeName":"Default",
"description":"test description updated",
"domain":"",
"userNotification":"test message text updated",
"userNotificationEnabled":true,
"extDomainTranslation":"aneela.com",
"extLabel":"portalurl",
"extDomain":"aneela.com",
"extDomainName":"aneela-com.d.zscalerportal.net",
"hideInfoTooltip":true,
"restrictedEntity":false,
"certManagedByZsRadio":"managed",
"certificateId":"",
"managedByZs":true
}`
A successful response returns code 204, meaning the user portal is updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Deleting a User Portal
To delete a user portal:
- Send a `DELETE` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/userPortal/{Id}?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the user portal.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the API Keys page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/145283994705985536/userPortal/145283994705985862?microtenantId=0`.
A successful response returns code 204, meaning the user portal is deleted. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).