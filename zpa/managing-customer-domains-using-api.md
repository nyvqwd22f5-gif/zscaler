# Managing Customer Domains Using API
Source: https://help.zscaler.com/zpa/managing-customer-domains-using-api
PDF: https://help.zscaler.com/pdf/com/en/1531044.pdf

This article provides information on Zscaler Private Access (ZPA) customer domain use cases using APIs. All APIs are rate limited. To learn more, see [Understanding Rate Limiting](/zpa/understanding-rate-limiting) and [Adding DNS Search Domains](/zpa/adding-dns-search-domains).
Getting All Domains for a Customer
To get all domains for a customer:
- Send a `GET` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/v2/associationtype/{type}/domains?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `type`: The association type of the domain. You must pass `SEARCH_SUFFIX` as the value for `type` to retrieve details of DNS search domains.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/v2/associationtype/SEARCH_SUFFIX/domains?microtenantId=0`.
- [View an example response](#getDomainsExample)
[]
`[
{
"id": "24493",
"modifiedTime": "1753246146",
"creationTime": "1753246146",
"modifiedBy": "72057594038609323",
"domain": "beta.co",
"associationType": "SEARCH_SUFFIX",
"capture": true,
"name": "beta.co"
}
]`
A successful response returns code 200. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).
Creating or Updating a Domain for a Customer
To create or update a domain for a customer:
- Send a `POST` request to the following endpoint: `/mgmtconfig/v1/admin/customers/{customerId}/v2/associationtype/{type}/domains?microtenantId={microtenantId}`.
-
Provide the following in the request endpoint:
- `customerId`: The ZPA tenant ID of the customer.
- `type`: The association type of the domain. You must pass `SEARCH_SUFFIX` as the value for `type` to create a DNS search domain.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
For example: `/mgmtconfig/v1/admin/customers/72057594037927936/v2/associationtype/SEARCH_SUFFIX/domains?microtenantId=0`.
- Include the request headers to provide information about the request context:
- Content-Type: `application/json`
- Authorization: `Bearer <access_token>`
- Provide the following JSON payload and include the following details:
- `assocationType`: The association type of the domain. You must pass `SEARCH_SUFFIX` to create a DNS search domain.
- `domain`: The domain of the customer.
- `name`: The name of the customer.
- `microtenantId`: The unique identifier of the Microtenant. If you are within a Microtenant, you must pass the `microtenantId` field when making an API call to retrieve data from that Microtenant. The `microtenantId` can be obtained from the [API Keys](/zpa/about-api-key-management) page, or can be obtained programmatically using the ZPA cloud service API. Access to certain operations is limited when you are within a Microtenant. If you are within the Default Microtenant, pass `microtenantId` as `0` when making requests to retrieve data from the Default Microtenant. If the `microtenantId` is not passed in the request when creating or updating a resource, then the resource is created or updated in the Default Microtenant. To learn more, see [Configuring Microtenants Using API](/zpa/configuring-microtenants-using-api).
- [View the JSON payload](#createUpdateDomainPayload)
[]
`[
{
"associationType": "SEARCH_SUFFIX",
"capture": true,
"domain": "string",
"name": "<name>",
"microtenantId": <microtenant ID>
}
]`
- [View the sample JSON payload](#createUpdateDomainSamplePayload)
[]
`[
{
"microtenantId": 0,
"domain": "beta.co",
"associationType": "SEARCH_SUFFIX",
"capture": true,
"name": "beta.co"
}
]`
A successful response returns code 204, meaning the domain is created or updated. To learn more, see [API Response Codes and Error Messages](/zpa/api-response-codes-and-error-messages).