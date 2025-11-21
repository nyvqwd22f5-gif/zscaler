# Managing Feature Configurations Using API
Source: https://help.zscaler.com/zpa/managing-feature-configurations-using-api
PDF: https://help.zscaler.com/pdf/com/en/1530915.pdf

This article provides information on feature configuration use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting).
Getting All Feature Configuration Details
To get all feature configuration details:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/configOverrides`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217316918451765248/configOverrides`.
- [View an example response](#getAllConfigOverridesExample)
[]
`{
"totalPages": "5",
"totalCount": "0",
"list": [
{
"id": "64089",
"customerId": "217316918451765248",
"customerName": "amehta",
"targetType": "feature_flag",
"targetGid": "0",
"configKey": "feature.application.inspect_traffic_with_zia",
"configValue": "enabled",
"configValueInt": "1",
"description": "Indicates if inspection of traffic with ZIA is enabled or not",
"sequence": "142824",
"modifiedTime": "1698080953",
"creationTime": "1698080893",
"modifiedBy": "72057594038609323"
},
{
"id": "78122",
"customerId": "217316918451765248",
"customerName": "amehta",
"targetType": "customer",
"targetGid": "217316918451765248",
"configKey": "config.feature.alt_cloud.enabled",
"configValue": "enabled",
"configValueInt": "1",
"sequence": "182536",
"modifiedTime": "1700187891",
"creationTime": "1700187891",
"modifiedBy": "72057594038623604"
}
]
}
`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Getting a Particular Feature Configuration by ID
To get details of a particular feature configuration by ID:
- Send a GET request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/configOverrides/{id}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identifier of the feature configuration.
For example: `/mgmtconfig/v1/admin/customers/217316918451765248/configOverrides/221321`.
- [View an example response](#getConfigOverrideByIdExample)
[]
`{
"id": "221321",
"customerId": "217316918451765248",
"customerName": "amehta",
"targetType": "feature_flag",
"targetGid": "0",
"configKey": "config.feature.samesite_none",
"configValue": "disabled",
"sequence": "567303",
"modifiedTime": "1753247506",
"creationTime": "1753247506",
"modifiedBy": "72057594038609323"
}
`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Creating a Feature Configuration for a Customer
To create a feature configuration for a customer:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/configOverrides/`.
- Provide the `customerId`, the ZPA tenant ID of the customer, in the request endpoint. For example: `/mgmtconfig/v1/admin/customers/217316918451765248/configOverrides/`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Provide the following JSON payload and include the following details:
- `configKey`: The key for the feature configuration. The supported values are:
- `config.feature.samesite_none`: Refers to the SameSite Cookie Attribute option when [configuring authentication settings](/zpa/configuring-authentication-settings) in ZPA.
- `config.feature.cors_enabled`: Refers to the CORS Request option when [configuring authentication settings](/zpa/configuring-authentication-settings) in ZPA.
- `configValue`: Indicates if the feature configuration is enabled (`true`) or disabled (`false`).
- `customerId`: The ZPA tenant ID of the customer.
- `targetType`: Indicates the target type of the feature configuration. The supported value is `"feature_flag"`.
- [View the JSON payload](#createConfigOverridePayload)
[]
`{
"customerId": <customer ID>,
"targetType": "string",
"configKey": "string",
"configValue": "string"
}
`
- [View an example JSON payload](#createConfigOverrideSamplePayload)
[]
` {
"customerId": 217316918451765248,
"targetType": "feature_flag",
"configKey": "config.feature.samesite_none",
"configValue": "disabled"
}
`
- [View an example response](#createConfigOverrideExampleResponse)
[]
` {
"id": "221321",
"customerId": "217316918451765248",
"targetType": "feature_flag",
"targetGid": "0",
"configKey": "config.feature.samesite_none",
"configValue": "disabled",
"modifiedTime": "1753247506",
"creationTime": "1753247506",
"modifiedBy": "72057594038609323"
}
`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Updating a Feature Configuration for a Customer
To update a feature configuration override for a customer:
- Send a `PUT` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/configOverrides/{id}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `id`: The unique identiifer of the feature configuration.
For example: `/mgmtconfig/v1/admin/customers/217316918451765248/configOverrides/221321`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Provide the following JSON payload and include the following details:
- `configKey`: The key for the feature configuration. The supported values are:
- `config.feature.samesite_none`: Refers to the SameSite Cookie Attribute option when [configuring authentication settings](/zpa/configuring-authentication-settings) in ZPA.
- `config.feature.cors_enabled`: Refers to the CORS Request option when [configuring authentication settings](/zpa/configuring-authentication-settings) in ZPA.
- `configValue`: Indicates if the feature configuration is enabled (`true`) or disabled (`false`).
- `customerId`: The ZPA tenant ID of the customer.
- `targetType`: Indicates the target type of the feature configuration. The supported value is `"feature_flag"`.
- [View the JSON payload](#updateConfigOverridePayload)
[]
` {
"customerId": <customer ID>,
"targetType": "string",
"configKey": "string",
"configValue": "string"
}`
- [View an example JSON payload](#updateConfigOverrideExamplePayload)
[]
` {
"customerId": 217316918451765248,
"targetType": "feature_flag",
"targetGid": 0,
"configKey": "config.feature.samesite_none",
"configValue": "enabled"
}
`
- [View an example response](#updateConfigOverrideExampleResponse)
[]
` {
"id": "221321",
"customerId": "217316918451765248",
"targetType": "feature_flag",
"targetGid": "0",
"configKey": "config.feature.samesite_none",
"configValue": "enabled",
"sequence": "567303",
"modifiedTime": "1753247506",
"creationTime": "1753247506",
"modifiedBy": "72057594038609323"
}
`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).